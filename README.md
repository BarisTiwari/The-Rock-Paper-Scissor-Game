# The-Rock-Paper-Scissor-Game
The Project is a miniature demo of a rock paper scissor game using random and some different function and i developed this to show that i am soo much furnished on my basics and my hands on knowledge on python.

==========================================================================
import random
import os
import time

moves = ["rock", "paper", "scissors"]

def normalize_choice(choice):
    choice = choice.strip().lower()

    if choice.startswith("r"): return "rock"
    if choice.startswith("p"): return "paper"
    if choice.startswith("s"): return "scissors"

    for mv in moves:
        if mv[0] == choice[0]:  # first letter match
            return mv
    return None

def intro():
    print("="*50)
    print("     ✊ Rock  ✋ Paper  ✌️ Scissors")
    print("="*50)
    print("First to 3 points wins the match!")
    print("Are You Ready To Grind.....?")

def get_player_choice(player_name):
    while True:
        raw = input(f"{player_name}, enter your move (rock/paper/scissors or r/p/s): ")
        move = normalize_choice(raw)
        if move:
            return move
        else:
            print("⚠️ Invalid move... try again.")

def get_computer_choice():
    return random.choice(moves)

def decide_winner(p1, p2):
    if p1 == p2:
        return "draw"
    elif (p1 == "rock" and p2 == "scissors") or \
         (p1 == "scissors" and p2 == "paper") or \
         (p1 == "paper" and p2 == "rock"):
        return "p1"
    else:
        return "p2"

# main game
def play_game(mode, player1, player2):
    p1_score, p2_score = 0, 0
    round_num = 1

    while p1_score < 3 and p2_score < 3:
        print(f"\n----- Round {round_num} -----")

        if mode == "vs_computer":
            p1_move = get_player_choice(player1)
            p2_move = get_computer_choice()
            print(f"{player2} played: {p2_move}")
        else:  # vs human
            p1_move = get_player_choice(player1)
            os.system('cls' if os.name == 'nt' else 'clear')  
            p2_move = get_player_choice(player2)

        print(f"{player1} played: {p1_move}")
        print(f"{player2} played: {p2_move}")

        res = decide_winner(p1_move, p2_move)

        if res == "draw":
            print("😅 It's a draw!")
        elif res == "p1":
            print(f"✅ {player1} wins this round!")
            p1_score += 1
        else:
            print(f"✅ {player2} wins this round!")
            p2_score += 1

        print(f"📊 Score => {player1}: {p1_score} | {player2}: {p2_score}")
        round_num += 1
        time.sleep(1)

    print("\n===== FINAL RESULT =====")
    if p1_score > p2_score:
        print(f"🏆 {player1} is the CHAMPION!")
    else:
        print(f"🏆 {player2} is the CHAMPION!")
        
if __name__ == "__main__":
    intro()

    p1_name, p2_name = "Player 1", "Player 2"

    edit = input("Do you want to edit player names? (y/n): ").strip().lower()
    if edit == "y":
        p1_name = input("Enter name for Player 1: ") or "Player 1"
        p2_name = input("Enter name for Player 2: ") or "Player 2"

    print("\nChoose Mode:")
    print("1. Play vs Computer")
    print("2. Play vs Friend")
    mode_input = input("Enter 1 or 2: ").strip()

    if mode_input == "1":
        play_game("vs_computer", p1_name, "Computer")
    else:
        play_game("vs_human", p1_name, p2_name)
print("===================================")





a = input("Do You Want Continue.....?")
if a == "y":
    print("This Option Is Just For Test")
else:
    print("Thanks For Playing The Game")


