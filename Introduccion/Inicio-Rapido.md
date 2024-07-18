# react-docs
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