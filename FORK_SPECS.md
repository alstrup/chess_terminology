# Fork Specifications: Precise Conditions

## Material-Winning Forks

### Check-and-Capture Fork
**Conditions:**
- Attacking piece: Any piece capable of giving check
- Target 1: Enemy king (must be in check)
- Target 2+: At least one undefended enemy piece
- Forking piece safety: Must be safe from capture or adequately defended
- Defensive resources: None effective (king must respond to check first)

**Example Position:**
![Check-and-Capture Fork](https://lichess1.org/export/fen.gif?fen=8/8/8/8/8/5r2/6N1/4K2k&color=white&theme=brown&piece=cburnett)

FEN: `8/8/8/8/8/5r2/6N1/4K2k w - - 0 1`
*White knight on g2 checks the black king and attacks the undefended rook on f3.*

### Double Hanging Fork
**Conditions:**
- Attacking piece: Any piece
- Targets: Two or more undefended enemy pieces
- Forking piece safety: Must be safe from capture
- Defensive resources: Only one piece can move per turn; at most one target can be saved

**Example Position:**
![Double Hanging Fork](https://lichess1.org/export/fen.gif?fen=8/8/2r5/8/8/2B5/8/K1k5&color=white&theme=brown&piece=cburnett)

FEN: `8/8/2r5/8/8/2B5/8/K1k5 w - - 0 1`
*White bishop on c3 attacks two undefended pieces: the rook on c6 and king on c1.*

### Triple Fork
**Conditions:**
- Attacking piece: Any piece (typically knight or queen)
- Targets: Three or more enemy pieces
- Target requirements: At least two targets must be either:
  - Undefended, OR
  - Worth more than the attacking piece
- Forking piece safety: Must be safe from capture
- Defensive resources: Only one piece can move; material loss inevitable

### Value Fork
**Conditions:**
- Attacking piece: Lower-value piece (typically knight or bishop)
- Targets: TWO or more pieces each worth MORE than the attacking piece
- Target defense: Can be defended (irrelevant if both worth more)
- Forking piece safety: Must be safe or exchange favorable
- Defensive resources: Only one high-value piece can escape

### Royal Fork
**Conditions:**
- Attacking piece: Any piece (commonly knight)
- Target 1: Enemy king (in check)
- Target 2: Enemy queen
- Queen defense: Irrelevant (king must move from check)
- Forking piece safety: Must be safe from capture
- Defensive resources: Blocking check while defending queen (rare)

**Example Position:**
![Royal Fork](https://lichess1.org/export/fen.gif?fen=8/2q5/8/3N4/8/8/8/4Kk2&color=white&theme=brown&piece=cburnett)

FEN: `8/2q5/8/3N4/8/8/8/4Kk2 w - - 0 1`
*White knight on d5 checks the black king on f1 and attacks the queen on c7.*

### Grand Fork
**Conditions:**
- Attacking piece: Typically knight or queen
- Targets: King + Queen + one or both rooks
- King status: Must be in check
- Other pieces: May be defended (irrelevant due to check)
- Forking piece safety: Must be safe from capture
- Defensive resources: Extremely limited

### Family Fork
**Conditions:**
- Attacking piece: Any piece
- Target 1: Enemy king (in check)
- Target 2: Enemy queen
- Target 3+: Any other enemy piece(s)
- Forking piece safety: Must be safe from capture
- Defensive resources: King must escape check first

## Positionally Sound Forks

### Strategic Fork
**Conditions:**
- Attacking piece: Any piece
- Targets: Two or more enemy pieces
- Material outcome: May not win material immediately
- Position requirements: Must improve according to engine evaluation
- Hidden value: Future tactics, better coordination, or space advantage
- Defensive resources: May exist but accepting fork improves attacker's position

## Forcing Forks (No Direct Material Gain)

### Tempo Fork
**Conditions:**
- Attacking piece: Any piece
- Targets: Two or more valuable enemy pieces
- Target defense: All targets adequately defended
- Outcome: Forces retreat without material gain
- Positional gain: Attacker improves development or centralization
- Defensive resources: All pieces can be defended but tempo lost

### Anti-Castle Fork
**Conditions:**
- Attacking piece: Any piece
- Target 1: Enemy king (unmoved)
- Target 2: Any other enemy piece
- King position: Must not have castled yet
- Outcome: Forces king to move, losing castling rights
- Defensive resources: Must choose between castling rights or other piece

### Forcing Fork
**Conditions:**
- Attacking piece: Any piece
- Targets: Two or more enemy pieces
- Target defense: All can be defended
- Outcome: Forces defensive moves, attacker gains initiative
- Defensive resources: Adequate but passive defense required

## Invalid/Pseudo Forks

### Broken Fork
**Conditions:**
- Attacking piece: Any piece
- Targets: Multiple enemy pieces but:
  - Only ONE piece worth more than attacker, OR
  - All targets adequately defended with no gain
- Escape route: High-value piece can move and create counter-threat
- Defensive resources: Simple piece movement nullifies fork

### Unsound Fork
**Conditions:**
- Attacking piece: High-value piece (queen or rook)
- Targets: Lower or equal value pieces
- Target defense: All targets defended
- Forking piece vulnerability: Can be captured for profit
- Outcome: Attacker loses material after exchanges
- Defensive resources: Direct capture or recapture sequence

## Critical Defensive Resources Against Any Fork

### Zwischenzug (In-Between Move)
- **Condition**: Defender has intermediate check or stronger threat
- **Effect**: Forces attacker to respond before capturing forked pieces
- **Example**: Counter-check before forking piece can capture

### Counter-Attack
- **Condition**: Defender creates stronger threat (mate threat > fork)
- **Effect**: Attacker must abandon fork to defend
- **Example**: Back-rank mate threat forcing fork abandonment

### Pin Defense
- **Condition**: Forking piece can be pinned to higher value piece
- **Effect**: Prevents forking piece from capturing
- **Example**: Bishop pins knight to king after knight fork

### Blocking with Defense
- **Condition**: One piece blocks check AND defends other forked piece
- **Effect**: Both pieces saved with single move
- **Example**: Bishop blocks check while protecting rook

## Forking Piece Requirements by Type

### Knight Forks
- Range: Up to 8 squares (L-shaped moves)
- Cannot be blocked
- All targets must be on opposite color from knight's current square

### Bishop Forks
- Range: Diagonal lines only
- Can be blocked by interposition
- All targets must be on same color squares

### Rook Forks
- Range: Horizontal and vertical lines
- Can be blocked by interposition
- Targets must share rank or file

### Queen Forks
- Range: All directions (combines rook + bishop)
- Can be blocked except on knight-move patterns
- Most flexible but highest risk due to queen value

### Pawn Forks
- Range: Two diagonal squares forward only
- Cannot retreat after forking
- Lowest risk due to pawn's minimal value

### King Forks
- Range: All adjacent squares (one square in any direction)
- Only effective in endgames or against undefended pieces
- Cannot fork pieces that can counter-attack the king