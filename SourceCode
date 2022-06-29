import pyautogui
from time import sleep
import pygame
import sys

def Start(message, message2):
    x = 100

    sleep(5)

    counter = 0
    for i in range(x):
        message = message
        message2 = message2
        counter +=1
        pyautogui.typewrite(message, interval=0.03)
        pyautogui.press("enter")
        pyautogui.typewrite(message2, interval=0.03)
        pyautogui.press("enter")






############################### TEXT INFO HERE ################################

class create_text():
    def __init__(self, x, y, text, color, backround_color, size=32, center=False):
        self.x = x
        self.y = y
        self.text = text
        self.color = color
        self.backround_color = backround_color


        # create a font object.
        # 1st parameter is the font file
        # which is present in pygame.
        # 2nd parameter is size of the font
        self.font = pygame.font.Font(None, size)

        # create a text surface object,
        # on which text is drawn on it.
        self.text = self.font.render(text, True, color, backround_color)

        # create a rectangular object for the
        # text surface object
        self.textRect = self.text.get_rect()

        # set the center of the rectangular object.

        self.textRect.center = (x, y)
    def display_text(self):
        screen.blit(self.text, self.textRect)


############################### TEXT INFO STOPS HERE ##########################

pygame.init()
clock = pygame.time.Clock()
screen = pygame.display.set_mode([600, 500])
# basic font for user typed
base_font = pygame.font.Font(None, 32)
user_text = ''
user_text2 = ''

programIcon = pygame.image.load('icon.png')
pygame.display.set_caption('Spam Machine made by Toni Boss Official')
pygame.display.set_icon(programIcon)


# create rectangle
input_rect = pygame.Rect(50, 200, 140, 32)
input_rect2 = pygame.Rect(50, 300, 140, 32)

explaination_text = create_text(300,50,"Type your 2 messages on the boxes bellow and click the","Black","White")
explaination_text2 = create_text(300,100,"start button to begin spamming.","Black","White")
warning = create_text(300,150,"When you want to stop the machine put your mouse cersor on the right","Red","White",25)
warning2 = create_text(300,170,"top corner of your screen and it will stop. when you click start you","Red","White",25)
warning3 = create_text(300,185,"have 5 seconds untill the machine starts.","Red","White",25)

start_btn = create_text(300,400, "START", "White", "Red")



color_active = pygame.Color('lightskyblue3')
color_passive = pygame.Color('chartreuse4')
color = color_passive
color2 = color_passive

active = False
active2 = False

while True:

    for event in pygame.event.get():

        # if user types QUIT then the screen will close
        if event.type == pygame.QUIT:
            pygame.quit()
            sys.exit()

        if event.type == pygame.MOUSEBUTTONDOWN:
            if input_rect.collidepoint(event.pos):
                active = True
            else:
                active = False
            if input_rect2.collidepoint(event.pos):
                active2 = True
            else:
                active2 = False
            if start_btn.textRect.collidepoint(event.pos):
                Start(user_text, user_text2)


        if event.type == pygame.KEYDOWN:
            if active:
                # Check for backspace
                if event.key == pygame.K_BACKSPACE:

                    # get text input from 0 to -1 i.e. end.
                    user_text = user_text[:-1]

                # Unicode standard is used for string
                # formation
                else:
                    user_text += event.unicode
            if active2:
                # Check for backspace
                if event.key == pygame.K_BACKSPACE:

                    # get text input from 0 to -1 i.e. end.
                    user_text2 = user_text2[:-1]

                # Unicode standard is used for string
                # formation
                else:
                    user_text2 += event.unicode


    # it will set background color of screen
    screen.fill((255, 255, 255))

    if active:
        color = color_active
    else:
        color = color_passive
    if active2:
        color2 = color_active
    else:
        color2 = color_passive


    # draw rectangle and argument passed which should
    # be on screen
    pygame.draw.rect(screen, color, input_rect)

    text_surface = base_font.render(user_text, True, (255, 255, 255))

    pygame.draw.rect(screen, color2, input_rect2)

    text_surface2 = base_font.render(user_text2, True, (255, 255, 255))

    # render at position stated in arguments
    screen.blit(text_surface, (input_rect.x + 5, input_rect.y + 5))
    screen.blit(text_surface2, (input_rect2.x + 5, input_rect2.y + 5))
    screen.blit(explaination_text.text, explaination_text.textRect)
    screen.blit(explaination_text2.text, explaination_text2.textRect)
    screen.blit(start_btn.text, start_btn.textRect)
    warning2.display_text()
    warning.display_text()
    warning3.display_text()
    # set width of textfield so that text cannot get
    # outside of user's text input
    input_rect.w = max(100, text_surface.get_width() + 10)
    input_rect2.w = max(100, text_surface2.get_width() + 10)

    # display.flip() will update only a portion of the
    # screen to updated, not full area

    pygame.display.update()
    # clock.tick(60) means that for every second at most
    # 60 frames should be passed.

    clock.tick(60)
