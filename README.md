# Introduction

**In this repository we will build a Basic programs using Object oriented programming in Python which will mainly focus on implementing 
Object oriented programming concepts.**

<br>

# Concepts
- Magic method
- Constructor
- Self object

# Programs
We will be building following programs
- [Atm Banking System](#atm-banking-system)
    - Our Atm Banking System will have the following features
        - [Select Bank](#select-bank)
            - User will be able to select bank
        - [Select option from Menu](#select-from-menu)
            - User will be able to select operations from the menu
        - [Create Pin](#create-pin)
            - User has to create pin in order to operate
        - [Check Pin](#check-pin)
            - Entered pin will be checked after creating pin 
        - [Deposit Money](#deposit-money)
            - User will be able to deposit money
        - [Withdraw Money](#withdraw-money)
            - User will be able withdraw money
        - [Check Balance](#check-balance)
            - User will be able to check balance

- [Custom Datatype]()
    - Custom datatype which will include the following features
        - [Addition]()
        - [Substraction]()
        - [Multiplication]()
        - [Division]()
 


All the features mentioned above will be implemented using OOP as said before.

# Usage of OOP
- User will be able to transit between multiple banks at the same time which will have **different** pin codes, balanace  etc.

# Atm Banking System
The features are mentioned below

### Select Bank
User will have to select a bank from the given options and then the menu method will be called by the object

```
def main():
    asiaBank = Atm()
    primeBank = Atm()

    while 1:
        choice = int(input("""Please Select your bank
        0. Exit
        
        1. Asia Bank: 
        2. Prime Bank
        """))

        if choice == 1:
            print(f"Thanks for choosing Asia Bank")
            while 1:
                stay = asiaBank.menu()
                if not stay:
                    break
        elif choice == 2:
            print(f"Thanks for choosing Prime Bank")
            while 1:
                stay = primeBank.menu()
                if not stay:
                    break
        elif choice == 0:
            break
        else:
            print("Please enter a valid choice")


main()
```
[Back to top](#programs)

### Select from Menu
User will have to select an operation from the menu

```
def menu(self):
        user_input = int(input("""
                        0. Enter 0 to exit
                        1. Enter 1 to create pin
                        2. Enter 2 to deposit
                        3. Enter 3 to withdraw
                        4. Enter 4 to check balance
        """))

        if user_input == 1:
            self.create_pin()
        elif user_input == 2:
            self.deposit()
        elif user_input == 3:
            self.withdraw()
        elif user_input == 4:
            self.check_balance()
        elif user_input < 0 or user_input > 4:
            print("Please Enter a valid input")

        return user_input
```
[Back to top](#programs)

### Create Pin
We will be creating pins for every object and pin is required to perform all other operations.Without a pin no one can perform any other operation. And if pin is created then every time someone is going to perform any operation pin will be checked.

```
def __init__(self):
        self.pin = ""
        self.balance = 0

def create_pin(self):
        if self.pin == "":
            self.pin = input("Create you pin please: ")
            print("Your pin has been set successfully")
        else:
            print("There is already a pin")
```
[Back to top](#programs)
### Check Pin
If there is a pin already existing in the program then we will check the pin everytime before performing any operation.
```
    def check_pin(self):
        pin = input("Enter your pin please: ")
        if pin == self.pin:
            return 1
        else:
            return 0
```
[Back to top](#programs)


### Deposit Money
In order to deposit money user has to have a pin. If he doesn't have a pin he has to create one and if he has then we will check the pin he has entered. After entering the right pin his entered amount will be added to balance.

```
    def deposit(self):
        if self.pin == "":
            self.create_pin()

        if self.check_pin():
            amount = input("Please enter your deposit amount: ")
            self.balance += int(amount)
            print("Amount has been deposited successfully")
        else:
            print("You have entered wrong pin")
            self.deposit()
```
[Back to top](#programs)


### Withdraw Money
Just like deposit withdraw method can be performed after entering the righ pin. In this case user has to enter a valid amount also. If the entered amount is withdrawable then he can withdraw money otherwise he will be asked to repeat the operation.

```
def withdraw(self):
        if self.pin == "":
            self.create_pin()
        if self.check_pin():
            amount = int(input("Please enter your withdrawal amount or press 0 to return to menu: "))
            if amount == 0:
                pass
            elif amount < 0:
                print("Invalid amount")
            elif self.balance >= amount:
                self.balance -= amount
                print("Amount has been withdrawn successfully")
            else:
                print("Insufficient balance")
                self.withdraw()
        else:
            print("You have entered wrong pin")
            self.withdraw()
```
[Back to top](#programs)


### Check Balance
User will be shown balance when he enters the correct pin just like all the above mentioned methods.
```
    def check_balance(self):
        if self.pin == "":
            self.create_pin()
        if self.check_pin():
            print(f"Your current balance is : {self.balance}")
        else:
            print("You have entered wrong pin")
            self.check_balance()
```
[Back to top](#programs)

