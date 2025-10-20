# Challenge-5
## Description
This document explains the modifications made to the PlayerMovement.cs script to implement jumping and sprinting mechanics for the player character.

<br>

## Jump

### Added fields

These fields control jump height, gravity strength, the CharacterController component, and internal variables required for jumping.

### Input method

This method detects when the player presses the jump button.

### Logic in Update()

Inside the Update() method, gravity and jump handling were added

<br>

## Sprint

### Added Fields

These fields define the sprint speed multiplier and a flag to check if the player is currently sprinting.

### Input Method

This detects when the player holds down the sprint button.

### Modification in Update()

The line that creates the movement vector was replaced with

### Input system Map
