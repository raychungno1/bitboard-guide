| [⬅️ Home](README.md) | [🏠 Home](README.md) | [Bitboard Setup ➡️](bitboard-setup.md) |

## Bitboard Features & Advantages

* **Tiny board** reprentation
* Easily generate **precalculated attack tables**
  * Save time when calculating piece attacks
  * A single lookup instead of using loops
* **Tiny move** representation encodes:
  * Source square
  * Target square
  * Promoted piece
  * Capture flag
  * Double pawn flag
  * Enpassant flag
  * Castling
* **Copy/make approach** for making moves
  * Preserve board state before making a move
  * Restore board state for undo
* Move ordering supports **minimax** search
  * Alpha-beta pruning
  * Iterative deepening
* Maintains simple & fast **evaluation functions**

| [⬅️ Home](README.md) | [🏠 Home](README.md) | [Bitboard Setup ➡️](bitboard-setup.md) |
