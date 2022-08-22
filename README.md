Docker: Uso práctico en el escenario de Microservicios

Docker soluciona problemas del desarrollo de software profesional, en este caso práctico: 
| Primera parte :
- En AWS se crearán 3 servidores Ec2(Elastic Compute Cloud), comparten la misma red de la VPC. (ec2 de capa gratuita t2.micro)
- Los servicios como Apache, PHP y MySQL se instalarán en 2 containers [PHP y Apache] - [MySQL].
- Se desplegara un site index.php que inserta data a una BD MySQL.
- Se haŕa una prueba de estres, cada vez que se acceda a index.php se creará un registro dentro de la BD, se simularan 250 inserciones.
Conclusión :
La prueba de estres soporta las 250 INSERT INTO, pero si fueran más? quizá 1,000 o 10,000.
| Segunda parte :
- Se elimina el Container donde corria la aplicación
- Se iniciara el servicios docker swarm para crear un cluster de 10 container que contengan la app donde encontramos index.php
- Se instalará NFS para compartir una ruta del servidor origen y compartir con los demas servidores.
- Se configurará un Dockerfile para crear una imagen nginx:latest que servirá como proxy con puerto 4500, cada vez que accedan al servidor origen mediante la prueba de estres sera derivada a los containers creados.
- Volvemos hacer la prueba de estres con mas de 1000 inserciones para poder ver como realiza la simulación, veemos que las 1000 inserciones son distribuidas entre los 10 containers.
Conclusión :
Docker nos ayudarnos a solucionar problemas del desarrollo de software profesional, en este pequeño ejemplo se puede abstraer un poco de lo que se puede realizar.

Nota : Si deseas realizar esta práctica en AWS o tu proveedor de servicios en la nube favorita, no olvides liberar los puertos del firewall propio de cada CSP

Pre-requisitos : Conocimientos básicos en Linux, Docker y AWS.
