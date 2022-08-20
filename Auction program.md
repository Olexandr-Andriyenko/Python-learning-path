# Auction program

Build a simple auction program with which you can save the bidders and their bids inside a dictionary.<br>
At the end of the program user should be informed who won the auction with the highest bid.<br>
At the beginning of the program the user can choose a currency.<br>
Do not forget to valid the users input, no one can bid zero or less and the user can select ONLY "EUR" or "USD" as currency!
<br>
<br>


<details><summary>Use the followeing ASCII art:</summary>
  
```python
 
                         ___________
                         \         /
                          )_______(
                          |"""""""|_.-._,.---------.,_.-._
                          |       | | |               | | ''-.
                          |       |_| |_             _| |_..-'
                          |_______| '-' `'---------'` '-'
                          )"""""""(
                         /_________\\
                       .-------------.
                      /_______________\\
  
```

</details>

<details><summary>Solution!</summary>
 
```python
  
 # Display the ASCII art
print('''\

 
                         ___________
                         \         /
                          )_______(
                          |"""""""|_.-._,.---------.,_.-._
                          |       | | |               | | ''-.
                          |       |_| |_             _| |_..-'
                          |_______| '-' `'---------'` '-'
                          )"""""""(
                         /_________\\
                       .-------------.
                      /_______________\\
  

''')
# Create a dictionary to store the information about the auction
auction_information = {}
# Ask the user to select a currency
# Do not forget to validate the input
currency_options =["EUR", "USD"]
while True:
    currency = input("Choose a currency (EUR / USD): ")
    if currency in currency_options:
        break
    print("Wrong input!")

# Continue the program as long as the following variable is true
continue_program = True
while continue_program:
    bidder_name = input("What is your name? ")
    # Valid that the bid is not 0 or less
    while True:
        bid = float(input("What is your bid? "))
        if bid > 0:
            break
        print("The bid have to be higher than 0!")
    # Add the bidders name and his bid to a dictionary
    auction_information[bidder_name] = float(bid)
    other_bidder = input("Are there any other bidders? Type 'yes or 'no': ")
    if other_bidder.lower() == "no":
        continue_program = False
# Search inside the dictionary "auction_information" the highest bid
# and display it with the bidders name to show the winner
highest_bid = 0
highest_bidder = ""
for bidder in auction_information:
    bid = auction_information[bidder]
    if bid > highest_bid:
        highest_bid = bid
        highest_bidder = bidder

# Display who is the winner
print(f"The winner is {highest_bidder} with a bid of {highest_bid} {currency}") 
  
```

</details>
