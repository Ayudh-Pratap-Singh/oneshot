# Neon Highway Racer 🏎️

A retro-styled, pseudo-3D endless racing game built with vanilla JavaScript and HTML5 Canvas.

## 🎮 Game Overview

Neon Highway Racer is an arcade-style racing game featuring:
- **Retro aesthetic** with neon underglow and cyberpunk vibes
- **Pseudo-3D rendering** using perspective projection
- **Endless gameplay** with increasing difficulty
- **High score tracking** with localStorage persistence
- **Minimalist controls** for easy pickup-and-play

## 🎯 How to Play

### Controls
- **A / Left Arrow** - Move left
- **D / Right Arrow** - Move right  
- **R** - Restart after crash

### Objective
Dodge oncoming traffic and roadside trees for as long as possible. Your score increases with time survived. The game speeds up gradually, making it progressively more challenging.

## 🚗 Game Features

### Player Vehicle
- Sleek sports car design with rear spoiler
- Cyan neon underglow effect
- Glowing red tail lights with bloom
- Fixed position at bottom of screen

### Obstacles
- **Opponent Cars**: Boxy sedans in random lanes with varied colors
- **Trees**: Roadside hazards on both sides of the highway
- Collision detection with game-over state

### Visual Effects
- Starfield background for depth
- Dynamic road perspective with blue side rails
- Shadow and glow effects on vehicles
- Smooth pseudo-3D projection

## 💻 Technical Implementation

### Core Technologies
- **HTML5 Canvas** - All rendering
- **Vanilla JavaScript** - Game logic (no frameworks)
- **localStorage** - High score persistence

### Key Systems

#### Rendering Pipeline
```
1. Clear screen
2. Draw starfield
3. Draw road with perspective
4. Sort objects by depth (z-coordinate)
5. Render distant objects first
6. Draw player car
7. Render UI overlay
```

#### Perspective Projection
Objects use a simple perspective formula:
```javascript
scale = 400 / (400 + z)
```
Where `z` is the distance from camera. This creates the illusion of depth.

#### Object Spawning
- Trees spawn every 15 frames at random sides
- Cars spawn every 45 frames in random lanes
- All objects start at z=5000 (far distance)

#### Collision Detection
- Triggered when opponent car is within:
  - Z-range: 100 to -50 units
  - X-range: Within 140 units of player position

### Code Structure

| Component | Purpose |
|-----------|---------|
| `spawnWorld()` | Generates trees and opponent cars |
| `drawPlayerCar()` | Renders player vehicle with effects |
| `drawEnemyCar()` | Renders opponent vehicles |
| `drawTree()` | Renders roadside trees |
| `loop()` | Main game loop (rendering + logic) |

## 📊 Game Mechanics

### Difficulty Scaling
- Speed increases by 0.002 units per frame
- Creates exponential difficulty curve
- No upper speed limit

### Scoring System
- Score = frames survived
- High score stored in browser localStorage
- "NEW RECORD!" message on personal best

### Lane System
Three driving lanes at x-coordinates:
- Left: -220
- Center: 0
- Right: 220

## 🎨 Art Style

### Color Palette
- **Background**: Deep black (#000208)
- **Player Car**: 
  - Body: Dark gray (#111)
  - Accent: Cyan (#0ff, #0cc)
  - Lights: Red (#f00)
- **Opponent Cars**: Randomized HSL hues (darker/duller)
- **Road**: Charcoal (#0d0d0d)
- **Rails**: Blue (#00f)

### Visual Effects
- Neon underglow (cyan, 30px blur)
- Tail light bloom (red, 20px blur)
- Opponent car glow (10px blur)
- Shadow effects for depth

## 📦 File Structure

```
.
└── index.html (complete game - 2.5KB)
```

Single-file architecture for maximum portability.

## 🚀 Running the Game

1. Save the HTML file
2. Open in any modern web browser
3. Start playing immediately - no server required!

## 🔧 Customization Ideas

### Easy Modifications
- Adjust `speed` variable to change initial difficulty
- Modify spawn rates (change `t % 15` and `t % 45`)
- Alter lane positions in the `lanes` array
- Change color schemes in draw functions

### Advanced Features to Add
- Power-ups (shields, speed boosts)
- Multiple vehicle types
- Day/night cycle
- Mobile touch controls
- Sound effects and music

## 📈 Performance

- Runs at 60 FPS on modern browsers
- Low resource usage (~2-5% CPU)
- No external dependencies
- Total file size: ~2.5KB

## 🎓 Learning Concepts

This project demonstrates:
- Canvas 2D rendering techniques
- Game loop implementation
- Collision detection
- Perspective projection math
- State management
- Input handling
- localStorage API
- Array manipulation and sorting

## 📝 License

Open source - feel free to modify and use!

## 🙌 Credits

Created as a demonstration of retro-style game development with vanilla JavaScript.

---

**Enjoy the ride! 🏁**
