Para usar packages de desarrollo (que instalamos para el proyecto) como webpack o webpack-cli podemos ejecutar el comando npx
por ejemplo en el caso de webpack:

```
npx webpack src/index.js
```
Este sustituye a:
```
node_modules\.bin\webpack src/index.js
```

-------------------------


Si tienen muchos errores y desean corregirlos les recomiendo agregar esta configuración al package.json
"lint": “standard”,
“lint-fix”: “standard --fix”

Y ejecutan:
npm run lint-fix

--------------------------------


También podemos poner este comando para que lo arregle automaticamente:
```
npm run lint -- --fix
```
---------------

evitar el revote de scroll
```css
overscroll-behavior: none; 
```
------------------------

Si quieren ocultar el scroll pero mantener la funcionalidad pueden usar.
```js
const List = styled.ul`
  display: flex;
  overflow: scroll;
  width: 100%;
  &::-webkit-scrollbar {
    display: none;
  }
```
Respuesta a:
Creando ListOfCategories y estilos globales
Les paso los estilos

html {
    box-sizing: border-box;
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
  }

  *, *:before, *:after {
    box-sizing: inherit;
  }

  ul, li, h1, h2, h3, p, button {
    margin: 0;
    padding: 0;
  }

  ul {
    list-style: none;
  }

  button: {
    background: transparent;
    border: 0;
    outline: 0;
  }

  body {
    background: #fefefe;
    height: 100vh;
    margin: 0 auto;
    max-width: 500px;
    overscroll-behavior: none;
    width: 100%;
  }

  #app {
    box-shadow: 0010pxrgba(0, 0, 0, 0.05);
    overflow-x: hidden;
    min-height: 100vh;
    padding-bottom: 10px;
  }```

Una forma util de usar SVG en react es importandolos como componentes cuando tenemos los assets .svg

Por ejemplo:
import { ReactComponent as DogIcon} from '../assets/dog.svg';