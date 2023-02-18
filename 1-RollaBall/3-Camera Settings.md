## 1. Positoin of Camera

To get a better vision, we always need to reset the position and angular of camera.
In this project, we will lift the camera up by 10 units, and tilt it down by 45 degrees.
A **typical thild person setup** is to set the camera as a child as the target object, which will let the camera object inherit the transform changes of the player GameObject.

But it will not work well in our case, because it will let the camera rotates following the sphere also. What we want to see is to exclude the influence caused by rotation, which means that let the position of the camera is only associative to the offest of the distance between the camera and the sphere.

## 2. C\# scripts

First, adding a `new scripts` component in camera's inspector.

```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class CameraController : MonoBehaviour
{
    public GameObject player;

    private Vector3 offset;// Set the offset in the script

    // Start is called before the first frame update
    void Start()
    {
        offset = transform.position - player.transform.position;
    }

    // Update is called once per frame
    void LateUpdate() // The order of Update() is random, so use LateUpdate to let it only be called once after each frame 
    {
        transform.position = player.transform.position + offset;//Only matching the position but not the rotation
    }
}

```

## 3. Add reference to camera
We set a public variable `player` in the script to let us manully give value to it. But it will not detect relative objects. So we need to add a reference to this variable.

Drag the `player` slot in the `hierarchy` to the `Player` field in the `inspector`.
Now if we run the project, the camera will follow the spheres movements but not rotation.
![[ReferenceToCamera.png]]
