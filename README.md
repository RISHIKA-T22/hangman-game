
import random

def choose_word():
    """Randomly selects a word from a predefined list."""
    word_list = ['python', 'hangman', 'developer', 'internship', 'function']
    return random.choice(word_list).lower()

def display_word(word, guessed_letters):
    """Returns the current state of the guessed word."""
    return ' '.join([letter if letter in guessed_letters else '_' for letter in word])

def hangman():
    word = choose_word()
    guessed_letters = set()
    correct_letters = set(word)
    attempts_left = 6

    print("🎯 Welcome to the Hangman Game!")
    print("Guess the word, one letter at a time.\n")

    while attempts_left > 0 and correct_letters != guessed_letters:
        print(f"Word: {display_word(word, guessed_letters)}")
        print(f"Attempts left: {attempts_left}")
        guess = input("Enter a letter: ").lower()

        if not guess.isalpha() or len(guess) != 1:
            print("⚠️ Please enter a valid single letter.\n")
            continue

        if guess in guessed_letters:
            print("🔁 You've already guessed that letter.\n")
            continue

        guessed_letters.add(guess)

        if guess in correct_letters:
            print("✅ Good guess!\n")
        else:
            attempts_left -= 1
            print("❌ Wrong guess!\n")

    # Game Result
    if correct_letters == guessed_letters:
        print(f"🎉 Congratulations! You guessed the word: {word}")
    else:
        print(f"💀 Game Over! The correct word was: {word}")

# Entry Point
if __name__ == "__main__":
    hangman()
