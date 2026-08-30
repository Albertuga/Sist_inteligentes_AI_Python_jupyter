# Sistemas_inteligentes
Juego/practica final (WUMPUS).

## El Mundo de Wumpus — Inteligencia Artificial & Minimax

Implementación interactiva en **Python** del clásico entorno del **Mundo de Wumpus** orientada a la toma de decisiones mediante agentes inteligentes. El proyecto combina un entorno dinámico con renderizado gráfico interactivo en Jupyter Notebook y algoritmos de búsqueda de adversarios (**Minimax**) para la resolución automática del juego y modos competitivos contra el usuario.

---

#### Mecánicas del Entorno

El agente debe navegar por una cuadrícula NxN con el objetivo de encontrar el tesoro evitando caer en peligros mortales:

* **Elementos del Tablero:**
  * 🧑 **Agente (`A`):** Inicia en la esquina inferior izquierda del mapa. Dispone de una flecha para abatir al Wumpus.
  * 👹 **Wumpus (`W`):** Monstruo estático que devora al agente si entra en su casilla.
  * 🕳️ **Huecos / Pozos (`C`):** Trampas dinámicas que se desplazan de forma aleatoria por casillas libres tras cada turno.
  * 💰 **Oro (`O`):** Objetivo final de la partida.
  * 💨 **Brisa (`S`):** Percepción generada en las casillas adyacentes a cada hueco.
  * 🦨 **Hedor (`H`):** Percepción generada en las casillas adyacentes al Wumpus.

---

#### 🧠 Algoritmo y Función de Utilidad

Para la toma de decisiones automática y el control adversarial (Minimax), el estado del tablero se evalúa mediante una función heurística de utilidad:

* **Recompensa por cercanía al Oro:** Basada en distancia euclídea inversa ($+20000 - d \times 1000$).
* **Penalización por cercanía al Wumpus:** Penaliza la aproximación si el monstruo sigue vivo ($-5000 + d \times 500$).
* **Penalizaciones de seguridad inmediata:** Evita casillas adyacentes con Hedor ($-2000$), Brisa ($-1000$) o Huecos directos ($-5000$).
* **Penalización por revisita:** Desincentiva bucles de exploración restando puntuación a posiciones ya exploradas.

---

#### Estructura del Repositorio

```text
├── ImagenesCasillasWumpus/                  # Sprites y assets gráficos
│   ├── CasillaAgente.png
│   ├── CasillaBrisa.png
│   ├── CasillaHedor.png
│   ├── CasillaHueco.png
│   ├── CasillaOro.png
│   ├── CasillaVacia.png
│   └── CasillaWumpus.png
├── JuegoWumpus_MuñozMorenoAlbertoRafael.ipynb # Cuaderno principal con el juego e IA
├── pics/                                    # Recursos visuales auxiliares
└── README.md

Recuerda instalar todas las depencencias necesarias para ejecutarlo (jupyter notebook)
