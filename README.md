# Caesar-Cipher-project-1-of-cyber-security-internship

"""
Task 01 - Caesar Cipher
Educational Cybersecurity Project

Encrypts and decrypts text using the Caesar Cipher.
"""

def caesar_cipher(text: str, shift: int) -> str:
    result = []

    for char in text:
        if char.isalpha() and char.isascii():
            base = ord('A') if char.isupper() else ord('a')
            shifted = (ord(char) - base + shift) % 26
            result.append(chr(base + shifted))
        else:
            result.append(char)

    return ''.join(result)


def get_shift() -> int:
    while True:
        try:
            return int(input("Enter shift value (e.g. 3): "))
        except ValueError:
            print("Please enter a valid integer.")


def main():
    print("=" * 50)
    print("        CAESAR CIPHER - TEXT ENCRYPTION")
    print("=" * 50)

    while True:
        choice = input(
            "\nChoose: [E]ncrypt  [D]ecrypt  [Q]uit: "
        ).strip().lower()

        if choice == "q":
            print("Goodbye!")
            break

        if choice not in ("e", "d"):
            print("Invalid choice. Please select E, D, or Q.")
            continue

        message = input("Enter your message: ")
        shift = get_shift()

        if choice == "d":
            shift = -shift

        result = caesar_cipher(message, shift)

        print("\nResult:")
        print(result)


if __name__ == "__main__":
    main()
