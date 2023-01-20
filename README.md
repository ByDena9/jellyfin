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

## Configuracion de Jellyfin
Accederemos a nuestro servidor desde un navegardor, nos pedira los credenciales para iniciar sesion:
![image](https://user-images.githubusercontent.com/114068764/213697305-41ecd241-b32b-4d62-8295-8927d7dbab8b.png)

### Configuracion de bibliotecas
Cuando accedamos por primera vez no tendremos nada en nuestro servidor, nos aparecera un interfaz vacia, esto pasa porque no hemos configurado las bibliotecas para poder añadir nuestras peliculas y series.

Para añadir bibliotecas nos iremos al `panel de control`:
![image](https://user-images.githubusercontent.com/114068764/213698028-99716e17-68e5-4340-a73a-a7693dac0e1b.png)

Nos iremos a bibliotecas, en bibliotecas le daremos a `añadir biblioteca de medios`
![image](https://user-images.githubusercontent.com/114068764/213698361-3dbc4b87-3c66-4f31-a1de-494c5fb1659e.png)

Podremos nombre a nuestra biblioteca y elegiremos el tipo de archivos que vamos a subir, despues le daremos a añadir carpeta:
![image](https://user-images.githubusercontent.com/114068764/213698846-9f9f8d1b-1655-4555-ab4c-96a7d1f09bd8.png)

![image](https://user-images.githubusercontent.com/114068764/213702238-5de41f97-bfa1-45c5-9b90-d14b36c01e58.png)

![image](https://user-images.githubusercontent.com/114068764/213702595-618df14a-8049-4576-abe4-17ca11016299.png)

![image](https://user-images.githubusercontent.com/114068764/213702850-5d29ad88-f043-45ce-8a3f-08ad56626718.png)

![image](https://user-images.githubusercontent.com/114068764/213703243-52d8ee2e-dd23-4b19-98d5-322c936ceb99.png)

Nos iremos al panel de control, bajaremos a complementos, desde aqui podemos instalar los plugins que necesitemos, pero primero agregaremos los repositorios que necesitemos:
![image](https://user-images.githubusercontent.com/114068764/213704954-09f67093-99a3-4ad8-994f-808414345925.png)

Aqui dejo algunos repositorios:
https://raw.githubusercontent.com/danieladov/JellyfinPluginManifest/master/manifest.json
https://repo.codyrobibero.dev/manifest.json
https://raw.githubusercontent.com/dkanada/jellyfin-plugin-intros/master/manifest.json

## Montar pcloud en nuestro servidor
Para montar pcloud en nuestro servidor seguiremos los pasos para la instalacion desde aqui: `https://github.com/pcloudcom/console-client`
