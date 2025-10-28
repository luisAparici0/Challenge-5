# Challenge-5
## Description
This document explains the modifications made to the PlayerMovement.cs script to implement jumping and sprinting mechanics for the player character.

<br>

## Awake 
<img width="500" alt="awake method" src="https://github.com/luisAparici0/Challenge-5/blob/main/images/awakeMethod.png" />

Initialize the variables controller, which will be used to determine whether the player is on the ground, and playerInput, which will be used to determine whether the player is running.

<br>


## Jump

### Added fields
<img width="500" alt="jump fields" src="https://github.com/luisAparici0/Challenge-5/blob/main/images/jumpFields.png" />


### Input method
A jump is only queued if Space is pressed while grounded (no buffering while airborne):

<img width="500" alt="jump method" src="https://github.com/luisAparici0/Challenge-5/blob/main/images/jumpMethod.png" />

### Modification in Update()
Gravity and vertical motion handling; consume the queued jump:

<img width="500" alt="jump logic" src="https://github.com/luisAparici0/Challenge-5/blob/main/images/jumpUpdate.png" />

Effect: Pressing Space repeatedly in the air will not trigger a jump upon landing.

<br>

## Sprint

### Added Fields
<img width="500" alt="sprint fields" src="https://github.com/luisAparici0/Challenge-5/blob/main/images/sprintFields.png" />
<img width="500" alt="sprint fields" src="https://github.com/luisAparici0/Challenge-5/blob/main/images/sprintFields2.png" />

### Input Method
<img width="500" alt="sprint method" src="https://github.com/luisAparici0/Challenge-5/blob/main/images/sprintMethod.png" />

### Modification in Update()

Each frame, query the Sprint action so sprint is true only while Shift is held, regardless of interactions like Press Only:

<img width="500" alt="sprint logic" src="https://github.com/luisAparici0/Challenge-5/blob/main/images/sprintUpdate.png" />
<img width="500" alt="sprint logic" src="https://github.com/luisAparici0/Challenge-5/blob/main/images/sprintUpdate2.png" />

Effect: The character moves faster only while Shift is held. Releasing Shift immediately restores normal speed.

### Input system Map
<img width="500" alt="input system map" src="https://github.com/luisAparici0/Challenge-5/blob/main/images/inputSystemMap.png" />

<br>

##Jump Control Player Input
<img width="662" height="532" alt="Jump Control" src="https://github.com/user-attachments/assets/1d00686b-b7f8-4412-ae60-f8ea5283b01f" />

##Sprint Control Player Input
<img width="664" height="526" alt="Sprint Control" src="https://github.com/user-attachments/assets/98da5c14-aa22-48d9-a4eb-38f612e95ffa" />

###Rigidbody
<img width="531" height="332" alt="Rigidbody Inspector" src="https://github.com/user-attachments/assets/7e64e9ff-ec3a-4e6c-8fd0-af39951d6a06" />

###Script
<img width="1329" height="787" alt="PlayerMovement C# Script 1" src="https://github.com/user-attachments/assets/6e85e09d-2426-4f72-9ac5-be7b9f637540" />

<img width="1536" height="485" alt="PlayerMovement C# Script 2" src="https://github.com/user-attachments/assets/d6f5093b-2016-4cd0-b4e2-7d536bbb6d27" />


<img width="680" height="691" alt="PlayerShooting C# Script" src="https://github.com/user-attachments/assets/7f2b7c03-9588-4cd2-8c13-8c1f8e89e40b" />




# Challenge 3

## Description
This project recreates an **Aztec pyramid (Templo Mayor)** on a terrain with different textures and natural elements.

## Terrain Development Process

We are tasked to recreate the main temple of capital city of ancient Tenōchtitlan, now known as Mexico City.  First, Pro-Builder package and Terrain Tools are downloaded to proceed.  Use Pro-Builder to create a plane that will act as the first level of the structure.  Modify position of created plane to (0,0,0) and modify the dimensions in x and z direction to 120 and 100, respectively.  Next, subdivide all faces pointing in the y-direction twice and move vertices in the orientation presented on the following image.  
<br><br>



*Base Plane Vertices*

Merge the faces presented in the following image and extrude them at a distance of 15.  Afterwards, translate vertices from bottom of extruded surface edges to the outer edge of the created plane using the Vertex Position Editor offered by Pro-Builder.  



Then, grab vertices close to plane edges in x direction and distance one segment at x = 55 and -55.  Take the other un-modified segments and set their distance in x-position to x = 50 and -50.  This is done for our future copies of the structures.  




Next step, manipulate vertices for the front face of the structure to angle edges similar to the edges as shown in the figure.  Finally, delete any remaining faces in non-extruded segments in the plane.  (Does not include vertices translation-induced extrude.  Angle of edges in the x-positions have a distance between upper and lower vertices of 5 and in z-positions of 7.5.



<br>
<br>
 

Base level had its scaling values increased by 1.2 and 1.3 for *x* and *z*, respectively.  The second level remains at a 1,1,1 scale for all axis,  reduce x and z-scaling values by 0.2 and 0.25, respectively.  Afterwards, modify x-position of west and east edge vertices to align with bottom vertices of lower level.  Then modify the other set of vertices in current level to be at a distance 5 from the outer vertices.  (Include photo).  Do this for all levels.










