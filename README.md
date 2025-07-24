# Astro Armada: Battleship

🌌🚀 A Battleship-inspired game with a futuristic aesthetic, adjustable AI difficulty, smart ship placement, and immersive visual and audio feedback!  
A personal practice project for JavaScript and Jest.  
🌐 Built for The Odin Project Online Course.

## Live Demo

[Play the Game](https://joelbaldapan.github.io/astroarmada-battleship/)  

## Features

- **Classic Battleship Gameplay**: Place your ships and try to sink the opponent’s fleet.
- **Adjustable AI Difficulty**: Four AI levels:
  - **Easy**: Random attacks.
  - **Normal**: Attacks adjacent cells after a hit.
  - **Hard**: Checkerboard pattern with adjacent targeting.
  - **Extreme**: Probability map for strategic attacks.
- **Probability & Target Visualizations**: See how the Extreme AI thinks.

## Getting Started

### Installation

1. **Clone the repository:**

   ```sh
   git clone https://github.com/joelbaldapan/astroarmada-battleship.git
   cd astroarmada-battleship
   ```

2. **Install dependencies:**

   ```sh
   npm install
   ```

3. **Run the game locally:**

   - Open `index.html` in your browser.

4. **Run tests:**
   ```sh
   npm test
   ```

---

## Project Structure

```
src/
  main.js            # Main game logic and DOM manipulation
  style.css          # Styles and custom fonts
  assets/            # Audio, fonts, images
  factories/         # Game logic factories (player, ship, gameboard)
tests/
  factories.test.js  # Jest unit tests
index.html           # Main HTML file
package.json         # Project metadata and scripts
```

## About the AI

Astro Armada: Battleship features four AI difficulty levels, each with unique strategies:

- **Easy (Random):**  
  The AI selects attack coordinates completely at random, with no memory or strategy.

- **Normal (Adjacent):**  
  The AI attacks randomly until it scores a hit. After a hit, it enters "adjacent mode" and targets neighboring cells to try to sink the ship. If the ship is sunk, it returns to random attacks.

- **Hard (Checkerboard):**  
  The AI attacks in a checkerboard pattern, ensuring every ship can be found efficiently. When it scores a hit, it switches to adjacent targeting like the Normal AI.

- **Extreme (Probability Map):**  
  The AI uses a probability map to determine the most likely locations of your ships:
  1. **Reset Probability Map:**  
     Every cell's probability is set to zero.
  2. **Update Probability Map:**  
     For each remaining ship, the AI checks all possible placements (horizontal and vertical) that don't overlap with previous misses or sunk ships. Each valid placement increases the probability score of the involved cells.
     - If the AI has a hit on an unsunk ship, it enters "adjacent mode" and focuses probability calculations around those hits.
  3. **Select Target:**  
     The AI attacks the cell(s) with the highest probability. If there are ties, it picks randomly among them.
  4. **Repeat:**  
     After each attack, the probability map is recalculated based on the updated board state.

You can toggle visualizations in-game to see the Extreme AI’s probability map and planned targets.

**Implementation:**

- The AI logic is implemented in [`playerFactory.js`](src/factories/playerFactory.js) (see the `decideAI` method and the `probabilityAI` class).
- The game controller coordinates AI moves in [`main.js`](src/main.js).

## Credits

- Developed by Joel Baldapan
- For The Odin Project

