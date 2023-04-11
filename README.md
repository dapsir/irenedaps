# irenedaps
Momo Project
// Define global variables int defaultPin = 0000; int defaultBalance = 1000; int maxAttempts = 3; int attempts = 0;

// Define functions void checkBalance(int balance) { cout << "Your balance is: " << balance << endl; }

int authenticate(int pin) { if (pin == defaultPin) { return defaultBalance; } else { attempts++; if (attempts >= maxAttempts) { cout << "Maximum attempts reached. Exiting program." << endl; exit(0); } else { cout << "Incorrect PIN. Please try again." << endl; return -1; } } }

void changePin(int &pin) { int newPin; cout << "Enter new PIN: "; cin >> newPin; pin = newPin; cout << "PIN changed successfully." << endl; }

void sendMoney(int &balance) { int recipientNumber, amount; cout << "Enter recipient's phone number: "; cin >> recipientNumber; cout << "Enter amount to send: "; cin >> amount; if (balance >= amount) { balance -= amount; cout << "Transaction successful. " << amount << " sent to " << recipientNumber << endl; } else { cout << "Insufficient funds. Transaction cancelled." << endl; } }

// Main function int main() { int pin = -1, balance = -1, choice;

while (true) {
    // Display menu options
    cout << "Welcome to Mobile Money Services!" << endl;
    cout << "1. Check Balance" << endl;
    cout << "2. Send Money" << endl;
    cout << "3. Change PIN" << endl;
    cout << "4. Exit" << endl;
    cout << "Enter choice: ";
    cin >> choice;

    switch (choice) {
        case 1:
            if (balance == -1) {
                balance = authenticate(pin);
            }
            checkBalance(balance);
            break;
        case 2:
            if (balance == -1) {
                balance = authenticate(pin);
            }
            sendMoney(balance);
            break;
        case 3:
            if (balance == -1) {
                balance = authenticate(pin);
            }
            changePin(pin);
            break;
        case 4:
            cout << "Exiting program. Goodbye!" << endl;
            return 0;
        default:
            cout << "Invalid choice. Please try again." << endl;
            break;
    }
}
return 0;
}
