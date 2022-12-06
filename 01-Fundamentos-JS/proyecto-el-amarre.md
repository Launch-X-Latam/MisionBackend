# Proyecto
## El amarre

Desde tiempos inmemoriables los animales han ideado formas diferentes de atraer pareja. 

Tenemos al pavo real macho con su ya conocido plumaje exotico

![Pavo Real](https://upload.wikimedia.org/wikipedia/commons/thumb/b/bf/Pavo_cristatus_Campo_Grande.jpg/250px-Pavo_cristatus_Campo_Grande.jpg)

Pasando por la hembra Mantis Religiosa comiendose la cabeza de su enamorado.

![Mantis](https://www.sopitas.com/wp-content/uploads/2016/07/mantis-comida-1.jpg)

Hasta tu **"amig@"** esperando el momento perfecto para saltar.

![Chapulin](https://static.wixstatic.com/media/8c78bb_338ea1ef9cca4d8689c41327432b266f~mv2.jpg/v1/crop/x_154,y_0,w_717,h_740/fill/w_337,h_348,al_c,q_80,usm_0.66_1.00_0.01,enc_auto/zxcdc.jpg)

Es por ello que te tengo una forma en la que tu crush literalmente, no te podrá decir que NO. El Amarre.

## Lo que aprendes
- HTML
- CSS
- Reproduicción de audio y video
- Funciones de JS
- Manejo del DOM
- Manejo de eventos

**Te recomiendo leer muy bien los comentarios del codigo.**

Archivo: index.html
```html
<!DOCTYPE html>
<html>
    <head>
        <!-- PARA PODER USAR ACENTOS Y Ñ -->
        <meta charset="utf-8">
        <!-- La étiqueta Title coloca el texto como titulo de la pestaña -->
        <title>¿Quieres ser mi Sempai/Waifu?</title>

        <!-- Con esta etiqueta link y la propiedad rel="stylesheet"  haciendo haciendo referencia al css podemos unir el archivo de estilo con el HTML. De preferencia se debe cargar antes que el HTML, por eso va dentro de <head> -->
        <link rel="stylesheet" href="app.css">
        <!-- Con script asociamos el archivo JavaScript al archivo HTML. 
        Al ponerlo en el HEAD, este carga antes del body. 
        Al ponerlo después, este carga después de lo que se ve en la página. 
        Es importante determinar que comportamiento queremos.
        -->
        <script src="antesdebody.js"></script>
    </head>
    <body>

    <!-- 
        Con div podemos hacer secciones de elementos HTML. Piensa en Div como un contenedor que en este caso recibe el estilo la clase de CSS modo_sexo
    -->
    <div class="modo_sexo">
        <h1>MODO SEXO ACTIVADO :3</h1><!-- H1 para titulos -->
        <img src="https://i.pinimg.com/originals/c5/e3/c9/c5e3c9b5260daa31f5a4ab03ff048ece.png"> <!-- Ponemos una imagen -->
    </div>

    <!-- Con la etiqueta mostramos un video a los usuarios.
    
    Los navegadores actuales no permiten la autoreprodución de videos con sonido. En este caso, se carga un video de una carpeta del proyecto.
    -->
    <video width="600" height="350" controls loop >
        <source src="img\video.mp4" type="video/mp4">
        NO SE PUEDE VER ESTE VIDEO
    </video>

    <h1>DI QUE SÍ POR FAVOR</h1>
    <!-- Los buttons nos generan botones accionables para el usuario. Estos reciben su estilo por medioo de su id -->
    <button id="btn_si">SÍ</button>
    <button id="btn_no">no :(</button>

    </body>

    <!-- Cargamos hasta el último el JS porque necesitamos que existan los elementos HTML para que los obtengamos en el JS -->
    <script src="app.js"></script>
</html>
```

**NOTA:** Al cargar el JS antes del HTML podríamos asegurar, por ejemplo, que un usuario no loggeado vea algo del contenido. Al cargarlo después, podemos colocarle eventos a los botones. Por ejemplo, que mande una notificación al presionar un botón.

```css
button:hover {
    cursor: pointer;
} 

h1 {
    color: blueviolet;
    font-family: Arial, Helvetica, sans-serif;
}

.modo_sexo  {
    height: 2000px;
    position: absolute;
    display: none;
    width: 100%;
    background-color: red;
    z-index: 1000;
}

#btn_si {
    background-color: cadetblue;
    border-color: cadetblue;
    color: azure;
    font-size: xx-large;
    padding: 32px;
    text-align: center;
    border-radius: 2px;
}
```

```JavaScript
function moverPosicionRandom(elm) {
    elm.style.position = 'absolute';
    elm.style.top = Math.random() * (window.innerHeight - elm.offsetHeight) + 'px';
    elm.style.left = Math.random() * (window.innerWidth - elm.offsetWidth) + 'px';
}

let btnSi = document.getElementById("btn_si");
let btnNo = document.getElementById("btn_no");
let divModoSexo = document.getElementsByClassName("modo_sexo")[0];

btnNo.addEventListener('mouseenter', function(e) { moverPosicionRandom(e.target) });

btnSi.addEventListener('click', function(e) {
    alert('Sabía que dirías que SÍ. Casemonos ya y tengamos hijos. TE AMO!!!! ❤️');

    divModoSexo.style.display = 'block';
    const cancion = new Audio('img\\modo_hot.mp3');
    //cancion.play();
});

divModoSexo.addEventListener('click', function(e) {
    const img = document.createElement("img");
    img.src = "https://i.pinimg.com/originals/c5/e3/c9/c5e3c9b5260daa31f5a4ab03ff048ece.png";
    console.log(img)
    divModoSexo.appendChild(img)
});

botones = document.getElementsByTagName("button")
console.log(botones)

window.addEventListener('beforeunload', (event) => {
    event.preventDefault();
    event.returnValue = "";
});
```

---

[**&#11176;** *Anterior* &#11007;](/01-Fundamentos-JS/poo.md "Programación Orientada a Objetos con JavaScript") 
[Siguiente **&#129042;**](/01-Fundamentos-JS/tarea-calculadora.md "Calculadora")

---

[*Volver* **&ldca;**](/README.md "Menu principal") 
[*Subir* **&#11165;**](# "Ir al título")