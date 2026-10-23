# PHP2Shell Advanced Exploit Framework

An advanced exploit framework targeting PHP Session Upload Progress vulnerabilities, featuring automated ASLR bypass, intelligent worker rotation, and a built-in reverse shell listener for reliable Remote Code Execution (RCE).

---

## 🚀 Features

* **Automated ASLR Bypass:** Leaks Zend Memory Manager chunk base and `libphp.so` base dynamically.
* **Smart Worker Rotation:** Flushes and rotates HTTP worker processes to ensure stability and prevent server crashes.
* **Built-in Reverse Shell Listener:** Automatically starts a multi-threaded TCP listener to capture reverse connections with an interactive TTY-like interface.
* **Evasion & Stealth:** Randomizes `User-Agent` headers and implements intelligent delays (`Jitter`) between requests.
* **Multi-Profile Support:** Fully compatible with official Debian/Apache environments (`bookworm`) and custom lab builds.

---

## 📋 Requirements

* Python 3.x
* Standard Python libraries (no external heavy packages required).

---

## ⚙️ Installation

Clone the repository and navigate to the project directory:

```bash
git clone [https://github.com/Tifa400/-php2shell-advanced.git](https://github.com/Tifa400/-php2shell-advanced.git)
cd -php2shell-advanced

💻 Usage
​1. Run with Built-in Reverse Shell Listener
​To launch the exploit and automatically listen for an incoming reverse shell connection

##bash
python3 Php2chell_exploit -u [http://target.local/index.php](http://target.local/index.php) --listen-port 4444

2. Execute a Single Command (Proof/File Output)
##bash

python3 Php2chell_exploit -u [http://target.local/index.php](http://target.local/index.php) -c "id>/out/p1" --proof-file out/p1

🎛️ Command-Line Arguments

| Argument | Description | Default |
| :--- | :--- | :--- |
| `-u`, `--url` | Target PHP page URL (Required) | `None` |
| `-c`, `--cmd` | Command to execute (Max 14 bytes for standard carrier) | `id>/out/p1` |
| `--listen-host` | Local host for the built-in reverse shell listener | `0.0.0.0` |
| `--listen-port` | Local port for the built-in reverse shell listener | `0` (Disabled) |
| `--profile` | Target environment profile (`bookworm` or `lab`) | `bookworm` |
| `--retries` | Number of attempts per leak stage | `3` |
| `-q`, `--quiet` | Suppress verbose output | `False` |

🛡️ Disclaimer
​This tool is created strictly for educational purposes, security research, and authorized penetration testing. Unauthorized testing or exploiting targets without explicit prior permission is illegal. The author assumes no liability for any misuse or damage caused by this program.