import pygame
import random
#initialize the pygame
pygame.init()
#creating screen of height width
screen=pygame.display.set_mode((800,600))
background=pygame.image.load('pic1.jpg')
pygame.display.set_caption('Space invaders')
try: 
 icon=pygame.image.load('spacecraft.png')
 pygame.display.set_icon(icon)
except: 
  print("cannot load")
#player
try:
 playerImg=pygame.image.load('spacecraft.png')
 playerX=350
 playerY=550
 playerX_diff=0
 playerY_diff=0
except: 
 print("player not found")
 playerImg=pygame.surface((50,50))
 playerImg.fill((255,0,0))
enemyImg=pygame.image.load('enemy.png')
enemyX=random.randint(0,800)
enemyY=random.randint(50,150)
enemyX_diff=0.3
enemyY_diff=40
#ready means u we cant see the bullet on the screen
bulletImg=pygame.image.load('bullot.jpg')
bulletX=0
bulletY=480#spaceship is at 480 so same level
bulletX_diff=0#bullet is not going to move in x direction
bulletY_diff=2
bullet_state="ready"
def player(x,y):
    screen.blit(playerImg,(playerX,playerY))
def enemy(x,y):
    screen.blit(enemyImg,(enemyX,enemyY))
def fire(x,y):
   global bullet_state
   bullet_state="fire"
   screen.blit(bulletImg,(x+16,y+10))#img and corrdinates of where 
   #do we want the bullet to appear// if we shot the bullet from x and y bullet will shot from little right side not
   #from the centre
   #
#Game Loop
running=True
while running:
   screen.fill((0,0,0))
   screen.blit(background,(0,0))
   playerY-=0.1#right hand side direction
   #any keystroke on the keyboard is also an event
   for event in pygame.event.get():
     if event.type==pygame.QUIT:
       running=False
        #red green blue
   if event.type==pygame.KEYDOWN:
        if event.key==pygame.K_LEFT:
          playerX_diff=-0.3
        if event.key==pygame.K_RIGHT:
          playerX_diff=0.3
        if event.key==pygame.K_SPACE and bullet_state=="ready":
          fire(playerX,bulletY)
   if event.type==pygame.KEYUP:
       if event.key==pygame.K_LEFT or event.key==pygame.K_RIGHT:
         playerX_diff=0
       if event.key==pygame.K_SPACE:
          fire(playerX,bulletY)
        #32*32 size of image so subract 32 from 800 if exceeds 800
   playerX+=playerX_diff   
   if playerX<=0:
      playerX=0
   
   elif playerX>=768:
     playerX=768

   enemyX+=enemyX_diff
   if enemyX<=0:
      enemyX_diff=0.3
      enemyY+=enemyY_diff
   elif enemyX>=768:
     enemyX_diff=-0.3
     enemyY+=enemyY_diff
     if bulletY<=0:
      bulletY=480
      bullet_state="ready"  
   if bullet_state=="fire":
    fire(playerX,bulletY)
    bulletY-=bulletY_diff
   player(playerX,playerY)
   enemy(enemyX,enemyY)
   pygame.display.update()
