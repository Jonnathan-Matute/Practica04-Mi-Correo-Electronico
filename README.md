# Resolución de problemas sobre PHP y MySQL

# OBJETIVO ALCANZADO:
•	Entender y organizar de una mejor manera los sitios de web en Internet 

•	Diseñar adecuadamente elementos gráficos en sitios web en Internet. 

•	Crear sitios web aplicando estándares actuales. 

# ACTIVIDADES A DESARROLLAR

Realizar los siguientes ajustes: Con base al archivo Práctica 04 – Creación de una aplicación web usando PHP y Base de Datos
a)	Agregar roles a la tabla usuario. Un usuario puede tener un rol de “admin” o “user” 
b)	Los usuarios con rol de “admin” pueden únicamente: modificar, eliminar y cambiar la contraseña de cualquier usuario de la base de datos. 
c)	Los usuarios con rol de “user” pueden modificar, eliminar y cambiar la contraseña de su usuario. 
 
 Luego, con base a estos ajustes realizados, se pide desarrollar una aplicación web usando PHP y Base de Datos que permita gestionar (enviar y recibir) mensajes electrónicos entre usuarios de la aplicación. De los mensajes electrónicos se desea conocer la fecha y hora, remitente, destinatario, asunto y mensaje. Para lo cuál, se pide como mínimo los siguientes requerimientos: 
 
 Usuario con  rol de user: 
 
d)	Visualizar en su pagina principal (index.php) el listado de todos los mensajes electrónicos recibidos, ordenados por los más recientes. 
e)	Visualizar el listado de todos los mensajes electrónicos enviados, ordenados por los más recientes. 
f)	Enviar mensajes electrónicos a otros usuarios de la aplicación web. 
g)	Buscar todos los mensajes electrónicos recibidos. La búsqueda se realizará por el correo del usuario remitente y se deberá aplicar Ajax para la búsqueda. 
h)	Buscar todos los mensajes electrónicos enviados. La búsqueda se realizará por el correo del usuario destinatario y se deberá aplicar Ajax para la búsqueda. 
i)	Modificar los datos del usuario. 
j)	Cambiar la contraseña del usuario. 
k)	Agregar un avatar (fotografía) a la cuenta del usuario. 
 
Usuario con rol de admin: 
 
l)	No puede recibir ni enviar mensajes electrónicos. 
m)	Visualizar en su pagina principal (index.php) el listado de todos los mensajes electrónicos, ordenados por los más recientes. 
n)	Eliminar los mensajes electrónicos de los usuarios con rol “user”. 
o)	Eliminar, modificar y cambiar contraseña de los usuarios con rol “user”. 
Por último, se debe aplicar parámetros de seguridad a través del uso de sesiones. Para lo cuál, se debe tener en cuenta: 
 
p)	Un usuario “anónimo”, es decir, un usuario que no ha iniciado sesión puede acceder únicamente a los archivos de la carpeta pública. 
q)	Un usuario con rol de “admin” puede acceder únicamente a los archivos de la carpeta admin → vista → admin y admin → controladores → admin  
r)	Un usuario con rol de “user” puede acceder únicamente a los archivos de la carpeta admin → vista → user y admin → controladores → user  
 
Prototipo de ejemplo de los archivos index de la practica: 

-  Index del usuario con rol user

![Figura 1 Index del usuario con rol user](https://user-images.githubusercontent.com/34014602/58283487-02e5cd00-7d6e-11e9-8ad6-93fac000ab76.jpg)

- Index del usuario con rol admin

![Figura 2 Index del usuario con rol admin](https://user-images.githubusercontent.com/34014602/58283567-36285c00-7d6e-11e9-8d1e-e4cfefbd244a.jpg)

# DESARROLLO DE LA PRACTICA

1.	Generar el diagrama E-R para la solución de la práctica 

![1](https://user-images.githubusercontent.com/34014602/58283706-97502f80-7d6e-11e9-9f2a-47bc1322c7f0.png)

2.	Nombre de la base de datos 

![4](https://user-images.githubusercontent.com/34014602/58284012-599fd680-7d6f-11e9-8fdb-cf9d0a5c2fa5.png)

3.	Sentencias SQL de la estructura de la base de datos 

----------------------------------------------------------------------------------------
CREATE TABLE roles ( rol_codigo int(11) NOT NULL AUTO_INCREMENT, rol_nombre varchar(10) NOT NULL,rol_eliminado varchar(1) NOT NULL, rol_fecha_creacion timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP,rol_fecha_modificacion timestamp NULL DEFAULT NULL, PRIMARY KEY (rol_codigo) ) ENGINE=InnoDB DEFAULT CHARSET=utf8 AUTO_INCREMENT=1 ;
----------------------------------------------------------------------------------------

----------------------------------------------------------------------------------------
CREATE TABLE usuario ( usu_codigo int(11) NOT NULL AUTO_INCREMENT, usu_cedula varchar(10) NOT NULL,usu_nombres varchar(50) NOT NULL, usu_apellidos varchar(50) NOT NULL, usu_direccion varchar(75) NOT NULL,usu_telefono varchar(50) NOT NULL, usu_correo varchar(20) NOT NULL, usu_password varchar(255) NOT NULL,usu_fecha_nacimiento date NOT NULL, usu_eliminado varchar(1) NOT NULL DEFAULT 'N', usu_fecha_creacion timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP, usu_fecha_modificacion timestamp NULL DEFAULT NULL, rol_usu_codigoint(11) NOT NULL, usu_imagen longblob NULL DEFAULT NULL, PRIMARY KEY (usu_codigo), UNIQUE KEY usu_cedula(usu_cedula), FOREIGN KEY (rol_usu_codigo) REFERENCES roles(rol_codigo) ) ENGINE=InnoDB DEFAULT CHARSET=utf8 AUTO_INCREMENT=1 ;
----------------------------------------------------------------------------------------

----------------------------------------------------------------------------------------
CREATE TABLE correo ( cor_codigo int(11) NOT NULL AUTO_INCREMENT, cor_usu_remite int(11) NOT NULL,cor_usu_destino int(11) NOT NULL, cor_asunto varchar(200) NOT NULL, cor_mensaje varchar(1000) NOT NULL,cor_fecha_envio timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP, cor_eliminado varchar(1) NOT NULL DEFAULT 'N',cor_elimina int(11) NULL DEFAULT NULL, cor_fecha_elimina timestamp NULL DEFAULT NULL, PRIMARY KEY (cor_codigo), FOREIGN KEY (cor_usu_remite) REFERENCES usuario(usu_codigo) ) ENGINE=InnoDB DEFAULT CHARSET=utf8 AUTO_INCREMENT=1 ;
----------------------------------------------------------------------------------------

4.	Repositorio en GitHub con el nombre “Practica04 – Mi Correo Electrónico” 

![2](https://user-images.githubusercontent.com/34014602/58283837-fa41c680-7d6e-11e9-8b7e-38157303d261.png)

5.	Commit y push por cada requerimiento. 

![3](https://user-images.githubusercontent.com/34014602/58284059-6fad9700-7d6f-11e9-8049-ba28e3728a56.png)

6.	Luego, se debe crear el archivo README del repositorio de GitHub. 

![read](https://user-images.githubusercontent.com/34014602/58284685-bea7fc00-7d70-11e9-80e0-9680b3e9fb7a.png)

7.	Diseño de las páginas HTML usando CSS y su FUNCIONAMIENTO.

a.	Login

![5](https://user-images.githubusercontent.com/34014602/58284111-8ce26580-7d6f-11e9-84b4-55ea89f3edcb.png)

b.	Formulario de registro

![6](https://user-images.githubusercontent.com/34014602/58284163-a5528000-7d6f-11e9-9e78-da6ab3013c16.png)

c.	Administrador

![7](https://user-images.githubusercontent.com/34014602/58284213-b8fde680-7d6f-11e9-801d-a26017223e3d.png)

d.	Usuario

![8](https://user-images.githubusercontent.com/34014602/58284215-bac7aa00-7d6f-11e9-988d-7924f7c3a4fb.png)

e.	Incognito

![9](https://user-images.githubusercontent.com/34014602/58284219-bb604080-7d6f-11e9-95f6-2d48400624cb.png)

8.	GitHub (usuario y URL del repositorio de la práctica)

# Usuario: 
Jonnathan-Matute

# Url: 
https://github.com/Jonnathan-Matute/Practica04-Mi-Correo-Electronico

# RESULTADO(S) OBTENIDO(S):

• 	Tener el conocimiento suficiente para que el estudiante pueda entender y organizar de una mejor manera los sitios de web y de negocios en Internet 

# CONCLUSIONES:

-	Después de haber realizado la practica sobre Java Script, nos podemos dar de cuenta que es una forma de cómo hacer dinámico o con ciertas características de moviente una página Web diseñada en HTML.

-	Un programa JavaScript es una serie de instrucciones compiladas en un archivo que tiene la extensión .js. Se puede probar desde un navegador web abriendo una página HTML que vincula el archivo.

-	Las funciones declaran un conjunto de instrucciones que realizan una tarea determinada. ¡Se puede llamar a una función desde cualquier parte del programa! Una función puede recibir información en forma de parámetros y devolver un valor o no.

# RECOMENDACIONES: 

•	Probar la solución de la práctica en al menos tres navegadores web; Google Chrome, Firefox y Safari

•	Debemos utilizar nombres cortos, que indiquen el tipo de los valores que almacenan.

Nombre de estudiante: Jonnathan Matute Curillo

Firma de estudiante: 

![Firma](https://user-images.githubusercontent.com/34014602/58284501-58bb7480-7d70-11e9-9dcd-797a590b6643.png)

