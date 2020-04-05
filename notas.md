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

porr si a alguien le muestra el boton gris con borde negro le dejo este estilo de Button para solucionarlo

export const Button = styled.button`
  display: flex;
  align-items: center;
  padding-top: 8px;
  & svg {
    margin-right: 4px;
  }
  background-color: transparent;
  border: 0px;

  Para utilizar async/await se debe utilizar:

  npm i -D @babel/runtime @babel/plugin-transform-runtime
  Para que funcione tambie hace falta agregar plugins: ["@babel/plugin-transform-runtime"] en la configuracion de opciones de babel-loader en el archivo de configuracion de webpack.

useEffect(() => {
    fetchData()
}, [])

const fetchData = async () => {
  const data = await useFetchCategories(state)

  setState({
    categories: data.categories,
    error: data.error,
    loading: data.loading
  })
}

Mas formas para hacer:
https://platzi.com/comentario/661882/
https://platzi.com/comentario/938769/
https://platzi.com/comentario/674511/
https://github.com/rojasleon/advanced-react/commit/c285630624d2d4bb027f232e002b7c84d278e236


  Con estos tutoriales te quedará muy claro cómo usar async await con React Hooks:

👉 https://www.robinwieruch.de/react-hooks-fetch-data
👉 https://dev.to/vinodchauhan7/react-hooks-with-async-await-1n9g

Bonus:

👉 https://platzi.com/blog/usestate-vs-usereducer/


getSnapshotBeforeUpdate() se invoca justo antes de que la salida renderizada más reciente se entregue, por ejemplo, al DOM. Permite al componente capturar cierta información del DOM (por ejemplo, la posición del scroll) antes de que se cambie potencialmente. Cualquier valor que se devuelva en este ciclo de vida se pasará como parametro al método componentDidUpdate().
Este caso de uso no es común, pero puede ourrir en IUs como un hilo de chat que necesita manejar la posición del scroll de manera especial.

componentDidCatch()
Este ciclo de vida se invoca después de que un error haya sido lanzado por un componente descendiente. Recibe dos parámetros:

error - Es un error que ha sido lanzado.
info- Un objeto con una clavecomponentStack contiene información sobre que componente ha devuelto un error.
componentDidCatch() se llama durante la fase “commit”, por lo tanto, los efectos secundarios se permiten. Debería utilizarse para cosas como errores de registro:

