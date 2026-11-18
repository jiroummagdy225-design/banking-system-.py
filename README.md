# banking-system-.py
account = None

def create_account():
    global account

    if account is not None:
        print("An account already exists")
        return

    name = input("Enter your name: ")
    account_number = input("Enter account number: ")
    initial_balance = float(input("Enter initial deposit: "))

    if initial_balance < 0:
        print("Invalid initial deposit")
        return

    account = {
        "name": name,
        "account_number": account_number,
        "balance": initial_balance
    }

    print("Account created successfully")


def deposit_money():
    if account is None:
        print("Please create an account first")
        return

    amount = float(input("Enter amount to deposit: "))

    if amount > 0:
        account["balance"] += amount
        print("Deposit successful")
    else:
        print("Invalid amount")


def withdraw_money():
    if account is None:
        print("Please create an account first")
        return

    amount = float(input("Enter amount to withdraw: "))

    if amount <= 0:
        print("Invalid amount")
    elif amount > account["balance"]:
        print("Insufficient balance")
    else:
        account["balance"] -= amount
        print("Withdrawal successful")


def check_balance():
    if account is None:
        print("Please create an account first")
    else:
        print("Your balance is:", account["balance"])


def display_account():
    if account is None:
        print("Please create an account first")
    else:
        print(" Account Information ")
        print("Name:", account["name"])
        print("Account Number:", account["account_number"])
        print("Balance:", account["balance"])


# Main Program

while True:
    print(" BANKING SYSTEM ")
    print(" Create a bank account")
    print(" Deposit money")
    print(" Withdraw money")
    print(" Check balance")
    print(" Display account information")
    print(" Exit")

    choice = input("Enter your choice (1-6): ")

    if choice == "1":
        create_account()

    elif choice == "2":
        deposit_money()

    elif choice == "3":
        withdraw_money()

    elif choice == "4":
        check_balance()

    elif choice == "5":
        display_account()

    elif choice == "6":
        print("Thank you for using our Banking System!")
        break

    else:
        print("Invalid choice! Please try again.")
