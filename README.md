# hangman_attempt. Trying to create a hangman game

word = list("learn")
hidden = []
for character in word:
    hidden.append("_")

attempts = 0
max_attempts = 4


isGameOver = False
while not isGameOver:

    print(f"You have {max_attempts - attempts} attempts remaining")

    print(f"The current word is: {' '.join(hidden)}")

    print("     _________")
    print("     |       |")
    print("     |       " + ("O" if attempts > 0 else ""))
    print("     |       " + ("/\\" if attempts > 1 else ""))
    print("     |       " + ("|" if attempts > 2 else ""))
    print("     |       " + ("/\\" if attempts > 3 else ""))
    print("     |")
    print("------------")
    print("            ")

    letterGuessed = input("Guess a letter: ")

    print("\n\n\n\n")

    if letterGuessed in word:
        print(
            "Wow, you got a letter. {letterGuessed} is there. I bet you cant do it again.")
        for i in range(len(word)):
            character = word[i]
            if character == letterGuessed:
                hidden[i] = word[i]
                word[i] = "_"

    else:
        print(f"Unlucky! {letterGuessed} is NOT there")
        attempts += 1

    if all("_" == char for char in word):
        print("Congratulations. You win!")
        isGameOver = True

    if attempts >= max_attempts:
        print("Ha. You Lose!")
        isGameOver = True
