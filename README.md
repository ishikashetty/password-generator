# password-generator
import random
import string

def generate_password(length=12, use_uppercase=True, use_digits=True, use_symbols=True):
    # Define character pools
    lower = string.ascii_lowercase
    upper = string.ascii_uppercase if use_uppercase else ''
    digits = string.digits if use_digits else ''
    symbols = string.punctuation if use_symbols else ''

    # Combine pools
    all_chars = lower + upper + digits + symbols

    # Ensure the pool isn't empty
    if not all_chars:
        raise ValueError("No characters selected for password generation.")

    # Generate password
    password = ''.join(random.choice(all_chars) for _ in range(length))
    return password

if __name__ == "__main__":
    # Example usage
    length = int(input("Enter password length: "))
    use_uppercase = input("Include uppercase letters? (y/n): ").lower() == 'y'
    use_digits = input("Include digits? (y/n): ").lower() == 'y'
    use_symbols = input("Include symbols? (y/n): ").lower() == 'y'

    password = generate_password(length, use_uppercase, use_digits, use_symbols)
    print(f"Generated password: {password}")
