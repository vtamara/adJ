adJ
===

Distribución de OpenBSD para fomentar la construcción del Reino de Dios 
desde la educación y el respeto por la Dignidad Humana


Concepto de estas fuentes
-------------------------

Estas fuentes buscan expresar brevemente los cambios por hacer a las fuentes de OpenBSD (y al sistema donde está desarrollando) para obtener adJ.  Una vez transformado puede compilar para generar juegos de distribución, instalador y el DVD de distribución de adJ.


Prerequisitos
-------------

1. Computador con procesador de 64 bits.
2. OpenBSD o adJ para 64 bits instalados.
3. Fuentes de la versión de OpenBSD que usa descargadas e instaladas en /usr/src, /usr/src/sys, /usr/ports y /usr/src/xenocara
4. Clone estas a su directorio preferido, por ejemplo:
```
mkdir ~/comp; cd ~/comp; git clone git://github.com/pasosdeJesus/adJ.git
```


Organización de fuentes
-----------------------

- arbolcd    Directorios y archivos de un DVD instalador
- arboldd    Directorios y archivos de un adJ instalado
- arboldes   Directorios, archivos y parches para desarrollar adJ
- distribucion.sh	Archivo de comandos para generar distribución
- hdes       Herramientas para generar distribución
- tminiroot  Transforma instalador que va en DVD a español
- ver.sh.plantilla	Plantilla con variables que controlan distribucion.sh



Pasos típicos para desarrollar
------------------------------

Muchas de las operaciones típicas se controlan activando o desactivando pasos 
que el archivo de comandos distribucion.sh hará.  Los pasos se 
activan/desactivan en el archivo ver.sh (si no tiene uno ejecute 
```cp ver.sh.plantilla ver.sh```), activa un paso poniendo "s" en la 
variable asociada y lo desactiva poniendo "n".

* Enlace arboldes/usr/ports/mystuff en /usr/ports/mystuff.  ```sudo ln -s ~/comp/adJ/usr/ports/mystuff /usr/ports```
* Actualice fuentes de /usr/src (con periodicidad) para mezclar cambios de OpenBSD activando autoCVS en ver.sh y ejecutando sudo ./distribucion.sh
* Implemente mejoras a /usr/src bien como archivos de comandos (por ubicar en hdes/) que hacen cambios automáticos o bien como parches (ubicar en arboldes/usr/src)
* Actualice/mejore portes o cree nuevos en arboldes/usr/ports/mystuff.  Al agregar o retirar actualizar distribucion.sh
* Mejore programas especiales distribuidos en adJ y los portes asociados
* Actualice manuales básico, escritorio y cortafuegos/servidor, así como los portes asociados
* Compile fuentes y portes siguiendo pasos de distribucion.sh cambiando paulatinamente variables auto* en ver.sh: transforme y compile kernel (autoKernel), instalelo (autoInsKernel), transforme y compile base (autoCompBase), instale y genere .tgz del sistema base (autoDist), genere bsd.rd (autoBsdrd), transforme y compile Xenocara (autoX), instale y genere .tgz de Xenocara (autoXDist), copie juegos de instalación a subdirectorio de la forma 5.x-amd64 (autoJuegosInst), compile portes particulares (autoPaquetes), descargue otros paquetes de repositorio (autoMasPaquetes), genere juego de instalación siteXX.tgz empleando arboldd y listado lista-site (autoSite), genere textos en el instalador (autoContenido)
* Una vez con juegos de instalación, paquetes y textos listos en subdirectorio 5.x-amd64 genere imagen ISO con sudo hdes/creaiso.sh
* Pruebe ISO con QEMU, primero arrancando desde CD (en ver.sh ponga qemuboot=d) con hdes/qemu.sh.  Después de instalar pruebe arrancando desde disco (en ver.sh ponga qemuboot=c)
* Envie sus mejoras a github --respecto a ramas mantenemos una rama para cada versión publicada (e.g ADJ_5_2) en la que eventualmente se aplicarán actualizaciones de seguridad para esa versión, la versión en desarrollo se mantiene en la rama Master.

