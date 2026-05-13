---
tags: [motion_capture, collision_avoidance, human-human_interaction, motion_analysis]
title: "Exploiting Motion Capture to Enhance Avoidance Behaviour in Games"
authors: Ben J. H. van Basten, Sander E. M. Jansen, Ioannis Karamouzas 
year: 2009
url:  
citekey: BastenMotionCapture2009 
aliases: "Exploiting Motion Capture to Enhance Avoidance Behaviour in Games"
created: 
modified:
---
zoteroLink: [Full Text PDF](zotero://select/groups/6528517/items/IIY8UAP8)
relations: 

> [!abstract]-
> Realistic simulation of interacting virtual characters is essential in computer games, training and simulation applications. The problem is very challenging since people are accustomed to real-world situations and thus, they can easily detect inconsistencies and artifacts in the simulations. Over the past twenty years several models have been proposed for simulating individuals, groups and crowds of characters. However, little effort has been made to actually understand how humans solve interactions and avoid inter-collisions in real-life. In this paper, we exploit motion capture data to gain more insights into human-human interactions. We propose four measures to describe the collision-avoidance behavior. Based on these measures, we extract simple rules that can be applied on top of existing agent and force based approaches, increasing the realism of the resulting simulations.

%% begin persistent data %% 
# @BastenMotionCapture2009
## 🟠1st Pass
### 1. Context

Comparison of gender and height differences. 

They look into anticipation and hesitation when walking towards one another. They look at overall speed of the interaction, and whether they walk further apart or collide with one another. 

Shows that MM give the widest berth, FM give the medium, and FF have the closest paths when navigating around each other. 

People also give less space to short people, and more space to tall people. 

### 2. Correctness

### 3. Contributions

 %% end persistent data %%
# ⭐Interesting Points

[[@BastenMotionCapture2009]] ([Page 3](zotero://open-pdf/groups/6528517/items/IIY8UAP8?page=31&annotation=QE2LZ79R))
> Reciprocal Velocity Obstacle for local navigation 

[[@BastenMotionCapture2009]] ([Page 3](zotero://open-pdf/groups/6528517/items/IIY8UAP8?page=31&annotation=5B9NJKS5))
> . The idea here is that each character adapts its velocity in order to avoid collisions with other characters as well as with the environment. 

[[@BastenMotionCapture2009]] ([Page 5](zotero://open-pdf/groups/6528517/items/IIY8UAP8?page=33&annotation=5R8LJHCS))
> This is investigated by comparing 4 different measures: collaboration, clearance, anticipation and synchronisation. 

[[@BastenMotionCapture2009]] ([Page 6](zotero://open-pdf/groups/6528517/items/IIY8UAP8?page=34&annotation=6MXEBMXD))
> Collaboration = 1 − |d1 − d2|  max(d1, d2) 

[[@BastenMotionCapture2009]] ([Page 6](zotero://open-pdf/groups/6528517/items/IIY8UAP8?page=34&annotation=A696US2Z))
> Clearance = min{dist(m1, m2) : m1 ∈ M1, m2 ∈ M2} 

[[@BastenMotionCapture2009]] ([Page 6](zotero://open-pdf/groups/6528517/items/IIY8UAP8?page=34&annotation=GKWFKXZP))
> Anticipation deals with the position at the moment of deviation. 

[[@BastenMotionCapture2009]] ([Page 6](zotero://open-pdf/groups/6528517/items/IIY8UAP8?page=34&annotation=Q8U8JWGQ))
> Note that collaboration is determined by lateral clearance, whereas anticipation deals with frontal clearance. 

[[@BastenMotionCapture2009]] ([Page 7](zotero://open-pdf/groups/6528517/items/IIY8UAP8?page=35&annotation=V4RGM8JX))
> the avoidance behaviour of the participants to be synchronized when they both start deviating at the same time. 

Note ([Page 8](zotero://open-pdf/groups/6528517/items/IIY8UAP8?page=36&annotation=CNXM2XMY))
- Gender and height have a significant effect on peoples anticipation of space, and when determining when to deviate from the current path in order to avoid a collision

%% Import Date: 2026-04-27T17:14:54.719+01:00 %%
