"""
Project: Rock-Paper-Scissors Game
Description:
A simple command-line game where the user plays Rock, Paper, Scissors
against the computer. The game includes score tracking and the option
to play multiple rounds until the user chooses to exit.
"""

import random

def get_user_choice():
    while True:
        choice = input("Choose Rock, Paper, or Scissors (or type 'exit' to quit): ").lower()
        if choice in ['rock', 'paper', 'scissors', 'exit']:
            return choice
        else:
            print("Invalid input. Please choose Rock, Paper, or Scissors.")

def get_computer_choice():
    return random.choice(['rock', 'paper', 'scissors'])

def determine_winner(user, computer):
    if user == computer:
        return 'tie'
    elif (user == 'rock' and computer == 'scissors') or \
         (user == 'scissors' and computer == 'paper') or \
         (user == 'paper' and computer == 'rock'):
        return 'user'
    else:
        return 'computer'

def display_result(user, computer, winner):
    print(f"\nYou chose: {user.capitalize()}")
    print(f"Computer chose: {computer.capitalize()}")

    if winner == 'tie':
        print("It's a tie!")
    elif winner == 'user':
        print("You win! 🎉")
    else:
        print("Computer wins! 🤖")

def play_game():
    user_score = 0
    computer_score = 0

    print("=== Welcome to Rock-Paper-Scissors! ===")

    while True:
        user_choice = get_user_choice()
        if user_choice == 'exit':
            print("\nThanks for playing!")
            print(f"Final Score - You: {user_score}, Computer: {computer_score}")
            break

        computer_choice = get_computer_choice()
        winner = determine_winner(user_choice, computer_choice)
        display_result(user_choice, computer_choice, winner)

        if winner == 'user':
            user_score += 1
        elif winner == 'computer':
            computer_score += 1

        print(f"Current Score - You: {user_score}, Computer: {computer_score}\n")

# Run the game
play_game()
