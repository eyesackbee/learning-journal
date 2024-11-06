# Text Appearing after Clicking Gameobject
## This tutorial shows how to make text appear on the screen after clicking on a gameobject with the mouse. This can be useful for things such as prompting dialogue from characters after clicking on their sprite in-game.
### Prerequisites
- Image of your sprite
  - All you need for this tutorial is the image of whatever sprite you will need to click on for the text to appear. This can be anything from a picture of a simple box, to a fully rendered character sprite. For this tutorial we will be using a simple solid coloured square made in MS Paint.

## Creating the Gameobject
1) Import your sprite image into Unity by going into the project window and navigating to the Assets folder. Right click inside this folder and select 'Import New Asset'.

![image](https://github.com/user-attachments/assets/a07769f9-24c5-4af5-b48e-d43326fb1664)

2) Click and drag the sprite onto the scene. You will see it appear in the hierarchy if this is done correctly.

![image](https://github.com/user-attachments/assets/b3ce2c85-8bc0-479b-9fa1-7ac2f75fb8d0)

3) Clicking on the sprite gameobject in the hierarchy, go to the inspector and navigate to the 'add component' button. Add a 'Box Collider 2D' to the gameobject.
   - We want to do this as we need the game to know when we are clicking on the gameobject specifically vs anywhere in general on the screen. We only want the text to appear when we click on the gameobject, not anywhere else, so this collider is necessary.
   - We don't need to edit the parameters on this component as it is already tailored to the dimensions of the sprite. Again, as we only want the text to appear if we click directly on the gameobject, there is no need to edit it at this point.

![image](https://github.com/user-attachments/assets/2f3bad62-9bad-41aa-8f42-d50217739e14)

## Creating the Scripts
1) 
