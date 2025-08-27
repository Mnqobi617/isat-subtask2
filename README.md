#include <iostream>
#include <string>
#include <cstdlib>  // for rand() and srand()
#include <ctime>    // for time()

using namespace std;

// Function to convert decimal to binary
string decimalToBinary(int num) {
    if (num == 0) return "0";
    string binary = "";
    while (num > 0) {
        binary = (num % 2 == 0 ? "0" : "1") + binary;
        num /= 2;
    }
    return binary;
}

// Function to convert binary to decimal
int binaryToDecimal(const string& binStr) {
    int decimal = 0;
    for (char bit : binStr) {
        if (bit != '0' && bit != '1') return -1; // invalid input
        decimal = decimal * 2 + (bit - '0');
    }
    return decimal;
}

// Function to convert decimal to hexadecimal
string decimalToHexadecimal(int num) {
    if (num == 0) return "0";
    string hexDigits = "0123456789ABCDEF";
    string hex = "";
    while (num > 0) {
        hex = hexDigits[num % 16] + hex;
        num /= 16;
    }
    return hex;
}

// Function to convert hexadecimal to decimal
int hexadecimalToDecimal(const string& hexStr) {
    int decimal = 0;
    for (char c : hexStr) {
        decimal *= 16;
        if (c >= '0' && c <= '9') decimal += c - '0';
        else if (c >= 'A' && c <= 'F') decimal += c - 'A' + 10;
        else if (c >= 'a' && c <= 'f') decimal += c - 'a' + 10;
        else return -1; // invalid input
    }
    return decimal;
}

// Demo function: generate random number and convert to binary
void demo() {
    int num = rand() % 100; // random number between 0 and 99
    cout << "Random number: " << num << endl;
    cout << "Binary representation: " << decimalToBinary(num) << endl;
}

int main() {
    srand(time(0)); // seed random number generator

    while (true) {
        cout << "\nConversion Menu:\n";
        cout << "1. Convert Decimal to Binary\n";
        cout << "2. Convert Binary to Decimal\n";
        cout << "3. Convert Decimal to Hexadecimal\n";
        cout << "4. Convert Hexadecimal to Decimal\n";
        cout << "5. Demo (generate random number and convert to binary)\n";
        cout << "6. Exit\n";

        cout << "Enter your choice (1-6): ";
        int choice;
        cin >> choice;

        if (choice == 1) {
            cout << "Enter a decimal number: ";
            int dec;
            cin >> dec;
            if (dec < 0) cout << "Invalid decimal number (must be non-negative)." << endl;
            else cout << "Binary representation: " << decimalToBinary(dec) << endl;
        }
        else if (choice == 2) {
            cout << "Enter a binary number: ";
            string bin;
            cin >> bin;
            int dec = binaryToDecimal(bin);
            if (dec == -1) cout << "Invalid binary number." << endl;
            else cout << "Decimal equivalent: " << dec << endl;
        }
        else if (choice == 3) {
            cout << "Enter a decimal number: ";
            int dec;
            cin >> dec;
            if (dec < 0) cout << "Invalid decimal number (must be non-negative)." << endl;
            else cout << "Hexadecimal representation: " << decimalToHexadecimal(dec) << endl;
        }
        else if (choice == 4) {
            cout << "Enter a hexadecimal number: ";
            string hex;
            cin >> hex;
            int dec = hexadecimalToDecimal(hex);
            if (dec == -1) cout << "Invalid hexadecimal number." << endl;
            else cout << "Decimal equivalent: " << dec << endl;
        }
        else if (choice == 5) {
            demo();
        }
        else if (choice == 6) {
            cout << "Exiting the program." << endl;
            break;
        }
        else {
            cout << "Invalid choice, please select between 1 and 6." << endl;
        }
    }

    return 0;
}



