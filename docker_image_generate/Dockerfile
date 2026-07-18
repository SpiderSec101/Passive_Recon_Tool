FROM kalilinux/kali-rolling

ENV DEBIAN_FRONTEND=noninteractive
ENV GOPATH=/go
ENV GOBIN=/go/bin
ENV PATH="${PATH}:/usr/local/go/bin:/go/bin:/root/.local/bin:/usr/games"

# Directory containing your application
WORKDIR /app

# ------------------------------------------------------------------
# Install OS packages (Added 'jq' and 'python3-setuptools')
# ------------------------------------------------------------------
RUN apt update && \
    apt -y upgrade && \
    apt install -y \
        python3 \
        python3-venv \
        python3-pip \
        python3-setuptools \
        golang-go \
        git \
        curl \
        wget \
        zsh \
        theharvester \
        lolcat \
        jq \
        docker.io && \
    apt clean && \
    rm -rf /var/lib/apt/lists/*

# ------------------------------------------------------------------
# Copy your source code
# ------------------------------------------------------------------
COPY . /app

# ------------------------------------------------------------------
# Python virtualenv & packages
# ------------------------------------------------------------------
RUN python3 -m venv /opt/venv
ENV PATH="/opt/venv/bin:${PATH}"

RUN pip install --upgrade pip

RUN if [ -f requirements.txt ]; then \
        pip install -r requirements.txt; \
    fi

# Install required Python packages for karma_v2 
# (No --break-system-packages needed inside a venv)
RUN pip install mmh3 dnsgen shodan bbot colored

# ------------------------------------------------------------------
# Go tools (Added 'nuclei')
# ------------------------------------------------------------------
RUN go install github.com/incogbyte/shosubgo@latest && \
    go install github.com/tomnomnom/httprobe@latest && \
    go install github.com/tomnomnom/anew@latest && \
    go install github.com/gwen001/github-subdomains@latest && \
    go install github.com/projectdiscovery/subfinder/v2/cmd/subfinder@latest && \
    go install github.com/d3mondev/puredns/v2@latest && \
    go install github.com/projectdiscovery/shuffledns/cmd/shuffledns@latest && \
    go install -v github.com/projectdiscovery/nuclei/v2/cmd/nuclei@latest && \
    go install -v github.com/projectdiscovery/httpx/cmd/httpx@latest

# ------------------------------------------------------------------
# Install Interlace (Fixed: pip handles build dependencies automatically)
# ------------------------------------------------------------------
RUN pip install git+https://github.com/codingo/Interlace.git


# Puredns Installation

RUN git clone https://github.com/blechschmidt/massdns.git && \
    cd massdns && \
    make && \
    make install

# ------------------------------------------------------------------
# Run your program
# ------------------------------------------------------------------
ENTRYPOINT ["python3", "-u", "docker_tool.py"]
