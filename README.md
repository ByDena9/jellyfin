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

### Configuracion de notificaciones con bot de discord
Nos vamos a panel de control/complementos, una vez estemos en complementos nos iremos a catalogo y buscaremos el plugin Webhooks:
![image](https://user-images.githubusercontent.com/114068764/214514887-2ff08d71-126b-456d-82c6-0ebd3acfa0df.png)

Lo instalaremos y reiniciaremos el contenedor:
![image](https://user-images.githubusercontent.com/114068764/214519323-24999b79-40ff-4695-8b1f-98050c3c66ad.png)

Una vez instalado nos vamos a nuestros complementos y le daremos a webhook, aqui podemos configurar varios tipos de alertas, para ello pondremos la url de nuestro servidor (o la ip con la que accedemos en caso de no tener un nombre de dominio) y le daremos a añadir el tipo de notificacion que vamos a usar (en este caso Discord):
![image](https://user-images.githubusercontent.com/114068764/214519909-ff6f9a6b-e3f3-4516-bb43-7615d6c0b382.png)

Antes de seguir necesitamos tener creado un bot en discord, para esto nos vamos a ajustes de nuestra cuenta de discord y le daremos a webhook, desde ahi le daremos a crear nuevo webhook, le pondremos nombre y le diremos en que canal de que servidor lo vamos a integrar:
![image](https://user-images.githubusercontent.com/114068764/214522030-b9958446-1c53-4f43-b3ac-1cf45d851f7e.png)

Una vez tengamos nuestro bot volveremos a donde estabamos en jellyfin, aqui pondremos el nombre de nuestro bot de discord y su url:
![image](https://user-images.githubusercontent.com/114068764/214520982-8c87ae14-3740-425e-91c2-f1045ed509ab.png)

Despues seleccionamos que queremos que nos notifique (aqui cada uno selecciona dependiendo de sus necesidades), * importante el no marcar la casilla de send all propierties ya que no funciona actualmente*:

![image](https://user-images.githubusercontent.com/114068764/214522571-9f176d2d-8e7a-44cb-9ae7-e7b0bbd68740.png)

Por ultimo en templates tendremos que coger el codigo de este enlace https://github.com/jellyfin/jellyfin-plugin-webhook/blob/master/Jellyfin.Plugin.Webhook/Templates/Discord.handlebars y lo pegaremos en templates:
![image](https://user-images.githubusercontent.com/114068764/214524946-f38f79a0-5abd-4ed4-bc4d-fd4ee65c3d50.png)

Por ultimo guardaremos la configuracion y probaremos que nuestras notificaciones funcionan correctamente:
![image](https://user-images.githubusercontent.com/114068764/214528209-e36ae3a0-7191-4a3b-b047-520c43b3ee13.png)

Si realizamos cualquier accion que hayamos configurado para que nos notifique veremos como nos avisara en nuestro canal de discord:
![image](https://user-images.githubusercontent.com/114068764/214528439-bde27483-eacb-4845-91b5-c29937815191.png)

## Personalizar nuestro jellyfin
Ahora vamos a explicar como podemos modificar el nombre de nuestro jellyfin, su icono, su logo y como añadir una intro para antes de ver una pelicula.

## Modificar nombre de jellyfin
Para esto tendremos que acceder al contenedor, una vez dentro del contenedor con el comando `docker exec -ti nombredelcontenedor /bin/bash` nos iremos a la ruta `/jellyfin/jellyfin-web` y modificaremos el archivo main.nombredelcontenedor.bundle.js

En este archivo buscaremos `document.tittle='jellyfin'` y `document.title=e||"jellyfin"` y cambiaremos `jellyfin` por el nombre que nosotros queramos:
![image](https://user-images.githubusercontent.com/114068764/214530942-c153e30b-17bc-4011-8a17-701166b2a3d6.png)
![image](https://user-images.githubusercontent.com/114068764/214531188-5df7a012-554b-4e2f-b7da-0ee7ae060769.png)

Una vez lo cambiemos guardaremos el archivo y modificaremos el archivo index.html, buacaremos `<title>nombrequequeramos</title>` y modificaremos el nombre por el nombre que hayamos puesto en el archivo de antes:
![image](https://user-images.githubusercontent.com/114068764/214531806-320578d6-b4a1-4c7f-9a8c-32f1f1b1b523.png)

Una vez hecho los pasos anteriores reiniciaremos nuestro contenedor de jellyfin y comprobaremos como se ha combiado el nombre de nuestro jellyfin:

![image](https://user-images.githubusercontent.com/114068764/214532212-2ccaa896-022a-4662-b1d6-8da6b57137d5.png)

## Personalizacion de icono y banner de jellyfin
### Modificar icono
Para esto tendremos que acceder al contenedor, una vez dentro del contenedor con el comando `docker exec -ti nombredelcontenedor /bin/bash` nos iremos a la ruta `/jellyfin/jellyfin-web`, aqui si hacemos un `ls| grep favicon` veremos como tenemos dos archivos llamados `favicon.ico` y `favicon.png`, lo que tenemos que hacer es sustituir los favicon por nuestro icono *tiene que tener el mismo nombre*:
![image](https://user-images.githubusercontent.com/114068764/214557700-aa0fef96-3f74-4527-a14c-c0f0a83bdabc.png)

### Modificar banner
Accederemos al contenedor, una vez entrado al contenedor con el comando `docker exec -ti nombredelcontenedor /bin/bash` nos iremos a la ruta `/jellyfin/jellyfin-web/assets/img`, aqui veremos tres archivos `banner-light.png` `banner-dark.png` `icon-transparent.png`, pues lo que tendremos que hacer será copiar nuestro banner tres veces poniendole el nombre de cada uno de estos archivos y borrar los que estaban:
![image](https://user-images.githubusercontent.com/114068764/214558421-cbfdfaef-1ef7-4051-9084-502ecc38f513.png)

Cuando hagamos todo esto reiniciamos nuestro contenedor de jellyfin y comprobaremos como se han aplicado los cambios:
![image](https://user-images.githubusercontent.com/114068764/214560034-1f17c51d-82d8-4798-8c27-29f0efd48079.png)

Video explicacion para modificar icono, baner y nombre de jellyfin: https://www.youtube.com/watch?v=F85qMyBeiDI

### Poner una intro
Para esto necesitaremos instalarnos un plugin llamado intros:
![image](https://user-images.githubusercontent.com/114068764/214560934-384d7297-c9a2-4219-baba-d727739a7150.png)

Una vez lo tengamos instalado y hayamos reiniciado el contenedor tendremos que coger una intro personalizada que tengamos y la tendremos que poner en una carpeta dentro del contenedor de jellyfi
Una vez la tengamos dentro del contenedor nos iremos al plugin que hemos instalado, y configuraremos para que ponga nuestra intro:
![image](https://user-images.githubusercontent.com/114068764/214562125-85e39176-d5df-4c83-a0a0-05d797bce744.png)

Una vez puesta reiniciamos el contenedor, y ahora si le damos a ver cualquier cosa que tengamos en nuestro jellyfin (peliculas, series, etc) veremos como antes de empezar a verlo nos aparecera la intro que nosotros le hemos puesto:
![image](https://user-images.githubusercontent.com/114068764/214562729-a36ef1e9-5ba0-4c40-9142-1f464c62e5ac.png)

Tambien el plugin por defecto trae unas intro para poner por si no queremos ponerle ninguna personalizada:
![image](https://user-images.githubusercontent.com/114068764/214562946-e4f76f59-13b6-465d-908c-f3a32618a63e.png)

Video para poner una intro en jellyfin y más configuraciones: https://www.youtube.com/watch?v=8W0PrQe6WgM&t=426s

### Otros plugins interesantes
`Reports` y `Playback reporting` son dos plugins que sirven para obtener informacion sobre lo que esta pasando en el servidor:
![image](https://user-images.githubusercontent.com/114068764/214564064-6625dc42-bc9a-47a5-8253-ad08d47b79ad.png)

Con `Playback reporting` podemos tener tanto informacion sobre los usuario (actividad, ultima conexion, etc) como graficas para saber el uso que se le esta dando al servidor, como por ejemplo que peliculas son las mas vistas, cuantas veces la han visto, etc. Tambien podemos hacer una copia de esas graficas para guardarlas:
![image](https://user-images.githubusercontent.com/114068764/214564503-3e882c7a-e618-43ce-9b20-bea6e2456d49.png)
![image](https://user-images.githubusercontent.com/114068764/214565273-aa4c3eef-065e-4538-a3ee-00ebd5376dce.png)
![image](https://user-images.githubusercontent.com/114068764/214565349-51de6bfd-59b1-4e53-a41b-245c760bf9b5.png)

Con `Report` podemos hacer algo parecido al anterior pero de una manera mas general:
![image](https://user-images.githubusercontent.com/114068764/214565519-9fcb5832-a273-422e-8444-3a918d677471.png)


## Montar pcloud en nuestro servidor
Para montar pcloud en nuestro servidor nos iremos al repositorio oficial de pcloud y seguiremos los pasos para conectar nuestra nube con nuestro servidor: `https://github.com/pcloudcom/console-client`
