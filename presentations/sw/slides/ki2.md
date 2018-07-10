
class: center, middle
# Künstliche Intelligenz 2

---

## Technologie
### Künstliche Intelligenz 2

__Programmiersprache(n):__
- JavaScript
- Rust

__Framework(s):__
- node.js
- neon-bindings
- Jest
- socket.io

__Methode(n) und Algorithmen:__
- MiniMax-Algorithmus

---

## Code-Snippets
### Künstliche Intelligenz 2

#### Funktion
```rust
evaluate_board(chess: Chess) -> f64
```

```rust
for x in 0..8 {
    for y in 0..8 {
        let board = Setup::board(&chess);
        let mut square = Square::from_coords(y, x).unwrap();

        if board.piece_at(square) != None {
            totalvalue += get_piece_value(&board.piece_at(square).unwrap(), 
                                          x as usize, 
                                          y as usize);
        }
    }
}
```

---

## Code-Snippets
### Künstliche Intelligenz 2

#### Funktion
```rust
minimax_root(depth: i8, chess: Chess, is_maximising_player: bool) -> String
```

```rust
let moves: MoveList = Position::legals(&chess);

for mov in moves {
    let undo_chess: Chess = chess_copy.play(&mov).unwrap();
    
    let value = minimax(depth, undo_chess, -10000.0, 10000.0, is_maximising_player);

    let mut best_move_value = best_move_value;
    
    if value >= best_move_value {
        best_move_value = value;
        best_move = mov;
    }
}
```

---

## Code-Snippets
### Künstliche Intelligenz 2

#### Funktion
```rust
minimax(i8, Chess, f64, f64, bool) -> f64
```

```rust
let moves: MoveList = Position::legals(&chess);

for mov in moves {
    if is_maximising_player == true {
        best_move = -9999.0;
        best_move = 
                max(best_move, 
                    minimax(depth - 1, chess, alpha, beta, !is_maximising_player));
        alpha = max(alpha, best_move);
    } else {
        best_move = 9999.0;
        best_move = 
                min(best_move, 
                    minimax(depth - 1, chess, alpha, beta, !is_maximising_player));
        beta = min(beta, best_move);
    }

    if beta <= alpha {
        return best_move;
    }
}
```

---

## Code-Snippets
### Künstliche Intelligenz 2

#### Funktion
```rust
minimax(i8, Chess, f64, f64, bool) -> f64
```

```rust
if depth == 0 {
    return -evaluate_board(chess);
}
```