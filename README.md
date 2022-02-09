# CiscoPhones
Migracion a asterisk de telefonos Cisco 3905 y 7821.

Luego de mucho trabajo (Gracias Fabian Oyarce!), pude dejar operativos estos modelos de telefonos funcionando en centrales asterisk.
No importa si es asterisk puro, o una distro basada en asterisk tipo VITAL-PBX, funcionan perfecto.

Pasos a seguir:

1 - En principio, vamos a necesitar un servidor TFTP, en linux puede usarse el servicio de xnetd, funciona muy bien.
En el directorio, debemos copiar los archivos de este repositorio, teniendo en cuenta de descomprimir el archivo que termina en 001, ya que por un limite de tamaño de 25 Mb. por archivo de git tuve que fraccionarlo en varios archivos.
Se debe copiar la estructura tal cual esta, con la carpeta spanish_colombia en la raiz del tftp, respetando los archivos que contenga, los cuales les cambia el idioma de ingles a español a los telefonos.
Una vez descomprimidos, se pueden borrar los archivos con extension 001, 002 y 003.

2 - En el telefono, debemos seguir los pasos de este video, https://www.youtube.com/watch?v=zAYvfDKlPLc&t=1s , presisamente en el minuto 7:26 comienza la configuracion en cuestion. Tanto para los modelos 3905 o 7821 las opciones del menu son identicas. Este paso puede automatizarse, si se incluye en el DHCP la opcion 150, la cual le indica al telefono la direccion ip del servidor TFTP. Tener en cuenta, que es necesario poner dicha direccion ip en hexadecimal, por ejemplo, si la direccion ip del servidor TFTP es 192.168.0.100, en hexadecimal es 0xc0a80064. En internet hay varias calculadoras para hacer la conversion.

3 - Crear las extensiones en el asterisk.

4 - Renombrar los archivos SEP[MAC_3905].cnf.xml o SEP[MAC_7821].cnf.xml segun el modelo, cambiando lo que esta entre corchetes con la mac del telefono, de esta forma:

SEP11F32F7B87.cnf.xml (siempre las letras en mayusculas hasta el primer punto, tal cual esta en el ejemplo).

5 - Modificar el archivo en cuestion con los datos de la cuenta creada en el asterisk, segun corresponda. No modificar otros valores, a no ser que se sepa lo que se esta modificando. Los valores que yo fui descubriendo investigando, estan informados con comentarios.

6 - Una vez que el TFTP server este configurado en los telefonos, de forma manual o via DHCP, los mismos actualizaran al firmware correspondiente (si no se desea esto, eliminar los archivos con extension .loads y los archivos a los cuales se hace referencia en estos archivos .loads), se aprovisionaran con los datos especificados en los archivos cnf.xlm y luego de un par de reinicios, deben quedar registrados contra el asterisk.

