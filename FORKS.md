# Chess Fork Taxonomy and Classification

## Overview
A fork is a chess tactic where a single piece attacks two or more enemy pieces simultaneously. Not all apparent forks are tactically sound or lead to material gain. This document provides a comprehensive classification system for forks based on their tactical properties, material outcomes, and the pieces involved.
  
### Fundamental Requirement
**A fork MUST attack at least TWO enemy pieces.** Single-piece attacks, regardless of their tactical merit, are not forks.

## Forks vs Double Attacks

- **Double attack**: Any move that creates two or more concurrent threats (e.g., two attacked pieces, a mate threat plus an attacked piece, or two independent tactical threats).
- **Fork**: A subtype of double attack where a single piece, with one move, simultaneously attacks at least two enemy pieces. We treat the king as a piece: giving check while attacking another piece is a fork.
- **Not a fork (by this convention)**: A move that threatens mate and also attacks one piece, or a position where two different pieces each create one threat. These are double attacks, but not forks here because they are not one piece attacking two pieces right now.
- Practical note: The same evaluation tools apply to both (defender counting, forking-square safety, checks/counterchecks, zwischenzugs). The rest of this document focuses on forks as defined above.

## Core Principles

### Fork Terminology by Nature
- **Absolute Fork**: A fork involving the king (forces immediate response due to check)
- **Relative Fork**: A fork based on material value differences (attacking pieces worth more than the attacker)

### The Fundamental Fork Equation
For a fork to win material under normal conditions, at least one of these sufficient conditions often applies (assuming the forking piece remains safe and no forcing resource like a zwischenzug/countercheck exists):
1. **Multiple undefended pieces** - At least two targets are hanging
2. **King in check** (Absolute Fork) - Forces immediate response, often leaving other pieces vulnerable
3. **Multiple high-value targets** (Relative Fork) - Only one can escape, the other is captured
4. **Overloaded defender** - One piece cannot defend multiple targets

### Critical Insight: The Escape Problem
**Only one piece can move per turn.** This creates the tactical foundation for forks, with important caveats:
- If you attack two undefended pieces, you will often win at least one (provided your forking piece remains safe and no forcing defense exists)
- If you attack two pieces worth more than your attacking piece, you often win material (only one can escape), subject to interpositions, counterattacks, and recaptures
- If you attack only one high-value piece (even with other lower-value pieces), that piece can usually move away
- **Zwischenzug possibility**: An intermediate move (often a check or stronger threat) can refute or defuse a fork; always scan for in-between moves

## Fork Classifications by Tactical Outcome

### 1. Material-Winning Forks

#### Check-and-Capture Fork
- **Definition**: King in check + at least one undefended piece (absolute fork)
- **Example**: Knight checks king and attacks undefended rook

#### Double Hanging Fork
- **Definition**: Attacks two or more undefended pieces
- **Example**: Bishop attacks undefended knight and undefended rook

#### Triple Fork
- **Definition**: Attacks three or more undefended pieces, at least two of which are worth more than the attacking piece
- **Example**: Knight attacks king, queen, and bishop

#### Value Fork
- **Definition**: Attacks TWO or more pieces worth MORE than the attacking piece, even if they are defended (relative fork)
- **Example**: Knight (300cp) forks Queen (900cp) and Rook (500cp) - wins at least 200cp
- **Critical**: Both targets must be worth more; if only one is, it can escape

#### Royal Fork (Material-Winning Variant)
- **Definition**: King + Queen (absolute fork)

#### Grand Fork
- **Definition**: King + Queen + one or both Rooks (triple or quadruple fork)
- **Alternative name**: Royal Family Fork

#### Family Fork
- **Definition**: King + Queen + any other piece(s) (triple fork)
- **Example**: Knight checks king, attacks queen and bishop

### 2. Positionally Sound Forks

#### Strategic Fork
- **Definition**: Engine-approved fork with hidden tactical or positional value
- **Outcome**: Improves position through means not immediately apparent
- **Example**: Fork that sets up future tactics or improves piece coordination

### 3. Forcing Forks (No Direct Material Gain)

#### Tempo Fork
- **Definition**: Forces valuable pieces to retreat without winning material
- **Example**: Knight checks king and protected bishop, forcing the king to move. No material is lost, but the knight centralized.
- **Value**: Development advantage or positional improvement

#### Anti-Castle Fork
- **Definition**: Forces opponent to lose castling rights by attacking two pieces
- **Example**: Bishop attacks king and knight, forcing king to move and lose castling rights

#### Forcing Fork
- **Definition**: Creates threats requiring response but all targets can be defended
- **Outcome**: Forces opponent into defensive moves
- **Example**: Rook attacks two pawns; opponent defends both but loses initiative

### 4. Invalid/Pseudo Forks

#### Broken Fork (Invalid Fork)
- **Definition**: Appears to attack multiple pieces but can be fully defended or the forking piece can be captured profitably
- **Outcome**: No material gain or positional advantage
- **Example**: Knight attacks queen and defended pawn; queen moves and makes a threat
- **Key Flaw**: Single high-value piece can escape, others aren't worth capturing

#### Unsound Fork (Recapture-Refuted)
- **Definition**: Forking piece can be captured for equal or greater value, either immediately or after the first capture
- **Outcome**: Actually loses material
- **Example**: Queen forks two rooks but both are defended; capturing one leads to losing material
- **Critical Error**: Forking piece is more valuable than potential gains

## Fork Classifications by Attacking Piece

### Knight Forks
- **Strengths**: 
  - Can attack up to 8 squares simultaneously
  - Jumps over pieces (cannot be blocked)
  - Attacks cannot be blocked by interposition
  - Color-changing ability reaches all squares

### Bishop Forks
- **Strengths**:
  - Long-range diagonal attacks
  - Can fork pieces on opposite sides of the board
  - Often hidden behind other pieces until revealed
- **Limitations**:
  - Only attacks squares of one color
- **Special Terminology**:
  - **Cross-fork**: Bishop attacks pieces on opposite corners of its diagonal range
- **Tactical Themes**:
  - **Color Complex Weakness**: Exploiting when opponent's pieces cluster on same color

### Rook Forks
- **Strengths**:
  - Controls entire ranks and files
  - Powerful on open boards
  - Can fork from a distance
- **Special Terminology**:
  - **Lateral Fork**: Rook attacks pieces on same rank
- **Common Patterns**:
  - Forking king and another piece on same rank/file
  - Double attack on pawns on 7th rank

### Queen Forks
- **Strengths**:
  - Combines rook and bishop movement
  - Can create multiple threats from one square
  - Maximum flexibility in fork patterns
- **Weaknesses**:
  - High value makes it vulnerable to counterattack
  - Often unsound if forking lesser pieces

### Pawn Forks
- **Strengths**:
  - Low value makes almost any capture profitable
  - Advances toward promotion while forking
- **Limitations**:
  - Short range (only attacks two squares)
  - Only moves forward

### King Forks
- **Strengths**:
  - Powerful in endgames where king activity dominates
  - Can attack a loose piece while checking, or attack two loose pieces when close

## Special Considerations

### King in Check Dynamics (Absolute Forks)
When one forked piece is the king:
1. **Must Respond**: King must move, block, or the checking piece must be captured
2. **Blocking Complications**: If another forked piece can block, the fork may fail
3. **Forcing Nature**: Makes this an absolute fork - response is mandatory

### The Value Differential Principle (Relative Forks)
For a fork to be tactically sound based on value:
- **Forking Piece Value < Target Values**: The attacker should be less valuable (relative fork principle)
- **Multiple High-Value Targets**: If attacking pieces worth more, need at least two
- **Single High-Value Target**: One high-value piece can escape unless it's hanging

### Defender Counting
- **Hanging**: 0 defenders - will be captured
- **Under-defended**: Fewer defenders than attackers after fork
- **Adequately defended**: Equal or more defenders than attackers

### Forking Square Safety
The safety of the forking square itself is critical:
- **Overprotected**: More defenders than attackers on the forking square
- **Adequately protected**: Equal defenders and attackers
- **Under-protected**: Fewer defenders than attackers
- **Exchange evaluation**: Consider the sequence of captures on the forking square

### Positional vs Tactical Assessment
A fork can be:
- **Tactically sound**: Wins material based on pure calculation
- **Positionally strong**: Best move even without material gain
- **Both or neither**: These dimensions are independent

## Common Fork Failures

### Why Forks Fail
1. **Single High-Value Escape**: Only one piece worth more than attacker (it moves away)
2. **All Targets Defended**: Every attacked piece is protected and of equal or lower value
3. **Forking Piece Vulnerable**: Can be captured for profit
4. **Blocking Saves Both**: One piece blocks check and protects the other piece
5. **Counter-Pin**: Opponent pins the forking piece, preventing captures
6. **Zwischenzug (In-Between Move)**: Opponent inserts an intermediate check or stronger threat that refutes or neutralizes the fork
7. **Counter-Attack**: Opponent creates a stronger threat (check, mate threat)
   - Forces abandonment of the fork to deal with the threat

### Evaluation Guidelines
When assessing a potential fork:
1. Count undefended pieces (2+ = winning fork)
2. Check for king in check (forces response)
3. Count pieces worth more than attacker (need 2+)
4. Verify forking piece safety
5. Consider blocking possibilities in checks
6. Scan for zwischenzugs (in-between moves), counterchecks, and other forcing resources

## Defense Against Forks

### Preventive Principles
- **Spacing discipline**: Avoid placing two high-value pieces on common fork patterns
- **Color rule**: Knight and bishop forks require pieces on same color complex
- **King safety**: Knights can not check a king next to it; keep king away from typical knight fork squares
- **Overprotect key squares**: Control typical forking squares before tactical operations
- **Don’t cluster**: Avoid aligning multiple pieces on one line/diagonal where bishop/rook/queen forks become possible
- **Keep pieces defended**: Reduce hanging targets; add a defender whenever possible

## Practical Application

### Fork Recognition Checklist
- [ ] How many pieces are attacked?
- [ ] How many are insufficiently defended?
- [ ] Is the king in check?
- [ ] How many targets are worth more than the attacker?
- [ ] Can the forking piece be captured profitably?
- [ ] Can the forking piece be pinned?
- [ ] Can one attacked piece move and protect the other one?
- [ ] Is there a zwischenzug or countercheck available?
