# Ambiente de desenvolvimento web no Debian KDE
Neste repositório compartilho meu ambiente de desenvolvimento web no Linux Debian KDE, desde a instalação do Sistema Operacional, configurações básicas, instalção de linguagens, softwares e etc.




**Imagem do Neovim aberto com codigo javascript no Debian KDE personalizado**




## Instalação do Debian KDE e configurações básicas

Meu notebook é um Lenovo Thinkpad E431 e ele utiliza um modulo wifi proprietário, então os drivers do mesmo devem ser instalados após a instalação do Sistema Operacional, pois o Linux usa somente drivers de software livre por padrão. O modulo Wifi que ele possui é o Broadcom BCM43142. Pesquisando em alguns foruns e comunidades Linux, achei os comandos de instalação para o Debian:

`su`

`apt install dkms linux-headers-$(uname -r|sed 's,[^-]*-[^-]*-,,') broadcom-sta-dkms`

`sudo modprobe -r b44 b43 b43legacy ssb brcmsmac bcma`

`sudo modprobe wl`

Eu também sofria com problemas de internet no Linux, principalmente nas atualizações de repositórios via terminal e as vezes na navegação Web. Novamente realizando pesquisas em foruns e comunidades Linux achei uma solução, utilizar o dns do google:

`sudo nano /etc/NetworkManager/NetworkManager.conf`

Adicione *dns=none* na parte [main] do arquivo.

`sudo su -`

`mv /etc/resolv.conf /etc/bkp-link-resolv.conf`

`echo "nameserver 8.8.8.8" > /etc/resolv.conf`

`exit`

Outra configuração que realizo após a instalação é dimuir a frequência de uso da memória Swap, pois ela é uma memória mais lente, então deixo ela somente para emergências. Além de que fazer Swap em SSD, pode reduzir a vida útil do mesmo:

`sudo nano /etc/sysctl.conf`

Adicione a seguinte linha ao arquivo:

`vm.swappiness=1`

Configurar o sudo no Debian (não vem como padrão igual outras distros)

Atualizar repositórios:

```
sudo apt update && sudo apt upgrade -y

sudo apt install git zsh curl neovim neofetch htop tilix tmux

$ git config --global user.name "John Doe"

$ git config --global user.email johndoe@example.com

```

Eu também personalizo o KDE como mostrado [neste repositório](https://www.google.com).

## Instalação das linguagens de programação

Primeiro iremos instalar o NVM (Node Version Manager):

`curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.36.0/install.sh | bash`

Reinicie o terminal e confira se o NVM foi instalado corretamente com:

`nvm -v`

Agora vamos instalar o node.js e com isso o npm também já é instalado:

`nvm ls-remote`

Selecione a versão LTS mais recente:

`nvm install <versão>`

Agora testamos se tudo foi instalado corretamente:

`node -v`

`npm -v`

## Dotfiles

* Tilix (Tema, settings) - Exportar as cores como um tema
* Tmux (dotfiles)
* ZShell (tema, zshrc)
* Vim (init.vim, comando de instalação do vim-plug)
* VS Code (settings.json, dica da extensão settings sync)

## Ainda será documentado

* Falta ainda definir todos os arquivos (temas e plugins) imagem na introdução (linha 7), link do repositório da personalização do KDE (linha 54)
* Instalador de programas automatizado (install.sh) (linguagens de programacao, zsh, chrome, vs code, tilix, spotify, e os outros aqui listados)
* Meu site (talvez começar com o GitHub pages)
