# python code for hangman game 
import random
    def play_hangman():
 # 1. List of 5 predefined words
    words = ["future", "growth", "jungle", "oceans", "planet"]
    
 # 2. Key concept: random (select a word from the list)
    word_to_guess = random.choice(words)
            
 # 3. Key concept: lists (track guessed letters)
    guessed_letters = []
    
    incorrect_guesses = 0
    max_incorrect = 6
    
    print("Welcome to Hangman!")
    
    # 4. Key concept: while loop (continue until win or lose)
    while incorrect_guesses < max_incorrect:
        
        # 5. Key concept: strings (build the display word)
        display_word = ""
        for letter in word_to_guess:
            if letter in guessed_letters:
                display_word += letter + " "
            else:
                display_word += "_ "
                
        print(f"\nWord: {display_word.strip()}")
        print(f"Incorrect guesses left: {max_incorrect - incorrect_guesses}")
        
        # Check win condition
        if "_" not in display_word:
            print("Congratulations! You guessed the word!")
            break
            
        # Basic console input
        guess = input("Guess a letter: ").lower()
        
        # 6. Key concept: if-else (handle different game states)
        if len(guess) != 1 or not guess.isalpha():
            print("Please enter a single valid letter.")
            continue
            
        if guess in guessed_letters:
            print("You already guessed that letter. Try again.")
            continue
            
        guessed_letters.append(guess)
        
        if guess in word_to_guess:
            print("Good guess!")
        else:
            print("Incorrect guess!")
            incorrect_guesses += 1
            
    # Check loss condition outside the loop
    if incorrect_guesses == max_incorrect:
        print(f"\nGame Over! You've run out of guesses. The word was '{word_to_guess}'.")

if __name__ == "__main__":
    play_hangman()
