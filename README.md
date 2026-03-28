```markdown
# ♟️ ChessMaster AI

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![JavaScript](https://img.shields.io/badge/JavaScript-ES6+-F7DF1E?logo=javascript)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
[![Chess](https://img.shields.io/badge/Chess-AI-8B5A2B?logo=chess)](https://en.wikipedia.org/wiki/Chess)

<p align="center">
  <img src="chessmaster.png" alt="ChessMaster AI Gameplay" width="800">
</p>

A sophisticated browser-based chess engine featuring an intelligent AI opponent with adjustable difficulty, comprehensive opening book integration, and a sleek modern interface. Play against a chess AI that uses alpha-beta pruning with position evaluation and piece-square tables for realistic gameplay.

**[Live Demo](https://kazim-45.github.io/chessmaster-ai)** | **[Report Bug](https://github.com/kazim-45/chessmaster-ai/issues)** | **[Request Feature](https://github.com/kazim-45/chessmaster-ai/issues)**

## ✨ Features

### 🤖 Intelligent AI Opponent
- **Three difficulty levels** (Easy, Medium, Hard)
- **Alpha-beta pruning** with move ordering for optimal search efficiency
- **Position evaluation** using piece-square tables
- **Human-like delay** (3-4 seconds) for natural gameplay feel
- **Opening book integration** for realistic early-game moves

### 📚 Comprehensive Opening Book
- **200+ opening variations** covering all major systems
- **Weighted move selection** for natural variety
- **Openings included**: Ruy Lopez, Sicilian Defense, Queen's Gambit, King's Indian, French Defense, Caro-Kann, and many more
- **Automatic opening detection** with real-time display

### 🎮 Game Features
- **Play as White or Black** - choose your side
- **Flip board perspective** - always view from your side
- **Undo moves** - take back mistakes
- **Complete move history** with SAN notation
- **Real-time evaluation bar** showing position advantage
- **Captured pieces display** for both players
- **Check and checkmate detection**
- **Stalemate and draw detection** (50-move rule, insufficient material)
- **Pawn promotion** with piece selection

### 🎨 Modern User Interface
- **Fully responsive design** - works on desktop, tablet, and mobile
- **Professional chess pieces** with color-coded styling
- **Move highlighting** (selected piece, last move, legal moves)
- **Check indication** with visual feedback
- **Game status panel** with turn and check information
- **Smooth animations** and transitions

## 🚀 Quick Start

### Play Online
Visit the live demo: **[https://kazim-45.github.io/chessmaster-ai](https://kazim-45.github.io/chessmaster-ai)**

### Run Locally
```bash
# Clone the repository
git clone https://github.com/kazim-45/chessmaster-ai.git

# Navigate to the directory
cd chessmaster-ai

# Open in your browser
open index.html  # On macOS
start index.html # On Windows
xdg-open index.html # On Linux
```

Or use a local server:
```bash
# Using Python
python -m http.server 8000

# Using Node.js
npx serve
```
Then open `http://localhost:8000` in your browser.

## 🎯 How to Play

1. **Select Your Side**: Click "Play ⬜" for White or "Play ⬛" for Black
2. **Choose Difficulty**: Select Easy, Medium, or Hard from the dropdown
3. **Make Moves**: 
   - Click on a piece to select it (highlighted squares show legal moves)
   - Click on a highlighted square to move
4. **Use Controls**:
   - **New Game** - Start fresh
   - **Undo** - Take back last move
   - **Flip** - Rotate board perspective
   - **Difficulty** - Adjust AI strength anytime

## 🧠 AI Architecture

### Search Algorithm
| Difficulty | Search Depth | Avg. Response | Est. Rating |
|------------|--------------|---------------|-------------|
| Easy | 1 ply | < 100ms | ~800 ELO |
| Medium | 2 plies | 100-500ms | ~1200 ELO |
| Hard | 3 plies | 500-2000ms | ~1500 ELO |

### Key Components

**Move Generation**
- Complete legal move generation for all pieces
- Special moves: castling, en passant, pawn promotion
- Move validation with check detection

**Alpha-Beta Pruning**
- Optimized minimax with alpha-beta cutoffs
- Move ordering for better pruning efficiency
- Configurable search depth

**Evaluation Function**
```javascript
Score = Material + Positional Value
- Material: Traditional piece values (P=100, N=320, B=330, R=500, Q=900, K=20000)
- Positional: Piece-square tables for all pieces
- Dynamic: Based on piece activity and control
```

**Opening Book**
- Hash-based dictionary of 200+ opening variations
- Weighted selection for natural variety
- Automatic fallback to AI search when book ends

## 📁 Project Structure

```
chessmaster-ai/
├── index.html              # Complete application (HTML/CSS/JS)
├── README.md               # Project documentation
├── LICENSE                 # MIT License
├── .gitignore              # Git ignore rules
└── chessmaster.png         # Game screenshot
```

## 🎨 Customization

### Change Board Colors
Modify the CSS variables in the `<style>` section:
```css
.sq.light { background: #f0d9b5; }  /* Light square */
.sq.dark { background: #b58863; }   /* Dark square */
```

### Adjust AI Strength
Modify the depth values in the difficulty selector:
```html
<option value="1">Easy</option>     <!-- Depth 1 -->
<option value="2" selected>Medium</option> <!-- Depth 2 -->
<option value="3">Hard</option>     <!-- Depth 3 -->
```

### Add Opening Book Moves
Extend the `BOOK` object in the JavaScript:
```javascript
const BOOK = {
  'e4 e5': ['Nf3', 'Nf3', 'Bc4'],  // Add your variations
  'e4 c5': ['Nf3', 'Nc3', 'd4'],   // Sicilian lines
  // Add more variations...
};
```

### Change AI Thinking Time
Modify the delay in the `doAI()` function:
```javascript
const delay = 3000 + Math.floor(Math.random() * 1000); // Current: 3-4 seconds
// Change to: const delay = 1000; // 1 second fixed delay
```

## 🧪 Testing Scenarios

Test these chess scenarios to verify functionality:

- [ ] **Checkmate** - Fool's Mate (1.f3 e5 2.g4 Qh4#)
- [ ] **Stalemate** - Set up position with no legal moves
- [ ] **En Passant** - Set up proper en passant position
- [ ] **Castling** - Both kingside and queenside
- [ ] **Pawn Promotion** - Advance pawn to 8th rank
- [ ] **50-Move Rule** - No captures or pawn moves for 50 moves
- [ ] **Opening Book** - Verify first moves follow opening variations

## 🛠️ Browser Support

| Browser | Version | Status |
|---------|---------|--------|
| Chrome | 60+ | ✅ Fully Supported |
| Firefox | 60+ | ✅ Fully Supported |
| Safari | 12+ | ✅ Fully Supported |
| Edge | 79+ | ✅ Fully Supported |
| Opera | 50+ | ✅ Fully Supported |
| Mobile Chrome | 60+ | ✅ Fully Supported |
| Mobile Safari | 12+ | ✅ Fully Supported |

## 🤝 Contributing

Contributions are welcome! Here's how you can help:

1. **Fork the repository**
2. **Create a feature branch**
   ```bash
   git checkout -b feature/amazing-feature
   ```
3. **Commit your changes**
   ```bash
   git commit -m 'Add amazing feature'
   ```
4. **Push to the branch**
   ```bash
   git push origin feature/amazing-feature
   ```
5. **Open a Pull Request**

### Development Priorities
- [ ] Add quiescence search for better tactical play
- [ ] Implement transposition tables for search optimization
- [ ] Add PGN import/export functionality
- [ ] Expand opening book coverage
- [ ] Add sound effects
- [ ] Implement game analysis mode
- [ ] Add engine vs engine mode
- [ ] Create move animation

## 📄 License

Distributed under the MIT License. See `LICENSE` file for more information.

## 🙏 Acknowledgments

- Chess piece icons from Unicode symbols
- Opening theory references from standard chess databases
- Inspired by classic chess engines and modern web chess applications
- Special thanks to the open-source chess community

## 📊 Statistics

```
Total Lines of Code: ~1200
AI Search Depth: 1-3 plies
Opening Book: 200+ variations
Supported Openings: 30+ major systems
Response Time: < 100ms - 2s
```

## 📧 Contact

**Kazim Khan (KAZIM)** 

[![Twitter](https://img.shields.io/badge/Twitter-@sigmundkhan-1DA1F2?logo=twitter)](https://x.com/sigmundkhan)
[![Instagram](https://img.shields.io/badge/Instagram-@alphamanofgod-E4405F?logo=instagram)](https://instagram.com/alphamanofgod)
[![Email](https://img.shields.io/badge/Email-muhammadkazim387%40gmail.com-D14836?logo=gmail)](mailto:muhammadkazim387@gmail.com)
[![Portfolio](https://img.shields.io/badge/Portfolio-kazimportfolio.vercel.app-000000?logo=vercel)](https://kazimportfolio.vercel.app)

**GitHub**: [@kazim-45](https://github.com/kazim-45)

Project Link: [https://github.com/kazim-45/chessmaster-ai](https://github.com/kazim-45/chessmaster-ai)

---

<p align="center">
  Made with ♟️ by KAZIM
</p>
<p align="center">
  <a href="https://github.com/kazim-45/chessmaster-ai/stargazers">⭐ Star this project</a> •
  <a href="https://github.com/kazim-45/chessmaster-ai/issues">🐛 Report Bug</a> •
  <a href="https://github.com/kazim-45/chessmaster-ai/issues">💡 Request Feature</a>
</p>
```
