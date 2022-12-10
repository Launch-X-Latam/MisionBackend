# Instalación de Git y configuración de GitHub

Git es un sistema de control de versiones distribuido, lo que significa que un clon local del proyecto es un repositorio de control de versiones completo. Estos repositorios locales plenamente funcionales permiten trabajar sin conexión o de forma remota con facilidad.

## Instalación de Git en Windows 

1. Descargar Git para Windows [-> dando clic aquí <-](https://git-scm.com/download/win)
   - Verifica que tipo de sistema operativo tienes, de 32 o 64 bits. Eso lo puedes verificar en **Configuración > Sistema > Información del sistema** y selecciona la opción correcta

2. Sigue todos los pasos predeterminados del instalador
3. Comprueba que se instalo Git correctamente abriendo un cmd simbolo de sistema ejecutando el comando ``git`` en la terminal. Si tienes como resultado lo siguiente:

![Git error](https://www.partitionwizard.com/images/uploads/articles/2021/05/git-is-not-recognized/git-is-not-recognized-1.png)

Habrá que colocar la ruta de Git en las variables de entorno de Windows. Puedes seguir este tutorial para resolver esto [-> da clic aquí <-](https://programmerclick.com/article/44141352196/).

## Instalación de Git en Mac

1. Instala [Homebrew](https://brew.sh/index_es) que es un instalador de paquetes de Mac. Para ello puedes ejecutar el siguiente comando en la terminal:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Sigue las instrucciones finales del instalador de Homebrew

2. Instala Git con Homebrew usando el siguiente comando:

```bash
brew install git
```

3. Comprueba que se instalo Git correctamente en la terminal ejecutando el comando ``git``.

## Instalación en Linux

Hay algunas distros de Linux como Kali Linux que ya tienen preinstalado Git. Sin embargo, así puedes instalarlo dependiedo de tu distro:

Debian/Ubuntu

```bash
sudo apt-get install git
```

Para Ubuntu, este PPA proporciona la última versión Git

```bash
sudo add-apt-repository ppa:git-core/ppa
sudo apt update
sudo apt install git
```

Fedora

```bash
dnf install git
```

Gentoo
```bash
emerge --ask --verbose dev-vcs/git
```

Arch Linux
```bash
pacman -S git
```

openSUSE
```bash
zypper install git
```

Mageia
```bash
urpmi git
```

Nix/NixOS
```bash
nix-env -i git
```

FreeBSD
```bash
pkg install git
```

## Instalación del SSH en tu cuenta de GitHub

1. Crea una cuenta de GitHub -> https://github.com/
2. Ve a Settings > SSH and GPG Keys
3. Sigue las instrucciones de acuerdo a tu sistema operativo:
   1. [Windows](#para-windows)
   2. [MacOs](#para-mac)
   3. [Linux](#para-linux)

### Para Windows

1. Abre Git Bash
2. Ejecuta `ls -al ~/.ssh` Para ver si hay llaves SSH presentes
3. checa la lista del directorio para ver si ya tienes una clave SSH pública. De forma predeterminada, los nombres de archivo de las claves públicas admitidas para GitHub son uno de los siguientes.
   - id_rsa.pub
   - id_ecdsa.pub
   - id_ed25519.pub

Si tienes una llave ve al paso 8

4. Si no tienes una llave generala con el siguiente comando sustituyendo el email ejemplo por el que tienes con tu cuenta de GitHub: 

```cmd
ssh-keygen -t ed25519 -C "your_email@example.com"
```

5. Sigue las instrucciones y si te pide una contraseña puedes crear una o solo darle Enter para seguir sin contraseña.
6. Inicia el agente SSH con el siguiente comando: 
```cmd
eval "$(ssh-agent -s)"
```
7. Añade tu clave privada al agente SSH con el siguiente comando:
```cmd
ssh-add ~/.ssh/id_ed25519
```

8. Copia en tu portapapeles la clave publica SSH con el siguiente comando:
```cmd
clip < ~/.ssh/id_ed25519.pub
```

9. Pegalo en la sección Settings > SSH and GPG Keys de GitHub y guarda los cambios.

### Para Mac

1. Abre Git Bash
2. Ejecuta `ls -al ~/.ssh` Para ver si hay llaves SSH presentes
3. checa la lista del directorio para ver si ya tienes una clave SSH pública. De forma predeterminada, los nombres de archivo de las claves públicas admitidas para GitHub son uno de los siguientes.
   - id_rsa.pub
   - id_ecdsa.pub
   - id_ed25519.pub

Si tienes una llave ve al paso 8

4. Si no tienes una llave generala con el siguiente comando sustituyendo el email ejemplo por el que tienes con tu cuenta de GitHub: 

```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```

5. Sigue las instrucciones y si te pide una contraseña puedes crear una o solo darle Enter para seguir sin contraseña.
6. Inicia el agente SSH con el siguiente comando: 
```bash
eval "$(ssh-agent -s)"
```
7. Añade tu clave privada al agente SSH con el siguiente comando:
```bash
ssh-add ~/.ssh/id_ed25519
```

8. Copia en tu portapapeles la clave publica SSH con el siguiente comando:
```bash
pbcopy < ~/.ssh/id_ed25519.pub
```

9. Pegalo en la sección Settings > SSH and GPG Keys de GitHub y guarda los cambios.

### Para Linux

1. Abre Git Bash
2. Ejecuta `ls -al ~/.ssh` Para ver si hay llaves SSH presentes
3. checa la lista del directorio para ver si ya tienes una clave SSH pública. De forma predeterminada, los nombres de archivo de las claves públicas admitidas para GitHub son uno de los siguientes.
   - id_rsa.pub
   - id_ecdsa.pub
   - id_ed25519.pub

Si tienes una llave ve al paso 8

4. Si no tienes una llave generala con el siguiente comando sustituyendo el email ejemplo por el que tienes con tu cuenta de GitHub: 

```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```

5. Sigue las instrucciones y si te pide una contraseña puedes crear una o solo darle Enter para seguir sin contraseña.
6. Inicia el agente SSH con el siguiente comando: 
```bash
eval "$(ssh-agent -s)"
```
7. Añade tu clave privada al agente SSH con el siguiente comando:
```bash
ssh-add ~/.ssh/id_ed25519
```

8. Copia en tu portapapeles la clave publica SSH con el siguiente comando:
```bash
cat ~/.ssh/id_ed25519.pub
```

9. Pegalo en la sección Settings > SSH and GPG Keys de GitHub y guarda los cambios.

---

[**&#11176;** *Anterior* &#11007;](/README.md "Menu principal") 
[Siguiente **&#129042;**](/00-Prework/mongo.md "Mongo")

---

[*Volver* **&ldca;**](/README.md "Menu principal") 
[*Subir* **&#11165;**](# "Ir al título")