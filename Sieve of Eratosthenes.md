# Sieve of Eratosthenes

The Sieve of Eratosthenes is an algorithm for determining a list or table of all prime numbers less than or equal to a given number.
Study more about the Sieve of Eratosthenes on the [wikipedia page](https://en.wikipedia.org/wiki/Sieve_of_Eratosthenes)!
<br>
<br>
Your task:
- Create a list with all numbers up to 100
- First prime number is 2
- Delete all multiples from this primenumber (2 x primenumber)
- Search for the next prime number
- Repeat all steps until you reached last number of your list

This animation shows how the algorithm works:

![Animation_Sieb_des_Eratosthenes_Überarbeitet](https://user-images.githubusercontent.com/92121260/193281633-22fa2d74-7391-4d17-81c7-a75f77bacc3d.gif)

<details>
 <summary>Solution</summary>

```python
# Create the variables
num_list = []
prime_num = 0
multiple_prim_num = 0
max_value = 100

# ------------------------------------------------------------- #
# Functions
# ------------------------------------------------------------- #
# Fill the list with numbers
def create_num():
    # Create numbers from 0 until max_value
    for num in range(max_value + 1):
        num_list.append(num)


# First prime number
def first_prim_num():
    global prime_num
    prime_num = 2
    return prime_num


# Delete all multiples from this primenumber (2 x primenumber)
def prim_multiple():
    global prime_num
    multiple = 2 * prime_num
    # replace the multiples inside the list by 0
    while multiple < max_value:
        num_list[multiple] = 0
        multiple += prime_num


# Search next prime number
def next_prim_num():
    global prime_num
    prime_num += 1
    while num_list[prime_num] == 0:
        prime_num += 1


# Output prime numbers
def out_prim_num():
    for index in range(2, max_value):
        if num_list[index] != 0:
            print(num_list[index], end=' ')



# ------------------------------------------------------------- #
# Main program
# ------------------------------------------------------------- #
create_num()
first_prim_num()
# You are done "sifting" when the current prime number is greater than the root of the upper bound. sqrt(100)
while prime_num < 100:
    prim_multiple()
    next_prim_num()
out_prim_num()


```  
  
</details>
