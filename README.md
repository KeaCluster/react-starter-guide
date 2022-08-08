# ReactJS-learning-path
Learning-path para React basics

[React Docs](https://reactjs.org/)

### Requisitos

- HTML
- CSS
- JavaScript
- Node
- npm
- Terminal
  
## Parte 1


### Sugerencia

Ver la primer hora del curso de React de [Bob Ziroll](https://www.youtube.com/watch?v=bMknfKXIFA8)

### Inicio

#### Instalación

La forma más sencilla de crear una nueva aplicación en React es utilizando el toolchain para ambiente de desarrollo  ```create-react-app```.

> Verificar Node >= 14.0.0 y npm >= 5.6

En una nueva carpeta, utilizar la terminal para ejecutar las siguientes lineas de comando

```console
npx create-react-app my-app
cd my-app
npm start
```

Después de ejecutar, deberíamos ver algo así
![Imagen inicial](./public/images/initial_screen.png)


#### Estructura del proyecto

![Estructura de directorios](./public/images/structure.png)



- ```src``` contiene todos los archivos esenciales para nuestro proyecto
- En la carpeta public se encuentra el archivo html incial ```index.html```. Este puede ser modificado como cualquier archivo ```.html```.

1. Directorio ```src```

![src dir](./public/images/src_dir.PNG)

1. ```App.js``` es el archivo **principal** de nuestra aplicación. Todos los componentes tendrán conexión a éste archivo.
2. ```index.js``` es un archivo de inicio de la aplicación. Aquí se hace referencia al elemento html con ```id root``` para su renderización en el DOM.
3. ```App.css e index.css``` contienen estilos de la aplicación. ```index.css``` contiene estilos globales. ```App.css``` contiene estilos más especificos para componentes.


## Parte 2

### JSX

Sintáxis JavaScript XML que permite escribir elementos HTML en JavaScript, para colocarlos dentro del DOM sin la necesidad de utilizar ```document.createElement()``` o ```appendChild()```.

> Creación de elementos HTML con ```document.createElement()```

```javascript
var tag = document.createElement("p");
```

> Creación de elementos HTML con ```JSX```


```javascript
const App = () => {
    return (
        <div className="App">
            <h1>Hello World</h1>
        </div>
    )
}

export default App;
```
```export default Component``` se refiere al componente que se va a exportar de nuestro archivo ```Componente.js```. De ésta forma se envían componentes a otros archivos ```.js``` para su funcionamiento.

#### Buenas prácticas JSX

1. Todos los elementos dentro de un componente deben estar encapsulados en un solo elemento html. Puede ser ```<div>``` o el elemento React.Fragment de ```jsx```:  

```javascript
<> 
    <h2>Los demás elementos van aquí</h2>
    <div> 
        <p>Deben estar encapsulados</p>
    </div>
</> 
```

### DOM y Virtual DOM

- Real DOM
  > Lo conocemos como *Document Object Model* y representa la UI de la aplicación.
  
  > Cuando hay algún cambio, el DOM se actualiza en su totalidad.

- Virtual DOM
  > Es una representación virtual del DOM real. Similar a un DOM temporal.
  
  > Cuando se agregan/eliminan/modifican elementos, el árbol del Virtual DOM se actualiza.
  
  > Luego, se compara Virtual DOM con el Real DOM para encontrar los nodos en el árbol que han cambiado.
  
  > Cuando se encuentran las diferencias, Virtual DOM encuentra la mejor forma de actualizar nodos especificos del Real DOM sin la necesidad de actualizarlo en su totalidad.

    ![Virtual DOM](./public/images/virtual_DOM.png)

## Parte 3

### React Components

Se pueden comparar con bloques de construcción de Lego. Cada componente es un bloque de piezas que representa una sección del modelo completo.

Estos componentes tienen como tarea hacer la construcción de la UI más fácil, dividiendo el problema de la app en piezas individuales que se pueden reutilizar. 

La división de los componentes generalmente ayudan a separar su estructura global en secciones que puedan funcionar de forma individual. Los componentes más comúnes son:

1. Inputs
2. Botones
3. Badge
4. Lista
5. Tabla
6. NavBar
7. Alert
8. Card
9. Tabs
10. Select

### Tipos de Componentes

#### Functional Components

Son simplemente funciones de javascript. Pueden o no recibir datos por medio de parámetros. Este tipo de componentes no toman en cuenta la existencia de otros componentes dentro de la aplicación.

```javascript
import React from 'react';

const Navbar = () => {
    return (
        <nav>
            // etc
        </nav>
    )

}

export default Navbar;
```

#### Class Components

Este tipo de componentes si están conectados con otros componentes y pueden comunicarse enviándose datos uno a otro. 

El uso de componentes funcionales es común cuando se sabe de antemano que ese componente no tendrá interactividad con otro.

```javascript
import React, { Component } from 'react';

class Navbar extends React.Component {
    render() {
        return  (
            <nav>
                // etc
            </nav>
        )
    }
}

export default Navbar;
```

### Importar componentes

Sean componentes funcionales o de clase, se pueden importar e implementar en la app de una forma muy sencilla. Para renderizarlos simplemente tenemos que importar el ```componente.js``` a el archivo de la página donde se va a renderizar, para SPAs comúnmente es ```App.js```. Para componentes que se implementarán dentro de otro componente, la sintáxis es la misma

```javascript

import Navbar from './Components/Navbar/Navbar.js';

const App = () => {
    return (
        <>
            <Navbar />
            <Carosuel />
            <Main />
            <Contact />
        </>
    );
}

export default App;
```

## Otros recursos
> - [Eve Porcello - React Essential Training](https://www.linkedin.com/learning/react-js-essential-training-14836121?u=100575394)
> - [Estefania Cassigena - React desde cero](https://www.freecodecamp.org/espanol/news/aprende-react-desde-cero-curso-de-react-con-proyectos/)
> - [Joel Olawanle - Getting started React](https://www.freecodecamp.org/news/get-started-with-react-for-beginners/)
> - [Jean-Marc Mockel - React Best Practices](https://www.freecodecamp.org/news/best-practices-for-react/)
> - [Ihechikara Vincent Abba - React Router v6](https://www.freecodecamp.org/news/how-to-use-react-router-version-6/)
> - [Reed Barger - React Router Cheatsheet](https://www.freecodecamp.org/news/react-router-cheatsheet/ )
> - [Understanding Functional Components vs Class Components](https://www.twilio.com/blog/react-choose-functional-components)