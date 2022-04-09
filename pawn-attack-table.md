| [⬅️ Knight Attack Tables](knight-attack-table.md) | [🏠 Home](README.md) | [Next ➡️](README.md) |

---

# Pawn Attack Table

The attack table for the pawn will be stored as a 2d array of bitboards. This is because white & black pawns have different attack patterns, so we need an additional dimension:

```c
U64 pawn_attacks[2][64];
```
So, if a `black` pawn is on `c6`, you could easily get the attacked squares:

```c
U64 attack = pawn_attacks[black][c6]
```
Our goal is to initialize this attack table by calling a method at the beginning of your program.

---

1. Define a function that generates the attack bitboard for a pawn of any color, on any square.

```c
U64 mask_pawn_attacks(int side, int square) {
  U64 attacks = 0ULL;
  U64 bitboard = set_bit(0ULL, square);

  /* 
    Pawn offsets are: 7, 9

    For the shifts that move horizontally,
    bitwise 'and' the shifted bitboard with not_h_file
    or not_a_file to determine if the attack wraps
    around the board
  */

  if (!side) // white pieces
  {
    if ((bitboard >> 7) & not_a_file) attacks |= (bitboard >> 7);
    if ((bitboard >> 9) & not_h_file) attacks |= (bitboard >> 9);

  } else { // black pieces
    ...
  }
  
  return attacks;
}
```
2. Modify `init_leapers_attacks` to also initialize the  `pawn_attacks` array. For each square, call `mask_pawn_attacks` for both colors. 

---

| [⬅️ Knight Attack Tables](knight-attack-table.md) | [🏠 Home](README.md) | [Next ➡️](README.md) |
