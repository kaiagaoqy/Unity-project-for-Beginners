Now it's time to let our balls to move!
## 1. Add Rigidbody Component
Add a Rigidbody component in the inspector
## 2. Install InputSystem Package
Install the input system package to use keyboard input in your game/project.
In the top menu, select Window -> PackageManager -> search for input system to install.
Click 'yes' and 'save' in the warning dialogue during the installing process.

For windows, no longer need to reset the building settings!
![[InstallInputSystem.png]]


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

6. Either drag the InputActions asset from the Project window to the Actions property of the Player Input component on the Player GameObject, or use the circle icon for the Actions property to select the InputActions asset. **(No longer need for version 2021.3.18f)**

