# Crud_Terminado

Guardar los dos programas en una misma carpeta y ejecutar "tabla_colores.py" una vez instaladas las bibliotecas correspondientes (qt5,mysql,phpmyadmin).


para ejecutar los métodos desde los botones es necesario dar click en el "id" de la persona que se desee saber la información


Instalar en la Rasp:

	-qt5: https://wiki.qt.io/Raspberry_Pi_Beginners_Guide
	-Mysql: https://www.luisllamas.es/como-instalar-mysql-en-raspberry-pi/
	-Opcional: phpmyAdmin https://www.luisllamas.es/como-instalar-phpmyadmin-en-raspberry-pi/

CREAR BASE DE DATOS EN LA RAPSBERRY UTILIZANDO  RASPBERRY:

CREATE DATABASE crud_db;

GRANT ALL PRIVILEGES ON crud_db.* TO 'root'@'localhost' IDENTIFIED BY ‘pass’; #root es el usuario y pass el password
FLUSH PRIVILEGES;

CREATE TABLE person
(id NVARCHAR(45),
 nombre NVARCHAR(45),
 apellido NVARCHAR(45),
 edad NVARCHAR(45),
 ocupación NVARCHAR(45),
 telefono NVARCHAR (45),
 domicilio NVARCHAR(45),
 fechaNac NVARCHAR(45),
 estCivil NVARCHAR(45),
 observaciones NVARCHAR(45));

para ejecutar un programa en Rasp utilizando crontab: https://kolwidi.com/blogs/blog-kolwidi/como-ejecutar-un-script-python-al-arrancar-tu-raspberry-pi

La nomenclatura que hay que seguir es esta:
m h  dom mon dow   command
Cada uno de los parámetros significa esto:
    • "m": minutos, los valores que acepta van de 0 a 59 
    • "h": hora, valores entre 0 y 23 
    • "dom": día del mes (day of the month), los valores van de 1 a 31 
    • "mon": mes, con valores de 1 a 12 
    • "dow": día de la semana (day of the week) y los valores que acepta van de 0 a 7, donde el 0 y el 7 se refiere al Domingo. 
    • comand: aquí seria donde especificamos el comando o archivo que queremos ejecutar, recuerda que hay que poner también la ruta donde esta el archivo o script en caso de que quieras ejecutar uno. 
Otros caracteres especiales son estos:
    • @reboot: para ejecutar un comando o script durante el arranque de la Raspberry Pi 
    • @annually: para ejecutar una tarea anualmente 
    • @monthly: para ejecutar una tarea mensualmente 
    • @weekly:para ejecutar una tarea semanalmente 
    • @daily: para ejecutar una tarea diariamente 
    • @hourly: para ejecutar una tarea cada hora  
    • #: para indicar comentarios 
    • &: este caracter especial, si se pone al final de la instrucción de ejecución, hará que la tarea se ejecute en segundo plano, de este modo el arranque de la placa Raspberry Pi seguirá su curso y en segundo plano se ejecuta la tarea. 
Además de los números únicos para cada uno de los primeros 5 parámetros, también puedes utilizar los siguientes formatos especiales:
    • Una secuencia de números, separados por una coma, por ejemplo: 0,15,30,45 
    • Un rango, por ejemplo: 4-8 
    • Una sucesión de rangos, por ejemplo: 0-15,30-45 
    • Un asterisco, para indicar 'todo', por ejemplo: * 
    • Para ejecutar cada n-veces agregando el sufijo "/c" donde "c" seria el numero, por ejemplo: */5 por cada 5 minutos. 

Estos serian algunos ejemplos:
    • * * * * * python /home/pi/Hola.py: ejecuta el script python "Hola.py" cada minuto 
    • 30 * * * * echo "Hola Scrip": saca por pantalla el mensaje "Hola Script" cada 30 minutos 
    • 30 9 * * 5 python /home/pi/Hola.py: ejecuta el scrip python todos los viernes a las 9:30 am 
    • */15 * * * * echo "frecuencia de 15min": se ejecuta cada 15 minutos 
    • @reboot python /home/pi/lectura_sensor.py: ejecuta el script python "lectura_sensor" cada vez que la placa Pi se reinicia 
      
Una vez que hagas modificaciones en crontab es aconsejable que lo reinicies con este comando:
sudo /etc/init.d/cron restart
