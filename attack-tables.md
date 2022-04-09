| [⬅️ Bitboard Setup](bitboard-setup.md) | [🏠 Home](README.md) | [Next ➡️](#) |

# Precalculated Attack Tables

To save time when generating moves, we can manually calculate each piece's attack patterns beforehand, so a single lookup can give you the available moves. 

Pawn, Knight, and King attack tables generated very similarly, since they are non-sliding pieces. 

Bishop, Rook, and Queen are sliding pieces, and require a much more complicated attack table using Magic Bitboards. 

[Home](README.md)