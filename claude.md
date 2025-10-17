# Claude Code Project: Side Scroller Game

## Project Overview
A browser-based side-scrolling game built entirely with HTML5 Canvas and vanilla JavaScript. The game features jump mechanics, obstacles, enemies, and collectibles with a scoring system.

## Development Journey

### Initial Attempt: Bash Version
The project started with an ambitious goal to create an ASCII-based side-scroller game in bash. Multiple iterations were attempted:

1. **First approach:** Complex multi-line ASCII art dinosaur character with advanced rendering
2. **Challenges encountered:**
   - Terminal input handling inconsistencies across macOS
   - Screen flashing issues with different rendering methods (`tput clear`, `\033[2J`, etc.)
   - Non-blocking input problems (`stty raw`, `stty -icanon`, various `read` approaches)
   - Character rendering artifacts and ghosting

3. **Multiple debugging attempts:**
   - Background process input handlers with FIFOs
   - Different `stty` configurations
   - Various escape code approaches
   - Simplified character representations

### Successful Pivot: HTML5 Canvas Version
After recognizing the terminal compatibility limitations, the project was rebuilt as a web application:

- **Technology Stack:** Pure HTML5, CSS3, and JavaScript
- **Architecture:** Single-file application for easy distribution
- **Game Engine:** Custom canvas-based rendering with requestAnimationFrame
- **Physics:** Simple gravity-based jump mechanics with hold-to-hover feature

## Technical Implementation

### Game Mechanics
- **Player Control:** Spacebar or mouse click to jump
- **Jump Physics:**
  - Initial jump force: -12 units
  - Gravity: 0.6 units/frame
  - Hover mechanic: Hold key to maintain position at jump apex
- **Collision Detection:** Bounding box algorithm with offset for forgiving gameplay

### Game Objects
1. **Obstacles** (red blocks on ground): +10 points when cleared
2. **Enemies** (red X markers, flying): +5 points when avoided
3. **Coins** (gold circles with $): +50 points when collected

### Spawn System
- **Obstacles:** Every 80 frames after start
- **Enemies:** Every 120 frames after frame 100
- **Coins:** Every 200 frames after frame 200

### Visual Design
- **Color Scheme:**
  - Background: Dark blue (#0f3460)
  - Player: Green (#00ff88)
  - Obstacles/Enemies: Red (#e94560, #ff6b6b)
  - Coins: Gold (#ffd700)
- **Grid Background:** Subtle dark blue lines for depth
- **Typography:** Courier New monospace font

## Files Structure

```
side-scroller/
├── game.html          # Complete game (HTML/CSS/JS)
├── README.md          # User documentation
├── LICENSE            # MIT License
├── .gitignore         # Git ignore rules
└── claude.md          # This development log
```

## Git Setup & Deployment

### SSH Configuration
1. Generated ED25519 SSH key pair
2. Added key to SSH agent
3. Configured GitHub SSH authentication
4. Successfully pushed to repository

### Repository Details
- **URL:** https://github.com/traskmountain/side-scroller
- **Branch:** main
- **Initial Commit:** Complete working game with documentation

## Key Learnings

### What Didn't Work
- Bash terminal games have severe cross-platform compatibility issues
- Non-interactive shell environments can't handle standard input for games
- ASCII rendering in terminals is unreliable for complex animations

### What Worked
- HTML5 Canvas provides consistent, reliable rendering
- Single-file web apps are highly portable
- Simple physics create engaging gameplay
- Progressive difficulty through timed spawning

## Future Enhancement Ideas

1. **Power-ups:** Temporary invincibility, score multipliers
2. **Multiple Characters:** Different player sprites with unique abilities
3. **Levels:** Background changes, difficulty tiers
4. **High Score System:** LocalStorage persistence
5. **Sound Effects:** Audio feedback for jumps, collisions, collections
6. **Mobile Support:** Touch controls for mobile devices
7. **Particle Effects:** Visual polish for collisions and collections

## Performance Notes

- Runs at consistent 60 FPS using requestAnimationFrame
- No external dependencies = fast load time
- Canvas rendering is hardware accelerated in modern browsers
- Game state updates are optimized with array filtering

## Accessibility Considerations

- Visual game relies on color and motion (could add colorblind mode)
- Keyboard and mouse input supported
- Simple controls make it easy to learn

---

**Built with Claude Code** - An exploration in game development, problem-solving, and knowing when to pivot technologies.

*Total Development Time:* ~2 hours including all iterations and debugging
*Final Line Count:* ~280 lines of code (HTML/CSS/JS combined)
*Commits:* 1 (clean, documented initial release)
