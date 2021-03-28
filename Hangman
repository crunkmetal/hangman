// CSC215 C/C++ programming
// March 27, 2021
// Assignment: Contest time sensitive fun!
// Hangman [ March Edition ]

// preprocessor directives
// define hex value for 'clover' symbol as a variable
#define CLOVER    ((char)0x05)
#include <iostream>
#include <vector>
#include <algorithm>
#include <ctime>
#include <cctype>

// NOT using standard template library namespace
// using namespace std;

// global directives
//maximum number of incorrect guesses allowed
const int MAX_WRONG = 8;
//collection of possible words to guess
std::vector<std::string> words;

// function prototypes
void intro();
void populateGuessWords();
void hangman();
void playAgain();
void openVideo();
void uATeam();
void shamrock();
// the one and only 'main' function
int main()
{
	// invoke function to display introduction
    intro();
	// invoke function to populate the guess words vector
    populateGuessWords();
	// invoke function for hangman gameplay
    hangman();
	// main function returns an integer
    return 0;
}
// function to display introduction and game rules
void intro()
{
	std::cout << "\n[] [] [] [] [] [] [] [] [] [] [] [] [] [] [] [] [] \n";
	std::cout << "[] [] [] [] [] [] [] [] [] [] [] [] [] [] [] [] [] \n";
	std::cout << "[] [] [] [] [] [] [] [] [] [] [] [] [] [] [] [] [] \n\n\n\n";
	
	std::cout << "\t\tWelcome to Hangman\n";
	//std::cout << "\t\t[ March Edition ]\n\n\n\n\n";
	std::cout << "\t\t" << CLOVER << " March Edition " << CLOVER << "\n\n\n\n\n";

	std::cout << "[] [] [] [] [] [] [] [] [] [] [] [] [] [] [] [] [] \n";
	std::cout << "[] [] [] [] [] [] [] [] [] [] [] [] [] [] [] [] [] \n";
	std::cout << "[] [] [] [] [] [] [] [] [] [] [] [] [] [] [] [] [] \n\n";

	std::cout << " Instructions:\n";
	std::cout << "  Guess what the word(s) is/are, one letter at a\n";
	std::cout << "  time... or not.  For the March Edition, all of\n";
	std::cout << "  the words have something to do with the month\n";
	std::cout << "  of March!\n\n";
	system("pause>nul|set/p =Press any key to PLAY...");
}
// function that populates a vector with words to guess
// words selected based on a 'march' theme
void populateGuessWords()
{
	// push_back method adds the word(s) in quotes to the 'words' vector
    words.push_back("SAINT_PATRICKS_DAY");
    words.push_back("LEPRECHAUN");
    words.push_back("IDES_OF_MARCH");
    words.push_back("MARCH_MADNESS");
    words.push_back("DAFFODIL");
    words.push_back("PISCES");
    words.push_back("SPRING");
    words.push_back("POT_OF_GOLD");
    words.push_back("RAINBOW");
    words.push_back("MARS");
    words.push_back("VERNAL_EQUINOX");
    words.push_back("ALEXANDER_GRAHAM_BELL");
    words.push_back("PEACE_CORPS");
}
// function to incorporate game play
void hangman()
{
    // random seed generator
    srand(static_cast<unsigned int>(time(0)));
	// shuffle words in guess word vector
    std::random_shuffle(words.begin(), words.end());
    //word to guess
    const std::string THE_WORD = words[0];
    //number of incorrect guesses
    int wrong = 0;
	char space = '_';
    //word guessed so far
    std::string soFar(THE_WORD.size(), '+');
    //letters already guessed
    std::string used;
	// print to display all of the 'spaces' in guess word
	if (THE_WORD.find(space) != std::string::npos)
	{
		for (int i = 0; i < THE_WORD.length(); ++i)
		{
			// if the user guess is in the word
			if (THE_WORD[i] == space)
			{
				// change it's status from hidden to display
				soFar[i] = space;
			}
		}
	}
    // while the word has not been guessed yet AND you have not used up all of your guesses    
    while ((wrong < MAX_WRONG) && (soFar != THE_WORD))
    {   // system command to clear the screen of previous writ
        system("CLS");
        std::cout << "\n";
        std::cout << "\n\nYou have " << (MAX_WRONG - wrong);
        std::cout << " incorrect guesses left.\n";
        std::cout << "You've used the following letters:\t" << used << std::endl;
        std::cout << "\nSo far, the word is:\t\" " << soFar << " \"" << std::endl;
        // char type variable 'guess' is used to collect users character guesses
        char guess;
        std::cout << "\nEnter your guess: ";
        std::cin >> guess;
        //make uppercase since secret word in uppercase
        guess = toupper(guess);
        // search if user's guess has already been used
    	// search through collection of previous guesses until the end of the accumulated std::string
    	// if user's guess has already been used, tell them and ask to guess again
        while (used.find(guess) != std::string::npos)
        {
            std::cout << "\nYou've already guessed " << guess << std::endl;
            std::cout << "Enter your guess: ";
            std::cin >> guess;
        	// capitalize a user's guess
            guess = toupper(guess);
        }
        // add users "guess" to the value of the "guessed characters" std::string
    	used += guess;
        // search the randomly chosen word-to-guess for the presence of the user's guess
        if (THE_WORD.find(guess) != std::string::npos)
        {
            for (int i = 0; i < THE_WORD.length(); ++i)
            {
                // if the user guess is in the word
                if (THE_WORD[i] == guess)
                {
                    // change it's status from hidden to display
                    soFar[i] = guess;
                }
            }
        }
        // if the user guess is NOT in the word
        else
        {
            std::cout << "\nSorry, " << guess << " isn't in the word.\n";
            // add to the 'wrong' guess count amount
            ++wrong;
        }
    }
	// response for losing (too many incorrect guesses)
	if(wrong >= MAX_WRONG)
	{
        system("CLS");
		// invoke function to display loss status
		uATeam();
        std::cout << "\n\n\n[] [] [] [] [] [] [] [] [] [] [] [] [] [] [] [] [] \n";
        std::cout << "[] [] [] [] [] [] [] [] [] [] [] [] [] [] [] [] [] \n";
        std::cout << "[] [] [] [] [] [] [] [] [] [] [] [] [] [] [] [] [] \n\n";
		std::cout << "You have made too many incorrect guesses...\n\n\n";
		std::cout << "\t\tG A M E  O V E R\n\n\n";
        std::cout << "\tThe word is:\t" << THE_WORD;
        std::cout << "\n\n\n[] [] [] [] [] [] [] [] [] [] [] [] [] [] [] [] [] \n";
        std::cout << "[] [] [] [] [] [] [] [] [] [] [] [] [] [] [] [] [] \n";
        std::cout << "[] [] [] [] [] [] [] [] [] [] [] [] [] [] [] [] [] \n\n\n";
        system("pause");
		// invoke function to ask player to play again
        playAgain();
	}
    // response for winning
	system("CLS");
	// invoke function to display loss status
	uATeam();

	std::cout << "\n[] [] [] [] [] [] [] [] [] [] [] [] [] [] [] [] \n";
	std::cout << "[] [] [] [] [] [] [] [] [] [] [] [] [] [] [] [] \n";
	std::cout << "[] [] [] [] [] [] [] [] [] [] [] [] [] [] [] [] \n\n";
	// invoke function to display a big shamrock
	shamrock();

    std::cout << "\t\t   WINNER!!!\n\n\n";
    std::cout << "\t\t\bG A M E  O V E R\n\n\n";
    std::cout << "  The word is:\t\t" << THE_WORD << "\n\n";


	
    std::cout << "[] [] [] [] [] [] [] [] [] [] [] [] [] [] [] [] \n";
    std::cout << "[] [] [] [] [] [] [] [] [] [] [] [] [] [] [] [] \n";
    std::cout << "[] [] [] [] [] [] [] [] [] [] [] [] [] [] [] [] \n\n\n";
    system("pause");
	// invoke function for winning scenario (unused)
    // openVideo();
    // invoke function to ask player to play again
    playAgain();
}
// function to ask player to play again
void playAgain()
{
    char playAgainResponse;
    std::cout << "\nWould you like to play again? (Y or N)\t";
    std::cin >> playAgainResponse;
    // if player does not wish to replay
    if (playAgainResponse == 'N' || playAgainResponse == 'n')
    {
        // exit the application entirely
        exit(0);
    }
    // if player wishes to play again
    if (playAgainResponse == 'Y' || playAgainResponse == 'y')
    {
    	// clear screen
		system("CLS");
    	// invoke start of game loop
        main();
    }
    // handle invalid user input
    else
    {
        std::cout << "\nYou have entered an invalid response.";
		// invoke function to play again
        playAgain();
    }
}
/*
// displays after player wins the game (unused)
void openVideo()
{
    // opens video file in user's default media program
	// make sure video is in proper folder - change this code to proper file directory for execution
    system("C:\\Users\\crunk\\Documents\\UAT\\codeJam\\CodeJamTrailer.mp4");
}
*/

// displays a jumbled screen (a limited recursive loop) after losing the game
void uATeam()
{   // displays file from directory path (unused)
    //system("C:\\Users\\crunk\\Documents\\UAT\\codeJam\\hangman_loss.gif");
    //system("pause");
    int i = 0;
    int team = 50;
	// a fuzzy disoriented display (visual representation of death?)
    while (i < team)
    {
        std::cout << "\t" << CLOVER << "\n";
        std::cout << "\t\t" << CLOVER << "\n";
        std::cout << "\t\t\t" << CLOVER << "\n";
		std::cout << "\t\t\t\t" << CLOVER << "\n";
		std::cout << "\t\t\t\t\t" << CLOVER << "\n";
		std::cout << "\t\t\t\t\t\t" << CLOVER << "\n";
		std::cout << "\t\t\t\t\t" << CLOVER << "\n";
		std::cout << "\t\t\t\t" << CLOVER << "\n";
		std::cout << "\t\t\t" << CLOVER << "\n";
		std::cout << "\t\t" << CLOVER << "\n";
        std::cout << "\t" << CLOVER << "\n";
        std::cout << CLOVER << "\n";
    	// if no variable incrementation took place, this would be a recursive loop
        i++;
    }
	// clear screen
	system("CLS");
}
// function to display a large shamrock
void shamrock()
{
	char shamrock = '7';
	char boarder = CLOVER;
	char emptySpace = '2';
	std::cout << "  " << CLOVER << " " << CLOVER << " " << CLOVER << " ";
	std::cout << CLOVER << " " << CLOVER << " " << CLOVER << " ";
	std::cout << CLOVER << " ";
	std::cout << "CONGRATULATIONS ";
	std::cout << CLOVER << " " << CLOVER << " " << CLOVER << " ";
	std::cout << CLOVER << " " << CLOVER << " " << CLOVER << " ";
	std::cout << CLOVER << " ";
	std::cout << "\n";
	std::cout << "  " << CLOVER << " " << CLOVER << " " << CLOVER << " ";
	std::cout << CLOVER << " " << CLOVER << " " << CLOVER << " ";
	std::cout << "You guessed the word! ";
	std::cout << CLOVER << " " << CLOVER << " " << CLOVER << " ";
	std::cout << CLOVER << " " << CLOVER;
	std::cout << "\n";
	std::cout << "  " << CLOVER << " " << CLOVER << " ";
	std::cout << "Here is a LUCKY SHAMROCK as a prize ";
	std::cout << CLOVER << " " << CLOVER;
	std::cout << "\n\n";
	
	//line one
	std::cout << "\t ";
	for (int i = 0; i <= 27; i++) {
		std::cout << emptySpace;
	}
	std::cout << std::endl;

	//line two
	std::cout << "\t ";
	for (int i = 0; i <= 1; i++) {
		std::cout << emptySpace;
	}
	for (int i = 0; i <= 23; i++) {
		std::cout << boarder;
	}
	for (int i = 0; i <= 1; i++) {
		std::cout << emptySpace;
	}
	std::cout << std::endl;

	//line three
	std::cout << "\t ";
	for (int i = 0; i <= 1; i++) {
		std::cout << emptySpace;
	}
	for (int i = 0; i <= 15; i++) {
		std::cout << boarder;
	}
	for (int i = 0; i <= 5; i++) {
		std::cout << shamrock;
	}
	for (int i = 0; i <= 2; i++) {
		std::cout << boarder;
	}
	for (int i = 0; i <= 0; i++) {
		std::cout << emptySpace;
	}
	std::cout << std::endl;

	//line four
	std::cout << "\t ";
	for (int i = 0; i <= 1; i++) {
		std::cout << emptySpace;
	}
	for (int i = 0; i <= 1; i++) {
		std::cout << boarder;
	}
	for (int i = 0; i <= 5; i++) {
		std::cout << shamrock;
	}
	for (int i = 0; i <= 5; i++) {
		std::cout << boarder;
	}
	for (int i = 0; i <= 8; i++) {
		std::cout << shamrock;
	}
	for (int i = 0; i <= 0; i++) {
		std::cout << boarder;
	}
	for (int i = 0; i <= 1; i++) {
		std::cout << emptySpace;
	}
	std::cout << std::endl;

	//line five
	std::cout << "\t ";
	for (int i = 0; i <= 1; i++) {
		std::cout << emptySpace;
	}
	for (int i = 0; i <= 0; i++) {
		std::cout << boarder;
	}
	for (int i = 0; i <= 7; i++) {
		std::cout << shamrock;
	}
	for (int i = 0; i <= 3; i++) {
		std::cout << boarder;
	}
	for (int i = 0; i <= 9; i++) {
		std::cout << shamrock;
	}
	for (int i = 0; i <= 0; i++) {
		std::cout << boarder;
	}
	for (int i = 0; i <= 1; i++) {
		std::cout << emptySpace;
	}
	std::cout << std::endl;

	//line six
	std::cout << "\t ";
	for (int i = 0; i <= 1; i++) {
		std::cout << emptySpace;
	}
	for (int i = 0; i <= 1; i++) {
		std::cout << boarder;
	}
	for (int i = 0; i <= 8; i++) {
		std::cout << shamrock;
	}
	for (int i = 0; i <= 1; i++) {
		std::cout << boarder;
	}
	for (int i = 0; i <= 10; i++) {
		std::cout << shamrock;
	}
	for (int i = 0; i <= 0; i++) {
		std::cout << boarder;
	}
	for (int i = 0; i <= 0; i++) {
		std::cout << emptySpace;
	}
	std::cout << std::endl;

	//line seven
	std::cout << "\t ";
	for (int i = 0; i <= 1; i++) {
		std::cout << emptySpace;
	}
	for (int i = 0; i <= 1; i++) {
		std::cout << boarder;
	}
	for (int i = 0; i <= 19; i++) {
		std::cout << shamrock;
	}
	for (int i = 0; i <= 1; i++) {
		std::cout << boarder;
	}
	for (int i = 0; i <= 1; i++) {
		std::cout << emptySpace;
	}
	std::cout << std::endl;

	//line eight
	std::cout << "\t ";
	for (int i = 0; i <= 1; i++) {
		std::cout << emptySpace;
	}
	for (int i = 0; i <= 1; i++) {
		std::cout << boarder;
	}
	for (int i = 0; i <= 18; i++) {
		std::cout << shamrock;
	}
	for (int i = 0; i <= 2; i++) {
		std::cout << boarder;
	}
	for (int i = 0; i <= 1; i++) {
		std::cout << emptySpace;
	}
	std::cout << std::endl;

	//line nine
	std::cout << "\t ";
	for (int i = 0; i <= 1; i++) {
		std::cout << emptySpace;
	}
	for (int i = 0; i <= 2; i++) {
		std::cout << boarder;
	}
	for (int i = 0; i <= 16; i++) {
		std::cout << shamrock;
	}
	for (int i = 0; i <= 3; i++) {
		std::cout << boarder;
	}
	for (int i = 0; i <= 1; i++) {
		std::cout << emptySpace;
	}
	std::cout << std::endl;

	//line ten
	std::cout << "\t ";
	for (int i = 0; i <= 1; i++) {
		std::cout << emptySpace;
	}
	for (int i = 0; i <= 3; i++) {
		std::cout << boarder;
	}
	for (int i = 0; i <= 17; i++) {
		std::cout << shamrock;
	}
	for (int i = 0; i <= 1; i++) {
		std::cout << boarder;
	}
	for (int i = 0; i <= 1; i++) {
		std::cout << emptySpace;
	}
	std::cout << std::endl;

	//line eleven
	std::cout << "\t ";
	for (int i = 0; i <= 1; i++) {
		std::cout << emptySpace;
	}
	for (int i = 0; i <= 2; i++) {
		std::cout << boarder;
	}
	for (int i = 0; i <= 19; i++) {
		std::cout << shamrock;
	}
	for (int i = 0; i <= 1; i++) {
		std::cout << boarder;
	}
	for (int i = 0; i <= 0; i++) {
		std::cout << emptySpace;
	}
	std::cout << std::endl;

	//line twelve
	std::cout << "\t ";
	for (int i = 0; i <= 1; i++) {
		std::cout << emptySpace;
	}
	for (int i = 0; i <= 1; i++) {
		std::cout << boarder;
	}
	for (int i = 0; i <= 19; i++) {
		std::cout << shamrock;
	}
	for (int i = 0; i <= 1; i++) {
		std::cout << boarder;
	}
	for (int i = 0; i <= 1; i++) {
		std::cout << emptySpace;
	}
	std::cout << std::endl;

	// line thirteen
	std::cout << "\t ";
	for (int i = 0; i <= 1; i++) {
		std::cout << emptySpace;
	}
	for (int i = 0; i <= 0; i++) {
		std::cout << boarder;
	}
	for (int i = 0; i <= 7; i++) {
		std::cout << shamrock;
	}
	for (int i = 0; i <= 0; i++) {
		std::cout << boarder;
	}
	for (int i = 0; i <= 1; i++) {
		std::cout << shamrock;
	}
	for (int i = 0; i <= 0; i++) {
		std::cout << boarder;
	}
	for (int i = 0; i <= 7; i++) {
		std::cout << shamrock;
	}
	for (int i = 0; i <= 2; i++) {
		std::cout << boarder;
	}
	for (int i = 0; i <= 1; i++) {
		std::cout << emptySpace;
	}
	std::cout << std::endl;

	//line fourteen
	std::cout << "\t ";
	for (int i = 0; i <= 1; i++) {
		std::cout << emptySpace;
	}
	for (int i = 0; i <= 0; i++) {
		std::cout << boarder;
	}
	for (int i = 0; i <= 7; i++) {
		std::cout << shamrock;
	}
	for (int i = 0; i <= 0; i++) {
		std::cout << boarder;
	}
	for (int i = 0; i <= 1; i++) {
		std::cout << shamrock;
	}
	for (int i = 0; i <= 1; i++) {
		std::cout << boarder;
	}
	for (int i = 0; i <= 4; i++) {
		std::cout << shamrock;
	}
	for (int i = 0; i <= 4; i++) {
		std::cout << boarder;
	}
	for (int i = 0; i <= 1; i++) {
		std::cout << emptySpace;
	}
	std::cout << std::endl;

	//line fifteen
	std::cout << "\t ";
	for (int i = 0; i <= 1; i++) {
		std::cout << emptySpace;
	}
	for (int i = 0; i <= 1; i++) {
		std::cout << boarder;
	}
	for (int i = 0; i <= 5; i++) {
		std::cout << shamrock;
	}
	for (int i = 0; i <= 1; i++) {
		std::cout << boarder;
	}
	for (int i = 0; i <= 1; i++) {
		std::cout << shamrock;
	}
	for (int i = 0; i <= 3; i++) {
		std::cout << boarder;
	}
	for (int i = 0; i <= 1; i++) {
		std::cout << shamrock;
	}
	for (int i = 0; i <= 5; i++) {
		std::cout << boarder;
	}
	for (int i = 0; i <= 1; i++) {
		std::cout << emptySpace;
	}
	std::cout << std::endl;

	//line sixteen
	std::cout << "\t ";
	for (int i = 0; i <= 1; i++) {
		std::cout << emptySpace;
	}
	for (int i = 0; i <= 2; i++) {
		std::cout << boarder;
	}
	for (int i = 0; i <= 2; i++) {
		std::cout << shamrock;
	}
	for (int i = 0; i <= 3; i++) {
		std::cout << boarder;
	}
	for (int i = 0; i <= 1; i++) {
		std::cout << shamrock;
	}
	for (int i = 0; i <= 11; i++) {
		std::cout << boarder;
	}
	for (int i = 0; i <= 1; i++) {
		std::cout << emptySpace;
	}
	std::cout << std::endl;

	//line seventeen
	std::cout << "\t ";
	for (int i = 0; i <= 1; i++) {
		std::cout << emptySpace;
	}
	for (int i = 0; i <= 23; i++) {
		std::cout << boarder;
	}
	for (int i = 0; i <= 1; i++) {
		std::cout << emptySpace;
	}
	std::cout << std::endl;

	//line eighteen
	std::cout << "\t ";
	for (int i = 0; i <= 27; i++) {
		std::cout << emptySpace;
	}
	std::cout << std::endl;
	std::cout << std::endl;
}

