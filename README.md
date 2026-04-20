# UNO — Adversarial Search Simulation

An AI-powered UNO card game simulation built in Python as part of an Artificial Intelligence assignment. Three players compete against each other, each driven by a different search algorithm. The game includes both a terminal interface and a graphical GUI built with Tkinter.

---

## Overview

The simulation pits three AI players against each other in a simplified variant of UNO:

- **Player 1** uses Minimax with a defensive evaluation strategy.
- **Player 2** uses Expectimax with an offensive evaluation strategy.
- **Player 3** uses Minimax (simulation mode by default), but can also be switched to manual mode where a human player picks the moves.

---

## Game Rules

The deck contains 92 cards across four colors: Red, Green, Blue, and Yellow. Each color has two copies of cards numbered 1 through 9, one card of value 0, and four Skip cards.

A move is valid if the card being played matches either the color or the value of the top card on the discard pile.

On each turn, the current player plays a valid card from their hand onto the discard pile. If no valid card exists, the player draws one card from the deck and their turn ends. Playing a Skip card causes the next player in order to be skipped entirely.

The game ends when a player empties their hand (that player wins) or the deck runs out of cards.

---

## Algorithms

### Minimax

Minimax treats the current player as the MAX node and all opponents as MIN nodes. It searches to a depth of 3 and evaluates positions using the defensive evaluation function. It assumes opponents will always make the move that is worst for the current player.

### Expectimax

Expectimax treats opponent turns as chance nodes rather than adversarial ones. Opponent moves are averaged rather than minimized, reflecting the uncertainty of real opponent behavior. It searches to a depth of 3 and uses the offensive evaluation function.

### Evaluation Function

Both algorithms share the same variables:

- **CAI** — number of cards in the AI player's hand
- **COPP** — average number of cards in opponents' hands
- **S** — number of Skip cards in the AI player's hand

The two strategies compute scores differently:

- **Defensive (Minimax):** `50 - 7*CAI + 2*COPP + 4*S`
- **Offensive (Expectimax):** `50 - 5*CAI + 3*COPP + 2*S`

The defensive formula penalizes having many cards more heavily and values Skip cards highly, prioritizing self-preservation. The offensive formula places more weight on opponents having many cards, encouraging aggressive play when the opponent is disadvantaged.

---

## Requirements

This project uses only Python standard libraries. No external packages are required.

- Python 3.x
- `tkinter` (included with most standard Python installations)
- `random` (standard library)

---

## How to Run

### Terminal Mode

Run the notebook cells in order. When prompted, type `simulation` or `manual` to choose the mode for Player 3. The game will print the game tree, each player's decision, and the board state after every turn.

### GUI Mode

Run the final cell in the notebook to launch the Tkinter GUI. The window displays all three players' hands, the top card, the deck count, an action log, and a scored move breakdown for the player about to act.

Use the **Next Turn** button to advance the game one step at a time. Use the **Reset** button to start a new game. Use the **P3 mode** toggle to switch Player 3 between simulation and manual control. In manual mode, card buttons appear for Player 3's turn so you can pick which card to play.

---

## Project Structure

```
.
├── i242508_HarisOwais_A2.ipynb    # Full implementation and simulation notebook
└── README.md                      # This file
```

---

## GitHub Repository

`https://github.com/HarisOwais-i242508/UNO-Game-24i-2508-Haris-Owais-AI-Assignment-2`
