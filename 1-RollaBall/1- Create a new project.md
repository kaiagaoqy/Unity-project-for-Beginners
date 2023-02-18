## 1. Create a new project
To create an interactive game or project. We need to select a URP template for rendering. Although either 2D or 3D is ok, for this biginning project, we will 1. select the  `3D(URP)` template 2. Self-define the project name 3. Click `Create project` button to open the project in the editor

``` ad-important
The newest 3.4.1 Unity Hub splits the original URP template into 2D and 3D templates. To realize a mobile 3D interactive rendering as the official tutorial shows, please select the 3D(URP), from my hindsight....
```

![[OriginalPage.png]]

## 2. Create a new Scene
Now you can see the original scene as beblow. **Hierachy** on the left shows objects we have on the scene. We will set up our own objects later. And layput setting ( on the top right) of current page is set as Default, you can change it to whatever kind you like.
![[DefaultScene.png]]
- Select `File` on the top left -> `New Scene` to create a new **Basic(URP)** scene, and save it named as MiniGame in your `Assets` folder. For this project, we need no volume, so basic scene will be good enough
``` ad-info
Keep in mind to save your scene first before coding using C# and run the script.
```


![[BasicScene.png]]

## 3. Primitive Plane
Now we will create a plane, where other players can move on. Now we use the Primitive plane that is bundled with Unity.
Select GameObject->3D Object -> Plane to create a primitive plane, and rename it as ground.

![[CreatePrimitivePlane.png]]

``` ad-info
Press F to see the entile GameObject
```
We can use the grid setting at the top of the scene view (defaut shows the plane on the Y axis) to change the grid lines and their opacity ( grid lines are where the arrow points at)
The property of current object can be manually adjusted on the `Inspector` board or in the C# scripts (talk later)

![[GridSetting.png]]

To rescale the scale, we can
1. select the rescale icon on the scene view (or press the hotkey R) then drag the handle of each fields
2. Manually type a vaule in the Transform component found in the Inspector board
``` ad-info
The primitive plane is a single sided object, which means if you set y to a negative number, the plane will disppear from your scene
```

Now. let's set x,z=2, y =1

![[Pasted image 20230218001518.png]]

In the same way, let's create a sphere object then name it as Player.

Now, you will see the sphere is burried in the plane. The reason is all objects will be created at origin point $(0,0,0)$ and stacked based on the order of Hierarchy. So we need to move the sphere up until it rests on the plane. 

All the primitive objects, like a cube, sphere, etc have a standard size, like one by one by one in the unity measurement.

Let's set the coordinate of the sphere as $(0,0.5,0)$

