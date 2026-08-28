# Tank 1990 — Recreación con agente de IA

Recreación del clásico **Tank 1990 (Battle City)** en Python + Pygame, con un modo de **agente inteligente** que navega un mapa generado proceduralmente desde el tanque hasta la meta, comparando **búsqueda no informada** y **búsqueda informada (A\*)**.

Proyecto académico de Inteligencia Artificial: además de recrear el juego, sirve para **visualizar cómo se comportan distintos algoritmos de búsqueda** sobre una grilla con obstáculos.

## Características

- **Generación procedural de niveles** con densidad configurable de muros (BRICK) y pasto (GRASS). Cada mapa se valida con **BFS de conectividad** para garantizar que siempre exista un camino entre el tanque y la meta.
- **Modo agente — No informado:** exploración con **DFS aleatorio + backtracking**. El tanque avanza a vecinos aleatorios no visitados y retrocede cuando se queda sin salida.
- **Modo agente — Informado:** **A\*** con heurística **Manhattan**, costo uniforme por paso y reconstrucción de la ruta óptima por punteros de padre.
- **Animación paso a paso** de ambos agentes sobre la grilla (`RandomExplorer` y `RouteFollower`).
- Menú y submenú navegables con Pygame (sprites, botones y HUD).

## La IA en detalle

| | No informado | Informado |
|---|---|---|
| Algoritmo | DFS aleatorio con backtracking | A\* |
| Heurística | — | Distancia Manhattan |
| Estructura clave | Pila (backtracking) | Cola de prioridad (`heapq`) |
| Resultado | Camino válido (no óptimo) | Camino óptimo |

La generación del mapa usa **BFS** solo para comprobar que el nivel es resoluble antes de mostrarlo, así el agente nunca queda atrapado en un mapa imposible.

## Estructura del proyecto

```
.
├── main.py     # Bucle del juego, menús, carga de assets y render
├── agent.py    # Agentes de IA: RandomExplorer (DFS), a_star_camino (A*), RouteFollower
├── word.py     # Mundo: generación de niveles, BFS de conectividad y dibujo de la grilla
└── assets      # tank.png, brick.png, grass.png, win.png, bg.jpg
```

## Cómo ejecutarlo

Requiere **Python 3.10+** y **Pygame**.

```bash
# 1. (Opcional) crear entorno virtual
python -m venv venv
source venv/bin/activate      # Windows: venv\Scripts\activate

# 2. Instalar dependencias
pip install -r requirements.txt

# 3. Ejecutar
python main.py
```

> La ventana abre en 1920×1080. Si tu pantalla es más pequeña, ajusta `WIDTH` y `HEIGHT` en `main.py`.

## Cómo se usa

1. En el menú principal, entra a **Mode Agent**.
2. Elige el modo de búsqueda:
   - **No informado** → el tanque explora aleatoriamente hasta encontrar la meta.
   - **Informado** → A\* calcula la ruta óptima y el tanque la recorre.
3. `ESC` para volver al menú.

## Posibles mejoras

- Añadir BFS/Dijkstra clásicos para comparar visualmente contra A\*.
- Mostrar en pantalla nodos explorados y longitud de la ruta de cada algoritmo.
- Combate y enemigos (mecánica original de Battle City).

## Autora

**Juana Valentina González Ardila** — Ingeniera de Sistemas
[github.com/JuanaGonzalez21](https://github.com/JuanaGonzalez21) · [juanagonzalez.dev](https://juanagonzalez.dev)
