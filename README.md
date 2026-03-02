# 🚀 Guia Completo de Pós-instalação e Customização de Pacotes no Ubuntu

## 📦 Instalar os pacotes git e npm e depois atualizar o sistema:
```bash
sudo apt update && sudo apt upgrade -y
sudo apt install git -y
sudo apt install npm -y
npm install -g typescript
tsc --version
```

## 🌐 Instalar Google Chrome:
```bash
wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
sudo dpkg -i google-chrome-stable_current_amd64.deb
sudo apt --fix-broken install -y
sudo rm google-chrome-stable_current_amd64.deb
```

## 📦 Instalar o NVM (Node Version Manager):
```bash
sudo apt install curl -y
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.1/install.sh | bash
```

### ⚡ Carregar o NVM no terminal:
```bash
source ~/.nvm/nvm.sh
```

### 🚀 Instalar a versão mais recente do Node.js:
```bash
nvm install node  # Última versão estável
nvm install --lts # Última versão LTS
```

### ⚙️ Definir uma versão específica do Node:
```bash
nvm use 22.12.0
```

## 🐍 Instalar Python a partir do código-fonte

### 📁 Extrair e entrar no diretório:
```bash
tar -xf Python-3.14.2.tar.xz
cd Python-3.14.2
```

### 🔧 Instalar depend�?ncias de compilação:
```bash
sudo apt-get install build-essential gdb lcov pkg-config \
libbz2-dev libffi-dev libgdbm-dev libgdbm-compat-dev liblzma-dev \
libncurses-dev libreadline-dev libsqlite3-dev libssl-dev \
tk-dev uuid-dev zlib1g-dev -y
```

### ⚙️ Compilar e instalar o Python:
```bash
sudo ./configure --enable-optimizations --prefix=/opt/python3.14
sudo make -j$(nproc)
sudo make altinstall
echo "alias python3.14='/opt/python3.14/bin/python3.14'" >> ~/.bashrc
source ~/.bashrc
```

### ✅ Verificar a instalação:
```bash
python3.14 --version
```

### 📦 Instalar depend�?ncias com pip:
```bash
python3.14 -m pip install --upgrade pip
 /opt/python3.14/bin/python3.14 -m ensurepip --upgrade
```

## 📦 Instalando o Pyenv
```bash
curl -L https://github.com/pyenv/pyenv-installer/raw/master/bin/pyenv-installer | bash
```

### ⚙️ Configurando o Pyenv no .bashrc
```bash
echo -e '\nexport PYENV_ROOT="$HOME/.pyenv"\n[[ -d $PYENV_ROOT/bin ]] && export PATH="$PYENV_ROOT/bin:$PATH"\neval "$(pyenv init -)"' >> ~/.bashrc
source ~/.bashrc
```

### 🐍 Instalando Python via Pyenv
```bash
pyenv update
pyenv install -l
pyenv install 3.14.2
pyenv global 3.14.2
```

### 📦 Instalar Maven
```bash
sudo apt install maven -y
mvn -version
```

## ☕ Instalar Java (OpenJDK):
```bash
sudo apt install openjdk-21-jdk -y
java -version
```

## 🐳 Instalar Docker:
```bash
sudo apt-get install ca-certificates curl -y
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt update
sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin -y
```

### ⚙️ Configurar permissões do Docker:
```bash
sudo groupadd docker
sudo usermod -aG docker $USER
newgrp docker
docker run hello-world
sudo systemctl start docker
sudo systemctl enable docker
sudo systemctl enable docker.service
sudo systemctl enable containerd.service
```

### 🔧 Ajustar permissões adicionais:
```bash
sudo chown "$USER":"$USER" /home/"$USER"/.docker -R
sudo chmod g+rwx "$HOME/.docker" -R
sudo systemctl start docker
sudo systemctl enable docker
sudo systemctl enable docker.service
sudo systemctl enable containerd.service
```

## 📦 Instalar Docker Compose:
```bash
sudo curl -L "https://github.com/docker/compose/releases/download/1.29.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
sudo chmod +x /usr/local/bin/docker-compose
docker-compose --version

sudo apt install -y docker-compose-plugin
docker-compose --version
```

## ☁️ Instalar AWS CLI v2
```bash
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip" && unzip -o awscliv2.zip && sudo ./aws/install --update && aws --version
```

## 🛠️ Outros aplicativos para instalar

### 📦 Instalar Flatpak e OBS Studio 🎥
```bash
sudo apt install flatpak
sudo apt install gnome-software-plugin-flatpak
flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo
flatpak install flathub com.obsproject.Studio -y
```

### 🎧 Instalar Blanket (sons de fundo)
```bash
flatpak install flathub com.rafaelmardojai.Blanket -y
flatpak run com.rafaelmardojai.Blanket (se não aparecer o ícone para executar)
```

### 💻 VS Code
```bash
sudo snap install code --classic
```

### 🧠 IntelliJ IDEA
```bash
sudo snap install intellij-idea-community --classic
```

### 🌍 Eclipse
```bash
sudo snap install eclipse --classic
```

### 🔺 Angular CLI
```bash
sudo npm install -g @angular/cli
ng version
```

### 📱 Ionic CLI
```bash
sudo npm install -g @ionic/cli
ionic --version
```

### 🦋 Flutter via Snap
```bash
sudo snap install flutter --classic
```

## 🎯 Outros aplicativos úteis
```bash
sudo apt install gdebi -y
sudo apt install gnome-tweaks -y
sudo snap install vlc --classic
sudo snap install amberol --classic
```

## 🔄 Limpar pacotes antigos
```bash
sudo apt autoremove -y
sudo apt autoclean
```

## 🧩 Zsh + Oh My Zsh + Spaceship Prompt - Ubuntu 22.04

### ⚡ 1. Instalar Zsh

```bash
sudo apt update
sudo apt install zsh -y
which zsh
chsh -s /usr/bin/zsh
```

Reinicie o terminal ou faça logout/login.

---

### 🛠️ 2. Instalar Oh My Zsh

```bash
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

---

### 🚀 3. Instalar Spaceship Prompt

```bash
git clone https://github.com/spaceship-prompt/spaceship-prompt.git "$ZSH_CUSTOM/themes/spaceship-prompt" --depth=1
ln -s "$ZSH_CUSTOM/themes/spaceship-prompt/spaceship.zsh-theme" "$ZSH_CUSTOM/themes/spaceship.zsh-theme"
```

Edite `nano ~/.zshrc`:

```bash
ZSH_THEME="spaceship"
```

---

### 🔹 4. Plugins essenciais

#### Autosuggestions

```bash
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```

#### Syntax Highlighting

```bash
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```

No `nano ~/.zshrc`:

```bash
plugins=(git zsh-autosuggestions zsh-syntax-highlighting)
```

---

### 🔄 5. Recarregar configurações

```bash
source ~/.zshrc
```

---

### 🎉 Pronto!

* Sugestões automáticas de comandos
* Destaque de sintaxe
* Prompt informativo e personalizável

#### 💡 Dica

Atualizar Oh My Zsh:

```bash
omz update
```


## 🐬 Instalar MySQL Server

### 📦 Instalar MySQL Server:
```bash
sudo apt update
sudo apt install mysql-server -y
```

### 🔧 Verificar o status do MySQL:
```bash
sudo systemctl status mysql
```

### 🔧 Configurar o MySQL (opcional):
```bash
sudo mysql_secure_installation
```

y 2 y y y y


### 🔑 Acessar o MySQL:
```bash
sudo mysql -u root -p
```

## 🐘 Instalar PostgreSQL 17

### 📥 Adicionar o repositório oficial (PGDG):
```bash
echo "deb http://apt.postgresql.org/pub/repos/apt jammy-pgdg main" | sudo tee /etc/apt/sources.list.d/pgdg.list
wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | gpg --dearmor | sudo tee /usr/share/keyrings/postgresql.gpg > /dev/null
```

### 🔄 Atualizar os pacotes:
```bash
sudo apt update
```

### 🐘 Instalar o PostgreSQL Server (versão 17):
```bash
sudo apt install postgresql-17 postgresql-client-17 -y
```

### 🔧 Verificar o status do PostgreSQL:
```bash
sudo systemctl status postgresql
```

### ⚡ Habilitar o serviço ao iniciar:
```bash
sudo systemctl enable postgresql
```

### 🚪 Acessar o PostgreSQL com o usuário padrão:
```bash
sudo -i -u postgres
psql
```

### 🔑 Acessar o PostgreSQL diretamente:
```bash
sudo -u postgres psql
```

### ✅ Verificar a versão instalada:
```bash
psql --version
```

### 🔍 Verificar o binário da versão 17 diretamente:
```bash
/usr/lib/postgresql/17/bin/psql --version
```
