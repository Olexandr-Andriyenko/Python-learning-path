# Caesar cipher

Study the [rules of Caesar cipher](https://en.wikipedia.org/wiki/Caesar_cipher) and build your own!<br>
This is one of the simplest and most widely known encryption techniques. It is a type of substitution cipher in which each letter in the plaintext is replaced by a letter some fixed number of positions down the alphabet. 
<br>
<br>
Ask the user at the begining whether he likes to "encode" or "decode".
<br>
<br>
Use the knowledge about functions to structure your code!

<details><summary>Use this ASCII art </summary>
  
```python
  
           
 ,adPPYba, ,adPPYYba,  ,adPPYba, ,adPPYba, ,adPPYYba, 8b,dPPYba,  
a8"     "" ""     `Y8 a8P_____88 I8[    "" ""     `Y8 88P'   "Y8  
8b         ,adPPPPP88 8PP"  `"Y8ba,  ,adPPPPP88 88          
"8a,   ,aa 88,    ,88 "8b,   ,aa aa    ]8I 88,    ,88 88          
 `"Ybbd8"' `"8bbdP"Y8  `"Ybbd8"' `"YbbdP"' `"8bbdP"Y8 88   
            88             88                                 
           ""             88                                 
                          88                                 
 ,adPPYba, 88 8b,dPPYba,  88,dPPYba,   ,adPPYba, 8b,dPPYba,  
a8"     "" 88 88P'    "8a 88P'    "8a a8P_____88 88P'   "Y8  
8b         88 88       d8 88       88 8PP" 88          
"8a,   ,aa 88 88b,   ,a8" 88       88 "8b,   ,aa 88          
 `"Ybbd8"' 88 88`YbbdP"'  88       88  `"Ybbd8"' 88          
              88                                             
              88           
  
````

</details>
                                                                                                    
<details><summary>For this task you should use a list of alphabet letters</summary>
  
```python

alphabet = ['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j', 'k', 'l', 'm', 'n', 'o', 'p', 'q', 'r', 's', 't', 'u', 'v', 'w', 'x', 'y', 'z', 'a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j', 'k', 'l', 'm', 'n', 'o', 'p', 'q', 'r', 's', 't', 'u', 'v', 'w', 'x', 'y', 'z']
  
```  
  
</details>


<details><summary>Solution</summary>

```python
# List of the alphabet
alphabet = ['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j', 'k', 'l', 'm', 'n', 'o', 'p', 'q', 'r', 's', 't', 'u',
            'v', 'w', 'x', 'y', 'z', 'a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j', 'k', 'l', 'm', 'n', 'o', 'p',
            'q', 'r', 's', 't', 'u', 'v', 'w', 'x', 'y', 'z']


# Function to encrypt a message
def encrypt_message(shift_number, message):
    message_encrypted = ""
    for letter in message:
        if letter in alphabet:
            # The "index" method is really helpful to find out the position
            # in a list of specific character
            position = alphabet.index(letter) + shift_number
            message_encrypted += alphabet[position]
    return message_encrypted


# Function to decrypt a message, a "key" is needed for this task
def decrypt_message(key, message):
    message_decrypted = ""
    for letter in message:
        if letter in alphabet:
            # The "index" method is really helpful to find out the position
            # in a list of specific character
            position = alphabet.index(letter) - key
            message_decrypted += alphabet[position]
    return message_decrypted

# --------------------------------------------------------------------------------#
# The actual program starts here
# Display the ASCII art
print('''\
  
           
 ,adPPYba, ,adPPYYba,  ,adPPYba, ,adPPYba, ,adPPYYba, 8b,dPPYba,  
a8"     "" ""     `Y8 a8P_____88 I8[    "" ""     `Y8 88P'   "Y8  
8b         ,adPPPPP88 8PP"  `"Y8ba,  ,adPPPPP88 88          
"8a,   ,aa 88,    ,88 "8b,   ,aa aa    ]8I 88,    ,88 88          
 `"Ybbd8"' `"8bbdP"Y8  `"Ybbd8"' `"YbbdP"' `"8bbdP"Y8 88   
            88             88                                 
           ""             88                                 
                          88                                 
 ,adPPYba, 88 8b,dPPYba,  88,dPPYba,   ,adPPYba, 8b,dPPYba,  
a8"     "" 88 88P'    "8a 88P'    "8a a8P_____88 88P'   "Y8  
8b         88 88       d8 88       88 8PP" 88          
"8a,   ,aa 88 88b,   ,a8" 88       88 "8b,   ,aa 88          
 `"Ybbd8"' 88 88`YbbdP"'  88       88  `"Ybbd8"' 88          
              88                                             
              88           
  
''')
# Continue this program as long the user stop it
continue_program = True
while continue_program:
    # Display information for the user
    what_to_do = input("Type 'encode' to encrypt, type 'decode' to decrypt: ")
    # Ask the user which message he likes to encrypt or decrypt
    if what_to_do.lower() == "encode":
        message = input("Type your message: ")
        shift_number = int(input("Type the shift number: "))
        encoded_message = encrypt_message(shift_number, message)
        print(f"Here's the encoded result: {encoded_message}")

    if what_to_do.lower() == "decode":
        message = input("Type your message: ")
        shift_number = int(input("Type the shift number: "))
        decrypted_message = decrypt_message(shift_number, message)
        print(f"Here's the encoded result: {decrypted_message}")

    # Ask the user whether he likes to continue or exit
    user_want_continue = input("Type 'yes' if you want to go again. Otherwise type 'no'.")
    if user_want_continue.lower() == "no":
        # Set this variable to false for exit the while loop
        continue_program = False

  
  
````

</details>
