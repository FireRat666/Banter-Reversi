# Banter Reversi (Othello)

A fully synchronized multiplayer Reversi (Othello) game designed for Banter spaces. Players can place pieces on an 8x8 board, capture opponent pieces by flanking them, and the game state is automatically synced between all users in the space.

## Features

* **Multiplayer Sync**: Game state (board, current player, winner) is synced via Banter's `SetPublicSpaceProps`.
* **Valid Move Highlighting**: Valid moves for the current player are highlighted in blue on the board.
* **Automatic Rules**: Enforces standard Reversi rules, including flanking captures and turn passing if no moves are available.
* **Reset Functionality**: Includes a physical reset button to restart the game.
* **Customizable**: Position, rotation, and scale can be configured via URL parameters.

## Installation

To add Reversi to your Banter space, simply include the script in your `index.html` file. You can host the file yourself or use a direct link if available.

```html
<script src="https://banter-reversi.firer.at/Reversi.js?boardPosition=0 1.1 -2&boardRotation=0 0 0"></script>
```

## Configuration

You can configure the board's placement and behavior using query parameters in the script `src` URL.

| Parameter | Type | Default | Description |
| :--- | :--- | :--- | :--- |
| `boardPosition` | Vector3 | `0 1.1 -2` | The world position of the board center (x y z). |
| `boardRotation` | Vector3 | `0 0 0` | The rotation of the board in Euler angles (x y z). |
| `boardScale` | Vector3 | `1 1 1` | The scale of the board (x y z). |
| `resetPosition` | Vector3 | `0 0 2.5` | The local position of the reset button relative to the board. |
| `resetRotation` | Vector3 | `0 0 0` | The local rotation of the reset button. |
| `resetScale` | Vector3 | `1 1 1` | The local scale of the reset button. |
| `hideUI` | Boolean | `false` | If `true`, the reset button will not be created. |
| `instance` | String | *URL* | A unique ID for this board. Use this if you have multiple boards in one scene to keep their states separate. |

### Example: Multiple Boards

If you want two separate games going on in the same space, give them unique `instance` IDs:

```html
<!-- Table 1 -->
<script src="https://banter-reversi.firer.at/Reversi.js?instance=table1&boardPosition=5 1 0"></script>

<!-- Table 2 -->
<script src="https://banter-reversi.firer.at/Reversi.js?instance=table2&boardPosition=-5 1 0"></script>
```

## How to Play

1. **Black** moves first.
2. Click on a valid empty square (highlighted in **Blue**) to place a piece.
3. A move is valid only if it flanks one or more opponent pieces between the new piece and an existing piece of your color.
4. Flanked pieces are flipped to your color.
5. If a player cannot make a valid move, their turn is skipped.
6. The game ends when the board is full or neither player can move.
7. The player with the most pieces on the board wins.

## Requirements

* Banter SDK (automatically available in Banter spaces).
