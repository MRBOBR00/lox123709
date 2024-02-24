from pygame import* 
init()

win_width= 700
win_height = 500
FPS = 60
clock = time.Clock()
exit = False

window = display.set_mode((win_width, win_height))

mouse.set_visible(0) 
display.update() 
display.set_caption("Ping Pong")

bg = image.load("bg.jpg") 
player_l = Player('player2.png')
player_r = Player('player1.png') 
color = (255, 255, 255) 
rect_color = (255, 0, 0)

class GameSprite(sprite.Sprite): 
    def init(self, player_image, player_x, player_y, player_speed, wigth, height): 
        super().init() 
        self.image = transform.scale(image.load(player_image),(wigth, height)) 
        self.speed = player_speed 
        self.rect = self.image.get_rect()
        self.rect.x = player_x 
        self.rect.y = player_y 
    def reset(self): 
        window.blit(self.image, (self.rect.x, self.rect.y))

class Player(GameSprite): 
    def update_1(self): 
        keys = key.get_pressed() 
        if keys[K_w]and self.rect.y > 5: 
            self.rect.y -= self.speed 
        if keys[K_s]and self.rect.y < 725: 
            self.rect.y += self.speed


def update_l(self):
        keys = key.get_pressed()
        if keys[K_w] and self.rect.y > 5:
            self.rect.y -= self.speed
        if keys[K_x] and self.rect.y < win_height - 80:
            self.rect.y += self.speed



def update_r(self):
    keys = key.get_pressed()
    if keys[K_UP] and self.rect.y > 5:
        self.rect.y -= self.speed
    if keys[K_DOWN] and self.rect.y < win_height - 80:
        self.rect.y += self.speed


while exit != True:
    for e in event.get():
        if e.type == QUIT:
            exit = True
    window.blit(bg, (0,0))
    if finish != True:
        if sprite.collide_rect(player_l, ball) or sprite.collide_rect(player_r, ball):
            speed_x *= -1
        if ball.rect.y > win_height - 80 or ball.rect.y <0:
            speed_y *= - 1
        ball.update(speed_x, speed_y)
        player_l.update_1()
        player_r.update_r()
        
    else:
        window.blit
    player_r.reset()
    player_r.reset()
    ball.reset()
    display.update()
    clock.tick(FPS)
