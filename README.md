# Hangman
No ascii cowboy yet!

#HANGMAN 10guesses
from random import randint

def Choose_Word(s):
    return s[randint(0, len(s)-1)]

#SUBJECTS
words = ["tree", "dog", "cat", "apple", "banana"]
animals = ["dog", "cat", "mouse", "elephant", "emu", "zebra", "dolphin", "fox", "panda", "monkey"]
sport = ["basketball", "tennis", "raquet", "bat", "puck", "cricket", "football", "squash", "lacrosse"]
food = ["butter", "sugar", "salt", "pepper", "watermelon", "banana", "apple", "pineapple", "pizza", "pie", "lemon", "cake", "chicken", "beef", "lamb", "pork"]
rand_sub = [animals, sport, food]

guesses = 10
guess = ""
letters = []
GuessLets = []
sub = []

sub_choice = input("Choose a subject:\n1: Animals\n2: Sport\n3: Food\n4: Random subject\n\n")
if sub_choice == "1":
    sub = animals
elif sub_choice == "2":
    sub = sport
elif sub_choice == "3":
    sub = food
elif sub_choice == "4":
    sub = rand_sub[randint(0, 2)]



answer = Choose_Word(sub)
for a in answer:
    letters.append(a)
    GuessLets.append("_")

print(' '.join(GuessLets))

while GuessLets != letters and guesses > 0:
    letter = input("Guess a letter: ")
    c = 0
    for a in range(len(answer)):
        if answer[a] == letter:
            GuessLets[a] = letter
            c+=1
    if c == 0:
        guesses -= 1
    print(' '.join(GuessLets))
    print("Guesses left:", guesses)
else:
    if guesses > 0:
        print("WELL DONE!")
    else:
        print("You were hung...\nThe word was:", ''.join(answer))


