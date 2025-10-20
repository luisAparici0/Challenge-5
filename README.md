# Challenge-5
## Description
This document explains the modifications made to the PlayerMovement.cs script to implement jumping and sprinting mechanics for the player character.

<br>

## Jump

### Added fields
<img width="500" alt="jump fields" src="https://github.com/user-attachments/images/jumpFields.png" />
These fields control jump height, gravity strength, the CharacterController component, and internal variables required for jumping.

### Input method
<img width="500" alt="jump method" src="https://github.com/user-attachments/images/jumpMethod.png" />
This method detects when the player presses the jump button.

### Logic in Update()
<img width="500" alt="jump logic" src="https://github.com/user-attachments/images/jumpUpdate.png" />
Inside the Update() method, gravity and jump handling were added

<br>

## Sprint

### Added Fields
<img width="500" alt="sprint fields" src="https://github.com/user-attachments/images/sprintFields.png" />
These fields define the sprint speed multiplier and a flag to check if the player is currently sprinting.

### Input Method
<img width="500" alt="sprint method" src="https://github.com/user-attachments/images/sprintMethod.png" />
This detects when the player holds down the sprint button.

### Modification in Update()
<img width="500" alt="sprint logic" src="https://github.com/user-attachments/images/sprintUpdate.png" />
The line that creates the movement vector was replaced with

### Input system Map
<img width="500" alt="input system map" src="https://github.com/user-attachments/images/inputSystemMap.png" />
