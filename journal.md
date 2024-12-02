# learning-journal
This is my learning journal for programming.
bzinga
# 2024-10-15
Started the learning journal.
Learned about the Unity Documentation website. As someone who is new to programming and doesn't know much about C# documentation, I think this website will be very useful to me in the future.
Float - number with a fraction
Int / integer - whole number
F at end of float number - set it as a float number
Time delete time - time that's elapsed since last update

# 2024-11-05

Windows + Alt + R = Screen recording

Started on learning how to get text to appear by a trigger. I am wanting to have characters speak in my final game, so learning how to get text to appear is very important. I am going to look on youtube for a tutorial and follow along with it.

I found some videos that seem to explain the basic idea, but they are a bit hard for me to follow as I don't really understand the documentation and the prerequisities seem to be a lot, and I just want to make a simple tutorial to understand how to do it. For the tutorial I am wanting to simply click on a button and have the text appear before disappearing.

https://www.youtube.com/watch?v=DOP_G5bsySA - easy dialogue system

I looked at one of my friend's tutorials which showed how to have a game object appear when another one is pressed. This was done by having two scripts for both game objects, and having the first one set to being invisible upon the start of the game. The second gameobject then had a script which said when the mouse was pressed on it, the other gameobject would appear. Since text is also a gameobject, I could utilise this tutorial to make this one of my own.

Firstly I made a simple square in MS Paint that would act as the button. Since for the game I am envisioning, I want the player to click on the actual sprite of a character to start their dialogue, I will use a sprite instead of a button for this tutorial. 
I then made an empty game object and added a sprite renderer component to it. I then dragged the MS Paint square into the sprite slot. This made the square show up when I started the game.
Next I created an empty Gameobject and added in text mesh pro - text. I added in some random text and then made my two scripts - 'Square' and 'Text'. I attached these both to their relevant gameobjects.

I ran into an issue because I realised that the tutorial my friend made wouldn't work with showing text. While I got it attached to a gameobject, since the text wasn't a sprite, the code my friend used didn't work. If I wanted it to work with that code, I would need the text to instead be a sprite, which would require having every line of dialogue be a 2D picture asset, which is not an efficient way to do it. I looked up documentation and found out about textrenderer and DrawText, but I wasn't sure if this would be useful. So I asked for help at this point.

Paul showed me that instead of having an empty gameobject and adding text to it, I add text from create UI. This will put the text in a 'canvas' group. This will also be where additional elements of the UI will go in the final game, such as the dialogue border, character icon, and so on. While I theoretically could write a script for the text and have it set to invisible, I can just set it as invisible from inside Unity. This saves some time and space as I don't have to create a script for it at all.

In order to make the sprite be clickable, I have to add a Box Collider 2D to it. Inside the script, I can delete both start and update as I have no need for them here. This is the code for the square;

![image](https://github.com/user-attachments/assets/3012b1ca-da03-4646-b489-f74b85f44a4c)

We use monobehaviour so that the script can attach itself to gameobjects in the editor, and so that our new class 'Square' has access to all the functions that monobehaviour has, such as the start and update methods. 'Square' means nothing important in this example, its just the name of the new class I come up with to attach it to the sprite and differentiate itself from other things in the script.

We use public gameobject target so that inside the unity editor, where the script is attached to the gameobject we have a little box where we can put the 'target' of the code. In this case I dragged and dropped the text from the canvas group. Because we made this public I can do this, as if it were private it'd only be doable via code in the script. 

![image](https://github.com/user-attachments/assets/0adf6b1b-79c1-4f85-a63a-137b6e339ef8)

Now in the code we write down the input, so that the text will become 'active' (visible in-game) when we click with our mouse button.

In the final game obviously this code won't be perfect, as I will need to also make the text go away and I will have to make the system more efficient to support having numerous lines of dialogue. It could be something to explore to make the tutorial better, but I am quite behind as is so I might just make the tutorial simple.

# 2024-11-06

Writing my first tutorial today, referencing all the things I wrote in here yesterday to remind myself how to do it. Couldn't figure out how to add another md file to this repository without making a new one, so I cheated and downloaded one of Paul's files, reuploaded it and just replaced all of his text with my own. I will be quite embarassed if there is an easier way.

Turns out there was an easier way. When adding a new file to a repository, I just have to put '.md' at the end of the name. 

# 2024-11-26

Starting work on next tutorials and trying to come up with a way to prototype my game. I am struggling to find tutorials for the kind of game I wanted to make (food prep game similar to Papa's Pizzeria), with the few tutorials I have found being very complicated and in 3D rather than 2D.

I found a main menu tutorial that I'll be following later - https://www.youtube.com/watch?v=DX7HyN7oJjE

I found a food prep style tutorial, and while it is for 3D I might be able to use it for my own prototype - https://www.youtube.com/watch?v=WGGAckunBcQ

I was wondering just what exactly I wanted to do in my food prep game, whether it would be more of a simple point-and-click or a Cooking Mama style game. Realistically I don't think I have the skills to do something as complex as the latter, so I will probably use the tutorial as a reference to do a game where you try and match a plate of ingredients to a customer's specification. I think it could be interesting if in the prototype the customer was capable of asking for a randomised plate each time, but we will have to see what I can do with my limited knowledge.

I created basic art assets for burger ingredients and imported them into Unity. Looking at the tutorial, it seems that this prototype will boil down into around 3 or so scripts.
1) A script that designates what the order we will be replicating is -> gameflow
2) A script that checks the final order when we are done making it to make sure it matches what was requested and win or lose the game -> platecheck
3) A script that duplicates the sprites of the ingredients to make the 'order' visible on the plate -> clickplace

The tutorial had a mechanic for 'cooking' the meat, but I decided not to bother with that for this. The way their method went about this was to have the 'gameflow' script list a public integer 'ordervalue', in which each number unit corresponded to an ingredient. Such as:
'12101'
The first and last numbers are tied to the buns - one on the bottom and one on top. The 1000th number, '2', is the amount of meat patties. The 100th number, '1', is the amount of bacon, and the 10th is cheese, which would mean we would have 1 unit of bacon and no cheese on this example burger. 

We would then have another integer named 'platevalue', which would start at '00000'. We want it to be so when we click on the ingredient and get it added to the plate, the corresponding number in the platevalue goes up to match the amount of the ingredient on the plate; the amount of times we click on it. In our gameflow script we would only need to assign the integer for the final order, and then the integer for the plate value at the start. We could make the integers public, so we could adjust the order inside Unity for testing purposes to see if it works. If I were to try and make it to be a randomised order each time for replay value, it would be harder and I'm not really sure how I would go about doing that by myself, as I would probably need to set parameters so that we don't get a crazy amount of things on an order, like 7 bottom buns and 9 patties.

For the next step, I would need to make the script so that when we click on the ingredient sprites it will add the correct numbers to our plate value. I would need to add 2D colliders on every sprite so that void OnMouseDown would interact with the game object properly. We also want this script to duplicate the ingredient sprite and place it on the plate sprite, though since this is 2D I will probably not have the sprites layer over each other perfectly for clarity. We will be adding another public integer which is 'foodvalue', and then in the editor we can manually assign each ingredient how much value they add. We would then want to do platevalue += foodvalue, so that the plate value will update according to the food value that is put on it and can be checked against the order value at the end.

To get it so that clicking on the game object adds the value, what we would do is have a big bracket for the OnMouseDown and then have several 'if' statements for each of the ingredient game objects. We would refer to each one by name, ergo:

```c#
if (gameObject.name== "Bun")
```

and then have it place a duplicate sprite over the plate sprite. This would involve having to fiddle around with vectors which I am not looking forward to, but as long as it works I guess?

The final script would be the platecheck. Like the ingredients, we would attach a 2D collider to the plate sprite, so that when we are ready to serve the order and check if it meets the order value we just have to click on the plate. Then it would be another OnMouseDown and an if statement to check if the plate value matches the order value;

```c#
private void OnMouseDown
{
  if (gameflow.orderValue==gameflow.plateValue)
    {
        Debug.Log("correct");
    }
}
```

So in this case, getting the order correct (matching the ordervalue with the platevalue) would win you the game via a message in the debug log. In my actual prototype, I could probably just add some text on screen that says 'correct' or something similar, and then repeat the game or take you back to the main menu.

This, in theory, would be the method I would use to create my prototype. My main concerns with it right now is the issue of messing around with the cloned sprites to get them to all be visible without overlapping each other, and the general issue of how inexperience I am with coding. I will try to follow the tutorial I found and see how the results go.

Following the tutorial, I hit a snag in terms of how I was going to display the ingredients on the plate. In the 3D tutorial, the models were stacked on top of each other neatly in the same position using gravity, but working with 2D I couldn't do this. If I stacked the sprites on top of each other, only the top one would be visible, and it is important to be able to see every ingredient you have selected.
I decided it would probably be better for clarity if instead I could stack the sprites on top of each other somehow, showing the position of the ingredient in the burger while not blocking the others. Paul gave me this code:

```c#
static float offset= 0;

private void OnMouseDown
{
  Transform clone = Instantiate(transform);
  clone.localScale = Vector3.one * 0.5f
  clone.localPosition = new Vector3(4, 3 + offset, - offset);
  offset += 0.1f;
}
```

# 2024-12-02

Today I am going to focus on doing some more tutorials. I am resuming the start menu.

I am using my project file that has the text appearing in it, so I already have a scene for the start menu to go to once you click play. The first step is to create a new game object, specifically UI > Button text mesh pro. After fiddling with the aesthetics of the button to your liking, then we go to the main camera in the hierachy and make a script to attach to it. This script will be called 'MainMenu'.

The tutorial deletes start and update, and adds 'scene management' to the script at the top.

```c#
using UnityEngine.SceneManagement;
```

After looking up this function, it seems that scene management is needed when you are switching between scenes. As we are going from a main menu scene to the scene where I did the text appearing when a sprite is pressed, we naturally need this to be added. 

```c#
public class MainMenu : MonoBehaviour
{
   public void PlayGame()
    {
        SceneManager.LoadSceneAsync("Text Appear");
    }

}
```

This is the code the tutorial gives for making the button start the next scene. We want it so that when 'PlayGame' runs, it will load the next scene we want, whether that be level 1 of our game or so forth. In this case it is the level of the previous tutorial I have done, "Text Appear".

Now we have the code for it, we go back to the button itself in the hierarchy. If we scroll in the editor we can find a little section that lets us control what the button will do when we click it, and we manually drag the main camera from the hierarchy into the object slot. When we do, in the function tab to the top right, we can manually go through and select a function that is referenced in the main camera, and we just have to select 'PlayGame'. This makes it so that pressing the button will run 'PlayGame', and as we have indicated we want the scene to change to "Text Appear" when this runs, that is what happens.

![image](https://github.com/user-attachments/assets/92403fd9-e2d9-4fae-816e-bc2af26226a7)

I believe I am able to write my tutorial on this now, so I will move onto another one. I am going to choose doing a 'quit' button next, as the tutorial I am using for reference already has one and it will be a useful thing to know to make my prototype.

Since I am using the same tutorial video for the quit game as start game, they seem to use the same script but just with the addition of the function to quit the game added. They add a new public function called QuitGame, and shut down the game with the Application.Quit command. It is actually less lines of code than I anticipated and seems very simple. The challenge will be writing the tutorial but avoid having to reference the start game tutorial as something that must be read first. 

Application.Quit is ignored in the game editor, so I am going to have to quickly export a build of my game to test it. Finished both tutorials, now I need to pick a topic for the last one while also juggle the prototype!
