# 🐧 Ubuntu Dev Workstation — Setup Técnico & Pós-Instalação

<p align="center">
  <img src="https://img.shields.io/badge/OS-Ubuntu%2026.04.1%20LTS-E95420?style=for-the-badge&logo=ubuntu&logoColor=white" alt="Ubuntu" />
  <img src="https://img.shields.io/badge/Shell-Bash%20%7C%20Zsh-4EAA25?style=for-the-badge&logo=gnu-bash&logoColor=white" alt="Shell" />
  <img src="https://img.shields.io/badge/Docker-Engine%20%26%20Compose-2496ED?style=for-the-badge&logo=docker&logoColor=white" alt="Docker" />
  <img src="https://img.shields.io/badge/Java-21%20LTS-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white" alt="Java" />
  <img src="https://img.shields.io/badge/Go-1.22%2B-00ADD8?style=for-the-badge&logo=go&logoColor=white" alt="Go" />
  <img src="https://img.shields.io/badge/Cloud-AWS%20CLI%20v2-232F3E?style=for-the-badge&logo=amazon-aws&logoColor=white" alt="AWS" />
  <img src="https://img.shields.io/badge/License-MIT-007ACC?style=for-the-badge" alt="License" />
</p>

---

## 📌 Visão Geral

Este repositório reúne um guia consolidado e padronizado de **pós-instalação, automação de ambiente e configuração de workstations Ubuntu** voltado para Engenharia de Software Back-end, Cloud/DevOps e Produtividade.

O foco central é transformar uma instalação limpa do Ubuntu em uma máquina de alta performance, estável e pronta para compilação, containerização e operação corporativa, eliminando retrabalho de setup manual.

---

## 🧭 Rotas de Shell Disponíveis

O repositório oferece **duas abordagens independentes de personalização**. Escolha a que melhor atende ao seu fluxo de trabalho:

| Rota | Documento | Foco | Destaques |
| :--- | :--- | :--- | :--- |
| **Bash Nativo** | [Customização_Ubuntu_padrao_bash.md](Customização_Ubuntu_padrao_bash.md) | Simplicidade e Estabilidade | Mantém o shell padrão do Ubuntu com aliases produtivos, sem overhead de plugins externos. |
| **Zsh + Oh My Zsh** | [Customização_Ubuntu_zsh_oh_myZsh.md](Customização_Ubuntu_zsh_oh_myZsh.md) | Produtividade e Visual Moderno | Tema Spaceship, autossugestão de comandos, realce de sintaxe em tempo real e plugins do ecossistema Zsh. |

---

## 🛠️ Matriz do Toolchain & Tecnologias

O provisionamento cobre todo o ciclo de ferramentas necessárias para desenvolvimento profissional:

### 1. Runtimes & Linguagens
* **Java 21 LTS:** OpenJDK para desenvolvimento corporativo e Spring Boot.
* **Go (Golang 1.22+):** Compilação de alta performance, microserviços e CLIs.
* **Node.js (LTS):** Gerenciado via NVM (Node Version Manager) para isolamento de versões.
* **Python 3.12+:** Gerenciado via Pyenv para virtual environments limpos.

### 2. Infraestrutura & Nuvem
* **Docker Engine & Docker Compose:** Instalação oficial via repositório APT da Docker (sem sudo obrigatório).
* **AWS CLI v2:** Integração com serviços de nuvem e automações de infra.
* **Rclone:** Sincronização incremental e rotinas de backup com armazenamento em nuvem.

### 3. IDEs, IA & Produtividade
* **IDEs:** Antigravity IDE, Visual Studio Code e IntelliJ IDEA Community.
* **Inteligência Artificial:** Ollama (execução local acelerada por GPU) e Antigravity CLI (`agy`).
* **Testes de API & Git:** Postman e GitHub Desktop.
* **Mensageria:** Telegram Desktop, Discord e Whatsie.

### 4. Manutenção & Saúde do SO
* Scripting de limpeza e remoção de órfãos para **APT**, **Snap** e **Flatpak**.

---

## 🚀 Fluxo Recomendado de Execução

Ao configurar uma máquina do zero, execute as etapas nesta ordem lógica:

```text
[1. Update do SO] ──> [2. Escolha do Shell] ──> [3. Runtimes (Java/Go/Node/Python)]
                                                            │
[6. IDEs & IA]    <── [5. Cloud & Backup]   <── [4. Docker & Containers]
       │
       ▼
[7. Limpeza & Validação Final]
```

1. **Atualização Base:** Atualize índices de pacotes (`apt update && apt upgrade`).
2. **Seleção de Shell:** Abra o guia do [Bash](Customização_Ubuntu_padrao_bash.md) ou do [Zsh](Customização_Ubuntu_zsh_oh_myZsh.md).
3. **Linguagens:** Instale compiladores e gerenciadores de versão em etapas separadas.
4. **Virtualização:** Configure Docker Engine e permissões do grupo do usuário.
5. **Nuvem:** Configure credenciais da AWS e destinos no Rclone.
6. **Workspace:** Instale editores, IDEs e runners locais de IA.
7. **Sanitização:** Execute a rotina de faxina para manter o disco limpo e enxuto.

---

## 🗂️ Estrutura de Arquivos

```text
.
├── Customização_Ubuntu_padrao_bash.md   # Guia detalhado para Shell Bash nativo
├── Customização_Ubuntu_zsh_oh_myZsh.md  # Guia detalhado para Shell Zsh + Oh My Zsh
├── README.md                            # Documentação principal e índice técnico
└── LICENSE                              # Licença MIT de uso e distribuição
```

---

## 💡 Recomendações Técnicas

* **Backup prévio:** Sempre faça backup de `~/.bashrc`, `~/.zshrc` e variáveis de ambiente antes de customizações profundas de PATH.
* **Permissões Docker:** Adicione o usuário ao grupo `docker` e reinicie a sessão antes de rodar containers sem privilégios de superusuário.
* **Instalação Modular:** Prefira instalar cada stack em blocos independentes para isolar eventuais falhas de dependência de rede ou repositório.

---

## 👨‍💻 Autor & Contato

<div align="center">
  <pre>
======-::--=-=-----=-.:..--.-+++*+
======-:-----:... ..::.--:..-++=--  👤 AUTOR:       Lucivaldo Junior (Luci Junior)
+=====-:-:.     .    :-=++=-==-:=*  🐧 SISTEMA:     Ubuntu 26.04.1 LTS (Workstation)
+++===-::    =#%@@%#. --==+++==-=+  ────────────────────────────────────────────────
++++==-.   .::=+*@@@%-.:-=====-..:  🧠 PAPEL:       Tech Lead & Arquiteto Back-end
**++++:   .++:==:%=:+#..:-====:..:  ☕ STACK:       Java 21 | Go 1.22+ | Docker
======:   .+##+--#***@-.::====---=  ☁️ NUVEM:       AWS | Docker Swarm | Linux
      ...  .===++-=*##...:=====+++  🛠️ TOOLCHAIN:   Spring Boot | PostgreSQL | Redis
        ..  :==+*#%*#*. .-======++  🤖 ECOSSISTEMA: Nexus & Lucy (Automação & IA)
 ...     .  -=+**#%%#%%*+=-===++==  🐙 GITHUB:      https://github.com/luci-jr
**++.    ::..==+=+*##%%%%%++##**#=  💼 LINKEDIN:    https://linkedin.com/in/lucivaldo-junior
####-     --::.  =.:-==*##%*--:+#%  ────────────────────────────────────────────────
***#-      -=-:.:+    --+##%#:  .-  "Fala, irmão! O que tu queres codar?"
*#*#.       .::..      .--:=#%=     Sempre aberto a conexões técnicas e novos projetos.
***-                    .::==*#=    📍 Belém, Pará — Brasil
++-                      :--:-=*+.  📧 lucivaldo.junior.dev@gmail.com
=-                    .-+-:-+=-:-+  🛰️ Telegram: @luci_junior
  </pre>
</div>

---

## 📄 Licença

Este projeto está licenciado sob os termos da licença [MIT](LICENSE).
