from random import*
from pygame import*
import pygame, sys


okko = display.set_mode((600, 600))


fon = transform.scale(image.load("nnn.webp"),(2000,2000))

x1 = -300
y1 = -300

class GameObject(sprite.Sprite):
    def __init__(self, pict, x,y,h,w):
        self.image = transform.scale(image.load(pict), (h,w))
        self.rect = self.image.get_rect()
        self.rect.x =x
        self.rect.y = y
        self.last_pos_x = 0
        self.last_pos_y = 0
    def ris(self):
        okko.blit(self.image, (self.rect.x, self.rect.y))
hp = 100
arm = 10 #100
stam = 100
puli = 100
class siiidjey(GameObject):
    def zdorov(self):
        global hp, arm
        if hp < 1:
            game = False
        if sprite.collide_rect(self, vrag_1):
            arm -= 20
            if arm < 0:
                hp += arm
        if sprite.collide_rect(self, vragg_pul):
            arm -= 40
            if arm < 0:
                hp += arm

    def sdvig(self):
        global x1,y1,stam
        knopki = key.get_pressed()
        if knopki[K_RIGHT]:
            x1 -= 5
        if knopki[K_LEFT]:
            x1 += 5
        if knopki[K_UP]:
            y1 += 5
        if knopki[K_DOWN]:
            y1 -= 5
        if knopki[K_RIGHT] and knopki[K_LSHIFT] and stam > 0:
            x1 -= 10
        if knopki[K_LEFT] and knopki[K_LSHIFT] and stam > 0:
            x1 += 10
        if knopki[K_UP] and knopki[K_LSHIFT] and stam > 0:
            y1 += 10
        if knopki[K_DOWN] and knopki[K_LSHIFT] and stam > 0:
            y1 -= 10
class vrag_1(GameObject):
    def peremesh(self):
        self.ris() 
    def presled(self):
        self.ris()
        if self.rect.x < x1:
            self.rect.x += 1
        if self.rect.y < y1:
            self.rect.y += 1

font.init()
font = pygame.font.Font(None, 20)
hp_l = font.render(str(hp), False, (0, 255, 13))

game = True
player  = siiidjey("Suuuuuuuudjey.jpg", 300,300, 40,40) 
import time as t
t0 = t.time()
sttime = t.time()

chel = vrag_1("png-transparent-outlast-digital-art-painting-outlast-fictional-character-painting-outlast-thumbnail.png", 200, 300, 40, 40)
chel.rect.x = x1+100
chel.rect.y = y1 + 200
    
while game:
    for i in event.get():
        if i.type == QUIT:
            game = False
    curtime = t.time()
    
    if (curtime - sttime) > 2 and arm < 95:
        sttime = t.time()
        arm+=5
    elif (curtime - sttime) > 2 and arm < 95 and arm > 100:
        sttime = t.time()
        arm == 100
    t_fin = t.time()
    

    okko.blit(fon,(x1,y1))
    hp_l = font.render(str(hp), False, (0, 255, 13))
    okko.blit(hp_l, (20,20))
    player.ris()
    player.sdvig()
    chel.presled()
    okko.blit(hp_l, (40, 20))
    display.update()
print(t_fin-t0)
