# INICIO RÁPIDO
Apuntes de la documentacion oficial de React

## Creación y anidado de componentes

Los componentes de React son funciones JS que devuelven marcado:

```
function MyButton() {
    return (
        <button>Soy un botón</button>
    );
}
```

## Anidarlo a otro componente

```
export default function MyApp() {
    return (
        <div>
            <h1>Bienvenido a mi aplicación</h1>
            <MyButton />
        </div>
    );

}
```

## Añadir estilos

```
<img className="avatar">
```

> React no prescribe como debes añadir tus archivos CSS. En el caso mas simple añades una etiqueta <link> a tu HTML.

## Mostrar datos

JSX te permite poner marcado dentro de JS utilizando llaves.

```
return (
    <h1>
        {user.name}
    </h1>
);
```
Tambien puedes poner marcado en atributos JSX utilizando llaves en lugar de comillas.

```
return (
    <img 
        className="avatar"
        src={user.imageUrl}
    />
);
```
## Renderizado condicional

En React, no hay una sintaxis especial para escribir condiconales. Usarás las mismas técnicas que usas al escribir código regular de JS. 

```
let content;
if (isLoggedIn) {
    content = <AdminPanel />;
} else {
    content = <LoginForm />
}
return (
    <div>
        {content}
    </div>
);
```
 > If no funciona dentro de JSX, en cambio el operador ? condicional si.

```
 <div>
    {isLoggedIn ? ( <AdminPanel /> ): ( <LoginForm /> )}
 </div>
```

 > Cuando no necesites la rama else, puedes utilizar la sintaxis lógica &&.

``` 
 <div>
    {isLoggedIn && <AdminPanel />}
 </div> 
```
## Renderizado de listas

Dependerás de funcionalidades de JS como bucles y la funcion map() de los arreglos.

```
const products = [
    { title: 'Col', id: 1 },
    { title: 'Ajo', id: 2 },
    { title: 'Manzana', id: 3 }
];

const listItems = products.map( product => 
    <li key = {product.id}>
        {product.title}
    </li>
);

return (
    <ul>{listItems}</ul>
)
```
## Responder a eventos

Puedes hacerlo declarando la funcion controladora de eventos dentro de tus componentes.

```
function MyButton(){
    function handleClick() {
        alert('Me hiciste click');
    }

    return (
        <button onClick={handleClick}>
            Hazme Click
        </button>
    );
}
```
> Nota que onClick={handleClick} no tiene paréntesis al final. No llames a la función contoladora del evento, solo necesitas pasarla hacia abajo.

## Actualizar pantalla

Para que tu componente "recuerde" alguna información y la muestre, le deberas añadir estado.

Primero, importa "useState" de React:

```
import { useState } from 'react';
```
Ahora puedes declarar una variable de estado dentro de tu componente.

```
function MyButton() {
    const [count, setCount] = useState(0);

    //...
}
```
Obtendrás el estado actual (count), y la función que te permite actualizarlo (setCount). El valor por defecto será 0, o el que pases como argumento a useState.

```
function MyButton() {
  const [count, setCount] = useState(0);

  function handleClick() {
    setCount(count + 1);
  }

  return (
    <button onClick={handleClick}>
      Hiciste clic {count} veces
    </button>
  );
}
```
> Si renderizas el mismo componente varias veces, cada uno obtendrá su propio estado.

## El uso de los Hooks

Las gunciones que comiencen con "use" se llaman Hooks. Puedes encontrar Hooks nativos  y tambien puedes escribir tus propios Hooks.

## Compartir datos entre componentes

Para hacer que ambos componentes MyButton muestren el mismo count y se actualicen juntos, necesitas mover el estado de los botones individuales "hacia arriba" al componente más cercano que contiene a todos.

```
export default function MyApp() {
  const [count, setCount] = useState(0);

  function handleClick() {
    setCount(count + 1);
  }

  return (
    <div>
      <h1>Contadores que se actualizan separadamente</h1>
      <MyButton count={count} onClick={handleClick} />
      <MyButton count={count} onClick={handleClick} />
    </div>
  );
}
```
> La información que pasas hacia abajo se llaman props. 