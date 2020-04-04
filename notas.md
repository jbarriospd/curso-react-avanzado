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
