# Hungman-Game
import random
def chwo():
    words = ["project", "javascript", "programming", "internship", "company", "developer", "syntax"]
    return random.choice(words)
def diswo(word, guesslet):
    display = ""
    for letter in word:
        if letter in guesslet:
            display += letter
        else:
            display += " _ "
    return display
def hung():
    max_att = 6
    word = chwo()
    guesslet = []
    attempts = 0
    print("Welcome to hung Game")
    name = input("\nEnter username :")
    while True:
        print("" + diswo(word, guesslet))
        guess = input("\nGuess a letter: ").lower()
        if len(guess) != 1 or not guess.isalpha():
            print("Only single letter is accepted ")
            continue
        if guess in guesslet:
            print("Try using another letter")
            continue
        guesslet.append(guess)
        if guess in word:
            if all(letter in guesslet for letter in word):
                print(word)
                print("\nCongratulations! "+name+" You Won the game ")
                break
        else:
            attempts += 1
            print("Incorrect attempt.")
            print(f"Attempts left: {max_att - attempts}")
            if attempts == max_att:
                print("Game Over! The word was: " + word)
                print("Better luck next time")
                break
