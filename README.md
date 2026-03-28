# ♟️ ChessMaster AI

> A fully self-contained chess engine with opening book, position evaluation, and AI opponent — built in a single HTML file with zero dependencies.

![HTML](https://img.shields.io/badge/HTML5-E34F26?style=flat-square&logo=html5&logoColor=white)
![CSS](https://img.shields.io/badge/CSS3-1572B6?style=flat-square&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black)
![No Dependencies](https://img.shields.io/badge/dependencies-none-brightgreen?style=flat-square)
![Single File](https://img.shields.io/badge/bundle-1%20file-blue?style=flat-square)

---

## Overview

ChessMaster AI is a browser-based chess application powered by a hand-rolled minimax engine with alpha-beta pruning, an opening book covering 100+ positions across all major opening systems, and a real-time evaluation bar. No frameworks. No servers. No install. Just open and play.

Built as a portfolio project demonstrating vanilla JavaScript game logic, tree-search AI, and polished UI design — all within a single deployable HTML file.

---

## Features

**Gameplay**
- Full legal move generation including castling, en passant, and pawn promotion
- Check, checkmate, and stalemate detection
- 50-move rule enforcement
- Move history with SAN (Standard Algebraic Notation)
- Undo system (takes back both your move and the AI's)
- Play as White or Black; board flip support

**AI Engine**
- Minimax search with alpha-beta pruning
- Three difficulty levels: Easy / Medium / Hard (depth 1–3)
- Piece-Square Tables (PST) for positional evaluation
- Move ordering (captures and promotions searched first)
- **Opening book** covering 100+ positions across all major systems (see below)
- Human-like 3–4 second thinking delay with animated indicator

**Opening Recognition**
- Live opening name displayed in the sidebar during play
- 80+ named lines detected by sequence matching — from starting position down to specific variations

**UI**
- Responsive layout — works on desktop and mobile
- Visual evaluation bar (white advantage ↑ / black advantage ↓)
- Legal move highlighting (dots for moves, rings for captures)
- Last-move highlight, check highlight
- Captured pieces display
- Pawn promotion modal

---

## Opening Book Coverage

The AI plays from a weighted opening book for the first ~14 moves per side, choosing among theoretically sound responses with natural variation.

| System | Lines Covered |
|---|---|
| **Ruy Lopez** | Morphy, Berlin, Closed, Exchange |
| **Italian Game** | Giuoco Piano, Two Knights, Fried Liver Attack |
| **Scotch Game** | Main line, Scotch Gambit |
| **Petrov Defense** | Classical, Steinitz |
| **King's Gambit** | Accepted |
| **Sicilian Defense** | Najdorf, Dragon, Scheveningen, Accelerated Dragon, Kan, Classical |
| **French Defense** | Winawer, Tarrasch, Advance, Classical |
| **Caro-Kann** | Classical, Advance, Panov Attack |
| **Scandinavian** | Main line, Mieses-Kotroc |
| **Queen's Gambit** | Declined, Accepted, Exchange |
| **Slav Defense** | Main line |
| **King's Indian** | Main line, Sämisch |
| **Nimzo-Indian** | Rubinstein, Classical |
| **Queen's Indian** | Main line |
| **Grünfeld Defense** | Exchange |
| **Modern Benoni** | Main line |
| **English Opening** | Reversed Sicilian, Four Knights, Symmetrical |
| **Réti Opening** | Main line |
_and more..._

After leaving book, the engine falls back to the minimax search.

---

## Getting Started

No install required. Download the file and open it in any modern browser.

```bash
# Clone the repo
git clone https://github.com/kazim-45/chessmaster-ai.git
cd chessmaster-ai

# Open directly — no server needed
open app.html         # macOS
start app.html        # Windows
xdg-open app.html     # Linux
```

Or just **[download the raw HTML file](./app.html)** and double-click it.

---

## How It Works

### Move Generation
All legal moves are generated from scratch on each ply: sliding pieces (bishop, rook, queen) use ray casting; knights and kings use fixed offsets; pawns handle direction-aware logic including double pushes, en passant captures, and promotion. After generation, moves are filtered through a legality check that ensures the king is not left in check.

### Search
The engine uses **minimax with alpha-beta pruning**. At each node it generates and scores all legal moves, ordering captures and promotions first to improve cutoffs. Depth is set per difficulty level (1–3 plies). At depth 0, the static evaluation function scores the board.

### Evaluation
The static evaluator sums material values and **Piece-Square Table** (PST) bonuses. PSTs encode positional preferences — knights prefer the center, kings prefer the back rank in the middlegame, passed pawns are rewarded. The score is from White's perspective; negative means Black is better.

### Opening Book
A dictionary maps SAN move sequences to weighted response arrays. On each AI move, the current move list is joined into a key; if a match exists, a random response is selected (duplicates in the array increase probability). Book play continues for up to 14 moves per side.

---

## Project Structure

```
chessmaster-ai/
└── app.html          # Entire application — HTML + CSS + JS, zero deps
```

Everything lives in one file by design: it stays portable, forkable, and instantly deployable anywhere static files are served.

---

## Roadmap

- [ ] Stockfish.js integration via Web Worker for stronger engine
- [ ] PGN import / export
- [ ] Opening explorer panel (ECO codes)
- [ ] Endgame tablebase hints
- [ ] Timed games (clock support)
- [ ] Drag-and-drop piece movement

---

## License

MIT — free to use, modify, and distribute.

---

<p align="center">Built with vanilla JS · No frameworks · No dependencies · Single file</p>
