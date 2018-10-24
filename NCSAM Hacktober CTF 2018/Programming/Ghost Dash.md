### Description:

Some guy created a game that he claims is unbeatable.
Prove him wrong by getting the trick-or-treater past 100 ghosts.

### Game:

```python
'''
Program Title:  UNBREAKABLE GAME
Author:         Jason Scott (Syntax)
Date:           2018
Python3.6
'''

import pygame
import time
import random
from binascii import unhexlify

pygame.init()

displayWidth = 800
displayHeight = 600
alpha = b'4142434445464748494a4b4c4d4e4f505152535455565758595a6162636465666768696a6b6c6d6e6f707172737475767778797a313233343536373839305f2d'
colBlack = (0,0,0)
colWhite = (255,255,255)
colBlock = (116,77,37)
colRed = (255,0,0)
colGreen = (0,255,0)
colBlue = (0,0,255)
colButton = (130,130,130)
colButton_hover = (200,200,200)
colButton_click = (75,75,75)
colBG = (0, 0, 26)
colGrey = (1, 1, 1)
hidden = b'666c61672d6a6b5f6e6f745f7468655f7265616c5f666c6167'

imgMySprite = pygame.image.load('img/imgPlayer.png')
imgEnemySprite = pygame.image.load('img/imgEnemy.png')
gameDisplay = pygame.display.set_mode((displayWidth, displayHeight))
pygame.display.set_caption('Ghost Dash')
clock = pygame.time.Clock()
pygame_gs = (displayWidth, displayHeight, imgMySprite.get_rect().size[0], imgMySprite.get_rect().size[1])
pause = True
pauseText = ('Continue', 'Quit')

def u(n):
	return unhexlify(n).decode('utf-8')

def chgSprite(direction):
    if direction == 'L':
        imgMySprite = pygame.image.load('img/imgSprite_L.png')
    elif direction == 'R':
        imgMySprite = pygame.image.load('img/imgSprite_R.png')
    else:
        imgMySprite = pygame.image.load('img/imgPlayer.png')

def drawButton(text, color, colorHover, colorClick, x, y, w, h, action=None):
    mousePos = pygame.mouse.get_pos()
    mouseClick = pygame.mouse.get_pressed()

    if (x + w) > mousePos[0] > x and (y + h) > mousePos[1] > y:
        pygame.draw.rect(gameDisplay, colorHover, (x, y, w, h))
        if mouseClick[0] == 1 and action != None:
            action()            
    else:
        pygame.draw.rect(gameDisplay, color, (x, y, w, h))

    textSmall = pygame.font.Font('freesansbold.ttf',20)
    textSurf, textRec = textObjects(text, textSmall)
    textRec.center = ((x + (w/2)), (y + (h/2)))
    gameDisplay.blit(textSurf, textRec)

def escaped(count):
    font = pygame.font.SysFont(None, 25)
    text = font.render(u(b'446f646765643a20') + str(count), True, colWhite)
    gameDisplay.blit(text, (0,0))

a = u(alpha)

def checkBorder(x,y,w,h):
    if x > displayWidth - (w / 2):
        return ((displayWidth - (w / 2)), y)
    elif x < 0 - (x / 2):
        return ((0 - (x / 2)), y)
    if y > displayHeight - (h / 1.5):
        return (x, (displayHeight - (h / 1.5)))
    elif y < 0 - (h / 4):
        return (x, (0 - (h / 4)))    

def get_intersect(x1,x2,w1,w2,y1,y2,h1):
    if y1 < (y2 + h1):
        if x1 > x2 and x1 < (x2 + w2) or (x1 + w1) > x2 and (x1 + w1) < (x2 + w2):
            do_coll()

def things(x, y):
	gameDisplay.blit(imgEnemySprite, (x,y))

def morty(x,y):
    gameDisplay.blit(imgMySprite, (x,y))

def textObjects(text, font):
    textSurface = font.render(text, True, colWhite)
    return textSurface, textSurface.get_rect()

def messageShow(text):
    lgText = pygame.font.Font('freesansbold.ttf', 115)
    textSurf, textRec = textObjects(text, lgText)
    textRec.center = ((displayWidth/2), (displayHeight/2))
    gameDisplay.blit(textSurf, textRec)

    pygame.display.update()

    time.sleep(2)
    gameLoop()

def closeGame():
    pygame.quit()
    quit()

def do_coll():
	messageShow(u(b'424f4f2120476f7463686121'))


def set_pref():
	return str(a[31] + a[37] + a[26] + a[32] + a[-1:])


def gameIntro():
    intro = True

    while intro:
        for event in pygame.event.get():
            if event.type == pygame.QUIT:
                pygame.quit()
                quit()

        gameDisplay.fill(colBG)
        txtLarge = pygame.font.Font('freesansbold.ttf',72)
        txtMed = pygame.font.Font('freesansbold.ttf', 32)
        textSurf, textRec = textObjects("Ghost Dash", txtLarge)
        textRec.center = ((displayWidth/2), (displayHeight/2))
        gameDisplay.blit(textSurf, textRec)

        drawButton('GO!', colButton, colButton_hover, colButton_click, (displayWidth/4 - 100), (displayHeight/1.25 - 25), 200, 50, gameLoop)
        drawButton('Quit', colButton, colButton_hover, colButton_click, (displayWidth/1.3 - 100), (displayHeight/1.25 - 25), 200, 50, closeGame)

        pygame.display.update()
        clock.tick(15)

def gameUnpause():
        global pause
        pause = False

def gamePause():

    while pause:
        for event in pygame.event.get():
            if event.type == pygame.QUIT:
                pygame.quit()
                quit()

        gameDisplay.fill(colBG)
        txtLarge = pygame.font.Font('freesansbold.ttf',115)
        textSurf, textRec = textObjects("Paused", txtLarge)
        textRec.center = ((displayWidth/2), (displayHeight/2))
        gameDisplay.blit(textSurf, textRec)

        drawButton(pauseText[0], colButton, colButton_hover, colButton_click, (displayWidth/4 - 100), (displayHeight/1.25 - 25), 200, 50, gameUnpause)
        drawButton(pauseText[1], colButton, colButton_hover, colButton_click, (displayWidth/1.3 - 100), (displayHeight/1.25 - 25), 200, 50, closeGame)

        pygame.display.update()
        clock.tick(15)

def gs(b):
    gs_ = str(a[32:34]+a[40]+a[44:46]+a[3]+a[40]+a[29]+a[32]+a[30])
    print("{}{}".format(set_pref(), gs_))

def get_flag():
	print('{}'.format(u(hidden)))

def gameLoop():
    global pause
    x = (displayWidth * 0.45)
    y = (displayHeight * 0.85)
    xChange = 0
    yChange = 0

    thingStartx = random.randrange(0, displayWidth)
    thingStarty = -600
    thingSpeed = 4
    thingWidth = 100
    thingHeight = 100
    thingCount = 1

    gss = 0
    gf = 0

    gameExit = False
    while not gameExit:
        for event in pygame.event.get():
            if event.type == pygame.QUIT:
                pygame.quit()
                quit()

            if event.type == pygame.KEYDOWN:
                if event.key == pygame.K_p:
                    pause = True
                    gamePause()
                if event.key == pygame.K_LEFT:
                    xChange = -5
                elif event.key == pygame.K_RIGHT:
                    xChange = 5
                elif event.key == pygame.K_UP:
                    yChange = -2
                elif event.key == pygame.K_DOWN:
                    yChange = 5

            if event.type == pygame.KEYUP:
                if event.key == pygame.K_LEFT or event.key == pygame.K_RIGHT:
                    xChange = 0
                if event.key == pygame.K_UP or event.key == pygame.K_DOWN:
                    yChange = 0

        x += xChange
        y += yChange

        gameDisplay.fill(colBG)

        things(thingStartx, thingStarty)
        thingStarty += thingSpeed
        morty(x,y)
        escaped(gss)

        if thingStarty > displayHeight:
            thingStarty = 0 - thingHeight
            thingStartx = random.randrange(0, displayWidth)
            gss += colGrey[0]
            gf = gss
            thingSpeed += 1
            if gf > (5*20):
                    gf = (25 * 4)
                    pauseText = gs(gf)

        if x > displayWidth - (imgMySprite.get_rect().size[0] / 2):
            x = displayWidth - (imgMySprite.get_rect().size[0] / 2)
        elif x < 0 - (imgMySprite.get_rect().size[0] / 2):
            x = 0 - (imgMySprite.get_rect().size[0] / 2)
        if y > displayHeight - (imgMySprite.get_rect().size[1] / 1.5):
            y = displayHeight - (imgMySprite.get_rect().size[1] / 1.5)
        elif y < 0 - (imgMySprite.get_rect().size[1] / 4):
            y = 0 - (imgMySprite.get_rect().size[1] / 4)

        get_intersect(x, thingStartx, imgMySprite.get_rect().size[0], thingWidth, y, thingStarty, thingHeight)

        pygame.display.update()
        clock.tick(60)

gameIntro()
gameLoop()
pygame.quit()
quit()
```
