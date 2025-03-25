# WolvCTF 2025 Forensics WU
# Challenge: Breakout 
**Description of the challenge:**
Something fishy about that photo... What could be hidden in this game?


# Files

We are provided with a [breakout.jpg](https://www.mediafire.com/file/ta6pw9qyh0kydma/breakout.jpg/file) image:
![](https://i.imgur.com/QXlmZwP.jpeg)


## Analysis

First, I try to check for strings, no results. So I decide to apply some color filters to see if there isn't anything hidden in the image, no results as well.

What I decide to do next is to run **Steghide**:

First I run the **`steghide info`** command in **Steghide**, a steganography tool, which is used to retrieve metadata about a file that may contain hidden data.

So I type: `steghide info breakout.jpg`, here's what I get:

![](https://i.imgur.com/2zLClj1.png)

As you can see, we have a hidden **breakout.ch8** file.

Note that a **CH8 file** is commonly associated with **CHIP-8**, a simple interpreted programming language used for running retro games and applications. These files typically contain **CHIP-8 bytecode** that can be executed using a **CHIP-8 emulator**.

What I do next is extract the hidden **breakout.ch8** file, so I type: `steghide extract -sf breakout.jpg` 

![](https://i.imgur.com/Kkiner8.png)

Once I got the file, I go to an online CHIP-8 emulator: [https://johnearnest.github.io/Octo/](https://johnearnest.github.io/Octo/)

I open the breakout.ch8 file:

![enter image description here](https://i.imgur.com/p5O26Ex.png)

And click on Run:

![enter image description here](https://i.imgur.com/FYFMUPe.png)

As you can see we have a breakout game :)

So let's play !

After finsihing the game, you get the flag:

![](https://i.imgur.com/d0vFIZL.gif)

**WCTF{GAME_OVER_VMASBKLTNUFMGS}**

