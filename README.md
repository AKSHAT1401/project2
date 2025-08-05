import random
import string

def generate_password():
    print("Password Generator")
    print("------------------")

    try:
        length = int(input("Enter desired password length: "))

        if length <= 0:
            print("Length must be greater than 0.")
            return

        # Ask user for complexity preferences
        use_uppercase = input("Include uppercase letters? (y/n): ").lower() == 'y'
        use_digits = input("Include numbers? (y/n): ").lower() == 'y'
        use_symbols = input("Include symbols? (y/n): ").lower() == 'y'

        # Base character set
        char_set = string.ascii_lowercase

        if use_uppercase:
            char_set += string.ascii_uppercase
        if use_digits:
            char_set += string.digits
        if use_symbols:
            char_set += string.punctuation

        if not char_set:
            print("No character types selected. Cannot generate password.")
            return

        # Generate password
        password = ''.join(random.choice(char_set) for _ in range(length))
        print(f"\nGenerated Password: {password}")

    except ValueError:
        print("Invalid input. Please enter a valid number.")
