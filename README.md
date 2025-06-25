import random

def hangman():
    words = ["apple", "tiger", "house", "pizza", "robot"]
    word = random.choice(words)
    guessed = ["_"] * len(word)
    attempts = 6
    guessed_letters = []

    print("Welcome to Hangman!")
    print("Guess the word:")

    while attempts > 0 and "_" in guessed:
        print("Word:", " ".join(guessed))
        print(f"Incorrect guesses left: {attempts}")
        guess = input("Enter a letter: ").lower()

        if not guess.isalpha() or len(guess) != 1:
            print("Please enter a single alphabet.")
            continue

        if guess in guessed_letters:
            print("You've already guessed that letter.")
            continue

        guessed_letters.append(guess)

        if guess in word:
            for i, letter in enumerate(word):
                if letter == guess:
                    guessed[i] = guess
            print("Good guess!")
        else:
            attempts -= 1
            print("Oops! Wrong guess.")

    if "_" not in guessed:
        print(f"Congratulations! You guessed the word: {word}")
    else:
        print(f"Game over! The word was: {word}")

hangman()
