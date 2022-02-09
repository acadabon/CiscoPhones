# CiscoPhones
Migracion a asterisk de telefonos Cisco 3905 y 7821

Luego de mucho trabajo, pude dejar operativos estos modelos de telefonos funcionando en centrales asterisk.
No importa es asterisk puro, o una distro basada en asterisk tipo VITAL PBX, funcionan perfecto

Pasos a seguir:

En principio, vamos a necesitar un servidor TFTP, en linux puede usarse el servicio de xnetd, funciona muy bien.
En el directorio, debemos copiar los archivos de este repositorio, teniendo en cuenta de descomprimir el archivo que termina en 001, ya que por limite de 25 Mb. de git tuve que fraccionarlo en varios archivos.

