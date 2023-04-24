<img src="icon.png" align="right" />

# The Zeus Cloud Game :joystick:

## The Mission	:bulb:

Zeus the god of Olympus is trapped in a spiral of clouds and needs to clear Olympus of all of them. Zeus is the god of the sky and the air and he will be the only one capable of achieving this mission. You, together with him, will manage to clear the Olympus of all of them. Join in to him in this exciting adventure

## Inicialization of the Game :video_game:

```
manuelzambrano@Manuels-MacBook-Pro game % python3 mycloud.py 
```

## Environment
This project is interpreted/tested on Ubuntu 14.04 LTS using python3 (version 3.4.3)

## File Descriptions & Assets :mag_right:

* `player.png` -  Main graphic character.
* `Games.ttf` - Typography.
* `mycloud.py` - Code.
* `lasser.png` - Lasser graphic.
* `background.png` - Background graphic. 
* `sound1.mp3` - shot sound.
* `sound2.mp3` - Colition between the bullet and the cloud.
* `sound3.mp3` - Background music.
* `cloud1.png` - Dark cloud graphic.
* `cloud2.png` - Dark cloud graphic.
* `cloud3.png` - Dark cloud graphic.
* `cloud4.png` - Dark cloud graphic.
* `cloud5.png` - Dark cloud graphic.
* `cloud6.png` - Gray cloud graphic.
* `cloud7.png` - Gray cloud graphic.
* `cloud8.png` - Gray cloud graphic.
* `cloud9.png` - Gray cloud graphic.
* `cloud10.png` - Gray cloud graphic.
* `cloud11.png` - Light graphic cloud.
* `cloud12.png` - Blue cloud graphic.
* `cloud13.png` - Blue cloud graphic.
* `cloud14.png` - Blue cloud graphic.
* `cloud15.png` - Blue cloud graphic.
* `regularExplosion00.png` - Explotion graphic.
* `regularExplosion01.png` - Explotion graphic.
* `regularExplosion02.png` - Explotion graphic.
* `regularExplosion03.png` - Explotion graphic.
* `regularExplosion04.png` - Explotion graphic.
* `regularExplosion05.png` - Explotion graphic.
* `regularExplosion06.png` - Explotion graphic.
* `regularExplosion08.png` - Explotion graphic.


## Code Structure with examples

1. The pygame and random libraries are imported first.
```
import pygame
import random
```

2. Constants such as the width and height of the screen, and colors in RGB are defined.
```
WIDTH = 1138
HEIGHT = 640
BLACK = (0, 0, 0)
WHITE = (255, 255, 255)
GREEN = (0, 255, 0)
```

3. Pygame and its sound mixer are initialized. Then a window is created with the defined screen size.
```
pygame.init()
pygame.mixer.init()
screen = pygame.display.set_mode((WIDTH, HEIGHT))
pygame.display.set_caption("Shooter")
clock = pygame.time.Clock()
```

4. The draw_text function is defined, which will be used later to draw text on the screen.
```
def draw_text(surface, text, size, x, y):
    font = pygame.font.SysFont("games", size)
    text_surface = font.render(text, True, (255, 255, 255))
    text_rect = text_surface.get_rect()
    text_rect.midtop = (x, y)
    surface.blit(text_surface, text_rect)
```

5. The draw_shield_bar function is defined, which is used to display a shield bar on the screen.
```
def draw_shield_bar(surface, x, y, percentage):
    BAR_LENGHT = 100
    BAR_HEIGHT = 10
    fill = (percentage / 100) * BAR_LENGHT
    border = pygame.Rect(x, y, BAR_LENGHT, BAR_HEIGHT)
    fill = pygame.Rect (x, y, fill, BAR_HEIGHT)
    pygame.draw.rect(surface, GREEN, fill)
    pygame.draw.rect(surface, WHITE, border, 2)
```

6. The Player class is defined, which is the object controlled by the player in the game. It has methods to move and shoot.
```
class Player(pygame.sprite.Sprite):
	def __init__(self):
		super().__init__()
		self.image = pygame.image.load("player.png").convert()
		self.image.set_colorkey(BLACK)
		self.rect = self.image.get_rect()
		self.rect.centerx = WIDTH // 2
		self.rect.bottom = HEIGHT - 10
		self.speed_x = 0
		self.shield = 100
```

7. The Cloud class is defined, which represents the clouds that fall from the top of the screen.
```
class Meteor(pygame.sprite.Sprite):
	def __init__(self):
		super().__init__()
		self.image = random.choice(meteor_images)
		self.image.set_colorkey(BLACK)
		self.rect = self.image.get_rect()
		self.rect.x = random.randrange(WIDTH - self.rect.width)
		self.rect.y = random.randrange(-150, -100)
		self.speedy = random.randrange(1, 10) # velocidad de las nubes
		self.speedx = random.randrange(-5, 5)
	
	def update(self):
		self.rect.x += self.speedx
		self.rect.y += self.speedy
		if self.rect.top > HEIGHT + 10 or self.rect.left < -40 or self.rect.right > WIDTH + 22 :
			self.rect.x = random.randrange(WIDTH - self.rect.width)
			self.rect.y = random.randrange(-100, -40)
			self.speedy = random.randrange(1, 8) 
```

8. The Cloud class is defined, which is the object that the player shoots to destroy the clouds.
```
class Cloud(pygame.sprite.Sprite):
	def __init__(self, x, y):
		super(). __init__()
		self.image = pygame.image.load("lasser1.png")
		self.image.set_colorkey(BLACK)
		self.rect = self.image.get_rect()
		self.rect.y = y
		self.rect.centerx = x
		self.speedy = -10

	def update(self):
		self.rect.y += self.speedy
		if self.rect.bottom < 0:
			self.kill()
```

9. The show_go_screen function is defined, which displays the game's start screen.
```
def show_go_screen():
	screen.blit(background, [0, 0])
	draw_text(screen, "The Zeus Cloud", 65, WIDTH // 2, HEIGHT / 4)
	draw_text(screen, "ZEUS GAME", 35, WIDTH // 2, HEIGHT // 2)
	draw_text(screen, "Press any key to begin", 30, WIDTH //2, HEIGHT * 3/4)
	pygame.display.flip()
	waiting = True
	while waiting:
		clock.tick(60)
		for event in pygame.event.get():
			if event.type == pygame.QUIT:
					pygame.quit()
			if event.type == pygame.KEYUP:
					waiting = False

```

10. A list of cloud images is loaded into the variable cloud_images.
```
cloud_images = []
cloud_list = ["cloud1.png", "cloud2.png", "cloud3.png", "cloud4.png", "cloud5.png", "cloud6.png", "cloud7.png", "cloud8.png", "cloud9.png", "cloud10.png",
            	"cloud11.png", "cloud12.png", "cloud13.png", "cloud14.png", "cloud15.png"]
for img in cloud_list:
    cloud_images.append(pygame.image.load(img).convert())

```

11. A list of explosion images is loaded into the explosion_anim variable.
```
explosion_anim = []
for i in range(9):
        file = "regularExplosion0{}.png".format(i)
        img = pygame.image.load(file).convert()
        img.set_colorkey(BLACK)
        img_scale = pygame.transform.scale(img, (70, 70))
        explosion_anim.append(img_scale)
```

12. The Explosion class is defined, which is used to animate an explosion when a collision occurs.
```
class Explosion(pygame.sprite.Sprite):
    def __init__(self, center):
        super().__init__()
        self.image = explosion_anim[0]
        self.rect = self.image.get_rect()
        self.rect.center = center
        self.frame = 0
        self.last_update = pygame.time.get_ticks()
        self.frame_rate = 50 #VELOCIDAD DE LA EXPLOSION
        
    def update(self):
        now = pygame.time.get_ticks()
        if now - self.last_update > self.frame_rate:
            self.last_update = now
            self.frame +=1
            if self.frame ==len(explosion_anim):
                self.kill()
            else:
                center = self.rect.center
                self.image = explosion_anim[self.frame]
                self.rect = self.image.get_rect()
                self.rect.center = center
```

## Authors:

* Nathen Willians - @Alleywaynate
* Manuel Zambrado - @mnlazs
* Dae Thomas - @
