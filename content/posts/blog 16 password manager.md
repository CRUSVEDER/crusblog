---
title: 16. Password Vault Manager
date: 2024-12-18
Toc: true
draft: false
tags:
  - project
---
---
# Building CRUSVAULT: A Secure Password Vault

Welcome to this blog post about creating **CRUSVAULT**, a secure and interactive password vault application using Python. This project leverages encryption, password management techniques, and a user-friendly interface. Let's dive into the details of its features, code explanation, and how to build it.
![Image Description](/images/Pasted%20image%2020250110042304.png)

[password manager git link](https://github.com/CRUSVEDER/PasswordManager)

---

## Features of CRUSVAULT

- Secure password encryption using the `cryptography` library.
- Interactive command-line interface (CLI) with `rich` for a visually appealing experience.
- Manage multiple vaults with the ability to add, edit, delete, or retrieve passwords.
- Password strength checker and generator.
- Easy vault creation, renaming, and deletion options.
- ASCII art header for a personalized touch.

---

## Prerequisites

Before you begin, ensure you have the following installed:

1. Python 3.7 or higher.
2. The required Python libraries:
    
    ```bash
    pip install bcrypt cryptography rich pyfiglet
    ```
    

---

## How to Build CRUSVAULT

1. **Set Up Your Project Environment**:
    
    - Create a new folder for the project, e.g., `crusvault_project`.
    - Save the script as `crusvault.py` inside the folder.
2. **Code Explanation**:
    

### ASCII Art Header

```python
import pyfiglet
result = pyfiglet.figlet_format("CRUSVAULT", font="slant")
print(f"[bold cyan]{result}[/bold cyan]")
```

- Displays an eye-catching ASCII header using the `pyfiglet` library.

### Encryption Functions

```python
from cryptography.fernet import Fernet
from cryptography.hazmat.primitives.kdf.pbkdf2 import PBKDF2HMAC
from cryptography.hazmat.primitives.hashes import SHA256
from cryptography.hazmat.backends import default_backend
import base64

def generate_key(master_password):
    salt = b"password_vault_salt"
    kdf = PBKDF2HMAC(
        algorithm=SHA256(),
        length=32,
        salt=salt,
        iterations=100_000,
        backend=default_backend()
    )
    key = kdf.derive(master_password.encode())
    return base64.urlsafe_b64encode(key)
```

- Generates a unique key derived from the user's master password and a fixed salt.
- Uses `PBKDF2HMAC` for secure key derivation.

```python
def encrypt_data(key, data):
    fernet = Fernet(key)
    return fernet.encrypt(data.encode())

def decrypt_data(key, encrypted_data):
    try:
        fernet = Fernet(key)
        return fernet.decrypt(encrypted_data).decode()
    except Exception as e:
        console.print(f"[red]Error decrypting data: {e}[/red]")
        raise ValueError("Decryption failed. Please check the master password and vault integrity.")
```

- `encrypt_data` encrypts plain text data using the generated key.
- `decrypt_data` decrypts the encrypted data back into plain text.

### Vault Operations

```python
import os
import json

def save_to_file(file_name, encrypted_data):
    with open(file_name, 'wb') as file:
        file.write(encrypted_data)

def load_from_file(file_name):
    if not os.path.exists(file_name):
        return None
    with open(file_name, 'rb') as file:
        return file.read()
```

- Handles saving and loading vault data from a file securely.

### Adding and Retrieving Passwords

```python
def add_password(vault_file, master_password, service, password):
    key = generate_key(master_password)
    vault_data = load_from_file(vault_file)

    try:
        if vault_data:
            vault = decrypt_data(key, vault_data)
        else:
            vault = "{}"
    except Exception:
        console.print("[bold red]Error decrypting vault data.[/bold red]")
        return

    vault_dict = json.loads(vault) if vault else {}
    encrypted_password = encrypt_data(key, password)
    vault_dict[service] = encrypted_password.decode()

    encrypted_vault = encrypt_data(key, json.dumps(vault_dict))
    save_to_file(vault_file, encrypted_vault)
    console.print("[green]Password added successfully![/green]")
```

- Adds an encrypted password for a given service to the vault.

```python
def retrieve_password(vault_file, master_password, service):
    key = generate_key(master_password)
    vault_data = load_from_file(vault_file)

    if not vault_data:
        console.print("[bold red]No passwords stored yet.[/bold red]")
        return None

    try:
        vault = decrypt_data(key, vault_data)
        vault_dict = json.loads(vault)
        encrypted_password = vault_dict.get(service)
        if not encrypted_password:
            return "[yellow]Service not found in vault.[/yellow]"
        return decrypt_data(key, encrypted_password)
    except Exception:
        console.print("[bold red]Error retrieving password.[/bold red]")
        return None
```

- Retrieves and decrypts a stored password for a specified service.

### Password Generator

```python
def generate_password(length=12):
    characters = string.ascii_letters + string.digits + string.punctuation
    password = [random.choice(string.ascii_uppercase),
                random.choice(string.ascii_lowercase),
                random.choice(string.digits),
                random.choice(string.punctuation)]
    password += [random.choice(characters) for _ in range(length - 4)]
    random.shuffle(password)
    return ''.join(password)
```

- Creates a strong, random password with a mix of uppercase, lowercase, digits, and symbols.

### Main Menu

```python
from rich.console import Console
from rich.table import Table
from rich.prompt import Prompt
console = Console()

# CLI for managing the vault
def main_menu():
    vault_file = "password_vault.lock"
    master_password = Prompt.ask("[bold cyan]Enter your master password[/bold cyan]", password=True)
    
    while True:
        console.print("\n[bold cyan]Main Menu[/bold cyan]")
        table = Table(show_header=True, header_style="bold magenta")
        table.add_column("Option", style="dim", width=5)
        table.add_column("Action", justify="left")
        table.add_row("1", "Add Password")
        table.add_row("2", "Retrieve Password")
        table.add_row("3", "View All Services")
        table.add_row("4", "Exit")
        console.print(table)

        choice = Prompt.ask("[bold green]Choose an option[/bold green]")

        if choice == "1":
            service = Prompt.ask("[bold yellow]Enter the service name[/bold yellow]")
            password = Prompt.ask("[bold yellow]Enter the password[/bold yellow]", password=True)
            add_password(vault_file, master_password, service, password)

        elif choice == "2":
            service = Prompt.ask("[bold yellow]Enter the service name[/bold yellow]")
            password = retrieve_password(vault_file, master_password, service)
            console.print(f"[bold green]Stored password for {service}:[/bold green] {password}")

        elif choice == "3":
            console.print("[cyan]Viewing all services is not implemented in this snippet.[/cyan]")

        elif choice == "4":
            console.print("[bold cyan]Goodbye![/bold cyan]")
            break

        else:
            console.print("[bold red]Invalid choice. Please try again.[/bold red]")

if __name__ == "__main__":
    main_menu()
```

---

## Running the Application

1. Save the script as `crusvault.py`.
2. Run the script:
    
    ```bash
    python crusvault.py
    ```
    
3. Follow the interactive prompts to manage your passwords.

---

## Conclusion

CRUSVAULT is a simple yet powerful example of how Python can be used to create secure and interactive applications. With proper encryption techniques and a user-friendly interface, you can manage your passwords efficiently. Happy coding!

---