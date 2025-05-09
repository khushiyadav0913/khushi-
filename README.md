class BankAccount:
    def __init__(self, account_number, account_holder, balance=0.0):
        self.account_number = account_number
        self.account_holder = account_holder
        self.balance = balance

    def deposit(self, amount):
        if amount > 0:
            self.balance += amount
            print(f"Deposited {amount}. New balance: {self.balance}")
        else:
            print("Deposit amount must be positive.")

    def withdraw(self, amount):
        if amount > 0 and amount <= self.balance:
            self.balance -= amount
            print(f"Withdrew {amount}. New balance: {self.balance}")
        else:
            print("Insufficient funds or invalid amount.")

    def display(self):
        print(f"Account Number: {self.account_number}")
        print(f"Account Holder: {self.account_holder}")
        print(f"Balance: {self.balance}")

def main():
    accounts = {}

    while True:
        print("\n--- Banking System Menu ---")
        print("1. Create Account")
        print("2. Deposit")
        print("3. Withdraw")
        print("4. Check Balance")
        print("5. Exit")

        choice = input("Enter your choice: ")

        if choice == '1':
            acc_num = input("Enter account number: ")
            name = input("Enter account holder name: ")
            accounts[acc_num] = BankAccount(acc_num, name)
            print("Account created successfully.")

        elif choice == '2':
            acc_num = input("Enter account number: ")
            if acc_num in accounts:
                amount = float(input("Enter amount to deposit: "))
                accounts[acc_num].deposit(amount)
            else:
                print("Account not found.")

        elif choice == '3':
            acc_num = input("Enter account number: ")
            if acc_num in accounts:
                amount = float(input("Enter amount to withdraw: "))
                accounts[acc_num].withdraw(amount)
            else:
                print("Account not found.")

        elif choice == '4':
            acc_num = input("Enter account number: ")
            if acc_num in accounts:
                accounts[acc_num].display()
            else:
                print("Account not found.")

        elif choice == '5':
            print("Thank you for using the banking system!")
            break

        else:
            print("Invalid choice. Please try again.")

if __name__ == "__main__":
    main()
