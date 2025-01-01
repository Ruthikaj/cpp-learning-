#include <iostream>
#include <string>
#include <algorithm>
using namespace std;

// Function to convert the input string into a special string
string convertToSpecialString(string input) {
    int start = 0; // Start index of a word

    for (int i = 0; i <= input.length(); ++i) {
        // Check if we reached the end of a word (non-alphanumeric or end of string)
        if (i == input.length() || !isalnum(input[i])) {
            if (start < i) { // If there is a valid word
                reverse(input.begin() + start, input.begin() + i); // Reverse the word in-place
            }
            start = i + 1; // Update start to point to the next word
        }
    }

    return input; // Return the modified string
}

int main() {
    string input;
    cout << "Enter a string: ";
    getline(cin, input);

    // Convert the string and print the result
    cout << "Special string: " << convertToSpecialString(input) << endl;

    return 0;
}



---------------------------------------------------------------------------------------------------------------------------------------------------
// Start the loop: input = "How are you?", length = 12

// Iteration 1: i = 0, input[0] = 'H' (is alphanumeric)
// Accumulating the word: start = 0

// Iteration 2: i = 1, input[1] = 'o' (is alphanumeric)
// Continue accumulating the word.

// Iteration 3: i = 2, input[2] = 'w' (is alphanumeric)
// Continue accumulating the word.

// Iteration 4: i = 3, input[3] = ' ' (not alphanumeric)
// Reverse "How" in-place: reverse(input.begin() + 0, input.begin() + 3)
// Result after reversing: "Woh are you?"
// Update start = 4 (next word starts after the space).

// Iteration 5: i = 4, input[4] = 'a' (is alphanumeric)
// Accumulating the word: start = 4

// Iteration 6: i = 5, input[5] = 'r' (is alphanumeric)
// Continue accumulating the word.

// Iteration 7: i = 6, input[6] = 'e' (is alphanumeric)
// Continue accumulating the word.

// Iteration 8: i = 7, input[7] = ' ' (not alphanumeric)
// Reverse "are" in-place: reverse(input.begin() + 4, input.begin() + 7)
// Result after reversing: "Woh era you?"
// Update start = 8 (next word starts after the space).

// Iteration 9: i = 8, input[8] = 'y' (is alphanumeric)
// Accumulating the word: start = 8

// Iteration 10: i = 9, input[9] = 'o' (is alphanumeric)
// Continue accumulating the word.

// Iteration 11: i = 10, input[10] = 'u' (is alphanumeric)
// Continue accumulating the word.

// Iteration 12: i = 11, input[11] = '?' (not alphanumeric)
// Reverse "you" in-place: reverse(input.begin() + 8, input.begin() + 11)
// Result after reversing: "Woh era uoy?"
// Update start = 12 (no more words left).

// Final Output: "Woh era uoy?"

