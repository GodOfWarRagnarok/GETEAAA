from random import*
from pygame import*
import pygame, sys


okko = display.set_mode((1280,700))


fon = transform.scale(image.load("saratov.png"),(2500,2500))

x1 = 0
y1 = 0

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
        
        global x1,y1,stam,x,y
        knopki = key.get_pressed()
        if knopki[K_RIGHT] and x1 > -1110:
            x1 -= 5
        if knopki[K_LEFT] and x1 < 0:
            x1 += 5
        if knopki[K_UP] and y1 < 0:
            y1 += 5
        if knopki[K_DOWN] and y1 > -1800:
            y1 -= 5
        if knopki[K_RIGHT] and x1 < -1100:
            x1 -= 5
        if knopki[K_LEFT] and x1 < 0:
            x1 += 5
        if knopki[K_UP] and y1 < 0:
            y1 += 5
        if knopki[K_DOWN] and y1 > -1800:
            y1 -= 5

        #if knopki[K_RIGHT] and knopki[K_LSHIFT] and stam > 0:
        #    x1 -= 10
        #if knopki[K_LEFT] and knopki[K_LSHIFT] and stam > 0:
        #    x1 += 10
        #if knopki[K_UP] and knopki[K_LSHIFT] and stam > 0:
        #    y1 += 10
        #if knopki[K_DOWN] and knopki[K_LSHIFT] and stam > 0:
        #    y1 -= 10
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
player  = siiidjey("Suuuuuuuudjey.jpg", 640,350, 60,40) 
import time as t
t0 = t.time()
sttime = t.time()

    
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
    
    okko.fill((100,100,255))
    okko.blit(fon,(x1,y1))
    okko.blit(fon,(0,0),(0,0,80,80))
    hp_l = font.render(str(hp), False, (0, 255, 13))
    player.ris()
    player.sdvig()
    okko.blit(hp_l, (40, 20))
    display.update()
print(t_fin-t0)
