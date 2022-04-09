| [⬅️ Attack Tables](attack-tables.md) | [🏠 Home](README.md) | [Knight Attack Table ➡️](knight-attack-table.md) |

---

# King Attack Table

The attack table for the king will be stored as an array of bitboards:

```c
U64 king_attacks[64];
```
So, if a king is on `e4`, you could easily get the attacked squares:

```c
U64 attack = king_attacks[e4]
```
Our goal is to initialize this attack table by calling a method at the beginning of your program.

---
1. Define 2 new constants to represent "not the a file" and "not the h file".

```c
/*     not A file     |       not H file
                      |
  8  0 1 1 1 1 1 1 1  |  8  1 1 1 1 1 1 1 0
  7  0 1 1 1 1 1 1 1  |  7  1 1 1 1 1 1 1 0
  6  0 1 1 1 1 1 1 1  |  6  1 1 1 1 1 1 1 0
  5  0 1 1 1 1 1 1 1  |  5  1 1 1 1 1 1 1 0
  4  0 1 1 1 1 1 1 1  |  4  1 1 1 1 1 1 1 0
  3  0 1 1 1 1 1 1 1  |  3  1 1 1 1 1 1 1 0
  2  0 1 1 1 1 1 1 1  |  2  1 1 1 1 1 1 1 0
  1  0 1 1 1 1 1 1 1  |  1  1 1 1 1 1 1 1 0
     a b c d e f g h  |     a b c d e f g h  */

const U64 not_a_file = 18374403900871474942ULL;
const U64 not_h_file = 9187201950435737471ULL;
```

2. Define a function that generates the attack bitboard for a king on any square.

```c
U64 mask_king_attacks(int square) {
  U64 attacks = 0ULL;
  U64 bitboard = set_bit(0ULL, square);

  /* 
    King offsets are: 8, 9, 7, 1

    For the shifts that move horizontally,
    bitwise 'and' the shifted bitboard with not_h_file
    or not_a_file to determine if the attack wraps
    around the board
  */

  ...
  // Example horizontal shift
  if ((bitboard >> 1) & not_h_file) attacks |= (bitboard >> 1);
  ...
  
  return attacks;
}
```
3. Define a function that loops through each square and saves the attack bitboard to the `king_attacks` array.
```c
void init_leapers_attacks()
{
    for (int square = 0; square < 64; square++)
    {
        king_attacks[square] = mask_king_attacks(square);
    }
}
```
---

| [⬅️ Attack Tables](attack-tables.md) | [🏠 Home](README.md) | [Knight Attack Table ➡️](knight-attack-table.md) |
