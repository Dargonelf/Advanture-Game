import time
import random


inventory = ['Worn Battleaxe']
weapon = ['Ashbringer Sword', 'Nightfall Axe',
          'Spinal Reaper Axe', 'Ashkandi, Greatsword of the Brotherhood']
possibleNPCs = ['Booty Bay Bandits', 'Scarlet Crusader Soldier',
                'Blackrock Clan Orc']
place = []
weapon = random.choice(weapon)
possibleNPCs = random.choice(possibleNPCs)


def print_pause(String):
    print(String)
    time.sleep(3)


def intro():
    print_pause("You find yourself standing in an open field,\n "
                "filled with grass and yellow wildflowers.\n")
    print_pause(f"Rumor has it that a {possibleNPCs} is somewhere\n "
                "around here, and has been terrifying the nearby village.")
    print_pause("In front of you is a house.")
    print_pause("To your right is a dark cave.")
    print_pause("In your hand you hold your trusty\n "
                "but, dull and not very effective Worn Battleaxe.")
    print_pause("\n Enter 1 to knock on the door of House."
                "\n Enter 2 to peer into the cave."
                "\n What would you like to do?")


def house():
    print_pause("You approach the door of the house.")
    print_pause("You are about to knock, when the door\n "
                "and out steps a " + possibleNPCs + " ")
    print_pause(f"This is one of {possibleNPCs} house!")
    if 'Worn Battleaxe' in inventory:
        print_pause("you feel a bit under-prepared for this,\n "
                    "with only having a dull and Worn Battleaxe.")
        hit = ''
        while hit != '1' and hit != '2':
            hit = input("Would you like to (1) Fight or (2) Run away?")
            if hit == '1':
                print_pause("You fought Bravely, But what could have\n "
                            "you done with just a Worn Battleaxe.")
                print_pause(f"That wretched {possibleNPCs}, Killed you.")
                print_pause("\n \n \t YOU LOSE!")
                play_again()
            if hit == '2':
                field()
                print_pause("\n \n \t YOU LOSE!")
                play_again()

    elif weapon in inventory:
        print_pause(f"The {possibleNPCs} attack you \n ")
        hit = ''
        while hit != '1' and hit != '2':
            hit = input("Would you like to (1) Fight or (2) Run away?\n ")
            if hit == '1':
                print_pause("As the " + possibleNPCs + " moves to attack,\n "
                            "you unsheath your new " + weapon + '.')
                print_pause(f"The " + weapon + " of " + {possibleNPCs} " \n "
                            "shines brightly in your hand as you\n "
                            "brace yourself for the attack.")
                print_pause(f"But the {possibleNPCs} takes one look at\n"
                            "your shiny new toy and runs.")
                print_pause(f"You have rid the town of the {possibleNPCs} "
                            "YOU ARE Triumphant!")
                print_pause("\n \n \t YOU WON")
                play_again()
            if hit == '2':
                field()
                print_pause("\n \n \t YOU LOSE")
                play_again()
    else:
        print_pause("\n \n \t YOU LOSE")
        play_again()


def cave():
    if 'cave' not in place:
        print_pause("You Peer cautiously into the cave.")
        print_pause("It turns out to be only a very small cave.")
        print_pause("You have found the " + weapon + "!\n")
        print_pause("You Discard your dull worn Battleaxe and\n "
                    "take the " + weapon + " with you.")
        inventory.remove('Worn Battleaxe')
        inventory.append(weapon)
        print_pause("You walk Back out to the field.")
        place.append('cave')
    else:
        print_pause("\n You Peer cautiously into the cave.")
        print_pause("You've been here before, and gotton all the good\n "
                    "stuff it's just an empty cave now.")
        print_pause("You walk Back out to the field.")


def field():
    print_pause("You run into the field. Luckily,\n "
                "you don't seem to have been followed.")
    print_pause("You Run off cowardly to the field. NANI!")


def adventure_game():
    hit = ''
    if 'started' not in place:
        intro()
        place.append('started')
        while hit != '1' and hit != '2':
            hit = input("\n (Please enter 1 or 2.)\n")
            if hit == '1':
                house()
            if hit == '2':
                cave()
                adventure_game()
    else:

        while hit != '1' and hit != '2':
            hit = input("\n (Please enter 1 or 2.)\n")
            if hit == '1':
                house()
            if hit == '2':
                cave()
                adventure_game()


def play_again():
    hit = input("\nWOULD YOU LIKE TO PLAY AGAIN!!!\n"
                "If YES Enter 1\n"
                "If NO Enter 2\n")
    if hit == '1':
        adventure_game()
    elif hit == '2':
        print_pause("Thanks for playing!\n"
                    "\n"
                    "Good Luck")
    else:
        print_pause("Please Enter 1 or 2")
        play_again()


adventure_game()
