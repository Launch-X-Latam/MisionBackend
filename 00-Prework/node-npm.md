# Instalación de Node.js

Node. js sirve para crear sitios web dinámicos muy eficientes, escritos con el lenguaje de programación JavaScript.

## Instalación en Windows

Instala Node.js desde el instalador de Windows [-> da clic aquí <-](https://nodejs.org/en/#home-downloadhead)

## Instalación en MacOS

- Puedes instalar directamente node.js con el siguiente comando ejecutandolo desde la terminal:

```bash
curl "https://nodejs.org/dist/latest/node-${VERSION:-$(wget -qO- https://nodejs.org/dist/latest/ | sed -nE 's|.*>node-(.*)\.pkg</a>.*|\1|p')}.pkg" > "$HOME/Downloads/node-latest.pkg" && sudo installer -store -pkg "$HOME/Downloads/node-latest.pkg" -target "/"
```

- También peudes instalar [Homebrew](https://brew.sh/index_es) que es un instalador de paquetes de Mac. Para ello puedes ejecutar el siguiente comando en la terminal:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Sigue las instrucciones finales del instalador de Homebrew.

```bash
brew install node
```

## Instalación en Linux

Así puedes Instalar Node.js dependiedo de tu distro:

Arch Linux

```bash
pacman -S nodejs npm
```

CentOS, Fedora y Red Hat Enterprise Linux
```bash
dnf module install nodejs:18/common
```

Ubuntu
```bash
curl -fsSL https://deb.nodesource.com/setup_19.x | sudo -E bash - &&\

sudo apt-get install -y nodejs
```

Debian
```bash
curl -fsSL https://deb.nodesource.com/setup_19.x | bash - &&\

apt-get install -y nodejs
```
FreeBSD
```bash
pkg install node
```
Gentoo
```bash
emerge nodejs
```

---

[**&#11176;** *Anterior* &#11007;](/00-Prework/mysql.md "Instalación de MySQL") 
[Siguiente **&#129042;**](/README.md "Menu principal")

---

[*Volver* **&ldca;**](/README.md "Menu principal") 
[*Subir* **&#11165;**](# "Ir al título")