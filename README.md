import random

def guess_the_number():
    print("Welcome to Guess the Number!")
    print("Difficulty levels:")
    print("1. Easy (unlimited guesses)")
    print("2. Medium (10 guesses)")
    print("3. Hard (5 guesses)")
    
    level = input("Choose difficulty (1-3): ")
    if level == "1":
        max_attempts = float('inf')
    elif level == "2":
        max_attempts = 10
    else:
        max_attempts = 5
    
    number = random.randint(1, 100)
    attempts = 0
    score = 1000  # Starting score
    
    while attempts < max_attempts:
        guess = input("Guess a number between 1-100: ")
        
        try:
            guess = int(guess)
        except ValueError:
            print("Please enter a valid number!")
            continue
            
        attempts += 1
        
        if guess < number:
            print("Too low!")
            score -= 50
        elif guess > number:
            print("Too high!")
            score -= 50
        else:
            print(f"Congratulations! You guessed it in {attempts} attempts!")
            print(f"Your final score is: {max(0, score)}")  # Ensure score doesn't go negative
            return
    
    print(f"Sorry, you're out of guesses! The number was {number}.")

if __name__ == "__main__":
    guess_the_number()
