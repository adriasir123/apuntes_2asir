ldapsearch -x -D "cn=admin,dc=alberto,dc=gonzalonazareno,dc=org" -b dc=alberto, dc=gonzalonazareno,dc=org -W (para que pregunte contraseña)
(mostrar árbol pero de manera autenticada)
(si queremos acceder a los datos de forma anónima, aunque veremos vemos que si accedemos de forma autenticada, quitamos el -D y el -W)



echo "asdasd" | base64 -d (pasar de base64 a en claro, se puede poner el hash de la contraseña en base64 para ver el hash encriptado)


SSHA (salted SHA)
Determinados parámetros que se le añaden a la contraseña para reforzar la encriptación





ou.ldif (fichero para crear una OU o los objetos)

dn: ou=People,dc=alberto,dc=gonzalonazareno,dc=org
objectClass: organizationalUnit
ou: People

dn: ou=Groups,dc=alberto,dc=gonzalonazareno,dc=org (el nombre del objeto y donde esté no importa, lo que es fijo son los atributos que vienen con los objectClass)
objectClass: organizationalUnit
ou: Groups

(básicamente se han creado 2 OU y ningún objeto. Éstas OU y todo lo que hagamos, estarán partiendo de la base dc, domain controller es el nombre)


¿Cómo añadimos estas OU?

ldapadd -x -D "cn=admin,dc=example,dc=com" -W password -f newgroups.ldif
(se toma en cuenta el fichero con todas las OU, objetos...etc. El -D es para que la acción sea autenticada, y -W para que pida contraseña, y -F para que se tome en cuenta ese fichero en específico)

¿Cómo es la creación de las OU y los objetos a partir del fichero?
De forma secuencial. Es decir, si intentamos crear un objeto dentro de una OU que no se ha creado previamente, evidentemente daría un error

28/11/19

Decodificar base64
echo "RWZyYcOtbiBNYW5zbwo" | base64 -d


29/11/19

¿Para no tener que escribir siempre la base?
sudo nano /etc/ldap/ldap.conf

BASE	dc=adjaro,dc=gonzalonazareno,dc=org
URI (en caso de que estemos accediendo a ldap de forma remota)



¿Cambiar objectClass y añadir atributos?

ldapmodify -x -D "cn=admin,dc=adjaro,dc=gonzalonazareno,dc=org" -W
changetype: modify
Añadimos los objectClass que tenía + los nuevos
Aquí los atributos que queremos añadir


ldapsearch -x cn


2/12/19

ldapmodify -x -D "cn=admin,dc=adjaro,dc=gonzalonazareno,dc=org" -W
changetype: modify <-- Indica que se van a modificar atributos, u otras cosas
replace: mail <-- Indica que va a reemplazar el valor de un atributo
mail: user@gmail.com

Para terminar de editar, hacer ctrl+d (esto no cierra el proceso, simplemente termina de forma correcta, haciendo saber que ya se ha terminado de editar)
Esta manera de modificar un objeto es sin fichero, directamente en consola

También se puede modificar un objeto creando directamente un fichero ldif





Para ejecutar el ldif y que añada los cambios...
ldapmodify -x -D "cn=admin,dc=adjaro,dc=gonzalonazareno,dc=org" -W -f correo-pepe.ldif



zless comprimido.gz (para mostrar ficheros comprimidos)
(hay muchos comandos con z para hacer operaciones con ficheros comprimidos)


olcLogLevel 128 (son códigos numéricos y cada uno hace una cosa en específico) (se pueden sumar, y se añaden las cosas de las que se guardan logs)



/etc/ldap/slapd.d (se encuentra la información sobre el árbol de configuración de ldap)




















<!--stackedit_data:
eyJoaXN0b3J5IjpbLTk3OTcyNDQyMSwtMTA4NDQ2MTM5MywxMD
EyNzcxNTQzXX0=
-->