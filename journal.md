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
