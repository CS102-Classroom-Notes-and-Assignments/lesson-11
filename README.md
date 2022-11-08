# lesson-11

## WHAT IS PYTHON?
- Interpretative language
- Emphasizes code readability
- Dynamic type system (no explicit types)
- Easier to write; good for prototyping
- Slower than C/C++!

***Python Docs:*** https://docs.python.org/3/tutorial/index.html

## HELLO WORLD
### FIRST PYTHON PROGRAM
```py
print("Hello World")
```
Note that there are no semicolons!

## CONDITIONALS
#### IF, ELIF, ELSE
```py
temp = 50 # in F
freezing = 32
boiling = 212

if temp <= freezing:
    print("I'm freezing!")
elif temp >= boiling:
    print("I'm boiling!")
else:
    print("I'm somewhere in between")
```

No types for variables
Note the indentation; it's required!
You need a colon for conditionals


## LOOPS & ARRAYS
### WHILE LOOPS
```py
# Three Year-Old Simulator

print("\t Welcome to the 'Three-Year-Old Simulator'\n")
print("This program simulates a conversation with a three-year-old child.")
print("Try to stop the madness.\n")

response = ""
while response != "Because.":
    response = input("Why?\n")

print("Oh. Okay.")

input("\n\nPress the enter key to exit.")
```


## FOR LOOPS
- The final number gets excluded!

```py
print("Counting!")

for i in range(10):
    print(i, end=" ") # end makes print not end in a \n

print("\n\nCounting by fives:")
for i in range(0, 50, 5):
    print(i, end=" ")

print("\n\nCounting backwards:")
for i in range(10, 0, -1):
    print(i, end=" ")
```

## ARRAYS
```py
word = "Python is awesome!"

print(word[0:6]) # excludes last

print(word[-5])

for i in word:
    print(i, end=" ")
```


## DICTIONARY
```py
nba_finals = {
    "1947": "Chicago Stags",
    "1998": "Utah Jazz",
    "2002": "New Jersey Nets",
    "2017": "Golden State Warriors ",
    "2018": "Golden State Warriors ",
    "2019": "Toronto Raptors",
    "2020": "Los Angeles Lakers",
    "2021": "Milwaukee Bucks",
    "2022": "Golden State Warriors"
}

print("Winner in year 2022: ", nba_finals["2002"])
print("Winner in year 2025: ",  nba_finals["2025"] if "2025" in nba_finals else "not valid year")
```


## LIST
```py
# Create a list with some items and display them

inventory = ["sword", "armor", "shield", "potion"]
print("Your items:")
for item in inventory:
    print(item)
```

## DICTIONARY
### HANGMAN

#### HANGMAN GAME
```py
# Hangman Game
#
# The classic game of Hangman.  The computer picks a random word
# and the player tries to guess it, one letter at a time.  If the player
# can't guess the word in time, the little stick figure gets hanged.

# imports
import random

# constants
HANGMAN = (
"""
 ------
 |    |
 |
 |
 |
 |
 |
 |
 |
----------
""",
"""
 ------
 |    |
 |    O
 |
 |
 |
 |
 |
 |
----------
""",
"""
 ------
 |    |
 |    O
 |   -+-
 | 
 |   
 |   
 |   
 |   
----------
""",
"""
 ------
 |    |
 |    O
 |  /-+-
 |   
 |   
 |   
 |   
 |   
----------
""",
"""
 ------
 |    |
 |    O
 |  /-+-/
 |   
 |   
 |   
 |   
 |   
----------
""",
"""
 ------
 |    |
 |    O
 |  /-+-/
 |    |
 |   
 |   
 |   
 |   
----------
""",
"""
 ------
 |    |
 |    O
 |  /-+-/
 |    |
 |    |
 |   | 
 |   | 
 |   
----------
""",
"""
 ------
 |    |
 |    O
 |  /-+-/
 |    |
 |    |
 |   | |
 |   | |
 |  
----------
""")

MAX_WRONG = len(HANGMAN) - 1
WORDS = ("OVERUSED", "CLAM", "GUAM", "TAFFETA", "PYTHON")

# initialize variables
word = random.choice(WORDS)   # the word to be guessed
word_guessed_so_far = "-" * len(word)      # one dash for each letter in word to be guessed
wrong_guesses = 0                     # number of wrong guesses player has made
used_letters = []                     # letters already guessed


print("Welcome to Hangman.  Good luck!")

while wrong_guesses < MAX_WRONG and word_guessed_so_far != word:
    print(HANGMAN[wrong_guesses])
    print("\nYou've used the following letters:\n", used_letters)
    print("\nSo far, the word is:\n", word_guessed_so_far)

    guess = input("\n\nEnter your guess: ")
    guess = guess.upper()

    while guess in used_letters:
        print("You've already guessed the letter", guess)
        guess = input("Enter your guess: ")
        guess = guess.upper()

    used_letters.append(guess)

    if guess in word:
        print("\nYes!", guess, "is in the word!")

        # create a new word_guessed_so_far to include guess
        new = ""
        for i in range(len(word)):
            if guess == word[i]:
                new += guess
            else:
                new += word_guessed_so_far[i]              
        word_guessed_so_far = new

    else:
        print("\nSorry,", guess, "isn't in the word.")
        wrong_guesses += 1

if wrong_guesses == MAX_WRONG:
    print(HANGMAN[wrong_guesses])
    print("\nYou've been hanged!")
else:
    print("\nYou guessed it!")

print("\nThe word was", word)

input("\n\nPress the enter key to exit.")
```

###### Bonus Questions to consider:
- why was a tuple used instead of a list?
    - https://stackoverflow.com/questions/1708510/list-vs-tuple-when-to-use-each
- How can the code above be improved?

### Python Notebooks
- Jupyter Notebook
- https://colab.research.google.com/

## HOMEWORK
- Python Programming for the Absolute Beginner, chapters 1-4
- hw link: (5 points for completing the first question in class), rest for take home: https://classroom.github.com/a/A9yyYNO5
