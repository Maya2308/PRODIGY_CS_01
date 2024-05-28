# PRODIGY_CS_01
def caesar_cipher(text, shift, mode):
  """
  Encrypts or decrypts text using Caesar Cipher algorithm.

  Args:
      text: The text to encrypt or decrypt.
      shift: The number of positions to shift letters.
      mode: "encrypt" or "decrypt"

  Returns:
      The encrypted or decrypted text.
  """
  alphabet = 'abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ'
  shifted_alphabet = alphabet[shift:] + alphabet[:shift]
  result = ''
  for char in text:
    if char.isalpha():
      index = alphabet.find(char)
      new_char = shifted_alphabet[index]
      result += new_char if mode == "encrypt" else alphabet[index]
    else:
      result += char
  return result

# Get user input
message = input("Enter your message: ")
shift = int(input("Enter the shift value (positive for encrypt, negative for decrypt): "))
mode = input("Enter 'encrypt' or 'decrypt': ").lower()

# Check for valid mode
if mode not in ["encrypt", "decrypt"]:
  print("Invalid mode. Please enter 'encrypt' or 'decrypt'.")
  exit()

# Perform encryption or decryption
result = caesar_cipher(message, shift, mode)

# Print the result
print(f"{mode.title()}d message: {result}")
