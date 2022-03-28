---
title: "Project 2: Ataax"
weight: 5    
---
**Ataax is a 2 person game with red and blue pieces played on a 7x7 board** 

## How the Game is Played 
- Intially, there are pieces in all four corners and the red player goes first
    - red in top left / bottom right (a7/g1)
    - blue in top right / bottom left (a1/g7)
- Play continues until there are no moves left or there has been 25 consecutive jumps between both players
- winner is player with the most pieces at the end of the game 
    - if you have no pieces, you lose 
- to tie;
    - players must have same # of pieces
    - neither player can make a move OR the max number of jumps (25 consecutive between players) has been reached 
- two kinds of moves
    1. Extending: place a new piece of your color next to an existing piece (horizontally, vertically, diagonally adjacent)
    2. Jumping: move a piece of your color to a square that is no more than 2 rows and 2 columns away 
    - all opposing pieces that are touching (previously empty) square are replaced by your color
    - a player can only pass if you cannot move 
- at the beginning of the game, you can set blocks, pre-filled squares that may never be moved or or moved to
    - they are symmetrical about the center
    - reflected along x and y axis 
    - config 'file' may list a square on the right side of the board but another block must be placed symmetrically on the left side as well 

## Commands 
- there are commands that player inputs into the textual interface (GUI for EC) **do EC**
    ### Starting and Ending Games
    - new : Abandons the current game (if one is in progress), clears the board to its initial configuration, and starts a new game.
    - quit : Abandons any current game and exits the program. The end of input has the same effect.
    ### Commands to Set Parameters
    - auto <COLOR> : 
    - manual <COLOR> : 
    - block CR : 
    - seed N :
    ### Entering and Undoing Moves
    program must reject illegal moves from any player (they have no effect on the board; the program should tell the user that there is an error and request another move). An AI must not make illegal moves. 
    - c0r0-c1r1 : 
    - undo : 
    ### Miscellaneous Commands
    - help : Print a brief summary of the commands.
    - dump : prints board in exactly the following format 
        - "-" indicates an empty square 
        - "r" is a red square
        - "b" is a blue square
        - "X" indicades a block 
        - "===" 
    ### Helpful Commands (to Add)
    - board : Prints out a board in something nicer than the dump format. The staff's version, for example, prints row and column designations along the sides of the board.
    - verbose : Causes the board to get printed (as for board) after each move.
    - quiet : Turns off verbose mode, so that the board no longer gets printed after each move. 

## Output 
...

## Testing 
- make unit runs unit tests, same with make acceptance 
- to run individual acceptance tests ...

## Hints / Notes 
- _notifier instance variable and the announce() method that you see used throughout Board.java is a mechanism for the GUI (see the Extra Credit section). If you aren't working on the GUI, you can ignore this mechanism entirely.
- EXTENDED_SIDE is explained by _board instance var in Board.java
- The unrecordedSet() method in Board.java ..., set() method sets a square and makes the move as undoable ?
- use Move.move() to get Move object rather than calling Move constructor
- "Linearized indices" is just a fancy way of stating that we converted the standard 2D array indexing with a row and column index into 1D array indexing.
- see char arithmetic (int representation etc) for distance between squares; https://replit.com


## Tasks
- Implement the logic of Ataax: 
    - What kind of move it is, if move is allowed, making a move and updating board, setting blocks, etc 
- Implement an 'AI' player that you can play the game against 
    - the AI needs to be able to force a win if possible within 4 moves of a given position 
    - cannot use more than 10 seconds to make any given move
    - techniques will be covered in lecture 

## Skeleton Notes 
### Move
    - for efficency, all moves are generated at the beginning and static move gets them 
    - Constuctor: takes in col0,row0 and col1,row1, which are offset from ...?
        - _isExtend = row1-row0 <= 1 || col1-col0 == 1
        - _isJump = (row1-row0 <= 2 && col1-col0 <= 2) && (row1-row0 > 0 && col1-col0 > 0) #non-adjacent

### Board 
    instance variables:
        - _notifier : see hints / notes
        - PieceColor[] _board : 11x11 board (outer rows and cols are blocks)
        - PieceColor _whoseMove : next player to move 
        - int _numJumps : num consecutive jumps since last clear or beginning of the game 
        - _totalOpen : total num unblocked squares 
        - int _totalOpen : num unblocked squares 
        - int[] _numPieces : num of blue and red pieces 
        - PieceColor _winner : set winner when game ends (empty if tie)
        - ArrayList<Move> _allMoves : list of all (non-undone) moves since last clear or beginning of the game
        - Stack<Integer> _undoSquares : stack of linearized indices of squares that have been modified and not undone. Nulls mark the beginnings of full moves. 
        - Stack<PieceColor> _undoPieces : stack of pieces formally at corresponding squares in _UNDOSQUARES

    methods : 
    - Board() - new, cleared board in intial config: 
        - make block grid outside 7x7
        - set 4 intial pieces + all others (in 7x7) as empty (do in clear)
        - set instance variables to *correct* intial setting
        : winner = null, numJumps, numMoves() = 0, 
        - how indexes of the board work : -> 
    - Board(Board board0) - see if additional copying is neccesary 
    - legalMove (Move move) - use Move.___ and index method : ___ summarize after checkpoint 
    - makeMove(Move move) :
        - determine if extend (+ piece) or jump (move piece)
        - after moving, if touching other opposite() squares (?)
        - change numMoves, numJumps, numPieces (red, blue), 
        - set numJumps to 0 if pass? 
    - legalBlock(char c, char r) 
    : true if legal to place block at C R
        -  < a && > g
        -  reflection 




