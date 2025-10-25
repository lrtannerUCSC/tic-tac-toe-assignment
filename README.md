# Tic-Tac-Toe with Negamax AI Implementation

## Overview
A complete Tic-Tac-Toe implementation featuring an unbeatable AI using the Negamax algorithm. This implementation uses a custom game engine with Bit/BitHolder architecture for piece management and board state tracking.

## Features
- **Complete Tic-Tac-Toe Rules**: 3x3 grid, turn-based gameplay, win/draw detection
- **Unbeatable AI**: Implements Negamax with perfect decision-making
- **State Serialization**: Save/load game state using string representation
- **Visual Game Engine**: Built on Bit/BitHolder system for sprite management
- **Debug Support**: Recursion counting and move evaluation logging

## Negamax AI Implementation

### Core Algorithm
The AI uses the **Negamax algorithm** - a simplified version of Minimax that leverages zero-sum game properties:

## Key Negamax Features

- **Single Evaluation Function**: Uses one function for both players by negating scores

- **Perfect Play**: Explores entire game tree to depth 9 (all possible moves)

- **Score System**:

    +10 for AI win

    -10 for human win

    0 for draw

- **State Representation**: Uses 9-character strings ('0'=empty, '1'=X, '2'=O)