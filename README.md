// Inventory Displayer Pointer
// Demonstrates passing constant pointers to constant objects

#include "pch.h"
#include <iostream>


using namespace std;

void minusPoints(int* const px, int* py); // Function to subtract points to user score
void addPoints(int* const px, int* py); // Function to add points to user score
void instructions(); // Function holding game instructions

int main()
{
	int  guess, correct; // users guess and correct number
	char again; // To rerun game	
	int plus = 10; // added to user score if correct
	int minus = 10; // subtracted from user score if incorrect
	int startingNumber = 5; // used for multiplying
	int multiplier = 1; // multiplier added each time
	int game = 1; // amount of games played

	// calling the function instructions()
	instructions();

	do // continue playing
	{

		int userScore = 0; // user score
		int scoreToWin = 50; // score to win

		cout << "\nGame: " << game << "\n\n"; // display how many games have been played

		do // Continue playing until score is reached
		{
			
			correct = (startingNumber * multiplier); // finding the correct answer

			cout << "\nYour question is: \n";
			cout << startingNumber << " * " << multiplier << " \n"; // displaying question
			cout << "Your guess is: \n";
			cin >> guess; // assigning user input to guess

			if (guess == correct) // if correct
			{
				//calling function to add points
				addPoints(&plus, &userScore);
				++multiplier; // increase multiplier
			}
			else // if incorrect
			{
				// calling function to minus points
				minusPoints(&minus, &userScore);
				++multiplier; // increase multiplier
			}



		} while (userScore != scoreToWin); // While statement to continue till 100 score

		++game; // Increase game count

		// Ask the recruit if they would like to run the simulation again
		cout << "====================================================================================================================\n"; // Spacing
		cout << "You have beat the game with a score of 50! \n";
		cout << "\nWould you like to play again? Y/N: "; // Ask user to play again
		cin >> again; // record user input


	} while (again == 'Y'); // While statement to play again

	cout << "Thank you for playing!\n";
	cout << "Ending game...\n";

	system("pause");
	

	return 0;
}

//creating the function to display instructions
void instructions()
{
	cout << "\t\t Multiples of Five! \n\n";
	cout << "You will be asked to answer a multiplication question based off the number 5. \n";
	cout << "If you get the answer correct your score will increase by 10.\n";
	cout << "If you answer the question incorrect your score will be reduced by 10. \n";
	cout << "Once your score reaches 50 you win! \n";
	cout << "Good Luck!\n";
}

//creating the function to subtract points from user score
void minusPoints(int* const px, int* py) // x is minus amount y is user score
{
	int minus = *px; // create variable to subtract with
	*py = (*py - minus); // subtract from user score
	cout << "\nIncorrect!\n";
	cout << "Your score is: " << *py << "\n"; // display score
}

//creating the function to add to user score
void addPoints(int* const px, int* py) // x is add amount y is user score
{
	int plus = *px; // create variable to add with
	*py = (*py + plus); // add to user score
	cout << "\nCorrect!\n";
	cout << "Your score is: " << *py << "\n"; // display user score
}



