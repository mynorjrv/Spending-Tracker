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
