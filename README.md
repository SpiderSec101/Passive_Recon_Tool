# 🔍 Passive Recon Tool

> A fast, modular, and extensible reconnaissance framework for security professionals, bug bounty hunters, penetration testers, and researchers.

![Python](https://img.shields.io/badge/Python-3.10%2B-blue.svg)
![Docker](https://img.shields.io/badge/Docker-Supported-2496ED?logo=docker&logoColor=white)
![Platform](https://img.shields.io/badge/Platform-Linux-lightgrey)

---

## 📖 Overview

**Passive Recon Tool** automates reconnaissance by combining multiple passive enumeration techniques into a single workflow. It helps to gather apex domains, subdomains, ipv4 addresses, different endpoints and dorks for manual scanning.

It supports running directly using Python or inside an isolated Docker container, making deployment simple across different environments. The tool is using threads so that multiple tasks can be performed simultaneously.

---

## ✨ Features

- Subdomain enumeration
- Passive subdomain bruteforcing
- SSL/TLS certificate enumeration
- Web crawling
- Cloud data enumeration
- Shodan scraping
- IPv4 addresses gathering
- Finding live domains
- Screenshot collection
- Multi-threaded execution
- Organized output structure
- Docker support
- Easy configuration

---

## 📂 Project Structure

---

# 🚀 Installation

## Option 1 — Python

### Clone the repository

```bash
git clone https://github.com/<username>/<repository>.git
cd <repository>
```

### Create Virtual Environment

```bash
python3 -m venv venv
source venv/bin/activate
```

### Install Dependencies

```bash
pip install -r requirements.txt
```

---

## Option 2 — Docker

### Build the Docker image

- Before creating the docker image, fill up the config.yaml file 
- Atleast provide the shodan and github api keys into the config.yaml file 

```bash
cd docker_image_generate

docker build -t passive_recon_tool .
```

---

# ⚡ Usage

- While running the python file be sure that the config.yaml is in the same directory as the python file is
- While creating the docker image put the config.yaml in the same directory where the Docker is present
- To run the tool atleast shodan and github api key is required
  
```
usage: passive_recon_tool.py [-h] [-o OUTPUT_DIR] target

Passive Recon Tool

positional arguments:
  target                Target domain (e.g. example.com)

options:
  -h, --help            show this help message and exit
  -o, --output-dir OUTPUT_DIR
                        Directory where recon results will be saved (default: ./output)

Example:
    python3 recon_tool.py target.com -o ./passive_recon_output


```

## Python

```bash
python3 passive_recon_tol.py target.com -o output_directory
```

---

## Docker

```bash
docker run --rm -it -v /var/run/docker.sock:/var/run/docker.sock -v "$(pwd):/workspace" passive_recon_tool target.com -o /workspace

```


---


# 📁 Output

Example output structure

```text
output/

project/
├── assets/
│   ├── Domains/
│   ├── endpoints/
│   ├── IP/
│   ├── secrets/
│   └── ss/
│       ├── host1.example.com/
│       │   └── screenshot.png
│       ├── host2.example.com/
│       │   └── screenshot.png
│       └── ...
└── burp
│       
└── exploit
│       
└── findings
│       
└── tmp

```

---

# 🛠 Configuration

Edit the configuration file

```text
config.yaml
```

Example

```ini
; Add your API keys under the relevant sections
; Example: 

; OpenAI
openai = ""

; Chaos
virustotal = ""

; Shodan
shodan = ""

; Github
spyse = ""

; Facebook
securitytrails = ""

; PassiveTotal
censys = ""

; Twitter
apikey = ""
secret = ""
```

---

# 📝 Requirements

- Python 3.10+
- Docker (optional)
- Linux (Recommended)
- config.yaml

---
# ⚠️ Disclaimer

This project is intended for:

- Authorized Security Assessments
- Penetration Testing
- Bug Bounty Programs
- Educational Purposes

The author is **not responsible** for any misuse of this tool.

Use responsibly and only on systems you have permission to test.

---

# ⭐ Support

If you found this project useful:

⭐ Star the repository

🍴 Fork the project

🐞 Report bugs

💡 Suggest new features

---

# 👨‍💻 Author

**Adil Hossain Sana (spider)**

GitHub: https://github.com/SpiderSec101


---

## 🌟 Acknowledgements

Thanks to the open-source security community and all the amazing tools that inspired this project.
