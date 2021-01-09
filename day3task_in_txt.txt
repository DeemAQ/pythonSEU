balance = 5000  # Current balance


def ATM():
    currentBalance = balance  # Local reference
    cash = 0
    while True:
        print("""Welcome to My Bank
        Please enter one of the following choices:
        [C]eck balance
        [W]ithdraw
        [D]eposit
        [T]ransfer
        [E]xit """)
        choice = input("> ")
        if choice.upper() == "C":  # Check balance
            check(currentBalance)
        elif choice.upper() == "W":  # Withdraw
            while True:
                cash = int(input("Enter amount to withdraw> "))
                if cash > 0:
                    currentBalance = withdraw(cash, currentBalance)
                    break
                else:
                    print("Enter an integer value")
        elif choice.upper() == "D":  # Deposit
            while True:
                cash = int(input("Enter amount to deposit> "))
                if cash > 0:
                    currentBalance = deposit(cash, currentBalance)
                    break
                else:
                    print("Enter an integer value")
            newBalance = deposit(cash, currentBalance)
        elif choice.upper() == "T":  # Transfer
            while True:
                cash = int(input("Enter amount to transfer> "))
                if cash > 0:
                    currentBalance = transfer(cash, currentBalance)
                    break
                else:
                    print("Enter an integer value")
            newBalance = transfer(cash, currentBalance)
        elif choice.upper() == "E":  # Exit the loop
            print("Exiting....")
            print("Thank you for using My Bank ATM")
            break
        else:
            print('Incorrect input')
    return 0


def withdraw(cash, currentBalance):  # Taking money from ATM
    # Update balance after subtraction
    # cash, is amount to withdraw
    if cash <= currentBalance:
        currentBalance = currentBalance - cash
        print(f"Dispensing the amount {cash}")
        print(f"Remaining balance is: {currentBalance}")
    else:
        print("No sufficient funds!")
        print("Try another option or [E]xit")
    return currentBalance


def deposit(cash, currentBalance):  # Put money into your account
    # Update balance after addition
    # TODO
    currentBalance += cash
    return currentBalance


def transfer(cash, currentBalance):  # Sending money to another person
    # The amount, a
    # Account number, acc
    # Update balance after subtraction
    # TODO
    if cash >= currentBalance:
        print("insufficient funds")
    else:
        currentBalance -= cash
    return currentBalance


def check(currentBalance):
    # Present balance
    # TODO
    print("current balance = %d SR" % currentBalance)
    return 0


ATM()
