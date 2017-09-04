# Proyecto - Curso React/Redux

## Indice

1.  Introduccion
2.  Enunciado
3.  Tecnologias
4.  Comentarios
5.  Guia
    
    -   Creando nuestra aplicacion
    -   Instalando complementos


## Introduccion

Es tiempo de que uses todo lo aprendido en el curso y realices una aplicacion web con React y Redux

Dicho esto vamos a crear una aplicacion que nos permita buscar peliculas utilizando [TMDB](https://www.themoviedb.org/documentation/api).

##  Enunciado

Se debera realizar una aplicacion web que permita realizar busquedas de peliculas, como asi tambien ver la informacion detallada de cualquiera de ellas, y de ser deseado, el usuario podra evaluar la misma.

El buscador debera traer, por defecto, las peliculas mas nuevas. Por si el usuario desea, se debera facilitar un campo para ingresar algun valor a buscar. 

Al ingresar algun valor se debera mostrar las peliculas relacionadas al mismo.

La aplicacion debe presentar la posibilidad de seleccionar una pelicula y ver informacion mas detallada acerca de ella, como ser Fecha de lanzamiento, Puntaje promedio, Sinopsis, Portada y algunos datos mas.

Dentro de esta vista se debera permitir al usuario evaluar la pelicula dandole un valor segun los establecidos por TMBD.

En el buscador como en la pagina de informacion de la pelicula el usuario debe poder marcar una pelicula como favorita. Para ello se utilizara LocalStorage para almacenar esta informacion.

El usuario podra ver sus peliculas favoritas mediante un link de navegacion ubicado en el header de la pagina.

##  Tecnologias

Como parte de este proyecto se debera utilizar:

- ReactJS
- React Router
- ReduxJS

Se debera utilizar:

- [TMDB](https://www.themoviedb.org/documentation/api).

##  Comentarios

La API de TMBD utiliza autentificacion mediante token, por lo tanto debera de permitir al usuario autenticarse para evaluar una pelicula.

##  Guia

### Creando nuestra aplicacion

Para crear nuestra aplicacion debemos instalar la herramienta provista por Facebook para generar aplicaciones react. Para ello ejecutaremos el siguiente script

```npm install -g create-react-app```

Con esta herramienta podremos crear aplicaciones web que utilizan react con tan solo ejecutar un comando. Para crear nuestra aplicacion ejecutaremos

```create-react-app movie-app```

Finalmente para ejecutar nuestra aplicacion tendremos que ejecutar

```
cd movie-app
npm start
```

### Instalando complementos

Como vimos en el curso utilizaremos algunos paquetes de NPM que no estan incluidos con React, como sabemos estos son, Redux y ReactRouter como asi tambien algunos mas para poder vincular a ellos. 

Para instalar todas estos paquetes ejecutaremos la instalacion de NPM para los paquetes `react-router-dom`, `redux` y `react-redux`

### Ruteo

Previo a empezar vamos a generar el ruteo basico de nuestra aplicacion.

Como se hablo en el enunciado se va a tener 3 vistas. 

El buscador, que seria la vista en la cual el usuario puede buscar peliculas y verlas listadas en pantalla.

La informacion de la pelicula, seria la vista que muestra en pantalla detalladamente la informacion de una pelicula.

Las peliculas favoritas del usuario, en la cual se muestran todas las peliculas que el usuario guardo para tener referencia luego.

Teniendo esto en cuenta debemos modificar el componente `App` para manejar estas tres vistas principales. Para ello deberiamos importar los siguientes modulos.

```
import { BrowserRouter, Route, Link } from 'react-router-dom';
```

Previo a agregar nuestras rutas al componente `App` debemos crear nuestras vistas, que si bien son componentes, estos seran componentes de gran nivel.

Para esto podriamos crearlos dentro de una carpeta `views`.

Una vez que tenemos creados nuestros componentes debemos importarlos para realizar el ruteo.

Para ello, debemos utilizar como Root del componente app el componente `BrowserRouter` y dentro de este, debemos injectar las rutas a renderizar. Para injectar las rutas debemos utilizar el componente `Route` en conjunto con los paths esperados y cual componente renderizar en caso de que se corresponda la url de nuestr aplicacion. Como ejemplo, para generar la ruta de peliculas favoritas tendremos la siguiente sentencia

```<Route path="/favourites" component={FavouritesView} />```