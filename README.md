import pygame
import random

# Inicialização do Pygame
pygame.init()

# Configurações da tela
WIDTH, HEIGHT = 800, 600
screen = pygame.display.set_mode((WIDTH, HEIGHT))
pygame.display.set_caption("Space Shooter")

# Cores
WHITE = (255, 255, 255)
BLACK = (0, 0, 0)
RED = (255, 0, 0)

# Jogador
player_size = 50
player_img = pygame.Surface((player_size, player_size))
player_img.fill(WHITE)
player_rect = player_img.get_rect(center=(WIDTH/2, HEIGHT-50))

# Tiro
bullet_img = pygame.Surface((5, 10))
bullet_img.fill(RED)
bullets = []

# Inimigo
enemy_img = pygame.Surface((50, 50))
enemy_img.fill(RED)
enemies = []

# Relógio
clock = pygame.time.Clock()

# Função para criar inimigos
def create_enemy():
    enemy = enemy_img.get_rect(center=(random.randint(50, WIDTH-50), 0))
    enemies.append(enemy)

# Loop principal
running = True
while running:
    screen.fill(BLACK)
    
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False
        
        if event.type == pygame.KEYDOWN:
            if event.key == pygame.K_SPACE:
                bullet_rect = bullet_img.get_rect(midtop=player_rect.midtop)
                bullets.append(bullet_rect)

    keys = pygame.key.get_pressed()
    if keys[pygame.K_LEFT] and player_rect.left > 0:
        player_rect.move_ip(-5, 0)
    if keys[pygame.K_RIGHT] and player_rect.right < 
