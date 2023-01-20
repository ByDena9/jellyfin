# jellyfin

## Configuracion de docker-compose
Clonamos el repositorio: `git clone https://github.com/ByDena9/jellyfin.git`

Modificamos nuestro docker-compose.yml `nano docker-compose.yml` y configuramos los volumenes donde vamos a montar nuestras peliculas y series.

### Modificacion de volumenes
Creamos el directorio que vamos a montar `mkdir`
En volumenes escribimos la carpeta que hemos creado y le vamos a montar la carpeta `/mnt` de jellyfin.

**Recuerda montar la carpeta `/config` para poder modificar o instalar plugins externos: `"/ubicacion-del-directorio-donde-vamos-a-montarlo:/config:rw"`**

Ejemplo de volumenes montados:
![image](https://user-images.githubusercontent.com/114068764/213692027-a0847e71-2647-417b-98db-05d5bb92cb8f.png)

### Asignacion de puertos
Pondremos el puerto por defecto para que jellyfin pueda funcionar: `8096`

## Instalacion
1. Levantamos el docker compose con `docker compose up -d`

2. Una vez levantado accederemos a nuestro servidor con un navegador.

3. Comenzaremos la instalacion, eleguiremos idioma y daremos a siguiente.

4. Crearemos nuestro usuario administrador.

5. Las bibliotecas las configuraremos mas adelante, le daremos a siguiente.

6. Eleguimos la ubicacion y el idioma predefinido.

7. Dejaremos activado el permitir conexiones remotas, le daremos a siguiente.

8. Una vez todo realizado le daremos a comenzar. Con esto ya tendriamos instalado nuestro servidor jellyfin.
