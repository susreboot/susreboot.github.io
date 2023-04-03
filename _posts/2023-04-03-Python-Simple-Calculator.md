---
    title: Python Calculator
    date: 03-04-2023
    categories: [programming]
    tags: [python]
---
<!-- Post Image -->
<style>
    .center {
  display: block;
  margin-left: auto;
  margin-right: auto;
  width: 50%;
}
    </style>
<img src="https://i.imgur.com/lHUuf1t.png" alt= “python” width="400rem" height="value" class="center">
<br/><br/>
<!-- End Post Image -->

This is a simple calculator Python project from “100 Days of Code: The Complete Python Pro Bootcamp” I am going through. It took some figuring out but the final project took shape!

Here is the Github repository if your curious to check it out: https://github.com/susreboot/Simple-Python-Calculator

Here is the Repl URL: https://replit.com/@systemreboot/100DOC-Calculator-App

Also here is the code for it if you’d rather not go to Github or Replit.

## main.py
```python
from art import logo, exit, calculator_logo, warning, improper, exit_error
import time
from os import system, name
import sys
 
# Function for exiting program
def clear():
   # for windows
    if name == 'nt':
        _ = system('cls')
 
   # for mac and linux
    else:
        _ = system('clear')
 
# Assign text colors to variables
class bcolors:
    HEADER = '\033[95m'
    OKBLUE = '\033[94m'
    OKCYAN = '\033[96m'
    OKGREEN = '\033[92m'
    WARNING = '\033[93m'
    FAIL = '\033[91m'
    ENDC = '\033[0m'
    BOLD = '\033[1m'
    UNDERLINE = '\033[4m'
    RED = '\033[31m'
# Print the application logo in green 
print(bcolors.OKGREEN + logo + bcolors.ENDC)
time.sleep(2)
clear()
 
# Mathmatical formulas functions, according to operators
def addition(n1, n2):
    return n1 + n2
 
def subtraction(n1, n2):
    return n1 - n2
 
def division(n1, n2):
    if n2 == 0:
        return "Warning!! You cannot Divide by zero!"
    else:
        return n1 / n2
 
def multiplication(n1, n2):
    return n1 * n2
 
# Set dictionary for mathmatical operators 
operations = {
    "+": addition,
    "-": subtraction,
    "/": division,
    "*": multiplication
}  
 
# Calculator function
def calculator(): 
    print(bcolors.OKGREEN + calculator_logo + bcolors.ENDC)
    print("")
    num1 = float(input("What is the first number? \n > "))
    should_continue = True
    while should_continue:
        operation = input("Choose an operator: \n (+) --Addition \n (-) --Subtraction \n (/) --Division \n (*) --Multiplication \n > ")
        num2 = float(input("What is next number? \n > "))
        calculation_function = operations[operation]
        answer = calculation_function(num1, num2)
        if answer == "Warning!! You cannot Divide by zero!":
            clear()
            print(bcolors.RED + warning + bcolors.ENDC)
            time.sleep(2.5)
            clear()
            calculator()
        clear()
        print(bcolors.OKGREEN + f"The Current Calculation is: {num1} {operation} {num2} = {answer}" + bcolors.ENDC)
        print("")
        # Asks the user what they want to do after the first calculation
        decide_step = input(f"Type 'y' or 'yes' to continue calculating with current value: {bcolors.OKGREEN}{answer}{bcolors.ENDC}, \nType 'n' or 'no' to start a new calculation, \nType 'x' or 'exit' to exit the program: " '\n > ').lower() 
        print("")
        if decide_step == "y" or decide_step == "yes":
            num1 = answer
        elif decide_step == "n" or decide_step == "no":
            should_continue = False
            clear()
            calculator()
        elif decide_step == "x" or decide_step == "exit":
            clear()
            print(exit)
            time.sleep(2)
            clear()
            should_continue = False
            break
        # If anything else is entered other than the input above, the program will display a message and exit
        else: 
            clear()
            print(bcolors.RED + improper + bcolors.ENDC)
            print(bcolors.RED + exit_error + bcolors.ENDC)
            time.sleep(3)
            clear()
            sys.exit()  
            should_continue = False
            break


calculator()

```


## art.py
```python
logo = """
 .d8888b.         d8888 888       .d8888b.  888     888 888             d8888 88888888888  .d88888b.  8888888b.               d8888 8888888b.  8888888b.  
d88P  Y88b       d88888 888      d88P  Y88b 888     888 888            d88888     888     d88P" "Y88b 888   Y88b             d88888 888   Y88b 888   Y88b 
888    888      d88P888 888      888    888 888     888 888           d88P888     888     888     888 888    888            d88P888 888    888 888    888 
888            d88P 888 888      888        888     888 888          d88P 888     888     888     888 888   d88P           d88P 888 888   d88P 888   d88P 
888           d88P  888 888      888        888     888 888         d88P  888     888     888     888 8888888P"           d88P  888 8888888P"  8888888P"  
888    888   d88P   888 888      888    888 888     888 888        d88P   888     888     888     888 888 T88b           d88P   888 888        888        
Y88b  d88P  d8888888888 888      Y88b  d88P Y88b. .d88P 888       d8888888888     888     Y88b. .d88P 888  T88b         d8888888888 888        888        
 "Y8888P"  d88P     888 88888888  "Y8888P"   "Y88888P"  88888888 d88P     888     888      "Y88888P"  888   T88b       d88P     888 888        888 
"""

exit = """ 
            ████████ ██   ██  █████  ███    ██ ██   ██ ███████     ███████  ██████  ██████      ██    ██ ███████ ██ ███    ██  ██████  
               ██    ██   ██ ██   ██ ████   ██ ██  ██  ██          ██      ██    ██ ██   ██     ██    ██ ██      ██ ████   ██ ██       
               ██    ███████ ███████ ██ ██  ██ █████   ███████     █████   ██    ██ ██████      ██    ██ ███████ ██ ██ ██  ██ ██   ███ 
               ██    ██   ██ ██   ██ ██  ██ ██ ██  ██       ██     ██      ██    ██ ██   ██     ██    ██      ██ ██ ██  ██ ██ ██    ██ 
               ██    ██   ██ ██   ██ ██   ████ ██   ██ ███████     ██       ██████  ██   ██      ██████  ███████ ██ ██   ████  ██████  

   #       #       ##########   #          #    #     ######           #     #       # # #     #         #       ######      #         #        # #     
#      ########       ###    #        ##########               ########## #       # # #     #    ##########              ########   #         #   #  
##    #       #      #     ##########   #    #   ##########        #    #        #         #          #     ##########  #    #    ########## # # #   
# #  #      ##      #        #     #         #        #            #    #       #         #           #          #     #    #       #     #     #    
#  #      ##       #         #              #         #           #     #     ##        ##           #           #         #        #          # #   
#       ##        #          #             #         #           #   # #    ##        ##            #           #         #         #         #   #  
#     ##         #            ######     #         ##           #     #   ##        ##            ##          ##         #           ######        # 
                                   
"""

calculator_logo = """
 _____________________
|  _________________  |
| | READT SET GO 0. | |
| |_________________| |
|  ___ ___ ___   ___  |
| | 7 | 8 | 9 | | + | |
| |___|___|___| |___| |
| | 4 | 5 | 6 | | - | |
| |___|___|___| |___| |
| | 1 | 2 | 3 | | x | |
| |___|___|___| |___| |
| | . | 0 | = | | / | |
| |___|___|___| |___| |
|_____________________|
"""

warning = """
        _____                _____       _____ _____   ______   ____ _____   ______        _____          
       |\    \   _____   ___|\    \  ___|\    |\    \ |\     \ |    |\    \ |\     \   ___|\    \         
       | |    | /    /| /    /\    \|    |\    \\    \| \     \|    |\\    \| \     \ /    /\    \        
       \/     / |    |||    |  |    |    | |    \|    \  \     |    | \|    \  \     |    |  |____|       
       /     /_  \   \/|    |__|    |    |/____/ |     \  |    |    |  |     \  |    |    |    ____       
      |     // \  \   \|    .--.    |    |\    \ |      \ |    |    |  |      \ |    |    |   |    |      
      |    |/   \ |    |    |  |    |    | |    ||    |\ \|    |    |  |    |\ \|    |    |   |_,  |      
      |\ ___/\   \|   /|____|  |____|____| |____||____||\_____/|____|  |____||\_____/|\ ___\___/  /|      
      | |   | \______/ |    |  |    |    | |    ||    |/ \|   ||    |  |    |/ \|   || |   /____ / |      
       \|___|/\ |    | |____|  |____|____| |____||____|   |___||____|  |____|   |___|/\|___|    | /       
          \(   \|____|/  \(      )/   \(     )/    \(       )/   \(      \(       )/    \( |____|/        
           '      )/      '      '     '     '      '       '     '       '       '      '   )/      
            
       _____                        _     _____  _       _     _        _             ______              
      / ____|                      | |   |  __ \(_)     (_)   | |      | |           |___  /              
     | |     __ _ _ __  _ __   ___ | |_  | |  | |___   ___  __| | ___  | |__  _   _     / / ___ _ __ ___  
     | |    / _` | '_ \| '_ \ / _ \| __| | |  | | \ \ / | |/ _` |/ _ \ | '_ \| | | |   / / / _ | '__/ _ \ 
     | |___| (_| | | | | | | | (_) | |_  | |__| | |\ V /| | (_| |  __/ | |_) | |_| |  / /_|  __| | | (_) |
      \_____\__,_|_| |_|_| |_|\___/ \__| |_____/|_| \_/ |_|\__,_|\___| |_.__/ \__, | /_____\___|_|  \___/ 
                                                                               __/ |                      
                                                                              |___/     
                                                                        
"""

improper = """
 ██▓███▄ ▄███▓██▓███  ██▀███  ▒█████  ██▓███ ▓█████ ██▀███      ▄████▄  ▒█████  ███▄ ▄███▓███▄ ▄███▓▄▄▄      ███▄    █▓█████▄ 
▓██▓██▒▀█▀ ██▓██░  ██▓██ ▒ ██▒██▒  ██▓██░  ██▓█   ▀▓██ ▒ ██▒   ▒██▀ ▀█ ▒██▒  ██▓██▒▀█▀ ██▓██▒▀█▀ ██▒████▄    ██ ▀█   █▒██▀ ██▌
▒██▓██    ▓██▓██░ ██▓▓██ ░▄█ ▒██░  ██▓██░ ██▓▒███  ▓██ ░▄█ ▒   ▒▓█    ▄▒██░  ██▓██    ▓██▓██    ▓██▒██  ▀█▄ ▓██  ▀█ ██░██   █▌
░██▒██    ▒██▒██▄█▓▒ ▒██▀▀█▄ ▒██   ██▒██▄█▓▒ ▒▓█  ▄▒██▀▀█▄     ▒▓▓▄ ▄██▒██   ██▒██    ▒██▒██    ▒██░██▄▄▄▄██▓██▒  ▐▌██░▓█▄   ▌
░██▒██▒   ░██▒██▒ ░  ░██▓ ▒██░ ████▓▒▒██▒ ░  ░▒████░██▓ ▒██▒   ▒ ▓███▀ ░ ████▓▒▒██▒   ░██▒██▒   ░██▒▓█   ▓██▒██░   ▓██░▒████▓ 
░▓ ░ ▒░   ░  ▒▓▒░ ░  ░ ▒▓ ░▒▓░ ▒░▒░▒░▒▓▒░ ░  ░░ ▒░ ░ ▒▓ ░▒▓░   ░ ░▒ ▒  ░ ▒░▒░▒░░ ▒░   ░  ░ ▒░   ░  ░▒▒   ▓▒█░ ▒░   ▒ ▒ ▒▒▓  ▒ 
 ▒ ░  ░      ░▒ ░      ░▒ ░ ▒░ ░ ▒ ▒░░▒ ░     ░ ░  ░ ░▒ ░ ▒░     ░  ▒    ░ ▒ ▒░░  ░      ░  ░      ░ ▒   ▒▒ ░ ░░   ░ ▒░░ ▒  ▒ 
 ▒ ░      ░  ░░        ░░   ░░ ░ ░ ▒ ░░         ░    ░░   ░    ░       ░ ░ ░ ▒ ░      ░  ░      ░    ░   ▒     ░   ░ ░ ░ ░  ░ 
 ░        ░             ░        ░ ░            ░  ░  ░        ░ ░         ░ ░        ░         ░        ░  ░        ░   ░    
                                                               ░                                                       ░      
                                                                                                                              
"""

exit_error = """
██╗    █████████╗  █████████████████╗   ██╗██████╗     ██████╗██████╗ ██████╗ ██████╗██████╗ █████╗███╗   ███╗    ██╗
██║    ██╔════╚██╗██╔██╚══██╔══██████╗  ████╔════╝     ██╔══████╔══████╔═══████╔════╝██╔══████╔══██████╗ ████║    ██║
██║    █████╗  ╚███╔╝██║  ██║  ████╔██╗ ████║  ███╗    ██████╔██████╔██║   ████║  █████████╔█████████╔████╔██║    ██║
╚═╝    ██╔══╝  ██╔██╗██║  ██║  ████║╚██╗████║   ██║    ██╔═══╝██╔══████║   ████║   ████╔══████╔══████║╚██╔╝██║    ╚═╝
██╗    █████████╔╝ ████║  ██║  ████║ ╚████╚██████╔╝    ██║    ██║  ██╚██████╔╚██████╔██║  ████║  ████║ ╚═╝ ██║    ██╗
╚═╝    ╚══════╚═╝  ╚═╚═╝  ╚═╝  ╚═╚═╝  ╚═══╝╚═════╝     ╚═╝    ╚═╝  ╚═╝╚═════╝ ╚═════╝╚═╝  ╚═╚═╝  ╚═╚═╝     ╚═╝    ╚═╝
    
"""

```