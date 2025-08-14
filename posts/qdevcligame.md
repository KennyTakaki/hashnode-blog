---
title: "AWS CDK Multi-Account Deployment Guide"
slug: q-dev-cli-game
tags: ["aws"]
publish: true
---

Here’s the English translation of your Markdown:

---

# Overview

I regularly use Amazon Q CLI in my work, so when I saw this event, I decided to participate:

I had previously made a simple game using Godot, so I was interested in the event. I’ve also experienced firsthand that Amazon Q CLI can create a simple SPA app in just a few hours, so I wanted to see if it could do the same for code in a different field. That’s why I joined.

I’ll keep a simple log of the time it took for the work. Since I was writing this while working, the time for writing is included in the total.

# Initial Summary

### Final Game Code

Repository here:
https://github.com/KennyTakaki/amazon-q-cli-game

### Number of Prompts

The game was generated in just 5 prompts:

1. Create project skeleton
2. Provide game specifications
3. Debug instructions
4. Debug instructions regarding language
5. Minor layout adjustments & README maintenance

### Work Time

Total time required: about 1 hour

1. (30 min) Preparations such as creating a Git repository and blog template
2. (30 min) Game development via prompts

Based on my regular usage, I feel that with specific enough instructions, you can achieve a high level of detail.

# Work

## Preparations (30 min)

* Create Git repository
* Create template for this blog post
* Obtain username on community.aws
* Set up development environment (devcontainer, install PyGame)
* Install Amazon Q CLI

This took about 30 minutes in total. For now, a sample game displayed correctly, so the environment setup seemed fine.


## Creating the Project Skeleton (Prompt 1: 10 min)

To make a game, you need various files, such as sprite sheets, audio assets, game logic code, and entity code. I asked Amazon Q Developer CLI how to organize these assets in the directory structure.

The `src` directory was divided into UI, game logic, game entities, and utils, and separated from `assets`. This seemed reasonable, so I decided to adopt it as is.

What surprised me was that, at this stage, the prompt output already included a working game. It felt like overkill, but also very convenient.

```
Please provide a recommended directory structure for creating a game with PyGame.
～～～～
Here’s a recommended directory structure for creating a game with PyGame.
It can be adjusted depending on the scale and complexity of the game, but a basic structure looks like this:
game_project/
│
├── main.py              # Game entry point
├── settings.py          # Game settings (resolution, FPS, colors, etc.)
│
├── assets/              # Game assets
│   ├── images/          # Sprites, background images, etc.
│   ├── sounds/          # Sound effects
│   ├── music/           # BGM
│   └── fonts/           # Fonts
│
├── src/                 # Source code
│   ├── entities/        # Game entities (player, enemies, etc.)
│   │   ├── player.py
│   │   ├── enemy.py
│   │   └── ...
│   │
│   ├── ui/              # User interface related
│   │   ├── menu.py
│   │   ├── hud.py
│   │   └── ...
│   │
│   ├── scenes/          # Game scenes
│   │   ├── main_menu.py
│   │   ├── game_level.py
│   │   ├── game_over.py
│   │   └── ...
│   │
│   ├── utils/           # Utility functions
│   │   ├── helpers.py
│   │   ├── physics.py
│   │   └── ...
~~~
├── data/                # Game data
│   ├── levels/          # Level data
│   ├── save/            # Save data
│   └── config/          # Configuration files
│
└── tests/               # Test code
    ├── test_player.py
    ├── test_physics.py
    └── ...
～～～～
```

## Providing Game Specifications (Prompt 2: 5 min)

To have Q CLI create the program, I needed to decide on the game specifications.
Since it should already support handling images from the terminal , I could have used an image of the game screen to exchange ideas. However, I decided to stick with a text-based specification, since I feel that logic for program execution is still best conveyed in text.

The game has a simple concept: guessing whether an AWS service name starts with “Amazon” or “AWS.” I wrote down the screen flow and possible interactions for each screen and input them into the prompt.

```
I’ll give you the game specifications; please build the game.
AWS has services whose names start with either “Amazon” or “AWS.”
The game will ask the player to choose between these two.

The game has three screens:
Start screen
Main screen
End screen

Screen transitions:
Start screen → Main screen
Main screen → End screen
End screen → Start screen

When the game starts, the start screen is displayed.
The start screen contains an explanation of the game.
It has a button labeled "Let's Play" to move to the main screen.

In the main screen loop:
1. Display an AWS service icon and service name, but omit the “Amazon” or “AWS” prefix.
2. Display buttons labeled “AWS” and “Amazon.”
3. The user chooses one of the buttons.
4. If correct, display ○, increment the correct count, and update the displayed score.
5. If incorrect, display ×, increment the incorrect count, and update the displayed score.

End conditions:
- The user can make up to 2 mistakes; the 3rd mistake ends the game.
- OR, if all service names in the list have been used, the game ends.

When the game ends, transition to the end screen.
The end screen displays the total correct and incorrect counts.
It also has a “Play Again” button that resets all counters and returns to the start screen.
```

## Debug Instructions (Prompt 3: 5 min)

However, the game generated from the previous prompt didn’t start correctly.

So I ran a concise debug prompt:

```
When starting the game, only a black screen appears and the intended behavior doesn’t occur. Please debug.
```

With that, the game logic began displaying as intended. I was impressed that such a short prompt led to the correct fix.

## Debug Instructions Regarding Language (Prompt 4: 5 min)

However, Japanese text was garbled, so I asked for a fix:

```
It seems the Japanese text is garbled. Can you fix it?
```

The response was to convert all text in the game to English to avoid the issue—a rather drastic move.
While this wasn’t what I intended, I let it slide since the game logic was otherwise complete.

```
To avoid the Japanese display problem, I have changed all text to English.
This should solve the character corruption issue.

Lastly, let’s also change the game title to English:
```

## Minor Layout Adjustments & README Maintenance (Prompt 5: 5 min)

Finally, I requested some small layout changes and README updates:

```
On the end screen, I want the evaluation message to appear within a white background area.

Also, please edit the README to match the current game specifications.
```


# Impressions

Working with Q Developer, I’ve noticed (as a model trait) that it often does more than requested. The initial project skeleton already included a functioning game, and the language debugging step resulted in an unsolicited switch to English.

I feel that to control the code output well, you need to give precise instructions or make good use of context. That said, it’s also refreshing to see something come together so quickly with minimal input.

In my professional work, as I’ve advanced in years and moved further from hands-on coding, I’ve found tools like this indispensable. In fact, coding without AI tools is starting to feel burdensome. It’s an amazing service and tool.

---

If you want, I can also refine the tone so it reads more like a polished tech blog article. Would you like me to do that?
