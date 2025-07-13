# Children's Roguelike Game Plan

## Project Overview

**Game Title**: Adventure Garden (Working Title)  
**Target Age**: 3-5 years old  
**Genre**: Child-friendly roguelike/adventure with educational math mode  
**Platform**: Cross-platform (Windows, Android, iOS)  
**Technology**: Unity 2022.3 LTS with C#  

## Core Concept

A gentle, colorful exploration game with two distinct but integrated modes:

1. **Adventure Mode**: Children discover procedurally generated rooms filled with friendly creatures and collectible treasures
2. **Math Mode**: Age-appropriate number learning through counting, simple addition/subtraction, and pattern recognition

Both modes share the same friendly garden setting with no failure states - only discovery, collection, and learning.

## Age-Appropriate Design Principles

### Cognitive Development Considerations (Ages 3-5)
- **Attention Span**: 5-15 minute play sessions
- **Reading Ability**: Minimal text, visual-first interface
- **Motor Skills**: Large touch targets, simple one-touch interactions
- **Learning Style**: Immediate positive feedback, repetition, pattern recognition

### Safety & Accessibility
- No in-app purchases or external links
- Parental controls for session time
- Offline gameplay (no internet required)
- High contrast visuals for accessibility
- Simple audio cues for visual impairments

## Game Design

### Game Modes

#### Adventure Mode Core Loop
1. **Start**: Begin in colorful "home garden"
2. **Choose**: Select the green adventure door
3. **Explore**: Navigate 2-3 simple rooms (3x3 or 4x4 grids)
4. **Collect**: Touch items to collect them (stars, flowers, toys)
5. **Meet**: Encounter friendly animals who give gifts
6. **Return**: Come back to home base with treasures
7. **Progress**: Unlock new doors/areas with collected items

#### Math Mode Core Loop
1. **Start**: Begin in the same "home garden"
2. **Choose**: Select the blue math learning door
3. **Learn**: Enter the "Number Garden" with math challenges
4. **Solve**: Complete age-appropriate math activities (counting, simple addition/subtraction)
5. **Achieve**: Earn number badges and math stickers
6. **Return**: Come back to home base with new math achievements
7. **Progress**: Unlock new math activities and share rewards with adventure mode

### Simplified Roguelike Elements
- **Procedural Generation**: Simple room layouts with pre-designed safe templates
- **Collection Progression**: Items unlock new areas instead of traditional RPG stats
- **Random Encounters**: Friendly animals with simple gift-giving interactions
- **No Permadeath**: Characters always return home safely with items
- **Variety**: Different themed areas (forest, beach, space, underwater)

### Math Mode Design Details

#### Age-Appropriate Math Skills
- **Ages 3-4**: Number recognition (1-10), counting objects, simple addition (1+1, 2+1)
- **Ages 4-5**: Basic addition/subtraction (up to 5), number sequencing, simple patterns

#### Math Activities

**1. Number Bridge Crossing**
- Bridges with missing numbers (1, ?, 3, 4)
- Child selects correct number from 3 visual options
- Success: bridge completes with sparkles and gentle celebration

**2. Fruit Counting Market**
- Friendly animals request quantities: "Can you give me 3 apples?"
- Child counts and drags correct number of fruits
- Visual feedback: happy animal animations + math stickers

**3. Addition/Subtraction Gardens**
- Visual problems using objects: 2 flowers + 1 flower = ?
- Child places answer by selecting from flower options
- Success: watch flowers grow with magical animations

**4. Pattern Completion**
- Simple visual patterns: red, blue, red, blue, ?
- Quantity patterns: 1 star, 2 stars, 3 stars, ?
- Shape and color combinations for advanced learners

**5. Number Path Adventures**
- Follow numbered stepping stones in correct order (1-5, then 1-10)
- Touch numbers in sequence to create magical pathways
- Each completed path unlocks new garden areas

#### Adaptive Difficulty System
- Game tracks individual progress and adjusts automatically
- Number ranges adapt: 1-3 → 1-5 → 1-10
- Parents can manually set difficulty levels
- No time pressure - children work at their own pace

#### Cross-Mode Integration
- Adventure mode items unlock new math challenges
- Math achievements unlock new adventure areas  
- Shared sticker book celebrates both types of accomplishments
- Character customization earned through both modes

### Visual Design
- **Art Style**: Bright, cartoon-like 2D sprites
- **Color Palette**: High contrast, primary colors
- **Characters**: Round, friendly animal designs
- **UI Elements**: Large buttons with clear icons
- **Animations**: Simple, gentle movements

### Audio Design
- **Music**: Gentle, non-repetitive background tracks
- **Sound Effects**: Pleasant collection sounds, friendly animal noises
- **Voice**: Optional simple word pronunciation for items
- **Volume**: Automatic adjustment, parental volume controls

## Technical Architecture

### Framework Choice: Unity
**Rationale**: 
- Excellent C# support
- Superior cross-platform deployment
- Visual editor reduces development time
- Large asset store for child-friendly resources
- Strong 2D rendering capabilities

### Project Structure
```
Assets/
├── Scripts/
│   ├── Core/
│   │   ├── GameManager.cs          # Main game state management
│   │   ├── SceneTransitionManager.cs # Safe scene loading
│   │   ├── SaveManager.cs          # Progress persistence
│   │   └── AudioManager.cs         # Sound/music control
│   ├── Player/
│   │   ├── PlayerController.cs     # Simple movement
│   │   ├── PlayerInventory.cs      # Collection system
│   │   └── TouchInputHandler.cs    # Touch/click input
│   ├── Generation/
│   │   ├── LevelGenerator.cs       # Simple room creation
│   │   ├── RoomTemplate.cs         # Pre-designed room layouts
│   │   ├── ItemSpawner.cs          # Collectible placement
│   │   └── CreatureSpawner.cs      # Friendly animal placement
│   ├── Math/
│   │   ├── MathGameManager.cs      # Math mode coordination
│   │   ├── MathProblemGenerator.cs # Age-appropriate problem creation
│   │   ├── DifficultyManager.cs    # Adaptive learning system
│   │   ├── MathActivityController.cs # Individual activity logic
│   │   └── ProgressTracker.cs      # Math skill progression
│   ├── UI/
│   │   ├── MainMenuUI.cs           # Home screen
│   │   ├── GameplayUI.cs           # In-game interface
│   │   ├── InventoryUI.cs          # Sticker book/collection
│   │   ├── MathUI.cs               # Math activity interfaces
│   │   ├── SettingsUI.cs           # Parental controls
│   │   └── TransitionUI.cs         # Loading screens
│   └── Creatures/
│       ├── FriendlyAnimal.cs       # Animal behavior
│       ├── AnimalInteraction.cs    # Gift-giving logic
│       └── AnimalAnimator.cs       # Simple animations
├── Prefabs/
│   ├── Player/
│   ├── Rooms/
│   ├── Items/
│   ├── Creatures/
│   ├── MathActivities/
│   └── UI/
├── Sprites/
│   ├── Characters/
│   ├── Items/
│   ├── Backgrounds/
│   └── UI/
├── Audio/
│   ├── Music/
│   ├── SFX/
│   └── Voice/
└── Scenes/
    ├── MainMenu.unity
    ├── HomeGarden.unity
    ├── AdventureMode.unity
    ├── MathMode.unity
    └── LoadingScene.unity
```

### Key Systems

#### 1. Dual-Mode State Machine
```
Home → Mode Selection → [Adventure Mode | Math Mode] → Activities → Return Home
```

**Adventure Path**: Home → Green Door → Adventure Rooms → Collection → Return  
**Math Path**: Home → Blue Door → Number Garden → Math Activities → Achievement → Return

#### 2. Grid-Based Movement
- Touch/click to move to adjacent tiles
- Visual path highlighting
- Smooth animation between positions

#### 3. Collection System
- Touch items to collect with satisfying animations
- Visual feedback (sparkles, gentle sounds)
- Automatic inventory management

#### 4. Progress Tracking
- Visual sticker book/album interface
- Achievement system (collected all flowers, met all animals)
- Unlock progression for new areas

#### 5. Safe Save System
- Auto-save after each collection and math achievement
- No progress loss possible
- Cloud save for device switching (optional)

#### 6. Math Learning System
- Adaptive difficulty based on individual progress
- Visual math problems using familiar objects (fruits, flowers, toys)
- Immediate positive feedback for all attempts
- Progress tracking for both math skills and engagement

## Development Timeline

### Phase 1: Foundation (Weeks 1-2)
**Goals**: Basic project setup and core mechanics

**Tasks**:
- [ ] Set up Unity project with cross-platform settings
- [ ] Create basic player character with grid movement
- [ ] Implement simple touch/click input system
- [ ] Design initial art style guide
- [ ] Create basic UI framework with mode selection
- [ ] Set up scene management system for dual modes

**Deliverables**:
- Playable character that can move in a simple room
- Basic UI with large, child-friendly buttons
- Art style reference and initial sprites

### Phase 2: Core Mechanics (Weeks 3-4)
**Goals**: Implement main gameplay systems

**Tasks**:
- [ ] Basic procedural room generation for adventure mode
- [ ] Item collection mechanics with visual feedback
- [ ] Simple inventory/sticker book system (shared between modes)
- [ ] Friendly creature interactions
- [ ] Basic math activity framework (counting, number recognition)
- [ ] Sound integration and audio manager
- [ ] Home base area with dual door selection (green/blue)

**Deliverables**:
- Complete core gameplay loop for both modes
- Collection system with 5+ item types
- 2-3 friendly creature types
- Basic math activities (counting 1-5, simple number recognition)
- Audio feedback for all interactions

### Phase 3: Content & Polish (Weeks 5-6)
**Goals**: Expand content and improve user experience

**Tasks**:
- [ ] Multiple room templates (forest, beach, space themes)
- [ ] Expanded item variety (10+ collectibles per theme)
- [ ] Additional creature types with unique gifts
- [ ] Complete math activity suite (addition/subtraction, patterns, sequences)
- [ ] Adaptive difficulty system for math mode
- [ ] Cross-mode reward integration
- [ ] Animation polish and particle effects
- [ ] Parental controls and settings menu
- [ ] Achievement system implementation (both modes)

**Deliverables**:
- 3+ themed areas with unique content
- Complete math learning system with 5+ activity types
- Polished animations and visual effects
- Complete settings and parental controls
- Achievement/progress tracking for both modes
- Seamless mode switching and reward sharing

### Phase 4: Testing & Deployment (Weeks 7-8)
**Goals**: Finalize and release

**Tasks**:
- [ ] Child testing sessions with target age group
- [ ] Bug fixes and feedback incorporation
- [ ] Performance optimization for mobile devices
- [ ] Platform-specific builds (Windows, Android, iOS)
- [ ] App store assets and descriptions
- [ ] Release preparation and submission

**Deliverables**:
- Tested, polished game ready for release
- Platform-specific builds
- App store submissions

## Target Platforms & Requirements

### Windows (Primary Development)
- **Minimum**: Windows 10, DirectX 11
- **Input**: Mouse and keyboard
- **Distribution**: Itch.io, Microsoft Store

### Android
- **Minimum**: Android 7.0 (API level 24)
- **Input**: Touch screen
- **Distribution**: Google Play Store

### iOS (Future)
- **Minimum**: iOS 11.0
- **Input**: Touch screen
- **Distribution**: Apple App Store

## Risk Assessment & Mitigation

### Technical Risks
- **Cross-platform compatibility**: Use Unity's built-in solutions, test early and often
- **Performance on older devices**: Optimize graphics, limit particles, profile regularly
- **Touch input accuracy**: Large touch targets, generous hit boxes

### Design Risks
- **Age appropriateness**: Regular testing with target age group
- **Engagement vs. simplicity**: Balance through iterative design
- **Parental approval**: Include comprehensive parental controls

### Timeline Risks
- **Feature creep**: Strict scope management, MVP focus
- **Art asset creation**: Start with placeholder art, polish iteratively
- **Platform certification**: Research requirements early, plan extra time

## Success Metrics

### Technical
- [ ] Stable 30+ FPS on target devices
- [ ] < 3 second load times between areas
- [ ] Zero critical bugs in target age testing

### Design
- [ ] 80%+ of test children complete first adventure and first math activity
- [ ] Average session length of 8-12 minutes across both modes
- [ ] Children show engagement with both adventure and math modes
- [ ] Positive feedback from 90%+ of parent testers
- [ ] Observable learning progress in target math skills

### Business
- [ ] Launch on at least 2 platforms
- [ ] 4+ star average rating
- [ ] 1000+ downloads in first month

## Next Steps

1. **Install Unity 2022.3 LTS** and create new 2D project
2. **Set up version control** (Git) for the project
3. **Create basic folder structure** as outlined above
4. **Design and create first character sprite** for player
5. **Implement basic grid movement system**

## Resources & References

### Development Tools
- **Unity 2022.3 LTS**: Game engine
- **Visual Studio Community**: IDE for C# development
- **Git**: Version control
- **Aseprite/Photoshop**: Sprite creation

### Art Style References
- Toca Boca games (simple, child-friendly design)
- Duck Duck Moose apps (educational game UI)
- PBS Kids games (age-appropriate interactions)

### Child Development Resources
- Common Sense Media age rating guidelines
- Children's Technology Review standards
- Educational gaming best practices

---

*This plan is a living document and should be updated as development progresses and new insights are gained through testing with the target audience.*