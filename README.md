# hang_man

import random
logo = ''' 
 _                                             
| |                                            
| |__   __ _ _ __   __ _ _ __ ___   __ _ _ __  
| '_ \ / _` | '_ \ / _` | '_ ` _ \ / _` | '_ \ 
| | | | (_| | | | | (_| | | | | | | (_| | | | |
|_| |_|\__,_|_| |_|\__, |_| |_| |_|\__,_|_| |_|
                    __/ |                      
                   |___/    '''
print(logo)                  
stages = ['''
  +---+
  |   |
  O   |
 /|\  |
 / \  |
      |
=========
''', '''
  +---+
  |   |
  O   |
 /|\  |
 /    |
      |
=========
''', '''
  +---+
  |   |
  O   |
 /|\  |
      |
      |
=========
''', '''
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
  |   |
      |
      |
=========
''', '''
  +---+
  |   |
  O   |
      |
      |
      |
=========
''', '''
  +---+
  |   |
      |
      |
      |
      |
=========
''']
word_list = ['abruptly', 'absurd', 'abyss', 'affix', 'askew', 'avenue', 'awkward', 'axiom', 'azure', 'bagpipes', 'bandwagon', 'banjo', 'bayou', 'beekeeper', 'bikini', 'blitz', 'blizzard', 'boggle', 'bookworm', 'boxcar', 'boxful', 'buckaroo', 'buffalo', 'buffoon', 'buxom', 'buzzard', 'buzzing', 'buzzwords', 'caliph', 'cobweb', 'cockiness', 'croquet', 'crypt', 
'curacao', 'cycle', 'daiquiri', 'dirndl', 'disavow', 'dizzying', 'duplex']

#- Get the computer to Randomly choose a word from the word_list and assign it to a variable called chosen_word.
chosen_word = random.choice(word_list)
print(f"Computer's choice is: {chosen_word}")
#TODO-1: - Create a variable called 'lives' to keep track of the number of lives left. 
#Set 'lives' to equal 6.
live = 6

#TODO-3: - Create an empty List called display.
#For each letter in the chosen_word, add a "_" to 'display'.
#So if the chosen_word was "apple", display should be ["_", "_", "_", "_", "_"] with 5 "_" representing each letter to guess.
display = []
lenght = len(chosen_word)
for letter in range(lenght):
  display+="_"
#TODO-1: - Use a while loop to let the user guess again. The loop should only stop once the user has guessed all the letters in the chosen_word and 'display' has no more blanks ("_"). Then you can tell the user they've won
correct_answer = False
while not correct_answer:

#TODO-2 - get the player to guess individual letters in the chosen_word and assign their answer to a variable called guess. Make guess lowercase.
  guess = input("Guess a letter:\n").lower()
  if guess in display:
        print(f"You've already guessed {guess}")

#TODO-2: - Loop through each position in the chosen_word;
#If the letter at that position matches 'guess' then reveal that letter in the display at that position.
#e.g. If the user guessed "p" and the chosen word was "apple", then display should be ["_", "p", "p", "_", "_"].
  for position in range(lenght):
    letter = chosen_word[position]
    #print(f"Current position: {position}\n Current letter: {letter}\n Guessed letter: {guess}")
    if letter == guess:
      display[position] = letter
#TODO-2: - If guess is not a letter in the chosen_word,
#Then reduce 'lives' by 1. 
#If lives goes down to 0 then the game should stop and it should print "You lose."
  if guess != chosen_word:
    print(f"You guessed {guess}, that's not in the word. You lose a life.")
    live +=-1
  elif live == 0:
    print("You lose.")

  #Join all the elements in the list and turn it into a String.
    print(f"{' '.join(display)}")
#TODO-3 - Check if the letter the user guessed (guess) is one of the letters in the chosen_word.
  #for letter in chosen_word:
    #if letter == guess:
      #print("Correct")
    #else:
      #print("Wrong")
  print(display)
  if "_"not in display:
    correct_answer = True
    print("you win.")
  print(stages[live])
