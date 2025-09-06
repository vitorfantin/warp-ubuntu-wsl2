# 🚀 Instalação do Warp Terminal no Ubuntu

Este guia mostra como instalar o [Warp Terminal](https://www.warp.dev)
no **Ubuntu** com suporte a **atualizações automáticas** via `apt`, além
de configurá-lo como **terminal padrão** do sistema (`Ctrl+Alt+T`).

------------------------------------------------------------------------

## 📥 Instalação via Repositório Oficial

### 1. Instalar pré-requisitos

``` bash
sudo apt-get install wget gpg
```

### 2. Baixar e instalar a chave GPG corretamente

``` bash
wget -qO- https://releases.warp.dev/linux/keys/warp.asc | gpg --dearmor > warpdotdev.gpg
sudo install -D -o root -g root -m 644 warpdotdev.gpg /etc/apt/keyrings/warpdotdev.gpg
rm warpdotdev.gpg
```

### 3. Adicionar o repositório oficial válido

``` bash
sudo sh -c 'echo "deb [arch=amd64 signed-by=/etc/apt/keyrings/warpdotdev.gpg] https://releases.warp.dev/linux/deb stable main" > /etc/apt/sources.list.d/warpdotdev.list'
```

### 4. Atualizar pacotes e instalar Warp

``` bash
sudo apt update
sudo apt install warp-terminal
```

------------------------------------------------------------------------

## 🔄 Atualização Automática

Com o repositório configurado, o Warp será atualizado junto com o
sistema:

``` bash
sudo apt upgrade
```

------------------------------------------------------------------------

## 🖥️ Definir Warp como Terminal Padrão

### 1. Registrar o Warp como opção de terminal (se necessário)

``` bash
sudo update-alternatives --install /usr/bin/x-terminal-emulator x-terminal-emulator /usr/bin/warp-terminal 50
```

### 2. Selecionar o Warp

``` bash
sudo update-alternatives --config x-terminal-emulator
```

Escolha o número correspondente ao **warp-terminal**.

------------------------------------------------------------------------

## ✅ Testar

Pressione **`Ctrl+Alt+T`** → o **Warp Terminal** deve abrir 🚀

------------------------------------------------------------------------

## 🔙 Reverter para o GNOME Terminal (ou outro)

Caso queira voltar para o terminal anterior, basta rodar novamente:

``` bash
sudo update-alternatives --config x-terminal-emulator
```

E escolher o **gnome-terminal** ou outro de sua preferência.
