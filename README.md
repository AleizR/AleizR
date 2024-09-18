import numpy as np
import matplotlib.pyplot as plt

# Función para dibujar una flor
def dibujar_flor(x, y, tamaño, pétalos, color_flor, color_centro):
    theta = np.linspace(0, 2 * np.pi, 100)
    
    for i in range(pétalos):
        angulo = (2 * np.pi / pétalos) * i
        x_petalo = tamaño * np.cos(theta + angulo) + x
        y_petalo = tamaño * np.sin(theta + angulo) + y
        plt.fill(x_petalo, y_petalo, color=color_flor, alpha=0.8)  # Brillante con alpha
    
    # Centro de la flor
    centro = plt.Circle((x, y), tamaño * 0.2, color=color_centro, zorder=10)
    plt.gca().add_patch(centro)

# Configuraciones del gráfico
fig, ax = plt.subplots()
ax.set_aspect('equal')
ax.set_facecolor('black')  # Fondo oscuro para resaltar el brillo

# Dibujar varias flores
colores_flores = ['#FFFF00', '#FFFF33', '#FFD700']  # Diferentes tonos de amarillo
for i in range(5):
    x = np.random.uniform(-10, 10)
    y = np.random.uniform(-10, 10)
    tamaño = np.random.uniform(0.5, 2)
    pétalos = np.random.randint(5, 10)
    color_flor = np.random.choice(colores_flores)
    
    dibujar_flor(x, y, tamaño, pétalos, color_flor, '#FFA500')  # Centro naranja brillante

# Ajustar límites y ocultar ejes
plt.xlim(-12, 12)
plt.ylim(-12, 12)
plt.axis('off')

# Mostrar gráfico
plt.show()
