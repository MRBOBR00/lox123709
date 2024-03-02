from pygame import *
bg = image.load("bg.jpg")
bg = transform.scale(bg, (650, 750))

# Создание окна
window = display.set_mode((650, 750))
display.set_caption("ping pong")
fps = 60
clock = time.Clock()

class GameSprite(sprite.Sprite):
    def __init__(self, player_image, player_x, player_y, player_speed, width, height):
        super().__init__()
        self.image = transform.scale(image.load(player_image), (width, height))
        self.speed = player_speed
        self.rect = self.image.get_rect()
        self.rect.x = player_x
        self.rect.y = player_y

    def reset(self):
        window.blit(self.image, (self.rect.x, self.rect.y))

class Player(GameSprite):
    def __init__(self, player_image, player_x, player_y, player_speed, width, hieght, speed):

    def update_l(self):
        keys = key.get_pressed()
        if keys[K_w] and self.rect.y > 5:
            self.rect.y -= self.speed
        if keys[K_s] and self.rect.y < 620:
            self.rect.y += self.speed

    def update_r(self):
        keys = key.get_pressed()
        if keys[K_UP] and self.rect.y > 5:
            self.rect.y -= self.speed
        if keys[K_DOWN] and self.rect.y < 620:
            self.rect.y += self.speed


class Ball(GameSprite):
    def __init__(self, color, width, height, speed_x, speed_y):
        def update(self):
            self.rect.x += self.speed_x
            self.rect.y += self.speed_y

exit = False

player1 = Player("player1.png", 30, 30, 4, 50, 150)
player2 = Player("player2.png", 580, 30, 4, 50, 150)
ball = Ball((255, 255, 255), 20, 20, 1, 1)

all_sprites = sprite.Group()
all_sprites.add(player1, player2, ball)

speed_y = 0.5
speed_x = 0.5
finish = False
win_height = 0

while exit != True:
    for e in event.get():
        if e.type == QUIT:
            exit = True
    keys = key.get pressed()
    window.blit(bg, (0,0))
    if finish != True:
        if sprite.collide_rect(player1, ball):
            speed_x *= -1
        if ball.rect.y > win_height - 80 or ball.rect.y < 0:
            speed_y *= -1
        ball.update()
        player1.update_l()
        player2.update_r()
        player2.reset()
        player1.reset()
        ball.reset()

    display.update()
    clock.tick(fps)
    
