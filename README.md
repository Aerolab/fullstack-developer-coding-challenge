# Aerolab Coding Challenge

![Screenshot](./screenshot.png?)

Tenemos un desafío para vos! El challenge tiene 4 puntos principales y otros 4 puntos opcionales (separados por especialidad). Te recomendamos que los leas todos antes de empezar, ya que seguramente puedas combinar algunos de ellos para ahorrar tiempo. Podés hacernos todas las consultas que sean necesarias, la idea es que el ejercicio sea claro y nos sirve para ir iterando los enunciados.

Una vez que lo tengas listo, subilo a un repo de github/gitlab/bitbucket y pasanos el link al repo y la versión online por mail.


## Parte 1

1) Implementar una vista mobile first de la grilla de productos, del la cual te damos [el diseño con todas las medidas](https://challenge-api.aerolab.co/design) para ver el diseño y chequear los tamaños relativos de cada elemento. Podés conseguir todos los assets ya exportados en [en la carpeta reference/assets](/Aerolab/challenge/blob/master/reference/assets) de este repo. 
**Sólo podés usar CSS moderno, nada de usar Bootstrap o similares.** Tené en cuenta que si bien el diseño es mobile, esperamos que lo adaptes lo mejor que puedas para resoluciones más altas, como Tablets y Desktops.

2) Utilizando **React**, implementá el diseño que creaste en el punto 1 consumiendo [la API del challenge](#Documentación). Podés usar cualquier framework o starter que gustes, como Create React App, Next.JS, o si tenés muchas ganas usar Vanilla directamente. Tenemos dos features para implementar:

* Hay un botón de mostrar más productos que debería cargar las páginas siguientes. Si querés podés agregar infinite scrolling para mejorar un poco más la UX.
* Hay botones de agregar/restar productos al carrito en cada producto. Esto no va conectado a ninguna API, pero debería actualizar el importe total y cantidad de productos del carrito que se ve en la navegación superior. Sería genial si evitás que se pierda el carrito al hacer refresh.

3) Queremos hacer una API específica de esta app que muestre la misma data de la API , pero con un par de modificaciones:

* Debería sumar al modelo de datos los precios en dólares calculados con la cotización del día que sale en la API.
* También estaría bueno que la API no muestre los productos viejos, que son los que se actualizaron por última vez hace más de un mes.

4) Queremos ver el site online! Subí el sitio a now, heroku u otro servicio similar y pasanos el link junto a tu resolución. Idealmente debería estar tanto la API como la web app dentro del mismo deployment.


## Parte 2: Electric Boogaloo

Los puntos a continuación son opcionales y podés resolver los que quieras para demostrar tus conocimientos en las áreas que más te interesen.

**UI**

a) Las fotos suelen venir en JPG, que es un formato que tiende a generar archivos grandes, y se sienten en la experiencia de usuario en malas conexiones. Hay alguna forma de mejorar esto, aunque sea en algunos browsers? 
(Hint: Podés cambiarle la extensión a las fotos que vienen en la API)

b) Estaría muy bueno que la app nos avise cuando estamos sin conexión para no generar falsas expectativas para los usuarios. Y sería genial que la app siga andando aún cuando no tenemos internet.


**JS**

a) El equipo de infraestructura nos pidió que nuestro proxy cargue los productos desde https://challenge-api.aerolab.co/slow/products , pero como el nombre indica, anda lentísimo y nos arruina la performance de la API. 
Hay algo que puedas hacer en el proxy para que no nos afecte tanto? La verdad es que los productos no cambian súper seguido.

b) Por otra parte, la lista de categorías de https://challenge-api.aerolab.co/categories viene en una lista plana. Nos vendría muy bien a futuro tener un endpoint `/category_tree` a la API que devuelva las categorías en forma de árbol, tomando como referencia el siguiente formato:

```
{
  id: 1, name: 'Categoria', parent_id: null,
  subcategories: [{ 
    id: 25, name: 'Subcategoria', parent_id: 1,
    subcategories: [ 
      { id: 54, name: 'Sub-subcategoria' parent_id: 25 } 
    ]
  }]
}
```


## Documentación

La API del challenge está en `https://challenge-api.aerolab.co/`. Sólo tiene 3 endpoints:

### Productos

Los productos los podés encontrar en [https://challenge-api.aerolab.co/products](https://challenge-api.aerolab.co/products). 

Hay varias páginas de productos para mostrar, lo que podés solicitar agregando `?page=numerodepagina`. Por ejemplo, para ver la segunda página podés ir a [https://challenge-api.aerolab.co/products?page=2](https://challenge-api.aerolab.co/products?page=2).

### Categorías

Las categorías las podés encontrar en [https://challenge-api.aerolab.co/categories](https://challenge-api.aerolab.co/categories). 

Cada categoría tiene un atributo `parent_id` que nos dice de qué categoría depende, formando un árbol de categorías. Como nota al margen, este endpoint sólo se utiliza para el ejercicio de la API y no se utiliza en la app en sí.

### Dólar

La cotización del dólar la podés encontrar en [https://challenge-api.aerolab.co/dollar](https://challenge-api.aerolab.co/dollar). Tiene información básica del rate y la fecha de actualización.
