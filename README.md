# Tic-Tac-Toe with Negamax AI Implementation

## Overview
A complete Tic-Tac-Toe implementation featuring an unbeatable AI using the Negamax algorithm. This implementation uses a custom game engine with Bit/BitHolder architecture for piece management and board state tracking.

## Features
- **Complete Tic-Tac-Toe Rules**: 3x3 grid, turn-based gameplay, win/draw detection
- **Unbeatable AI**: Implements Negamax with perfect decision-making
- **State Serialization**: Save/load game state using string representation
- **Visual Game Engine**: Built on Bit/BitHolder system for sprite management
- **Debug Support**: Recursion counting and move evaluation logging

## Negamax AI Implementation - Detailed Technical Breakdown

### Algorithm Overview
Negamax is a variant of the Minimax algorithm that exploits the zero-sum property of two-player games. The key insight is that the value of a position for one player is the negative of its value for the opponent. This allows us to use a single recursive function instead of separate maximizing and minimizing functions.

### Core Negamax Principles

#### 1. **Zero-Sum Game Foundation**
In Tic-Tac-Toe, what's beneficial for one player is equally detrimental to the other. The Negamax algorithm leverages this by:
- Evaluating positions from the current player's perspective
- Negating returned scores when switching to the opponent's turn
- Using a single evaluation function for both players

#### 2. **Recursive Tree Exploration**
The algorithm explores all possible future game states through recursion:
- Starting from the current board position
- Trying every possible legal move
- Recursing to evaluate the opponent's responses
- Propagating scores back up the tree

#### 3. **Player Parameter System**
The implementation uses integer constants to represent players:
- AI_PLAYER = 1 (maximizing player)
- HUMAN_PLAYER = -1 (minimizing player)
This allows easy perspective switching through simple negation (-player) during recursive calls.

### Implementation Details

#### State Representation
The game state is represented as a 9-character string where:
- '0' represents an empty square
- '1' represents a human player's X
- '2' represents an AI player's O
This compact representation enables efficient state copying and manipulation during the recursive search.

#### Move Evaluation Process
For each empty square, the AI:
1. Temporarily places its piece in the empty position
2. Recursively evaluates the resulting position from the opponent's perspective
3. Negates the returned score (since good for opponent = bad for AI)
4. Tracks the move with the highest evaluated score

#### Terminal State Detection
The algorithm identifies game-ending conditions through:
- Win detection using precomputed winning combinations (8 possible lines)
- Draw detection when all squares are filled with no winner
- Immediate return of evaluated scores for terminal states

#### Scoring System
- +10 points for an AI win
- -10 points for a human win
- 0 points for draws or non-terminal positions
The negation mechanism automatically handles score inversion when switching perspectives.

### AI Decision-Making Workflow

1. **Initialization**: Start with current board state and reset recursion counter
2. **Move Generation**: Identify all empty squares as candidate moves
3. **Evaluation**: For each candidate move:
   - Apply the move temporarily
   - Recursively evaluate resulting position using Negamax
   - Negate the returned score for correct perspective
   - Track the best-scoring move
4. **Execution**: Place the piece in the highest-scoring position
5. **Turn Management**: Advance to the next player's turn

### Performance Characteristics

#### Computational Complexity
- **Time Complexity**: O(b^d) where b is branching factor (up to 9) and d is maximum depth (9)
- **Space Complexity**: O(d) for recursion stack depth
- **State Evaluations**: Up to 9! (362,880) possible game states in worst case

#### Optimization Features
- **Early Termination**: Stops evaluating when win/draw is detected
- **Minimal State Copying**: Efficient string manipulation for state changes
- **Complete Information**: Exploits perfect information nature of Tic-Tac-Toe

### Advantages of This Implementation

1. **Algorithmic Elegance**: Single recursive function handles both player perspectives
2. **Perfect Play**: Guaranteed optimal moves through complete game tree exploration
3. **Code Maintainability**: Clear separation between game logic and AI decision-making
4. **Extensibility**: Framework can be adapted for other perfect information games

### Technical Integration

The Negamax implementation integrates with the game engine through:
- State synchronization between string representation and visual board
- Turn management coordination
- Move validation and execution
- Win/draw detection consistency between AI and game logic

## Game Engine Architecture

### Core Components
- **Bit**: Visual game pieces (X/O sprites) with owner association
- **BitHolder**: Board squares that can hold one Bit each
- **Player**: Manages player state and ownership
- **Game Options**: Configures grid dimensions (3x3)

### State Management
The game maintains synchronization between the visual representation and the AI's state string representation, enabling seamless integration between user interactions and AI decision-making.

## GitHub Repository
**URL:** [Insert your GitHub repository URL here]

This implementation demonstrates a practical application of the Negamax algorithm, showcasing how recursive game tree search can create perfect AI opponents in deterministic, perfect-information games like Tic-Tac-Toe. The solution provides both theoretical understanding and practical implementation of adversarial search algorithms.