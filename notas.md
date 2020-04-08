https://petgram-server-jose-chtlmx1qn.now.sh//categories

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

-------------------------------

Yo use una animación para cambiar el scale, dejo el snippet por si alguien quiere probarlo.

const scaleDown = keyframes`
    from {
      transform:scale(1);
    }
    to {
      transform:scale(0.5);
    }
`;
const scale = ({time = "1s", type = "ease"} = {}) => css`animation: ${time} ${scaleDown} ${type}`;

const Ul = styled.ul`
  display: flex;
  overflow:scroll;
  width:100%;
  ${props => props.fixed && css`
    background:#ffffff;
    border-radius: 60px;
    box-shadow: 0020px rgba(0, 0, 0, 0.3);
    left:0;
    margin:0 auto;
    max-width: 500px;
    padding:5px;
    position: fixed;
    right:0;
    top: -20;
    transform:scale(0.5);
    ${scale}
    z-index: 1;
  `}
`;

-----------

useEffect(function () {
  function onScroll (e) {
    const isShowFixed = window.scrollY > 200
    setShowFixed(isShowFixed)
  }

  document.addEventListener('scroll', onScroll)

  return function () {
    document.removeEventListener('scroll', onScroll)
  }
}, [showFixed])
-------------

loading tipo facebbok:

category/index.js

import React from'react';
import { ContainerCategorySkeleton, CategoryImage, CategoryTitle } from'./styles';

exportconst CategorySkeleton = props => {
    console.log(props)
    return (
        <ContainerCategorySkeleton>
            <CategoryImage light={props.light} />
            <CategoryTitle light={props.light} />
        </ContainerCategorySkeleton>
    )
}
category/style.js

import styled, { css } from 'styled-components';
import { skeletonStyle } from '../../../styles/skeleton';

export const ContainerCategorySkeleton = styled.div`
    display: flex;
    flex-direction: column;
    align-items: center;
`;

export const CategoryImage = styled.div`
    width:75px;
    height:75px;
    border-radius: 50%;
    ${
        props => css`
            ${skeletonStyle(props.light)}
        `
    }
`;

export const CategoryTitle = styled.div`
    width:26px;
    height:15px;
    margin-top: 8px;
    ${
        props => css`
            ${skeletonStyle(props.light)}
        `
    }
`;

/animation/skeleton/style.js (funciona para cualquier container)

import { css, keyframes } from 'styled-components';

const skeletonBackground = (light) => (
    css`
        background: ${ !light
            ? css`linear-gradient(-90deg, #C1C1C1 0%, #F8F8F8 50%, #C1C1C1 100%)`
            : css`linear-gradient(-90deg, #F0F0F0 0%, #F8F8F8 50%, #F0F0F0 100%)`};
            background-size:400% 400%;
            animation: ${skeletonLoading} 1.2s ease-in-out infinite;
    `
)

const skeletonLoading = keyframes`
    from {
        background-position:0% 0%;
    }
    to {
        background-position: -135% 0%;
    }
`;

export const skeletonStyle = (light = true) => skeletonBackground(light);

https://platzi.com/comentario/810440/

--------------------------------

Respuesta a:
Usando Intersection Observer
Excelente clase! No se hace el request hasta que el elemento se encuentre en el viewport.

Adicionalmente agregué el threshold al objeto de configuración del IntersectionObserver.

useEffect(
    function() {
      const observer = newwindow.IntersectionObserver(
        function(entries) {
          const { isIntersecting } = entries[0];
          if (isIntersecting) {
            setShow(true);
            observer.disconnect();
          }
        },
        {
          threshold: 0.5
        }
      );
      observer.observe(element.current);
    },
    [element]
  );```

----------------------------------

  Yo hice uso Intersection Observer, un poquito diferente, hago un solo IntersectionObserver que vigile a todos los elementos, peuden verlo en este link:
https://github.com/SoyOscarRH/SoyOscarRH.github.io/blob/master/Webpage/Code/Helpers/lazyLoadImages.ts

Y solo lo ejecutan una sola vez como por ejemplo:

import lazyLoadImages from".../lazyLoadImages"
document.addEventListener("DOMContentLoaded", lazyLoadImages)
Y las imagenes al final tienen que tener el src de una imagen por defecto (un placeholder), como por ejemplo:

<img
        className="lazy"
        data-src={`Assets/${folder}/${name}`}
        src={"Assets/Blank.png"}
/>
Y si lo quieren ver en vivo y directo:
https://SoyOscarRH.github.io/

----------------------------------------------
Otra manera de preguntar por una key en un objeto puede ser:

'IntersectionObserver'inwindow
Eso te devolverá un boolean.

-----------------------------------------------------------------------

HOC's : componentes de orden superior una funcion que se la pasa un componente y que devuelve otro componente

Cambiar el coor del like: https://platzi.com/comentario/827902/

Puedes devolver una función dentro del primer argumento que envías a la función useEffect. 😅

usEffect(() => {
  // código del hook
  return () => {
    // código para limpiar el hook
  };
}, []);
Dicho en otras palabras, dale un vistazo a este mini tutorial de la documentación oficial de React: https://reactjs.org/docs/hooks-effect.html#effects-with-cleanup. Incluye ejemplos con la misma funcionalidad programados en componentes creados como función vs. componentes creados como clases. 😉

----------------------

Hasta ahora hay un pequeño cambio al importar librerías

Para la instalacion

npm install apollo-boost @apollo/react-hooks graphql
index.js

import { ApolloProvider } from'@apollo/react-hooks';

<ApolloProviderclient={client}><App /></ApolloProvider>
hacer la query

useQuery(gql(``))

Tenga su link señor. Gracias! Esta más sencillo.

La otra manera de hacerlo es la siguiente:

import { ApolloClient } from 'apollo-client';
import { InMemoryCache } from 'apollo-cache-inmemory';
import { HttpLink } from 'apollo-link-http';

const cache = new InMemoryCache();
const link = new HttpLink({
  uri: 'http://[lo_que_sea]/graphql'
});

const client = new ApolloClient({
  cache,
  link
});```

--------------------------------------
Esta es la nueva forma de inicial el client de Apollo

import React from'react'
import ReactDom from'react-dom'
import { ApolloClient, HttpLink, InMemoryCache } from'apollo-boost'
import { ApolloProvider } from'react-apollo'

import { App } from'./App'

const cache = new InMemoryCache()

const link = new HttpLink({
    uri: 'https://petgram-server-jcamacaro.camacaro.now.sh/graphql'
})

const client = new ApolloClient({
    cache,
    link
})

// ReactDom.render(<App/>, document.getElementById('app'))

ReactDom.render(
    <ApolloProviderclient={client}>
        <App/>
    </ApolloProvider>, 
document.getElementById('app'))

---------------------------
Puden usar el loading para saber cuando la información ya ha sido cargada: 
https://platzi.com/comentario/1034069/

render props: https://platzi.com/comentario/768874/

https://medium.com/simply/comparison-hocs-vs-render-props-vs-hooks-55f9ffcd5dc6


Comparison: HOCs vs Render Props vs Hooks: to read!
https://medium.com/simply/comparison-hocs-vs-render-props-vs-hooks-55f9ffcd5dc6

Render Props:
 https://platzi.com/comentario/944580/

 Arreglo para clase Respuesta a:
Usar render Props para recuperar una foto: https://platzi.com/comentario/850745/
Hola Alex, si tienes separada la query, puedes utilizar el cliente de Apollo para hacer queries en respuesta a un click. Puedes importar el componente ApolloConsumer, que acepta una renderProp donde tendrás el cliente para hacer las queries.

Tienes más info y un ejemplo aquí: https://www.apollographql.com/docs/react/essentials/queries/#manually-firing-a-query

Los react hooks en apollo 😎😎😎

import { useQuery } from 'react-apollo-hooks'
import gql from 'graphql-tag'

const getPhotos = gql`
  query getPhotos($categoryId: ID) {
    photos(categoryId: $categoryId) {
      id
      categoryId
      src
      likes
      userId
      liked
    }
  }
`

export const useGetPhotos = categoryId => {
  const { loading, data, error } = useQuery(getPhotos, { variables: { categoryId } })
  return { loading, data, error }
}

placeholder de loading: https://platzi.com/comentario/973274/

Mi código con useMutation, el hook de react apollo para las mutaciones.

const [toggleLike] = useMutation(TOOGLE_LIKE, { variables: { input: { id } } });

const handleFavClick = () => {
  toggleLike()
  setLiked(!liked)
 }
 tambien vease en : https://platzi.com/comentario/1061495/