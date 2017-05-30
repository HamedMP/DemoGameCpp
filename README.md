# STD: Spaceship Tower Defense EIT Edition

STD is a version in the space of the famous game Tower Defense.<br>
There is a grid in which you can put spaceships to defense your land. Waves of
asteroids come to attack you, so you need to install a big defense in order to
keep the game going.

## How it works
Each spaceship automatically shots from the left to right, but in case a
increasing number of asteroids are on the same line in front of the spaceships. The asteroids move ramdonly in the vertical axis but constantly in the horizontal axis.

## How to prepare a good defense
There are three types of spaceships:
* _SNOW_ :  cheap white spaceship, fast moving and shooting, but very weak 
* _GRASS_ : green spaceship with a cost, speed, and frequency enhanced compared to white spaceship(_SNOW_)
* _BLOOD_:  expensive red spaceship, very slow moving and shooting but very hard to destroy. 

Each time a spaceship is hit by an asteroid, the spaceship loses a level and if it is a _SNOW_ spaceship it gets destroided with the asteroid.

For example a _BLOOD_ spaceship can degraded to a _GRASS_ spaceship.


## Rules and Puntuation
You can add only one spaceship per cell, if you can pay a well-known value with
your score.

Asteroids can move only from right to left, and if they reach the left border
score is decreased according on a well-known value.<br>
Pay attention, because if you
reach a negative score and you have not any other spaceships, you lose the
match. Otherwise, until you have some spaceships alive, you can keep going with
the game.<br>
If you kill every asteroid in a wave, you can call a next wave.

Every wave has a bigger number of asteroids, so make sure you have a great
defense!


## Keys for playing
* _p_: Game in pause
* _h_: Show help page
* _a_: Launch a new wave of asteroids
* _q_: Select spaceship _SNOW_
* _w_: Select spaceship _GRASS_
* _e_: Select spaceship _BLOOD_
* _mouse left-key_: put a ship inside a cell


## GUI
A very basic GUI is used for the game, developed by [Guillaume
Perez](http://www.i3s.unice.fr/~gperez/). It is based on the GLUT library.

# Code Use and Analysis

## Requirements
* Linux distribution
* GLUT is required for the GUI
```
# Installing GLUT via terminal 
sudo apt-get install freeglut3-dev
```

## Usage

The code has been tested under ubuntu 16.04 using qtcreator 4.2 and CMake 3.5.1.
To access the program, clone the repository:
```
$ git clone https://github.com/MarcosBernal/DemoGameCpp
```

You can use either the CMakelist.txt or the Makefile to build the program. In case of using Makefile:
```
make
make run
```

Some configurations, like difficulty or number of lines can be changed in the main menu of the game. But others havo to be changed in the file Config.h. Remember to compile the whole program after changing any value in Config.h.

# Software Structure

The project follows the following structure

    STD EIT Edition
     |
     +-- include    # Depends on libEngine.a (provided library)
     |  |
     |  +-- Engine.h    
     |  +-- GraphicPrimitives.h
     |  +-- ...    
     |  \-- <FileNameN>.txt
     |    
     +-- libLinux   # Depends on libEngine.a (provided library)
     |  |
     |  \-- libEngine.a
     |    
     +-- src
     |  |
     |  +-- Config.h
     |  |
     |  +-- headers
     |  |  |
     |  |  +-- Asteroid.h           
     |  |  +-- Spaceship.h          
     |  |  +-- Shot.h               
     |  |  +-- spaceLogic.h         
     |  |  +-- BLine.h              
     |  |  +-- Game.h               
     |  |  +-- MyControlEngine.h 
     |  |  +-- MyGameEngine.h 
     |  |  +-- MyGraphicEngine.h 
     |  |  +-- Observer.h
     |  |  \-- Wave.h 
     |  |
     |  \-- sources
     |     +-- <HeaderFile1>.cpp
     |     +--  ...
     |     \-- <HeaderFileN>.cpp
     |
     +-- CMakeLists.txt
     +-- Makefile   
     \-- README.md   

![UML Diagram](https://yuml.me/97cf1805.png)

# Improvements

- Added CMakeList.txt file. Now, it is possible working and test the code with any IDE instantly.
- Removed all warnings regarding *-Weffc++*. It should have improved the performance.
- Removed some warnings regarding *-Wnon-virtual-dtor*. When a class has virtual functions, [its destructor should be also virtual](https://en.wikipedia.org/wiki/Virtual_function#Virtual_destructors). GLUT custom library has to be improved.
- Added Main menu to configure the game. From there can be selected the number of lines and the difficulty.
- Added suppport for increassing the difficulty(number of asteroids and their lives) and increase or decrease the number of lines.
- Added a timer to reduce the resources consumed and improved the game experience. Now the game speed can be followed.


## Future improvements - TODO
- improve class relation:
	- elements such as Waves, Ships or Shots should be only contained in Game.h removing dependencies with other classes 
	- agroup elements that share features in a general class
	- maybe Observer and MyGameEngine should be joined into one class
- improve asteroids behavior and collision
- show the type of spaceship choosen
- improve difficulty by spamming more asteroids or reducind reward


## Credits
[__libEngine.a__](https://github.com/memo-p/libGraph) his project., the GLUT based library used in this project for GUI, was written
by [Guillaume Perez](http://www.i3s.unice.fr/~gperez/).

The original author of the previous version of Spaceships Tower Defense, [Lukesmolo](https://github.com/lukesmolo), which code can be accessed by [this link](https://github.com/lukesmolo/STD).

## License
STD is released under the GPLv2 license.











