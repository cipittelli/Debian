
# Debian: Pós-Instalação e Comandos Básicos no Terminal

![Debian Logo](https://upload.wikimedia.org/wikipedia/commons/thumb/0/0c/Debian_logo.svg/1024px-Debian_logo.svg.png)

> Guia completo para configurar, proteger e personalizar sua instalação Debian, com comandos essenciais para quem vem do Windows ou outras distribuições Linux.

---

## ✨ Sumário
- [1. Administração Geral e Atualizações](#1-administração-geral-e-atualizações)
- [2. Informações do Sistema](#2-informações-do-sistema)
- [3. Atualização do Sistema](#3-atualização-do-sistema)
- [4. Instalação de Aplicativos Importantes](#4-instalação-de-aplicativos-importantes)
- [5. Snap e Snap-store](#5-snap-e-snap-store)
- [6. Flatpak e Flathub](#6-flatpak-e-flathub)
- [7. Instalação de Arquivos .tar.xz](#7-instalação-de-arquivos-tarxz)
- [8. Administração de Segurança e Limpeza](#8-administração-de-segurança-e-limpeza)
- [9. Customizações Estéticas](#9-customizações-estéticas)
- [10. Atualizar Debian para a versão Testing](#10-atualizar-debian-para-a-versão-testing)
- [11. Hardening de Navegadores](#11-hardening-de-navegadores)
- [12. Extensões de Navegador Recomendadas](#12-extensões-de-navegador-recomendadas)
- [13. Comandos Básicos do Linux](#13-comandos-básicos-do-linux)

---

## 1. Administração Geral e Atualizações

### 1.1 Privilégio de superusuário root no terminal

```bash
su -          # Ambiente total (equivale ao C: do Windows)
sudo su       # Ambiente home (equivale ao D: do Windows)
sudo -i       # Outro modo para ambiente root completo
```

> 🔗 [Documentação oficial do Debian sobre sudoers](https://wiki.debian.org/sudo)
> _Quando recém-instalado, o terminal do debian necessita da permissão de root via **su -** para instalar apps; Por isso é Recomendável incluir o usuário criado na instalação como **“sudoer”**_

### 1.2 Tornar um usuário "sudoer"
```bash
su -
sudo nano /etc/sudoers
```
Abaixo da linha `# User privilege specification`, adicione:
```bash
nome-de-usuario ALL=(ALL:ALL) ALL
```

Feedback de senha com asteriscos. Abaixo da linha **# Cmnd alias specification**, adicione:
```bash
Defaults pwfeedback
```

Salve com `CTRL+X`, depois `Y`, depois `ENTER`.

---

## 2. Informações do Sistema
```bash
uname -r            # Kernel instalado
lsb_release -a      # Nome do sistema, versão e codinome
ls -ld /            # Data de instalação da distro
```

### TLDR - Manuais resumidos de comandos
```bash
sudo apt install tldr
tldr --update
tldr ip
```

### Melhorar desempenho com a memória swap
```bash
sudo nano /etc/sysctl.conf
vm.swappiness=50
```

---

## 3. Atualização do Sistema
```bash
flatpak update
sudo apt update
sudo apt upgrade -y
sudo apt full-upgrade -y
sudo apt dist-upgrade -y
sudo apt install firmware-linux
```

### Atualizações automáticas de segurança (opcional)
```bash
sudo apt install unattended-upgrades
sudo dpkg-reconfigure unattended-upgrades
```

### Corrigir erros na atualização
```bash
sudo apt --fix-broken install -y
sudo apt update -y
```

> ℹ️ O app **Software & Updates** pode substituir a maioria dos comandos de atualização.

---

## 4. Instalação de Aplicativos Importantes
```bash
sudo apt install gufw clamtk rkhunter stacer qbittorrent curl git gdebi timeshift gparted -y
sudo ufw enable
```

---

## 5. Snap e Snap-store

### Instalar Snapd e habilitar
```bash
sudo apt install snapd
sudo systemctl enable snapd
sudo systemctl start snapd
sudo ln -s /var/lib/snapd/snap /snap
```

### Instalar Snap Store (GUI)
```bash
sudo snap install snap-store
sudo reboot
```

> 🎨 Para instalar: Gemini Desktop, Google Desktop Apps, etc.

---

## 6. Flatpak e Flathub
```bash
sudo apt install flatpak
flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
```

### Remover Firefox ESR e instalar alternativos:
```bash
sudo apt remove firefox-esr -y
sudo apt autoremove -y
```

### Instalar apps populares via Flatpak
```bash
flatpak install flathub io.gitlab.librewolf-community -y
flatpak install flathub org.mozilla.firefox -y
flatpak install flathub com.google.Chrome -y
flatpak install flathub md.obsidian.Obsidian -y
flatpak install flathub com.spotify.Client -y
flatpak install flathub org.torproject.torbrowser-launcher -y
```

### Remoção geral:
```bash
flatpak uninstall --all
flatpak uninstall --unused
```

---

## 7. Instalação de Arquivos .tar.xz (exemplo: Firefox)
```bash
cd ~/Downloads
tar xJf firefox-140.0.2.tar.xz
sudo mv firefox /opt/
sudo ln -s /opt/firefox/firefox /usr/local/bin/firefox
sudo nano /usr/share/applications/firefox.desktop
```

Conteúdo do arquivo `.desktop`:
```ini
[Desktop Entry]
Name=Firefox Browser
Comment=Browse the Web
Exec=/opt/firefox/firefox %u
Terminal=false
Type=Application
Icon=/opt/firefox/browser/chrome/icons/default/default128.png
Categories=Network;WebBrowser;
StartupNotify=true
```

---

## 8. Administração de Segurança e Limpeza

### Escanear vírus:
```bash
sudo clamscan -r
```

### Verificar Rootkits:
```bash
sudo rkhunter --update
sudo rkhunter --check
```

### Limpar cache:
```bash
sudo sync
sudo sysctl -w vm.drop_caches=3
```

### Limpeza do sistema:
```bash
sudo apt autoremove -y
sudo apt autoclean
```

---

## 9. Customizações Estéticas (GRUB, Boot, GTK)

### Grub Customizer
```bash
sudo add-apt-repository ppa:danielrichter2007/grub-customizer
sudo apt install grub-customizer
```

### Plymouth Theme
```bash
sudo apt install plymouth-themes
sudo plymouth-set-default-theme -l
```

### Tema WhiteSur (estilo macOS)
```bash
git clone https://github.com/vinceliuice/WhiteSur-gtk-theme.git --depth=1
cd WhiteSur-gtk-theme
./install.sh
./install.sh -l -c light
```

---

## 10. Atualizar Debian para a versão Testing (avancado)
```bash
su -
nano /etc/apt/sources.list
# Substituir "bookworm" por "testing"
sudo apt update && sudo apt upgrade && sudo apt full-upgrade && sudo reboot
```

> ⚠️ Recomendado backup com Timeshift antes!

---

## 11. Hardening de Navegadores

### Firefox e derivados (`about:config`)
- `telemetry.enabled` → false
- `media.peerconnection.enabled` → false
- `privacy.resistFingerprinting` → true
- `identity.fxaccounts.enabled` → false

### Sandbox Flatpak (Firefox Flatpak)
```bash
sudo flatpak override org.mozilla.firefox --filesystem=xdg-config/gtk-3.0
```

---

## 12. Extensões de Navegador Recomendadas

- **CanvasBlocker**
- **uBlock Origin**
- **Privacy Badger**
- **Bitwarden**
- **Firefox Relay** (Opcional)
- **Dark Reader** (Conforto visual)

---

## 13. Comandos Básicos do Linux
```bash
ls -A                # Lista arquivos, incluindo ocultos
cd <pasta>           # Entra na pasta
cd ~                 # Volta para Home
clear ou CTRL+L      # Limpa o terminal
sudo apt update      # Atualiza lista de pacotes
man apt              # Mostra manual
mkdir pasta          # Cria nova pasta
rmdir pasta          # Remove pasta vazia
rm -r pasta          # Remove pasta com arquivos
apt-cache depends nome-do-app  # Dependências
```

---

> 📅 Atualizado em Julho de 2025  
> 🌐 Manual adaptado para novos usuários Linux Debian/Ubuntu com segurança, performance e personalização visual como prioridade.
