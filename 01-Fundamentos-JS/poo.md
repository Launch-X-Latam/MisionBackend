# Programación Orientada a Objetos con JavaScript

index.html
```HTML
<!DOCTYPE html>
    <head>
        <meta charset="utf-8"/>
        <title>POO en JavaScript</title>
        <!-- <script src="index.js"></script> -->
        <!-- <script src="Animales.js"></script> -->
        <script src="Persona.js"></script>
    </head>
    <body>
        <h1>
            POO en JavaScript
        </h1>
    </body>
</html>
```

Animales.js
```JavaScript
// Herencia
class Animales {
    
    #especie = "";
    #nombre = "";
    #edad = 0;
    #terrenosAbuela = "Terreno";

    constructor(nombre, edad) {
        this.nombre = nombre;
        this.edad = edad;
    }

    canta() {
        return `${this.nombre} puede cantar`;
    }

    correr() {
        return `${this.nombre} puede correr`;
    }

    getEspecie() {
        return this.#especie;
    }

    setEspecie(especie) {
        this.#especie = especie
    }
}

class Gatos extends Animales {

    constructor(nombre, edad, colorBigotes) {
        super(nombre, edad);
        this.colorBigotes = colorBigotes;
    }

    bigotes() {
        return `Tengo bigotes color ${this.colorBigotes}`;
    }

    anios() {
        return `Tengo ${this.edad} años`;
    }

    especiegato() {
        return `Soy un ${this.getEspecie()}`;
    }

}

let animal = new Animales("gato", 5);
animal.setEspecie("Felis Catus");


let gato = new Gatos("gato", 5, "blanco");

gato.setEspecie("Felis Catus");

console.log(gato.anios());
//console.log(animal.especie);
console.log(gato);
```

index.js
```JavaScript
// Intro a objetos y POO
let nombres = {
    nombre: "Jesús",
    apellido: "Guzmán"
};

console.log(nombres.nombre);
console.log(nombres.hasOwnProperty("telefono"));

console.log(nombres);

function perro(nombre, edad) {
    perro.nombre = nombre;
    perro.edad = edad;
}

perro.prototype.habla = function() {
    return "Wof Wof Soy un perro";
}

let firulais = new perro("Firulais", 9);
console.log(firulais.habla());
```

Persona.js
```JavaScript
// Polimorfismo
function Persona(nombre) {
    this.nombre = nombre;
    this.caminar = function() {
        console.log("CAMINANDO");
    }
}

function Alumno(nombre, llorandoSangre) {
    Persona.call(this, nombre);

    this.llorandoSangre = llorandoSangre;
    this.caminar = function() {
        console.log("CAMINANDO Y LLORANDO SANGRE");
    }
}

Alumno.prototype = Object.create(Persona.prototype);
Alumno.prototype.constructor = Alumno

let estudiante1 = new Alumno('Jesús Guzmán', "React");
let persona1 = new Persona("Memo Ochoa");

console.log(estudiante1.caminar());
console.log(persona1.caminar());

```

---

[**&#11176;** *Anterior* &#11007;](/01-Fundamentos-JS/fundamentos-js.md "") 
[Siguiente **&#129042;**](/01-Fundamentos-JS/proyecto-el-amarre.md "Proyecto")

---

[*Volver* **&ldca;**](/README.md "Menu principal") 
[*Subir* **&#11165;**](# "Ir al título")