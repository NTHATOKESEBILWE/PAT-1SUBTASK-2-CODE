# PAT-1SUBTASK-2-CODE
A PROGRAM THAT WILL HELP ALOT OF PEOPLE AND MAKE LIFE EASY WHEN COOKING
#include <iostream>
#include <limits> // for numeric_limits
using namespace std;

// Function to safely get integer input
int getValidInput(string message) {
    int value;

    while (true) {
        cout << message;
        cin >> value;

        if (cin.fail()) {
            cout << "Invalid input! Please enter a valid integer.\n";
            cin.clear(); // clear error flag
            cin.ignore(numeric_limits<streamsize>::max(), '\n'); // discard bad input
        } else {
            return value;
        }
    }
}

// Function to check temperatures
void checkTemperatures() {
    int t1, t2, t3;

    t1 = getValidInput("\nEnter first temperature: ");
    t2 = getValidInput("Enter second temperature: ");

    // Rule 2
    if ((t2 - t1) > 50) {
        cout << "Reduce fryer heat before taking the third reading.\n";
        return;
    }

    // Rule 3
    if ((t2 - t1) < 10) {
        cout << "Increase the fryer heat before taking the third reading.\n";
    }

    t3 = getValidInput("Enter third temperature: ");

    // Rule 4
    if (t3 >= 150 && t3 <= 190) {
        cout << "You may start frying the Magwinyas.\n";
    } else {
        cout << "Oil is not ready for frying!\n";
    }
}

int main() {
    int choice;

    do {
        cout << "\n==== MAGWINYA MAGIC SYSTEM ====\n";
        cout << "1. Enter temperature readings\n";
        cout << "2. Exit\n";

        choice = getValidInput("Choose an option: ");

        switch (choice) {
            case 1:
                checkTemperatures();
                break;
            case 2:
                cout << "Exiting program... Goodbye!\n";
                break;
            default:
                cout << "Invalid option. Try again.\n";
        }

    } while (choice != 2);

    return 0;
}
