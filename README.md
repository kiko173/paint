# paint

import pygame
import sys

# Initialize Pygame
pygame.init()

# Set display
width, height = 800, 600
screen = pygame.display.set_mode((width, height))
pygame.display.set_caption("Draw with mouse")

# Define colors
WHITE = (255, 255, 255)
BLACK = (0, 0, 0)
LINE_COLOR = (0, 0, 255)  # Blue color for drawing

# Set up screen background
screen.fill(WHITE)

# Function to handle drawing
def draw_line(start_pos, end_pos):
    pygame.draw.line(screen, LINE_COLOR, start_pos, end_pos, 5)  # Draw line with width 5

# Main loop
drawing = False
last_pos = None

while True:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            pygame.quit()
            sys.exit()
        if event.type == pygame.MOUSEBUTTONDOWN:
            drawing = True
            last_pos = pygame.mouse.get_pos()
        if event.type == pygame.MOUSEBUTTONUP:
            drawing = False
        if event.type == pygame.MOUSEMOTION and drawing:
            current_pos = pygame.mouse.get_pos()
            draw_line(last_pos, current_pos)
            last_pos = current_pos

    pygame.display.update()
