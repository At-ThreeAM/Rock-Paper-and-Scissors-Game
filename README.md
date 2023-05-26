# Rock-Paper-and-Scissors-Game

#include <stdio.h>
#include <stdlib.h>
#include <time.h>

#define ROCK 0
#define PAPER 1
#define SCISSORS 2

int generateComputerChoice() {
    // Generate a random number between 0 and 2
    return rand() % 3;
}

int determineWinner(int playerChoice, int computerChoice) {
    // Returns 1 if the player wins, -1 if the computer wins, and 0 for a tie

    if ((playerChoice == ROCK && computerChoice == SCISSORS) ||
        (playerChoice == PAPER && computerChoice == ROCK) ||
        (playerChoice == SCISSORS && computerChoice == PAPER)) {
        return 1;
    } else if (playerChoice == computerChoice) {
        return 0;
    } else {
        return -1;
    }
}

void printChoice(int choice) {
    switch (choice) {
        case ROCK:
            printf("Rock");
            break;
        case PAPER:
            printf("Paper");
            break;
        case SCISSORS:
            printf("Scissors");
            break;
    }
}

int main() {
    int playerChoice, computerChoice;
    int result;

    srand(time(NULL));  // Initialize random seed

    printf("Welcome to Rock, Paper, Scissors!\n");
    printf("Enter your choice:\n");
    printf("0 - Rock\n");
    printf("1 - Paper\n");
    printf("2 - Scissors\n");
    scanf("%d", &playerChoice);

    if (playerChoice < 0 || playerChoice > 2) {
        printf("Invalid choice! Please enter a number between 0 and 2.\n");
        return 1;
    }

    computerChoice = generateComputerChoice();

    printf("You chose: ");
    printChoice(playerChoice);
    printf("\n");

    printf("Computer chose: ");
    printChoice(computerChoice);
    printf("\n");

    result = determineWinner(playerChoice, computerChoice);

    if (result == 1) {
        printf("Congratulations! You win!\n");
    } else if (result == -1) {
        printf("Sorry! Computer wins!\n");
    } else {
        printf("It's a tie!\n");
    }

    return 0;
}
