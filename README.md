# Password Checker - Pwned Passwords API

This Python script checks if your password has been compromised in any data breaches using the **Have I Been Pwned (HIBP)** API. It securely checks your password without sending the full password to the API, ensuring your privacy.

## Features

- **Secure Password Checking**: Uses SHA-1 hashing to check passwords without exposing them.
- **Integration with HIBP API**: Connects to the Have I Been Pwned API to check for compromised passwords.
- **Command-Line Interface**: Easily check multiple passwords from the command line.
- **Privacy-Focused**: Only the first 5 characters of the hashed password are sent to the API.

## Requirements

- Python 3.x
- `requests` library

## Installation

1. **Install Python**: If you don't have Python installed, download and install it from [python.org](https://www.python.org/).

2. **Install the `requests` library**: You can install it using pip. Open your terminal or command prompt and run:
   ```bash
   pip install requests
   ```

3. **Download the Script**: Clone or download this repository to your local machine.

## Usage

Run the script from the command line and provide the passwords you want to check as arguments. For example:

```bash
python password_checker.py password123 securepassword mysecretpass
```

### Output Example:
```
password123 was found 12345 times... you should check the password
securepassword was not found. Carry on!
mysecretpass was found 10 times... you should check the password
```

## How It Works

1. **Hashing**: The script hashes your password using the SHA-1 algorithm and converts it to uppercase.
2. **API Request**: It sends the first 5 characters of the hashed password to the HIBP API.
3. **Response Handling**: The API returns a list of hashes that match the first 5 characters. The script compares the remaining part of your hashed password with the list.
4. **Result**: If a match is found, it returns the number of times the password has been compromised. If no match is found, the password is considered safe.

## Code Structure

- **`request_api_data(query_char)`**: Sends a request to the HIBP API with the first 5 characters of the hashed password.
- **`get_password_leaks_count(hashes, hash_to_check)`**: Compares the hashes returned by the API with the remaining part of the hashed password.
- **`pwned_api_check(password)`**: Hashes the password and calls the above functions to check if it has been compromised.
- **`main(args)`**: Handles command-line arguments and prints the results.

## Why Use This?

- **Security Awareness**: Helps you identify if your passwords have been exposed in data breaches.
- **Privacy Protection**: Ensures your passwords are never sent in full to any external service.
- **Ease of Use**: Simple command-line interface for quick checks.

## Future Improvements

- Add support for reading passwords from a file.
- Implement a GUI for non-technical users.
- Add rate-limiting to avoid overwhelming the API.
- Provide suggestions for stronger passwords.

## Contributing

Feel free to fork this repository and submit pull requests with your improvements. If you find any bugs or have suggestions, please open an issue.

## License

This project is open-source and available under the MIT License. See the [LICENSE](LICENSE) file for more details.

## Acknowledgments

- Thanks to **Have I Been Pwned** for providing the API and promoting password security.
- Inspired by the need for better password hygiene and security awareness.

Stay safe and secure! 🔒
