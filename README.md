import time

print("Please insert Your CARD")

# For card processing
time.sleep(5)

password = 1234

# Taking ATM pin from user
pin = int(input("Enter your ATM pin: "))

# User account balance
balance = 5000

# Checking pin is valid or not
if pin == password:
    # Loop will run until user opts to exit
    while True:
        # Showing options to user
        print(''' 
            1 == Balance
            2 == Withdraw Balance
            3 == Deposit Balance
            4 == Exit
        ''')

        try:
            # Taking an option from user
            option = int(input("Please enter your choice: "))
        except ValueError:
            print("Invalid input! Please enter a valid option.")
            continue  # Skip to next iteration if input is invalid

        # Option 1: Display balance
        if option == 1:
            print(f"Your current balance is {balance}")

        # Option 2: Withdraw balance
        elif option == 2:
            try:
                withdraw_amount = int(input("Please enter withdrawal amount: "))
                if withdraw_amount < 0:
                    print("Withdrawal amount cannot be negative.")
                elif withdraw_amount > balance:
                    print("Insufficient balance for withdrawal.")
                else:
                    balance -= withdraw_amount
                    print(f"{withdraw_amount} is debited from your account.")
                    print(f"Your updated balance is {balance}")
            except ValueError:
                print("Please enter a valid withdrawal amount.")

        # Option 3: Deposit balance
        elif option == 3:
            try:
                deposit_amount = int(input("Please enter deposit amount: "))
                if deposit_amount < 0:
                    print("Deposit amount cannot be negative.")
                else:
                    balance += deposit_amount
                    print(f"{deposit_amount} is credited to your account.")
                    print(f"Your updated balance is {balance}")
            except ValueError:
                print("Please enter a valid deposit amount.")

        # Option 4: Exit
        elif option == 4:
            print("Thank you for using the ATM. Goodbye!")
            break

        # Invalid option input
        else:
            print("Invalid option! Please select a valid option.")

else:
    print("Wrong PIN! Please try again.")
