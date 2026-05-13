Toggles for passthrough mode to make sure you know who is in the passthrough mode and is easy to switch on and off.

NEED TO HAVE

Disable the remote avatars for a specific player
- build a control that allows for e.g P1 to have P2 avatar disabled but P3 is still visible.

Short answer: you don’t directly “access what a player sees” from the server in Unity networking. Instead, you control **networked avatar GameObjects** and synchronize their visibility/state across clients using RPCs or synced variables. With **Meta Avatars SDK**, it works the same way conceptually, but there are a couple of gotchas.

---

## 1. Key idea: server controls state, clients render avatars

Each player’s avatar is usually a **networked object** (e.g., `NetworkObject` in Netcode for GameObjects or a `NetworkIdentity` in Mirror).

- The **server** decides _who should be visible_
    
- The **clients** actually enable/disable rendering
    

So instead of “getting visible avatars from server,” you:

1. Track avatars on the server
    
2. Send instructions (RPCs or synced vars)
    
3. Clients apply visibility changes locally
    

---

## 2. Basic pattern using RPC (Netcode example)

### Step A: Networked avatar script

```csharp
using Unity.Netcode;
using UnityEngine;

public class NetworkAvatar : NetworkBehaviour
{
    [SerializeField] private GameObject avatarVisual;

    [ClientRpc]
    public void SetVisibleClientRpc(bool visible)
    {
        avatarVisual.SetActive(visible);
    }
}
```

---

### Step B: Server toggles visibility

```csharp
public void SetAvatarVisibility(NetworkAvatar avatar, bool visible)
{
    if (!IsServer) return;

    avatar.SetVisibleClientRpc(visible);
}
```

---

## 3. Making avatars visible/invisible per player

If you want **per-player visibility** (e.g., only Player A sees Player B):

Use **ClientRpcParams**:

```csharp
public void SetVisibilityForClient(NetworkAvatar avatar, ulong clientId, bool visible)
{
    var rpcParams = new ClientRpcParams
    {
        Send = new ClientRpcSendParams
        {
            TargetClientIds = new ulong[] { clientId }
        }
    };

    avatar.SetVisibleClientRpc(visible, rpcParams);
}
```

---

## 4. Alternative: use NetworkVariables (often cleaner)

Instead of RPC spam, use a synced variable:

```csharp
public NetworkVariable<bool> isVisible = new NetworkVariable<bool>(true);

void OnEnable()
{
    isVisible.OnValueChanged += OnVisibilityChanged;
}

void OnVisibilityChanged(bool oldVal, bool newVal)
{
    avatarVisual.SetActive(newVal);
}
```

Server updates:

```csharp
avatar.isVisible.Value = false;
```

---

## 5. Meta Avatars specific notes

With **Meta Avatars SDK**:

- The avatar is usually rendered via `OvrAvatarEntity`
    
- Simply disabling the GameObject works, BUT:
    
    - You may also want to stop streaming pose data
        
    - Or disable mesh rendering only
        

Example:

```csharp
avatarEntity.gameObject.SetActive(false);
```

or better (keeps network alive but hides visuals):

```csharp
avatarEntity.Renderer.enabled = false;
```

---

## 6. Important limitation (this trips people up)

The server **does NOT know what is actually rendered on a client**.

So:

- You cannot query: “which avatars are visible to Player X?”
    
- You must **track that logic yourself on the server**
    

Example:

```csharp
Dictionary<ulong, HashSet<ulong>> visibilityMap;
```

---

## 7. Common use cases

### Hide distant players

Server calculates distance:

```csharp
if (distance > maxRange)
    avatar.SetVisibleClientRpc(false);
```

### Stealth / invisibility mechanic

Server decides:

```csharp
if (isInvisible)
    avatar.SetVisibleClientRpc(false);
```

### Performance culling

Only send avatars to nearby players

---

## 8. Best practice

- Use **server-authoritative logic**
    
- Prefer **NetworkVariables** for persistent state
    
- Use **RPCs for one-time events**
    
- Don’t rely on client-side hiding for gameplay-critical logic
    

---

If you tell me which networking system you're using (NGO, Mirror, Photon, etc.), I can give a more exact implementation tailored to your setup.