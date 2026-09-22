# 🚀 Guia Completo de Pós-instalação e Customização de Pacotes no Ubuntu (Zsh com Oh My Zsh)

> **Ambiente:** Ubuntu Linux (x86_64)  
> **Mantenedor:** Lucivaldo Junior (Luci Junior)  
> **Orquestração & Documentação:** Agente Pessoal Lucy (Ecossistema Nexus)  
> **Stack Principal:** Java 21 LTS | Go 1.26+ | Node.js | Docker | AWS | IA Local  
> **Shell Padrão:** Zsh com Oh My Zsh & Spaceship Prompt  

---

## 📋 Sumário
1. [📦 Atualização do Sistema & Pacotes Essenciais](#1--atualização-do-sistema--pacotes-essenciais)
2. [🐚 Terminal Zsh, Oh My Zsh & Spaceship Prompt](#2--terminal-zsh-oh-my-zsh--spaceship-prompt)
3. [🎛️ Utilitários Principais do Sistema (Flatpak, GNOME Tweaks & Periféricos)](#3-️-utilitários-principais-do-sistema-flatpak-gnome-tweaks--periféricos)
4. [🌐 Navegador Web (Google Chrome)](#4--navegador-web-google-chrome)
5. [🟢 Ecossistema Node.js & NVM](#5--ecossistema-nodejs--nvm)
6. [🦫 Linguagem Go (Golang 1.26+)](#6--linguagem-go-golang-126)
7. [☕ Linguagem Java (OpenJDK 21 LTS & Maven)](#7--linguagem-java-openjdk-21-lts--maven)
8. [🐍 Python 3.14 (Compilação a partir da Fonte & Pyenv)](#8--python-314-compilação-a-partir-da-fonte--pyenv)
9. [🐳 Docker Engine, Docker Compose & Containers](#9--docker-engine-docker-compose--containers)
10. [☁️ AWS CLI v2 & Rclone (Nuvem & Backup)](#10--aws-cli-v2--rclone-nuvem--backup)
11. [🛠️ IDEs, Editores & Inteligência Artificial](#11-️-ides-editores--inteligência-artificial)
12. [💬 Comunicação & Mensageria](#12--comunicação--mensageria)
13. [🎨 Multimídia, Gravação & Design](#13--multimídia-gravação--design)
14. [🎮 Jogos & Emulação Retrô](#14--jogos--emulação-retrô)
15. [🗄️ Bancos de Dados Locais (PostgreSQL & MySQL)](#15-️-bancos-de-dados-locais-postgresql--mysql)
16. [🧹 Manutenção, Faxina & Limpeza do Sistema](#16--manutenção-faxina--limpeza-do-sistema)

---

## 1. 📦 Atualização do Sistema & Pacotes Essenciais

Atualizar os índices de repositórios, os pacotes instalados no sistema e carregar as bibliotecas básicas de compilação:

```bash
# Atualiza a lista de pacotes e realiza a atualização geral do sistema operacional
sudo apt update && sudo apt upgrade -y

# Instala ferramentas essenciais de build (GCC, G++, Make), Git, Curl e utilitários de compressão
sudo apt install -y build-essential git curl wget unzip software-properties-gtk
```

---

## 2. 🐚 Terminal Zsh, Oh My Zsh & Spaceship Prompt

Configuração prioritária do shell para que todas as variáveis de ambiente, caminhos de binários (`PATH`) e aliases configurados nas etapas seguintes sejam gravados diretamente no `~/.zshrc`:

### ⚡ 1. Instalar o Zsh e definir como shell padrão:
```bash
sudo apt update && sudo apt install -y zsh
chsh -s $(which zsh)
```

### 🛠️ 2. Instalar o Oh My Zsh:
```bash
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

### 🚀 3. Instalar o Tema Spaceship Prompt:
```bash
git clone https://github.com/spaceship-prompt/spaceship-prompt.git "$ZSH_CUSTOM/themes/spaceship-prompt" --depth=1
ln -s "$ZSH_CUSTOM/themes/spaceship-prompt/spaceship.zsh-theme" "$ZSH_CUSTOM/themes/spaceship.zsh-theme"
```

### 🔹 4. Plugins Essenciais (Autosuggestions & Syntax Highlighting):
```bash
# Autosuggestions (sugestões automáticas baseadas no histórico)
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions

# Syntax Highlighting (realce de sintaxe em tempo real no terminal)
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```

No arquivo `~/.zshrc`, configure o tema e os plugins:
```bash
ZSH_THEME="spaceship"
plugins=(git zsh-autosuggestions zsh-syntax-highlighting)
```

Recarregue as configurações do shell:
```bash
source ~/.zshrc
```

---

## 3. 🎛️ Utilitários Principais do Sistema (Flatpak, GNOME Tweaks & Periféricos)

Categoria unificada com os utilitários indispensáveis para gerenciamento de pacotes, personalização visual do GNOME, integração de periféricos e virtualização:

### 📦 Flatpak & Flathub (Gerenciador Universal de Pacotes Sandbox):
```bash
# Instala o suporte a Flatpak e o plugin de integração com a GNOME Software
sudo apt install -y flatpak gnome-software-plugin-flatpak

# Adiciona o repositório oficial Flathub
flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo
```

### 🔧 GNOME Tweaks & Extension Manager (Personalização do Desktop):
```bash
# Ajustes finos de fontes, janelas, comportamento do mouse e gerenciamento de extensões do GNOME Shell
sudo apt install -y gnome-tweaks gnome-shell-extension-manager
```

### 🎛️ Gear Lever (Gerenciamento e Integração Ágil de AppImages):
```bash
# Permite abrir, atualizar e integrar arquivos AppImage diretamente no menu de aplicativos
flatpak install flathub it.mijorus.gearlever -y
```

### 🖱️ Solaar (Gerenciador de Periféricos sem Fio Logitech):
```bash
# Monitoramento de bateria e ajustes de emparelhamento para mouses e teclados Logitech
sudo apt install -y solaar
```

### 🎮 Input Remapper (Remapeamento Avançado de Teclas e Controles):
```bash
# Mapeamento flexível de botões de mouse para funções customizadas, macros e gamepads
sudo apt install -y input-remapper-gtk
```

### 📦 Gdebi (Instalador Gráfico Leve de Pacotes .deb):
```bash
# Instala arquivos .deb locais resolvendo e baixando automaticamente as dependências necessárias
sudo apt install -y gdebi
```

### 🖥️ VirtualBox (Virtualização Completa de Sistemas):
```bash
# Virtualização de máquinas virtuais completas (Windows Server, distribuições Linux, etc.)
sudo apt install -y virtualbox-qt
```

---

## 4. 🌐 Navegador Web (Google Chrome)

Instalação oficial do Google Chrome via pacote `.deb` estável:

```bash
# Baixa o pacote oficial do Chrome
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb

# Instala o pacote via dpkg e resolve eventuais dependências faltantes
sudo dpkg -i google-chrome-stable_current_amd64.deb
sudo apt --fix-broken install -y

# Remove o instalador temporário
rm -f google-chrome-stable_current_amd64.deb
```

---

## 5. 🟢 Ecossistema Node.js & NVM

Gerenciador de versões NVM para evitar conflitos de permissão e alternar facilmente entre versões:

```bash
# Instala o NVM (Node Version Manager)
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.1/install.sh | bash

# Carrega as variáveis do NVM na sessão atual
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"

# Instala a versão LTS mais recente e a define como padrão
nvm install --lts
nvm use --lts
nvm alias default 'lts/*'

# Instala TypeScript e utilitários globais
npm install -g typescript @angular/cli
```

---

## 6. 🦫 Linguagem Go (Golang 1.26+)

Instalação limpa do runtime oficial de Go a partir do binário compilado:

```bash
# Remove instalações antigas e baixa a versão mais recente do Go
sudo rm -rf /usr/local/go
wget https://go.dev/dl/go1.26.4.linux-amd64.tar.gz

# Extrai para /usr/local
sudo tar -C /usr/local -xzf go1.26.4.linux-amd64.tar.gz
rm -f go1.26.4.linux-amd64.tar.gz

# Adiciona o Go ao PATH no ~/.zshrc
echo 'export PATH=$PATH:/usr/local/go/bin:$HOME/go/bin' >> ~/.zshrc
source ~/.zshrc

# Valida a instalação
go version
```

---

## 7. ☕ Linguagem Java (OpenJDK 21 LTS & Maven)

Stack principal para desenvolvimento corporativo com Spring Boot:

```bash
# Instala o JDK 21 LTS e Maven
sudo apt install -y openjdk-21-jdk maven

# Valida as versões instaladas
java -version
javac -version
mvn -version
```

*(Opcional: Para compatibilidade com projetos legados JDK 11: `sudo apt install -y openjdk-11-jdk`)*

---

## 8. 🐍 Python 3.14 (Compilação a partir da Fonte & Pyenv)

### 🔧 Dependências de compilação C/C++:
```bash
sudo apt-get install -y build-essential gdb lcov pkg-config \
libbz2-dev libffi-dev libgdbm-dev libgdbm-compat-dev liblzma-dev \
libncurses-dev libreadline-dev libsqlite3-dev libssl-dev \
tk-dev uuid-dev zlib1g-dev
```

### ⚙️ Compilação e instalação em `/opt/python3.14`:
```bash
tar -xf Python-3.14.4.tar.xz
cd Python-3.14.4
sudo ./configure --enable-optimizations --prefix=/opt/python3.14
sudo make -j$(nproc)
sudo make altinstall

# Criação de aliases amigáveis no ~/.zshrc
echo "alias python3.14='/opt/python3.14/bin/python3.14'" >> ~/.zshrc
echo "alias python='/opt/python3.14/bin/python3.14'" >> ~/.zshrc

# Atualização do pip
sudo /opt/python3.14/bin/python3.14 -m ensurepip --upgrade
sudo /opt/python3.14/bin/python3.14 -m pip install --upgrade pip
```

### 📦 Instalação e Gerenciamento de Versões com Pyenv:

#### 1. Instalar o Pyenv:
```bash
curl -L https://github.com/pyenv/pyenv-installer/raw/master/bin/pyenv-installer | bash

# Configurar as variáveis de ambiente no ~/.zshrc:
echo -e '\n# Pyenv Configuration' >> ~/.zshrc
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.zshrc
echo '[[ -d $PYENV_ROOT/bin ]] && export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.zshrc
echo 'eval "$(pyenv init -)"' >> ~/.zshrc
source ~/.zshrc
```

#### 2. Atualizar a lista de versões disponíveis (novos releases):
```bash
# Atualiza os índices do pyenv para enxergar novas versões lançadas do Python
pyenv update
```

#### 3. Listar versões disponíveis para instalação:
```bash
# Lista todas as versões disponíveis (ou filtra pela família 3.12, 3.13, 3.14...)
pyenv install -l | grep -E "^\s*3\.(12|13|14)"
```

#### 4. Instalar uma versão específica do Python:
```bash
# Instala a versão desejada (o pyenv compilará com as dependências do sistema):
pyenv install 3.14.4
pyenv install 3.12.8
```

#### 5. Definir e alternar versões do Python:
```bash
# Define a versão padrão para todo o sistema do usuário (Global):
pyenv global 3.14.4

# Define a versão exclusiva para a pasta/projeto atual (cria arquivo .python-version):
pyenv local 3.12.8

# Lista todas as versões instaladas no computador:
pyenv versions

# Mostra a versão atualmente ativa no terminal e onde foi configurada:
pyenv version
```

#### 6. Desinstalar uma versão antiga:
```bash
pyenv uninstall 3.12.8
```

---

## 9. 🐳 Docker Engine, Docker Compose & Containers

Instalação oficial do Docker Engine com o plugin compose moderno:

```bash
# Prepara chaves e repositório oficial Docker
sudo apt install -y ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt update
sudo apt install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

# Configura permissão para rodar Docker sem sudo
sudo usermod -aG docker $USER
sudo systemctl enable --now docker.service
sudo systemctl enable --now containerd.service
```

---

## 10. ☁️ AWS CLI v2 & Rclone (Nuvem & Backup)

### ☁️ AWS CLI v2:
```bash
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip -o awscliv2.zip
sudo ./aws/install --update
rm -rf aws awscliv2.zip
aws --version
```

### 🔄 Rclone (Google Drive & Nexus Sync):
```bash
sudo apt install -y rclone
rclone version
```

---

## 11. 🛠️ IDEs, Editores & Inteligência Artificial

### 🌌 Antigravity IDE:
```bash
# Instalação via Snap oficial
sudo snap install antigravity-ide-snap --classic
```

### 💻 Visual Studio Code:
```bash
sudo snap install code --classic
```

### ☕ IntelliJ IDEA Community:
```bash
sudo snap install intellij-idea --classic
```

### 🚀 Postman (APIs REST):
```bash
sudo snap install postman
```

### 🐙 GitHub Desktop:
```bash
# Repositório de pacotes para GitHub Desktop no Linux
wget -qO - https://apt.packages.shiftkey.dev/gpg.key | gpg --dearmor | sudo tee /usr/share/keyrings/shiftkey-packages.gpg > /dev/null
sudo sh -c 'echo "deb [arch=amd64 signed-by=/usr/share/keyrings/shiftkey-packages.gpg] https://apt.packages.shiftkey.dev/ubuntu/ any main" > /etc/apt/sources.list.d/shiftkey-packages.list'
sudo apt update && sudo apt install -y github-desktop
```

### 👑 Antigravity CLI / Lucy (Google DeepMind Cloud & Nexus):
Instalação do CLI oficial (`agy`) e configuração do script executivo do Agente Pessoal Lucy na nuvem:
```bash
# Garante ~/.local/bin no PATH do Zsh
mkdir -p ~/.local/bin
echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.zshrc
source ~/.zshrc

# Valida o CLI oficial
agy --version

# Configuração do wrapper executivo (~/.local/bin/lucy):
cat << 'EOF' > ~/.local/bin/lucy
#!/usr/bin/env bash
printf '\e[?7h'
if [ -t 1 ] && command -v tput &>/dev/null; then
    COLS=$(tput cols 2>/dev/null || echo "")
    LINES=$(tput lines 2>/dev/null || echo "")
    [ -n "$COLS" ] && [ -n "$LINES" ] && stty cols "$COLS" rows "$LINES" 2>/dev/null || true
    [ -n "$COLS" ] && export COLUMNS="$COLS"
    [ -n "$LINES" ] && export LINES="$LINES"
fi
exec agy -i "Ative o Agente Pessoal Lucy conforme as diretrizes do Nexus." "$@"
EOF
chmod +x ~/.local/bin/lucy
```

### 🦙 Ollama & Lucy Local (Modelos de IA Locais na GPU RTX 4050):
Instalação do runner oficial do Ollama e script de execução local acelerada por hardware:
```bash
# Instala o runner oficial do Ollama
curl -fsSL https://ollama.com/install.sh | sh
ollama --version

# Configuração do wrapper local (~/.local/bin/lucy-local):
cat << 'EOF' > ~/.local/bin/lucy-local
#!/usr/bin/env bash
printf '\e[?7h'
if [ -t 1 ] && command -v tput &>/dev/null; then
    COLS=$(tput cols 2>/dev/null || echo "")
    LINES=$(tput lines 2>/dev/null || echo "")
    [ -n "$COLS" ] && [ -n "$LINES" ] && stty cols "$COLS" rows "$LINES" 2>/dev/null || true
    [ -n "$COLS" ] && export COLUMNS="$COLS"
    [ -n "$LINES" ] && export LINES="$LINES"
fi
if [ $# -eq 0 ]; then
    clear
    [ -f "$HOME/.ollama/lucy_banner.txt" ] && cat "$HOME/.ollama/lucy_banner.txt"
    exec ollama run lucy
else
    exec ollama run lucy "$@"
fi
EOF
chmod +x ~/.local/bin/lucy-local
```

---

## 12. 💬 Comunicação & Mensageria

Aplicativos essenciais para alinhamento profissional, reuniões e comunidades de devs:

### ✈️ Telegram Desktop:
```bash
sudo snap install telegram-desktop
```

### 🎮 Discord:
```bash
sudo snap install discord
```

### 💬 Whatsie (WhatsApp Web Desktop):
```bash
sudo snap install whatsie
```

### 👥 Microsoft Teams for Linux:
```bash
sudo snap install teams-for-linux
```

---

## 13. 🎨 Multimídia, Gravação & Design

### 🎥 OBS Studio (Gravação de Tela & Transmissão):
```bash
flatpak install flathub com.obsproject.Studio -y
```

### 🎬 VLC Media Player (Reprodutor Universal):
```bash
sudo snap install vlc
```

### 🎨 GIMP (Manipulação & Edição de Imagens):
```bash
sudo snap install gimp
```

### 🎵 Amberol (Player de Áudio Minimalista):
```bash
sudo snap install amberol
```

---

## 14. 🎮 Jogos & Emulação Retrô

### 🎮 Steam (Plataforma de Jogos & Proton):
```bash
flatpak install flathub com.valvesoftware.Steam -y
```

### 🕹️ Snes9x (Emulador de Super Nintendo):
```bash
flatpak install flathub com.snes9x.Snes9x -y
```

---

## 15. 🗄️ Bancos de Dados Locais (PostgreSQL & MySQL)

### 🐘 PostgreSQL:
```bash
# Repositório PGDG oficial
echo "deb http://apt.postgresql.org/pub/repos/apt $(lsb_release -cs)-pgdg main" | sudo tee /etc/apt/sources.list.d/pgdg.list
wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | gpg --dearmor | sudo tee /usr/share/keyrings/postgresql.gpg > /dev/null

sudo apt update
sudo apt install -y postgresql postgresql-contrib

# Iniciar e habilitar o serviço
sudo systemctl enable --now postgresql
```

*(Dica: Para rodar PostgreSQL via Docker Compose, consulte a pasta de infraestrutura do Nexus).*

### 🐬 MySQL Server:
```bash
sudo apt update && sudo apt install -y mysql-server
sudo systemctl enable --now mysql
sudo mysql_secure_installation
```

---

## 16. 🧹 Manutenção, Faxina & Limpeza do Sistema

### 🧹 Limpeza de Pacotes Residuais APT:
```bash
sudo apt autoremove -y
sudo apt autoclean
```

### 📦 Limpeza de Cache de Pacotes Snap Antigos:
```bash
sudo snap set system refresh.retain=2
```

### 🧩 Limpeza de Runtimes Flatpak Órfãos:
```bash
flatpak uninstall --unused -y
```

---

*Documento atualizado e sincronizado com o ecossistema de desenvolvimento de Lucivaldo Junior.*
