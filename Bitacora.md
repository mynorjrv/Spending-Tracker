# Commandos de waydroid e info

Waydroid al parecer conteneriza un sistema Android.

Para instalar sólo utilizo

```Bash
sudo dnf install waydroid
```

Antes de inicial hay que agregar el System OTA y el Vandor OTA. En Fedora, después de intalar, inicio Waydroid desde el menú de aplicaciones y procedo a instalar usando los links de la documentación.

La documentación está en https://docs.waydro.id/usage/install-on-desktops

Para iniciar el contenedos y mostrar la interfaz:

```Bash
sudo waydroid init
waydroid session start
waydroid show-full-ui
```

Para detener el contenedor puedo usar:

```Bash
waydroid session stop
sudo waydroid container stop
```

Pero al parecer no puedo sólo eliminar el contenedor. Después de correr los dos comandos anteriores puedo desinstalar waydroid con

```Bash
sudo dnf remove waydroid
```

Luego tengo que reiniciar y hacer

```Bash
sudo rm -rf /var/lib/waydroid /home/.waydroid ~/waydroid ~/.share/waydroid ~/.local/share/applications/*android* ~/.local/share/waydroid
```

Waydroid al parecer utiliza `lxc` (Linux containers). Para ver el status y ver los contenedor corriendo puedo usar:

```Bash
waydroid status
lxc list
```

# Trabajando en una VM de Ubuntu

Mmmmmm no me gustó waydroid, así que intentaré instalar Android Studio y Flutter en una VM de Ubuntu. Al parecer, Flutter se puede intalar en Ubuntu y Debian, por eso lo probaré en la VM.

## Instalando Android studio

Para instalar Android studio estpy siguiendo las instrucciones de 

<https://developer.android.com/studio/install>

que te manda a descargarlo a 

<https://developer.android.com/studio>.

Y ya empezaron con sus cosas de aceptar la licensia :) pero meh, esa es la intencion ahora.

Del segundo link descargo un .tar.gz y ahora si puedo seguir las instrucciones.


Antes de instalar android studio hay que instalar librerías de 32 bits, pero no se pueden instalar por default al parecer. Estaba leyendo en

<https://askubuntu.com/questions/1304803/ubuntu-20-04-install-both-32-bit-and-64-bit-libraries>

y en 

<https://unix.stackexchange.com/questions/12956/how-do-i-run-32-bit-programs-on-a-64-bit-debian-ubuntu/541354#541354> 

que hay que habilitar la arquitectura.

Para imprimir las arquitecturas uso 

```Bash
dpkg --print-architecture
dpkg --print-foreign-architectures
```

Esto debería imprimir `amd64` y `i386` pero no me me imprimió la segunda.


Aparentemente a correr programas de una arquitectura en otra se le llama MultiArch y se menciona en 

<https://help.ubuntu.com/community/MultiArch>

pero no menciona cómo puedo habilitar la otra arquitectura xd

Pero según el link de stackexchange, la arquitectura se agrega como 

```Bash
sudo dpkg --add-architecture i386
sudo apt-get update
```

Y luego instalo la librería como 

```Bash
sudo apt-get install libXX:i386
```

Y ahora sí aparece como arquitectura foránea. 

Como dato curioso, dpkg es un package manager de debian y supongo que significa Debian PacKaGe.

Ahora sí, instalo las dependencias con

```Bash
sudo apt-get install libc6:i386 libncurses5:i386 libstdc++6:i386 lib32z1 libbz2-1.0:i386
```

JAJAJAJAJAJAJA yyy sigo sin poder instalar. Mentira, no había hecho update, pero no encuentra libncurses5:i386

Según 

<https://askubuntu.com/questions/1252062/how-to-install-libncurses-so-5-in-ubuntu-20-04>

el problema es que libncurses está en los paquetes **universe**. Entonces primero tendría que hacer

```Bash
sudo add-apt-repository universe
sudo apt-get install libncurses5 libncurses5:i386
```

Y noup... No funcionó. Weno a probar mañana.

Intenté lo de 

https://askubuntu.com/questions/1367038/failed-to-download-libncurses5

pero no funcionó.

## Instalando android studio pero en Ubuntu 22.04

Porque no pude xd y al parecer en 22.04 es más fácil xd 

Uy siiii xd ahora pude instalar de un solo 

```Bash
sudo apt-get install libc6:i386 libncurses5:i386 libstdc++6:i386 lib32z1 libbz2-1.0:i386
```

Soooo toca instalar android studio.

Para decomprimir pero unzip no hace la chamba para -tar.gz sooooo leí de 

<https://askubuntu.com/questions/25347/what-command-do-i-need-to-unzip-extract-a-tar-gz-file> 

y usé los comandos 

```Bash
tar -xf android-studio-2024.3.1.15-linux.tar.gz
sudo mv android-studio /usr/local/
```

Ahora ejecuto el programa

```Bash
cd /usr/local/android-studio/bin/
sh studio.sh
```

La instalación parace ir bien. Menciona que se puede usa VM acceleration y manda a 

<https://developer.android.com/studio/run/emulator-acceleration?utm_source=android-studio#vm-linux>

... qué difícil instalar esta cosa xdxdxd
pero ya está descargando cosas

Yyyyy instalado. Ahora me sugiere pasarme a un native launcher y me manda a 

<https://youtrack.jetbrains.com/articles/SUPPORT-A-56/Switch-to-a-native-launcher-notification>

Al parecer se puede inciar la aplicación de manera "nativa" usanod 

```Bash
./studio
```

En lugar del `.sh`. Ahora crearé el ícono de escritorio como en las instrucciones. Se tiene que cerrar Studio y luego verificar si puedo entrar, sino hacer logout y regresar.

Pero todo bieeeeeeeeeeeeeeeeeeeen n.n Esto fue un paseo por el parque comparado a Ubuntu 24.04 xdxdxd

## Error en virtual device

Well well well, creo que aunque está funcionando bien paniquea por el espacio en disco para crear un teléfono virtual. Puedo hacer otra máquina o probar añadir espacio a esta. Otra cosa, empecé a probar el tutorial y creo que por ahora no añadiré código acá sino lo dejaré en una carpetita.

