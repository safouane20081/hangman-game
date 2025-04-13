import random 
hangman_stages = ['''
  +---+
  |   |
      |
      |
      |
      |
=========''', '''
  +---+
  |   |
  O   |
      |
      |
      |
=========''', '''
  +---+
  |   |
  O   |
  |   |
      |
      |
=========''', '''
  +---+
  |   |
  O   |
 /|   |
      |
      |
=========''', '''
  +---+
  |   |
  O   |
 /|\  |
      |
      |
=========''', '''
  +---+
  |   |
  O   |
 /|\  |
 /    |
      |
=========''', '''
  +---+
  |   |
  O   |
 /|\  |
 / \  |
      |
=========''']

words = ["Cristiano", "Messi", "Neymar"]
random_word = random.choice(words).capitalize()
display = ["_"] * len(random_word)
lives = 6
guessed_letters = []

print(" ".join(display))
print(hangman_stages[0])

while "_" in display and lives > 0:
    guessed = input("Please guess a letter: ").capitalize()
    if guessed in guessed_letters:
        print("You already guessed that. Try again.")
        print(f"You have {lives} more tries")
        continue
    guessed_letters.append(guessed)
    if guessed not in random_word:
        lives -= 1
        print("Wrong guess!")
    else:
        for x in range(len(random_word)):
            if random_word[x] == guessed:
                display[x] = guessed
    print(" ".join(display))
    print(f"You have {lives} more tries")
    print(hangman_stages[6 - lives])

if lives == 0:
    print("You lost! The word was:", random_word)
else:
    print("Congratulations! You guessed the word 🎉")

