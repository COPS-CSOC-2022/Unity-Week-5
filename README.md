# Unity-Week-5

_This week is all about UI and some music_

You will learn how to use the canvas gameobject in Unity editor and Singleton Design Pattern for adding music and sound effects.

Lets first talk about the UI.

For starters, UI elements are not standard GameObjects and cannot be used as such. UI elements are designed differently; a menu button which looks correct in a 4:3 resolution may look stretched or distorted in a 16:9 resolution if not set up right.

UI elements in Unity are not placed directly onto the scene. They are always placed as children of a special GameObject called the Canvas. The Canvas is like a “drawing sheet” for UI on the scene, where all UI elements will render. Creating a UI element from the Create context menu without an existing Canvas will automatically generate one.

![UI-Menu](https://user-images.githubusercontent.com/87766488/182778506-0f0df979-edd5-44f0-9b29-d4f7e0d60966.png)

The Rect Transform at the top appears to have many new properties that a standard GameObject’s Transform does not have.

This is because while a normal GameObject’s Transform describes an imaginary point in 3D space, a RectTransform defines an imaginary rectangle. This means we need additional properties for defining exactly where the rectangle is, how big it is and how it is oriented.

We can see some standard properties of a rectangle like the Height and Width, as well as two new properties called Anchors. Anchors are points that other entities can “lock” onto in the Canvas. This means that if a UI element (say, a button) is anchored to the Canvas on the right, resizing the Canvas will ensure that the Button is always on the relative right of the Canvas.

By default, you will not be able to modify the shape of the canvas area, and it will be a comparatively gigantic rectangle around your scene.

![image](https://user-images.githubusercontent.com/87766488/182780110-7d956142-ab32-4d92-b1b9-7362561d1014.png)

Next is the Canvas Component. This is the master component that holds a couple of universal options as to how the UI is drawn.

The first option we see is the Render Mode. This property defines the method that is used to draw the Canvas onto the game’s view. We have three options in the dropdown list.

Screen Space - Overlay : This render mode places UI elements on the screen rendered on top of the scene. If the screen is resized or changes resolution, the Canvas will automatically change size to match this.

Screen Space - Camera : This is similar to Screen Space - Overlay, but in this render mode the Canvas is placed a given distance in front of a specified Camera. The UI elements are rendered by this camera, which means that the Camera settings affect the appearance of the UI. If the Camera is set to Perspective, the UI elements will be rendered with perspective, and the amount of perspective distortion can be controlled by the Camera Field of View. If the screen is resized, changes resolution, or the camera frustum changes, the Canvas will automatically change size to match as well.

World Space : In World Space mode, UI elements behave as if they were normal GameObjects placed into the world. They are similar to sprites, however, so they are typically used as part of the game world instead of for the player, like in-game monitors and displays. Because of this nature, you can directly modify the values of the Canvas RectTransform in this mode.

Now set the "Order In Layer" field to 20 so that all the UI is rendered on top of other gameobjects.

Canvas Scaler : The Canvas Scaler component is used for controlling the overall scale and pixel density of UI elements in the Canvas. This scaling affects everything under the Canvas, including font sizes and image borders. In "UI scale mode" option set it to "Scale with screen size". By doing this all the UI will be scaled according to several screen sizes. Using the Scale With Screen Size mode, positions and sizes can be specified according to the pixels of a specified reference resolution. If the current screen resolution is larger then the reference resolution, the Canvas will keep having only the resolution of the reference resolution, but will scale up in order to fit the screen. If the current screen resolution is smaller than the reference resolution, the Canvas will similarly be scaled down to fit. If the current screen resolution has a different aspect ratio than the reference resolution, scaling each axis individually to fit the screen would result in non-uniform scaling, which is generally undesirable. Instead of this, the ReferenceResolution component will make the Canvas resolution deviate from the reference resolution in order to respect the aspect ratio of the screen.

## Task 1 - UI

Now your 1st task is to make game over UI element using Canvas. It should something like this: 

![UI-game_over](https://user-images.githubusercontent.com/87766488/182785871-856e9940-89db-4d81-81d9-6e4ecc1eb9a6.png)

Here MainMeu and PlayAgain are buttons. 
You will also be making a main menu scene which should look something like this: 

![UI-main_menu](https://user-images.githubusercontent.com/87766488/182786474-afce096d-a0ce-45bb-9230-b9554e30873c.png)

NOTE: Pls don't judge my designing skills :sweat:. 

In order to add functionality to buttons, you can watch this video: [LINK](https://www.youtube.com/watch?v=zc8ac_qUXQY), this would be more than enough for now.

Let's Jump right onto adding music to our game.

## Task 2 - Music and sound effects

We deal with 2 main components related to Audio in Unity, they are:

- Audio Listener
- Audio Source
Let's have a look at these components.

Audio Listener: This is a component that's automatically attached to the main camera every time you create a scene. It doesn't have any properties, since its only job is to act as the point of perception. Leaving the Audio Listener as it is, is recommended.

Audio Source : The Audio Source component has quite a few properties which we can tinker around with. This includes its pitch, panning, spatial blending (We'll get to that later), and if you open the 3D Sound Settings, you will find options for adding Doppler Effects and volume rolloffs. What interests us the most here is the AudioClip slot, however. That's where the sound effect to be played goes. Unity supports quite a few common sound formats, including .mp3 and .ogg etc.

Now for a better understanding about audio source and audio listener you can watch this [VIDEO](https://www.youtube.com/watch?v=6OT43pvUyfY) but the audio manager made by this guy is not recommended. Instead we wil use Singleton design pattern to make our audiomanager. 

Singleton Design Pattern : Generally speaking, a singleton in Unity is a globally accessible class that exists in :sweat:the scene, but only once. The idea is that any other script can access the singleton, allowing you to easily connect objects to important parts of the game, such as to the player or to other game systems. 
Honestly speaking you can understand this concept better from this [Video](https://www.youtube.com/watch?v=Y6cKPfUTrsA) rather than me trying to explain this :sweat:

You can download some sound effects from this website: [LINK](https://sfxr.me/)
For bg music just google up something according to your liking.


## Further Instructions

You have to integrate everything int the same folder you made in previous tasks. Every script should be named properly, indicating what that script is doing. You will asked to submit all the scripts and a recording of your final product at the end of week5. 
