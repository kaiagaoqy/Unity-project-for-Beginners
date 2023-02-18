Now it's time to let our balls to move!
## 1. Add Rigidbody Component
Add a Rigidbody component in the inspector
## 2. Install InputSystem Package
Install the input system package to use keyboard input in your game/project.
In the top menu, select Window -> PackageManager -> search for input system to install.
Click 'yes' and 'save' in the warning dialogue during the installing process.

For windows, no longer need to reset the building settings!
![InstallInputSystem.png](InstallInputSystem.png)


After automatic restarting of the project, adding the 'Player Input' component to the sphere
```
Player Input: get and set up the target object's movements, like detecting whether an action has happened and triggerring a notification which can be used by a script to trigger the following events in the game
```

Then you need to add input action assets to the sphere for the Player Input to use

Let’s recap this process:

1. In the Hierarchy, select the Player GameObject.

2. In the Inspector, select Add Component. Then search for and select Player Input.

3. In the Inspector, in the Player Input component you just created, select Create Actions. (This step is not visible in the video.)

4. Create a new folder named Input, and name your asset InputActions, as shown in the video.

Important: The following steps are not shown in the video.

5. In the Project window, locate this new InputActions asset in the folder you just created.

1. Either drag the InputActions asset from the Project window to the Actions property of the Player Input component on the Player GameObject, or use the circle icon for the Actions property to select the InputActions asset. **(No longer need for version 2021.3.18f)**
2. 
## 3. C/# Start!! Let the sphere move!
To create a C/# script for the sphere, we can add a compent called "New Script". Let's name it as "PlayerController"
The script will always be created at the top level folder of our projects. 
So to let our documents organized and tidy, we will create a new "Scripts" folder and move the script into it.

As you can see in the screeshot below, we can move the sphere using WASD and Up/Down/Left/Right arrow

![InputActionsSetting.png](InputActionsSetting.png)

Then let's work on the scripts
- Function `Start` will be called once the project is run
- Make sure the class name is the same as your file name
- 
``` c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.InputSystem;

public class PlayerController : MonoBehaviour
{
    public float speed = 0; // You can set it manually in the Insepctor

    private Rigidbody rb; // No need to let it visible to the inspector and make sure the data type is the same as it shown in the Inspector

    private float movementX;
    private float movementY;

    // Start is called before the first frame update
    void Start()
    {
        rb = GetComponent<Rigidbody>();//Get properties defined in RigidBody
    }

    private void OnMove(InputValue movementValue) // Called by the EventSystem when a Move event occurs.
    {
        Vector2 movementVector = movementValue.Get<Vector2>();//Representation of 2D vectors and points.

        movementX = movementVector.x;
        movementY = movementVector.y;
    }

    private void FixedUpdate()
    {
        Vector3 movement = new Vector3(movementX, 0.0f, movementY);//Creates a new vector with given x, y, z components. !Tip: coordinates must be in Float!!!!

        rb.AddForce(movement * speed); // Force is applied continuously along the direction of the force vector
    }

}
```