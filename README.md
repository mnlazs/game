# THE ZEUS CLOUD 

## The Mission

Zeus the god of Olympus is trapped in a spiral of clouds and needs to clear Olympus of all of them. Zeus is the god of the sky and the air and he will be the only one capable of achieving this mission. You, together with him, will manage to clear the Olympus of all of them. Join in to him in this exciting adventure

## Inicialization of the Game

```
manuelzambrano@Manuels-MacBook-Pro game % python3 mycloud.py 
```

## Environment
This project is interpreted/tested on Ubuntu 14.04 LTS using python3 (version 3.4.3)

## File Descriptions & Assets
A brief explanation of what is the purpose of each file according to its extension
List of extnsions:
* `sound.mp3` - Effects and background music of the game
* `files.png` - Game graphics
* `mycloud.py` - main file where the code is written
* `Games.ttf` - typography

### Assets:


* `player.png`
* `Games.ttf`
* `sound1.mp3`
* `sound2.mp3`
* `sound3.mp3`
* `cloud1.png`
* `cloud2.png`
* `cloud3.png`
* `cloud4.png`
* `cloud5.png`
* `cloud6.png`
* `cloud7.png`
* `cloud8.png`
* `cloud9.png`
* `mycloud.py`
* `cloud10.png`
* `cloud11.png`
* `cloud12.png`
* `cloud13.png`
* `cloud14.png`
* `cloud15.png`
* `lasser.png`
* `background.png`
* `regularExplosion00.png`
* `regularExplosion01.png`
* `regularExplosion02.png`
* `regularExplosion03.png`
* `regularexgplosion04.png`
* `regularExplosion05.png`
* `regularExplosion06.png`
* `regularExplosion08.png`


## Code Structure with examples

1. The pygame and random libraries are imported first.
```
import pygame
import random
```

2.Constants such as the width and height of the screen, and colors in RGB are defined.
‘‘‘
WIDTH = 1138
HEIGHT = 640
BLACK = (0, 0, 0)
WHITE = (255, 255, 255)
GREEN = (0, 255, 0)
‘‘‘
3.Pygame and its sound mixer are initialized. Then a window is created with the defined screen size.
4.The draw_text function is defined, which will be used later to draw text on the screen.
5.The draw_shield_bar function is defined, which is used to display a shield bar on the screen.
6.The Player class is defined, which is the object controlled by the player in the game. It has methods to move and shoot.
7.The Meteor class is defined, which represents the meteors that fall from the top of the screen.
8.The Bullet class is defined, which is the object that the player shoots to destroy the meteors.
9.The show_go_screen function is defined, which displays the game's start screen.
10.A list of meteor images is loaded into the variable meteor_images.
11.A list of explosion images is loaded into the explosion_anim variable.
12.The Explosion class is defined, which is used to animate an explosion when a collision occurs.

## Examples: 

```
➜  AirBnB_clone git:(feature) ✗ ./console.py
(hbnb) create User
bb4f4b81-7757-460b-9263-743c9ea6fef6
(hbnb) show User bb4f4b81-7757-460b-9263-743c9ea6fef6
[User] (bb4f4b81-7757-460b-9263-743c9ea6fef6) {'updated_at': datetime.datetime(2019, 11, 13, 17, 7, 45, 492139), 'id': 'bb4f4b81-7757-460b-9263-743c9ea6fef6', 'created_at': datetime.datetime(2019, 11, 13, 17, 7, 45, 492106)}
(hbnb) all User
["[User] (bb4f4b81-7757-460b-9263-743c9ea6fef6) {'updated_at': datetime.datetime(2019, 11, 13, 17, 7, 45, 492139), 'id': 'bb4f4b81-7757-460b-9263-743c9ea6fef6', 'created_at': datetime.datetime(2019, 11, 13, 17, 7, 45, 492106)}"]
(hbnb) update User bb4f4b81-7757-460b-9263-743c9ea6fef6 name Betty
['User', 'bb4f4b81-7757-460b-9263-743c9ea6fef6', 'name', 'Betty']
(hbnb) all User
["[User] (bb4f4b81-7757-460b-9263-743c9ea6fef6) {'updated_at': datetime.datetime(2019, 11, 13, 17, 7, 45, 492139), 'id': 'bb4f4b81-7757-460b-9263-743c9ea6fef6', 'name': 'Betty', 'created_at': datetime.datetime(2019, 11, 13, 17, 7, 45, 492106)}"]
(hbnb) destroy User bb4f4b81-7757-460b-9263-743c9ea6fef6
(hbnb) all User
[]
(hbnb) show User
** instance id missing **
(hbnb)

```

```
➜  AirBnB_clone git:(feature) ✗ ./console.py
(hbnb) User.create
*** Unknown syntax: User.create
(hbnb) User.create()
e6ee5344-04ef-454d-84e4-ba6fc613f1b4
(hbnb) User.all()
["[User] (e6ee5344-04ef-454d-84e4-ba6fc613f1b4) {'id': 'e6ee5344-04ef-454d-84e4-ba6fc613f1b4', 'updated_at': datetime.datetime(2019, 11, 13, 17, 14, 1, 963404), 'created_at': datetime.datetime(2019, 11, 13, 17, 14, 1, 963373)}"]
(hbnb) User.show()
** instance id missing **
(hbnb) User.show(e6ee5344-04ef-454d-84e4-ba6fc613f1b4)
[User] (e6ee5344-04ef-454d-84e4-ba6fc613f1b4) {'id': 'e6ee5344-04ef-454d-84e4-ba6fc613f1b4', 'updated_at': datetime.datetime(2019, 11, 13, 17, 14, 1, 963404), 'created_at': datetime.datetime(2019, 11, 13, 17, 14, 1, 963373)}
(hbnb) User.update("e6ee5344-04ef-454d-84e4-ba6fc613f1b4", "name", "Betty")
['User', '"e6ee5344-04ef-454d-84e4-ba6fc613f1b4"', '"name"', '"Betty"']
(hbnb) User.all()
['[User] (e6ee5344-04ef-454d-84e4-ba6fc613f1b4) {\'"name"\': \'"Betty"\', \'id\': \'e6ee5344-04ef-454d-84e4-ba6fc613f1b4\', \'updated_at\': datetime.datetime(2019, 11, 13, 17, 14, 1, 963404), \'created_at\': datetime.datetime(2019, 11, 13, 17, 14, 1, 963373)}']
(hbnb) User.destroy(e6ee5344-04ef-454d-84e4-ba6fc613f1b4)
(hbnb) User.all()
[]
(hbnb) quit
➜  AirBnB_clone git:(feature) ✗

```

## Authors:

* Ricardo Corona - @LW068
* Manuel Zambrado - @mnlazs
