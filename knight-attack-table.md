| [⬅️ King Attack Tables](king-attack-table.md) | [🏠 Home](README.md) | [Pawn Attack Table ➡️](pawn-attack-table.md) |

---

# Knight Attack Table
The attack table for the knight will be stored as an array of bitboards:

```c
U64 knight_attacks[64];
```
So, if a knight is on `c6`, you could easily get the attacked squares:

```c
U64 attack = knight_attacks[c6]
```
Our goal is to initialize this attack table by calling a method at the beginning of your program.

---

1. Define 2 new constants to represent "not the a or b file" and "not the h or g file".

```c
/*     not AB file    |       not HG file
                      |
  8  0 0 1 1 1 1 1 1  |  8  1 1 1 1 1 1 0 0
  7  0 0 1 1 1 1 1 1  |  7  1 1 1 1 1 1 0 0
  6  0 0 1 1 1 1 1 1  |  6  1 1 1 1 1 1 0 0
  5  0 0 1 1 1 1 1 1  |  5  1 1 1 1 1 1 0 0
  4  0 0 1 1 1 1 1 1  |  4  1 1 1 1 1 1 0 0
  3  0 0 1 1 1 1 1 1  |  3  1 1 1 1 1 1 0 0
  2  0 0 1 1 1 1 1 1  |  2  1 1 1 1 1 1 0 0
  1  0 0 1 1 1 1 1 1  |  1  1 1 1 1 1 1 0 0
     a b c d e f g h  |     a b c d e f g h  */

const U64 not_ab_file = 18229723555195321596ULL;
const U64 not_hg_file = 4557430888798830399ULL;
```

2. Define a function that generates the attack bitboard for a knight on any square.

```c
U64 mask_knight_attacks(int square) {
  U64 attacks = 0ULL;
  U64 bitboard = set_bit(0ULL, square);

  /* 
    Knight offsets are: 17, 15, 10, 6

    For the shifts that move horizontally by 1,
    bitwise 'and' the shifted bitboard with not_h_file
    or not_a_file to determine if the attack wraps
    around the board

    For the shifts that move horizontally by 2,
    bitwise 'and' the shifted bitboard with not_hg_file
    or not_ab_file to determine if the attack wraps
    around the board
  */

  ...
  // Example horizontal shifts
  if ((bitboard >> 15) & not_a_file) attacks |= (bitboard >> 15);
  if ((bitboard >> 10) & not_hg_file) attacks |= (bitboard >> 10);
  ...
  
  return attacks;
}
```
3. Modify `init_leapers_attacks` to also initialize the  `knight_attacks` array.

---

| [⬅️ King Attack Tables](king-attack-table.md) | [🏠 Home](README.md) | [Pawn Attack Table ➡️](pawn-attack-table.md) |
