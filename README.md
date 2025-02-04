# Banking System - Developed by Archit Singh

This is a simple Banking System implemented in Python that allows users to:

- Debit money from their account.
- Credit money to their account.
- Check their account balance.

## Features:

- **Debit Money:** Allows the user to debit a specific amount from their balance.
- **Credit Money:** Allows the user to credit a specific amount to their balance.
- **Check Balance:** Displays the current balance in the account.
- **Input Validation:** Ensures that only valid, positive amounts can be debited or credited, and the balance cannot go negative.

## Code Overview:

```python
# Author: Archit Singh
# This code is copyrighted and should not be copied without permission.

class Account:
    def __init__(self, balance, acc):
        self.balance = balance
        self.acc = acc

    def debit(self, amount):
        if amount > self.balance:
            print("\nInsufficient Balance! Transaction Failed.")
        elif amount <= 0:
            print("\nInvalid amount. Please enter a positive value.")
        else:
            self.balance -= amount
            print(f"\nAmount of ₹{amount} debited from your account.")
        self.display_balance()

    def credit(self, amount):
        if amount <= 0:
            print("\nInvalid amount. Please enter a positive value.")
        else:
            self.balance += amount
            print(f"\nAmount of ₹{amount} credited to your account.")
        self.display_balance()

    def display_balance(self):
        print(f"\nCurrent Balance: ₹{self.balance}")

def main():
    print("\nWelcome to the Banking System - Developed by Archit Singh")
    
    acc_number = input("\nEnter Account Number: ")
    while True:
        try:
            initial_balance = float(input("Enter Initial Balance: ₹"))
            if initial_balance < 0:
                print("Initial balance cannot be negative. Try again.")
                continue
            break
        except ValueError:
            print("Invalid input! Please enter a numeric value.")

    user_account = Account(initial_balance, acc_number)

    while True:
        print("\nChoose an option:")
        print("1. Debit Money")
        print("2. Credit Money")
        print("3. Check Balance")
        print("4. Exit")

        choice = input("Enter your choice: ")

        if choice == "1":
            try:
                amount = float(input("\nEnter amount to debit: ₹"))
                user_account.debit(amount)
            except ValueError:
                print("\nInvalid input! Please enter a numeric value.")

        elif choice == "2":
            try:
                amount = float(input("\nEnter amount to credit: ₹"))
                user_account.credit(amount)
            except ValueError:
                print("\nInvalid input! Please enter a numeric value.")

        elif choice == "3":
            user_account.display_balance()

        elif choice == "4":
            print("\nThank you for using the Banking System. Developed by Archit Singh.")
            break

        else:
            print("\nInvalid choice! Please select a valid option.")

if __name__ == "__main__":
    main()
