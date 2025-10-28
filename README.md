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




# Challenge 5

## Description
This document explains the modifications made to the PlayerMovement.cs script to implement jumping and sprinting actions for the player character, as well as its implementation using visual graphs.  

## Player Input Additions

Our player movement, rotation and firing actions were created and executed in class using the Input System Package.  In addition to these actions, we are tasked add a jump and sprint action for our player.  These can be implement by first creating our Actions in the created Input Action Asset.  First we'll add the 'Jump' action and set its 'Action Type' to 'Button'.  Next, create the 'Sprint' action with 'Action Type' as 'Button'.  We want to our action to send an input when the button is released to indicate the user stopped holding the sprint button.  This can be done by adding in the 'Interaction' tab a 'Press' interaction and change the 'Trigger Behavior' to 'Press and Release'.   

<img width="662" height="532" alt="Jump Control" src="https://github.com/user-attachments/assets/afaac2d4-5346-4ebb-b4de-9155cd73d10c" />
<br>
<br>
<img width="664" height="526" alt="Sprint Control" src="https://github.com/user-attachments/assets/44ec12a3-7d44-4d6a-8901-9d8f1c76a105" />


Both of these can be easily implemented with the new Input System Package messages OnJump() and OnSprint(), which don't require additional coding to set up as opposed to custom events. 
<br><br>

Next, we'll assign a 'Rigidbody' component to our character to implement physics.  This will allow us to use the 'Gravity' parameter to simulate jumping.  Make sure your player model and environment objects have colliders so that your character doesn't fall through them after applying the Rigidbody.  Finally, freeze rotation of our player in the 'x' and 'z' direction to ensure our model doesn't tip over when interacting with colliders in the game.  


<br>
<img width="531" height="332" alt="Rigidbody Inspector" src="https://github.com/user-attachments/assets/802aeb56-8199-4a35-9c92-9f05c5ea6425" />
<br>
<br>


###C# Script

Then, we'll go to our 'PlayerMovement' script and do the following:
<br>

1. Create 'private float height' and apply [SerializeField]  
2. Create 'public void OnJump() and have its parameter be 'InputValue button'
3. Create 'private bool contact' for 'Player 1' collider detection
3. Create 'Rigidbody _rigidbody' to apply force in y-direction for jump.
4. Initialize _rigidbody in Awake()
	_rigidbody = GetComponent<Rigidbody>();
5. public void OnJump(InputValue button)
    {
        if (contact)  
        {
            _rigidbody.AddForce(0,height,0);
        }
    }
   <br>

6. Use 'OnCollisionStay()' to check if 'Player 1' is in contact with a collider and 'OnCollisionExit()' to detect when 'Player 1' collider is not in contact with another collider.  These will change the value of 'contact' to indicate OnJump() method when to jump.

* private void OnCollisionStay(Collision collision)   
{ contact = true; } 

* private void OnCollisionExit(Collision collision)   
{ contact = false; }    

7. Next, we're tasked to add a sprint action for our character.  This can be done using the OnSprint() message.  Create 'private float sprint' and serialize it and a 'private float sprintValue', which will be use to multiply movement values in transform.Translate in x-z directions.  Then, write the following code in OnSprint():

    public void OnSprint(InputValue button)     
    {
        if (button.isPressed){ sprintValue = sprint;}       
        else{sprintValue = 1;}      
    }

8. Multiply 'sprintValue' in transform.Translate's x and z components.


<br>
<br>

###C# Script PlayerMovement
<br>
<img width="1329" height="787" alt="PlayerMovement C# Script 1" src="https://github.com/user-attachments/assets/5316d19f-ffaf-4830-90f8-eb8d00b3b84e" />
<br>
<img width="1536" height="485" alt="PlayerMovement C# Script 2" src="https://github.com/user-attachments/assets/c9161bf6-e2db-46c9-966b-c8a7467f9570" />


###C# Script Gameplay
<br>
![C# Gameplay](https://github.com/user-attachments/assets/c7fa1fbb-1261-4dff-a638-6de583112ce6)



### Visual Graphs:

Next task is to execute the same player actions but using Visual Graphs, including the already established Move, Look and Fire actions.  We can use the same Player Input action used for our C# Script.  First, the variables that will be used for our Visual Graphs were created.  
<br>
<img width="616" height="577" alt="Variables" src="https://github.com/user-attachments/assets/90e1ca72-6d91-4d2d-96d9-54551db56285" />

*Move Action*
<br>

- Erase both Start() and Update() nodes.
- Place 'On Input System Event Vector 2' node in
  - Assign 'Move' action in 'Input Action' box 
- Place 2 Vector 2 Nodes Get X and Y in graph.
- Connect output of 'On Input System Event Vector 2' to their inputs
- Place 2 sets of 'MovementSpeed' and 'SprintValue' variables.
- Multiply each set with Get X and Get Y and then multiply the results individually by Get Delta Time.
- Place 'Transform Translate' and connect flow from 'On Input System Event Vector 2' and Get X result to x-component and Get Y result to the z component.



<br>
![Movement Graph](https://github.com/user-attachments/assets/ec86cbc5-896d-4b8d-a26d-a744a494f53e)













