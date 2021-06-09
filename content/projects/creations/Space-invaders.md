{
  "title": "A ship that Fires Bullets",
  "date": "2018-02-11T12:41:05-05:00",
  "image": "/img/space-invaders.png",
  "description": "Space invadors (A ship that Fires Bullets) \"<em>is an open-source game project to help you understand the fundamentals of python programming while you make an interactive game.",
  "tags": ["python", "pyGame", "game","REST APIs"],
  "fact": "",
  "featured":true
}

Space invadors (A ship that Fires Bullets) is an open-source game project to help you understand the fundamentals of python programming while you make an interactive game.

## Planning the Project

- It is important to plan out each project before you start beginning programming, this is because you will have a better understanding of how your program will look like and also you will manage your time wisely. 
- To do this, you will have to make a description of your program like so;

```
In Alien Invasion, the player controls a rocket ship that appears at
the bottom center of the screen. The player can move the ship
right and left using the arrow keys and shoot bullets using the
spacebar. When the game begins, a fleet of aliens fills the sky and
moves across and down the screen. The player shoots and destroys
the aliens. If the player shoots all the aliens, a new fleet appears
that moves faster than the previous fleet. If any alien hits the
player’s ship or reaches the bottom of the screen, the player loses a
ship. If the player loses three ships, the game ends.
```

## Starting the Game Project

### Creating a PyGame Window and Responding to User Input

```python

import sys

import pygame

class AlienInvasion:
	"""Overall class to manage game assets and behaviour."""

	def __init__(self):
		"""Initalize the game, and create game resources."""
		pygame.init()

		self.screen = pygame.display.set_mode((1200, 800))
		pygame.display.set_caption("Alien invasion")

	def run_game(self):
		"""Start the main loop for the game."""
		while True:
			# Watch for Keyboard and mouse events.
			for event in pygame.event.get():
				if event.type == pygame.QUIT:
					sys.exit()
			# make the most recently draw screen visible.
			pygame.display.flip()

if __name__ == '__main__':
	# Make a game instance, and run the the game.
	ai = AlienInvasion()
	ai.run_game()
```


- Alien Invasion starts as a class called ```AlienInvasion```. 
- In the ```__init__()``` method, the ```pygame.init()``` function will initialize the background settings that Pygame will need to work properly.
- Then we call ```pygame.display.set_mode()``` to create a display window, on which we will draw all the game's graphical elements. 
- The arguments ```(1200, 800)``` us a tuple that defines the dimensions of the game window. In this case will be 1200 pixels wide by 800 pixels high. 
- We assign this display window to the attribute ```self.screen```, so it will be available in all methods in the class.
- The object we assigned to ```self.screen``` is called a ```surface```. A surface in Pygame is a part of the screen where a game element can be displayed. 
- Each element in the game, like an alien or a hip, is its own surface. 
- The surface returned by ```display.set_mode()``` represents the entire game window. 
- When we activate the game's animation loop, this surface will be redrawn on every pass through the loop, so it can be updated with any changes triggered by user input.
- The game is controlled by the ```run_game()``` method.  That method contains a ```while``` loop that returns continually.
- the ```while``` loop contains an event loop and code that manages screen updates.
- An ```event``` is an action that the user performs while playing the game, such as pressing a key or moving the mouse.
- To make our program respond to events, we write this event loop to listen for events and perform appropriate tasks depending on the kinds of events that may occur.
- To access the vents that Pygame detects, we will use the ```pygame.event.get()``` functions. This function returns a list of events that have taken place since the last time this function was called.
- Any keyboard or mouse event will cause this ```for``` loop to run. Inside of the loop we write a series of if statements to detect and respond to specifics events.
- For example; when a player clicks the game windows's close button, a ```pygame,QUIT``` event is detected and we call ```sys.wxit()``` to exit the game
-  The call to 	```pygame.display.flip()``` tells Pygame to make the most recently drawn screen visible. 
-  In this case, it simply draws an empty screen on each pass through the ```while``` loop, erasing the old screen so only the new screen is visible. 
-  When we move the game elements around, ```pygame.display.flip()``` continually updates the display to show the new positions of the game elements and hides the old ones, creating the illusion of smooth movement.
-  At the end of the file, we created an instance of the game, and then call run_game().
-  We place ```run_game()``` in an ```if``` block that only runs if the file is called directly. When you run this ```alien_invasion.py``` file, you should see an empty Pygame window.

## Setting the background Color
- Pygame will create a black screen by default. 
- To change this we will add this line to the end of the ```__init__()``` method.
```python
Set the background color.
➊ self.bg_color = (230, 230, 230)
```

- We also want the game to redraw the screen during each pass through the loop, to do that will add this like at the end of the ```run_game()``` method.
```python
# Redraw the screen during each pass through the loop.
➋ self.screen.fill(self.bg_color)
```

- Colors in Pygame are specified as RGB colors; a mix of red, green, and blue.
- Each color value can range from 0 to 255. 
- The color value (255, 0, 0) is red, (0, 255, 0) is green, (0, 0, 255) is blue. 
- You can mix them to create up to 16 million colors.


- At first we assign the color mix (gray) to ```self.bg_color``` inside the ```__init__()``` method. 
- We then fill the screen with the background color using the ```fill()``` which acts on a surface and takes only one argument; a color

### Creating a Settings Class

- Each time we introduce a new functionality to the game, we will have to create some new settings as well
- Instead of adding settings throughout the code
- You can write a module called ```settings``` that contains a class called ```Settings``` to store all these vales in one place.
- This will allow you to work with just one settings object any time we need to access an individual setting.
- For example;

```python
class Settings:
	"""A class to store all settings for Alien Invasion."""
	def __init__(self):
		"""Initialize the game's settings."""
		# Screen settings
		self.screen_width = 1200
		self.screen_height = 800
		self.bg_color = (230, 230, 230)
```

- To make this settings apply into your game you will have to first import them inside your game file like so ```from settings import Settings```
- You need to replace the settings you made manually inside your program to the variables you have created in the file ```settings.py```
- You then need to declare the class inside the class you will want to update your settings in this case will be the ```AlienInvasion```  class inside the ```__init__()``` method like so;
```python
self.settings = Settings()
```
- In this case you will have to change the screen settings. You can do that by declaring them like this;
```python
# Change the dimensions of the game
pygame.display.set_mode((self.settings.scrren_width, sef.settings. screen_height))

# Change Background color
self.screen.fill(self.settings.bg_color)
```
