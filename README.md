<h1>ExpNo 7 : Implement Alpha-beta pruning of Minimax Search Algorithm for a Simple TIC-TAC-TOE game</h1> 
<h3>Name:       </h3>
<h3>Register Number/Staff Id:           </h3>
<H3>Aim:</H3>
<p>
Implement Alpha-beta pruning of Minimax Search Algorithm for a Simple TIC-TAC-TOE game
</p>
<h1>GOALS of Alpha-Beta Pruning in MiniMax Search Algorithm</h1>

<h3>Improve the decision-making efficiency of the computer player by reducing the number of evaluated nodes in the game tree.</h3>
<h3>Tic-Tac-Toe game implementation incorporating the Alpha-Beta pruning and the Minimax algorithm with Python Code.</h3>
<h1>IMPLEMENTATION</h1>

The project involves developing a Tic-Tac-Toe game implementation incorporating the Alpha-Beta pruning with the Minimax algorithm. Using this algorithm, the computer player analyzes the game state, evaluates possible moves, and selects the optimal action based on the anticipated outcomes.

<h1>The Minimax algorithm</h1>

recursively evaluates all possible moves and their potential outcomes, creating a game tree.

<h1>Alpha-Beta pruning</h1>

Alpha–Beta (𝛼−𝛽) algorithm is actually an improved minimax using a heuristic. It stops evaluating a move when it makes sure that it’s worse than a previously examined move. Such moves need not to be evaluated further.

When added to a simple minimax algorithm, it gives the same output but cuts off certain branches that can’t possibly affect the final decision — dramatically improving the performance
<hr>
<h2>Sample Input and Output:</h2>

## Programme
```import time
import math

board = [["." for _ in range(3)] for _ in range(3)]

def print_board():
    for row in board:
        print(" | ".join(row))
        print("---------")

def winner(b):
    lines = b + list(map(list, zip(*b)))
    lines += [
        [b[i][i] for i in range(3)],
        [b[i][2 - i] for i in range(3)]
    ]

    for line in lines:
        if line == ["X"] * 3:
            return -1
        if line == ["O"] * 3:
            return 1

    return 0

def minimax(b, maximizing):
    result = winner(b)

    if result != 0:
        return result

    if all(cell != "." for row in b for cell in row):
        return 0

    if maximizing:
        best = -math.inf
        for i in range(3):
            for j in range(3):
                if b[i][j] == ".":
                    b[i][j] = "O"
                    best = max(best, minimax(b, False))
                    b[i][j] = "."
        return best
    else:
        best = math.inf
        for i in range(3):
            for j in range(3):
                if b[i][j] == ".":
                    b[i][j] = "X"
                    best = min(best, minimax(b, True))
                    b[i][j] = "."
        return best

def best_move():
    start = time.time()
    best_score = -math.inf
    move = None

    for i in range(3):
        for j in range(3):
            if board[i][j] == ".":
                board[i][j] = "O"
                score = minimax(board, False)
                board[i][j] = "."

                if score > best_score:
                    best_score = score
                    move = (i, j)

    elapsed = time.time() - start
    print(f"Evaluation time: {elapsed:.7f}s")
    print(f"Recommended move: X = {move[0]}, Y = {move[1]}")
    return move

print("TIC-TAC-TOE USING MINIMAX")
print("You are X. Computer is O.")
print("Coordinates range from 0 to 2.")

while True:
    move = best_move()
    x = int(input("Insert the X coordinate: "))
    y = int(input("Insert the Y coordinate: "))

    if not (0 <= x < 3 and 0 <= y < 3):
        print("Invalid coordinates. Try again.")
        continue

    if board[x][y] != ".":
        print("Cell occupied. Try again.")
        continue

    board[x][y] = "X"
    print_board()

    if winner(board) == -1:
        print("X wins!")
        break

    if all(cell != "." for row in board for cell in row):
        print("Draw!")
        break

    x, y = best_move()
    board[x][y] = "O"
    print_board()

    if winner(board) == 1:
        print("O wins!")
        break

    if all(cell != "." for row in board for cell in row):
        print("Draw!")
        break
```

![image](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/8d5e329a-9aff-41a6-bcf0-46efa10e1b92)
![image](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/438b242d-54ba-443e-b040-a936e6ae3b55)
![image](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/99a33390-fa11-4ade-a19f-e93bcd7aaec9)
![image](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/440797bd-53cb-49c1-b18d-89776864c3e7)
![image](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/81575a16-26b2-46f1-a8ac-27c9ed0a0fe5)

## Output
<img width="1259" height="669" alt="image" src="https://github.com/user-attachments/assets/312b2dd7-61e0-436f-bf6a-4ec6061a228d" />

<img width="1020" height="638" alt="image" src="https://github.com/user-attachments/assets/de49a025-fe39-414e-aa36-bd8be2095252" />

<img width="660" height="209" alt="image" src="https://github.com/user-attachments/assets/2ccc7f73-ee21-4851-b6fb-6ad749bf7751" />

<h2>Result:</h2>
<p>Thus,Implementation of  Minimax Search Algorithm for a Simple TIC-TAC-TOE game wasa done successfully.</p>
