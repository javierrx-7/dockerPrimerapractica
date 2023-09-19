# Descarga la imagen 'ubuntu y comprueba que está en tu equipo

docker run -it --name  pract1 ubuntu:22.04
# Una vez dentro utiliza el comando: 
cd home, apt update, apt upgrade, apt install net-tools, ifconfig
# Con esto hacemos que tenga todo lo necesario para funcionar. Y para iniciarlo usamos:
docker start 405
# Aquí lo que hemos hecho es instalar y poner a funcionar la imagen de ubuntu 22.04 con el nombre practdock.


# Crea un contenedor sin ponerle nombre. ¿está arrancado? Obtén el nombre
docker run -it hello-world
 docker ps -a
1af9f86fb5d9   hello-world     "/hello"        About a minute ago   Exited (0) About a minute ago              determined_kare(nombre predeterminado)

# Como podemos observar nos pone un nombre predeterminado si quisieramos tener un nombre propio le deberiamos añadir despues de -it - -name (nombre).
# Crea un contenedor con el nombre 'ubu1'. ¿Cómo puedes acceder a él?
docker run -it --name ubu1 ubuntu:22.04
 docker ps -a
d6d968e5c025   hello-world          "/hello"                 3 seconds ago       Exited (0) 2 seconds ago          ubu1 (Nombre puesto)
# Como podemos ver al poner en la línea de comandos - - name (nombre) nos pone ese nombre al contenedor de hello-world.
# Ahora para entrar en el contenedor utilizamos el comando:
docker exec -it ubu1 bash
# Con esto lo ejecutamos y entramos.
# Comprueba que ip tiene y si puedes hacer un ping a google.com
root@9714a3143afb:/home# ifconfig
eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 172.17.0.2  netmask 255.255.0.0  broadcast 172.17.255.255
root@d84842844ecf:/home# ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=110 time=31.8 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=110 time=19.7 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=110 time=20.2 ms
# Como podemos ver tiene una ip asignada y hace ping a google.
# Crea un contenedor con el nombre 'ubu2'. ¿Puedes hacer ping entre los contenedores?
docker run -it --name ubu2 ubuntu:22.04
root@66d51c4e494d:/home# ping 172.17.0.2
PING 172.17.0.2 (172.17.0.2) 56(84) bytes of data.
64 bytes from 172.17.0.2: icmp_seq=1 ttl=64 time=0.015 ms
64 bytes from 172.17.0.2: icmp_seq=2 ttl=64 time=0.031 ms
64 bytes from 172.17.0.2: icmp_seq=3 ttl=64 time=0.064 ms
64 bytes from 172.17.0.2: icmp_seq=4 ttl=64 time=0.057 ms
64 bytes from 172.17.0.2: icmp_seq=5 ttl=64 time=0.055 ms
Si hacen ping entre ellos.
# Sal del terminal, ¿que ocurrió con el contenedor?
# Se apagan los contenedores pero siguen ahí.
# Menos los que se iniciaron con start.
# ¿Cuanta memoria en el disco duro ocupaste? 
 888KiB
# ¿Hay alguna herramienta de docker para calcularlo?
 docker stats
CONTAINER ID   NAME      CPU %     MEM USAGE / LIMIT   MEM %     NET I/O       BLOCK I/O   PIDS
66d51c4e494d   ubu3      0.00%     888KiB / 15.39GiB   0.01%     11.5kB / 0B   0B / 0B     1

# Con docker stats podemos ver cuánto está ocupando nuestro contenedor.
# ¿Cuanta RAM ocupan los contenedores? Crea cuántos contenedores necesites para calcularlo.
0.01%

# dockerPrimerapractica
