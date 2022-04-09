| [⬅️ Features & Advantages](features-and-advantages.md) | [🏠 Home](README.md) | [Attack Tables ➡️](attack-tables.md) |

---

## Bitboard Setup

1. Create a definition for a **64-bit data type**. This will be your bitboard representation.
```c
#define U64 unsigned long long
```
2. Define constants to **represent board squares**. These will be used to index your bitboard.
```c
enum {
  a8, b8, c8, d8, e8, f8, g8, h8,
  a7, b7, c7, d7, e7, f7, g7, h7,
  a6, b6, c6, d6, e6, f6, g6, h6,
  a5, b5, c5, d5, e5, f5, g5, h5,
  a4, b4, c4, d4, e4, f4, g4, h4,
  a3, b3, c3, d3, e3, f3, g3, h3,
  a2, b2, c2, d2, e2, f2, g2, h2,
  a1, b1, c1, d1, e1, f1, g1, h1
};
```
3. Define constants to **represent side to move**.
```c
enum { white, black };
```
4. Define getters & setters for the bits in the bitboard
```c
U64 get_bit(U64 bitboard, int square) {
  return bitboard & (1ULL << square)
}

U64 set_bit(U64 bitboard, int square) {
  return bitboard | (1ULL << square)
}

U64 pop_bit(U64 bitboard, int square) {
  if (get_bit(bitboard, square)) return bitboard ^ (1ULL << square)
  return bitboard
}

// Tip: Call these functions w/ the enums from step 2!
get_bit(bitboard, e4)
bitboard = set_bit(bitboard, g6)
bitboard = pop_bit(bitboard, c2)
```
5. Define a function to print the bitboard. Very useful in testing. 
```c
void print_bitboard(U64 bitboard) {
  printf("\n");
  for (int rank = 0; rank < 8; rank++) {
    for (int file = 0; file < 8; file++) {
      if (!file) // Print rank
        printf("  %d ", 8 - rank);
      
      // Print bit state (either 1 or 0)
      int square = rank * 8 + file;
      printf(" %d", get_bit(bitboard, square));
    }
    printf("\n");
  }
  printf("\n     a b c d e f g h\n\n"); // Print board files
  printf("     Bitboard: %llud\n\n", bitboard); // Decimal representation
}
```

---

| [⬅️ Features & Advantages](features-and-advantages.md) | [🏠 Home](README.md) | [Attack Tables ➡️](attack-tables.md) |