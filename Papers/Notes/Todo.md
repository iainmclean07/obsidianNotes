
Development

- [ ] Development of passthrough controls
	- [ ] UI 
		- [x] Passthrough view / tab with all controls related to enabling disabling passthrough
			- [x] All passthrough
			- [x] single client passthrough
		- [x] Avatar controls
			- [x] Disable specific avatars for specific people
				- [x] Matrix of controls P1 -> P4 enabling and disabling of avatars 
					- [ ] Make dynamic with Bernard changes
						- [ ] Ensure that buttons map to the correct players
						- [ ] Understand the toggleMatrixGenerator script
							- [ ] Read through current code
							- [ ] Rewrite avatarToggle code to work with specific dynamically generated toggles
							- [ ] Add in the source and the target identification on the toggles
							- [ ] 
	- [ ] Logic
		- [x] Common bootstrap
			- [x] Avatar controller used on server and client
			- [x] Passthrough controller used on server and client
		- [x] Client only
			- [x] "Toggle" controls
				- [x] Enabling and disabling passthrough view on each headset
				- [x] Enabling and disabling the visible environment and disabling the skybox
		- [x] Server only
			- [ ] UI controls
			- [x] Server controls RPC methods
				- [x] Run on all client methods (enable disable passthrough for all)
				- [x] Run on specific clients for enabling / disabling avatars, passthrough
		- [ ] Image Scriptable Objects
			- [ ] Select the mesh renderers
			- [ ] Find out why it doesn't spawn on the client side


Writing

- [ ] Introduction
	- [ ] Contributions
		- [ ] Open Dataset with activity indicators
		- [ ] Proxemic analysis with chi squared test
		- [ ] Navigation and locomotory ability (clearance distances, avoidance behaviours e.g hesitation, crossing paths and frontal collisions)
		- [ ] Collision awareness? new metric? Gait analysis
- [ ] Related Work
	- [ ] Social XR
	- [ ] Proxemics
		- [ ] Read Virtual Proxemics: Locomotion in the Presence of Obstacles in Large Immersive Projection Environments
		- [ ] 
	- [ ] What is Hybrid Reality
	- [ ] Research Questions
- [ ] Evaluation
	- [ ] Experimental Design
		- [ ] Conditions
		- [ ] Experimental Task
	- [ ] Physical and Virtual Environments
	- [ ] Hardware and Software Setup
	- [ ] Experimental Procedure
	- [ ] Measures and Analysis Techniques
	- [ ] Participants
- [ ] Results
- [ ] Discussion
- [ ] Conclusion




PRE EXPERIMENT WEEK
- Test that the implementation works
	- Do avatars load
	- Do users join the vivox server
	- Does the passthrough controls work
	- Do the image sets spawn
	- Are the images grabbable
	- Do the images freeze against the whiteboard
	- Is muting required?
	- Does the data come into psi ok?
	- Do the avatars disappear for the correct clients?
	- 