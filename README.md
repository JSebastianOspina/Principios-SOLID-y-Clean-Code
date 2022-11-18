# Principios-SOLID-y-Clean-Code
Notas de clase del curso de Principios SOLID y Clean Code de Fernando Herrera en Udemy

> "Nuestro código tiene que ser simple y directo, debería leerse con la misma facilidad que un texto bien escrito"
> 
> "Código limpio es el que se ha escrito con la intención de que otra persona (o tu mismo) lo entienda."
- [Principios-SOLID-y-Clean-Code](#principios-solid-y-clean-code)
- [Deuda técnica](#deuda-t-cnica)
  * [Esquema de deuda técnica de Martin Fowler](#esquema-de-deuda-t-cnica-de-martin-fowler)
    + [Imprudente](#imprudente)
    + [Imprudente e Inadvertida](#imprudente-e-inadvertida)
    + [Prudente](#prudente)
    + [Prudente e inadvertida](#prudente-e-inadvertida)
- [Refactorización](#refactorizaci-n)
- [Clean Code](#clean-code)
  * [Nombres pronunciables y expresivos](#nombres-pronunciables-y-expresivos)
    + [Ejercicio](#ejercicio)
      - [Solución](#soluci-n)
  * [Nombre según el tipo de dato](#nombre-seg-n-el-tipo-de-dato)
    + [Arreglos](#arreglos)
    + [Booleanos](#booleanos)
    + [Números](#n-meros)
    + [Números](#n-meros-1)
    + [Ejercicio](#ejercicio-1)
      - [Solución](#soluci-n-1)
    + [Nombres de las clases](#nombres-de-las-clases)
      - [3 preguntas para saber si es un buen nombre](#3-preguntas-para-saber-si-es-un-buen-nombre)
    + [Nombres de funciones, argumentos y parámetros](#nombres-de-funciones--argumentos-y-par-metros)

# Deuda técnica

Falta de calidad en alguna parte de del código de nuestra aplicación. Esto genera un costo económico a futuro, que termina pagándose con mas tiempo invertido tratando de comprender el codigo, refactorizarlos, transferencia del código y solucionar los problemas generados en etapas mas tempranas del desarrollo. 

## Esquema de deuda técnica de Martin Fowler

Caer en deuda técnicas es normal y a menudo es inevitable. Un buen programador es consciente de ella y se preocupa por pagarla. La deuda técnica se paga **refactorizando** el código. 

La mala calidad en el software siempre la acaba asumiendo alguien, ya sea el cliente, el proveedor con recusos o el propio desarrollador dedicando tiemp oa refactorizar o malgastando tiempo programando sobre un sistema frágil.

### Imprudente

El desarrollador actua de forma consciente e imprudente, genera un rpoyecto de mala calidad y poco tolerante al cambio. "No hay tiempo, solo copia y pega eso"

### Imprudente e Inadvertida 

Se genera por el desconocimiento o falta de experiencia, se genera por falsos seniors y juniors.

### Prudente

Se es consciente de la deuda y de las fallas del código, el peligro radica en que si no se paga a tiempo se deben pagar mas intereses despues. Es común cuando se llega a un punto del proyecto y se empiezan a generar TODOS para refactorizar en posteriores versiones. 

### Prudente e inadvertida

Pasa inadvertida hasta el final del desarrollo de la codificación del proyecto. ¿Vale la pena volverlo a hacer, cambiar de arquitectura o patron, o seguir adelante?

# Refactorización

Proceso que tiene como objetivo mejorar el código sin alterar su comportamiento para que sea mas entendible y tolerante a cambios. Usualmente es **imprescindible contar con pruebas automáticas**. 

# Clean Code

Si aparece la necesidad de comentar algo antes de la siguiente linea de código para explicar su funcionamiento, esto significa que esa línea de código realmente no está lo suficientemente clara.

## Nombres pronunciables y expresivos

Se prioriza el uso de camelCase o UpperCamelCase. Estos deben ser lo necesariamente largos (y cortos al mismo tiempo) como para entender cual es la función de la variable y que almacena.

### Ejercicio

Cambiar el nombre de estas variables por nombres mas descriptivos.

```
//día de hoy - today
const ddmmyyyy = new Date();

//dias transcurridos en días
const d: number = 23;
 
//número de archivos en un directorio
const dir = 33;

// primer nombre - first name
const nombre = 'Fernando';
 
// primer apellido - last name
const apellido = 'Herrera';

// días desde la última modificación - days since modification
const dsm = 12;

// cantidad máxima de clases por estudiante - max classes per student
const max = 6
```

#### Solución

```
//día de hoy - today
const today = new Date();

//dias transcurridos en días
const elapsedDays: number = 23;
 
//número de archivos en un directorio
const numberOfFilesInDirectory = 33;

// primer nombre - first name
const firstName = 'Fernando';
 
// primer apellido - last name
const lastName = 'Herrera';

// días desde la última modificación - days since modification
const daysSinceLastModification = 12;

// cantidad máxima de clases por estudiante - max classes per student
const maxSClassesPerStudent = 6
```
## Nombre según el tipo de dato

### Arreglos

Debido a que contienen usualmente varios elementos, es común elegir nombres en plural.

```
// malo
const fruit = ['manzana','platano','fresa'];

// regular 
const fruitList = ['manzana','platano','fresa'];

// bueno
const fruits = ['manzana','platano','fresa'];

//mejor (ya que en este caso, son solo strings. Si el arreglo fuese de objetos de tipo Fruta, el mejor nombre sería el anterior)
const fruitNames = ['manzana','platano','fresa'];
```

### Booleanos

Se usan prefijos como is, have, can. Se procura que su significado sea positivo y evitar las negaciones en el nombre. Una regla general es que si debo tomar unos segundos para poder determnar que tipo de dato contiene la variable, es porque es un mal nombre. 

Don't ❌

```
const open = true;
const write = true;
const fruit = true;
const active = true;
const voValues = true;
const notEmpty = true;
```

Better 🔥

```
const isOpen = true;
const canWrite = true;
const hasFruit = true;
const isActive = true;
const hasValues = true;
const isEmpty = true;
```

### Números

Se usan prefijos como min, max, total, off.


Don't ❌

```
const fruits = 3;
const cars = 5;
```

Better 🔥

```
const maxFruits = 5;
const minFruits = 1;
const totalFruits = 4;
const totalOfCars = 5;
const numberOfCars = 5;
```

### Números

Deben representar acciones, se contruyen a partir del verbo que representa la acción seguido de un sustanivo. Deben ser descriptivos y concisos, debe expesar lo que hace especificamente sin entrar en su implementación. Esto se debe a el **principio de responsabilidad única**.


Don't ❌

```
createUserIfNotExist();
updateUserIfNotEmpty();
sendEmailIfFieldsValid();
```

Better 🔥

```
createUser();
updateUser();
sendEmail();
```

### Ejercicio
Cambiar el nombre de las variables.

```
// arreglo de temperaturas celsius
const arrayOfNums = [33.6, 12.34];

// Dirección ip del servidor
const ip = '123.123.123.123';

// Listado de usuarios
const people = [{id: 1, email: 'fernando@google.com'},{ id: 2, email: 'juan@google.com' }, { id: 3, email: 'melissa@google.com' }];

// Listado de emails de los usuarios
const emails = people.map( u => u.email );

// Variables booleanas de un video juego
const jump = false;
const run = true;
const noTieneItems = true;
const loading = false;

// Otros ejercicios
// tiempo inicial
const start = new Date().getTime();
//....
// 3 doritos después
//...
// Tiempo al final
const end = new Date().getTime() - start;


// Funciones
// Obtiene los libros
function book() {
throw new Error('Function not implemented.');
}

// obtiene libros desde un URL
function BooksUrl( u: string) {
throw new Error('Function not implemented.');
}

// obtiene el área de un cuadrado basado en sus lados
function areaCuadrado( s: number ) {
throw new Error('Function not implemented.');
}

// imprime el trabajo
function printJobIfJobIsActive() {
throw new Error('Function not implemented.');
}
```

#### Solución

```
// arreglo de temperaturas celsius
const temperaturesInCelsius = [33.6, 12.34];

// Dirección ip del servidor
const serverIp = '123.123.123.123';

// Listado de usuarios
const users = [{id: 1, email: 'fernando@google.com'},{ id: 2, email: 'juan@google.com' }, { id: 3, email: 'melissa@google.com' }];

// Listado de emails de los usuarios
const userEmails = users.map( user => user.email );

// Variables booleanas de un video juego
const canJump = false;
const canRun = true;
const hasItems = false;
const isLoading = false;

// Otros ejercicios
// tiempo inicial
const startTime = new Date().getTime();
//....
// 3 doritos después
//...
// Tiempo al final
const timePassed = new Date().getTime() - start;


// Funciones
// Obtiene los libros
function getBooks() {
throw new Error('Function not implemented.');
}

// obtiene libros desde un URL
function getBooksFromURL( url: string) {
throw new Error('Function not implemented.');
}

// obtiene el área de un cuadrado basado en sus lados
function getSquareArea( side: number ) {
throw new Error('Function not implemented.');
}

// imprime el trabajo
function printJob() {
throw new Error('Function not implemented.');
}
```

### Nombres de las clases

Las clases deben tener nombes formados por sustantivos o frases de sustantivo. Se debe evitar **nombres genéricos para evitar que las clases realicen mas trabajo del que deberían hacer**. El nombre es lo mas importante de la clase. Se usa UpperCamelCase

Don't ❌

```
class Manager{};
class Data{};
class Info{};
class Individual{};
class Processor{};
```

Tampoco exagerar en la especificidad del nombre

```
class SpecialViewingCaseMonsterManagerEventsHandlerActivitySingleton{};
```

#### 3 preguntas para saber si es un buen nombre
- ¿Qué hace exactamene la clase?
- ¿Como exactamente esta clase realiza cierta tarea?
- ¿Hay algo específico sobre su ubicación?

## Nombres de funciones, argumentos y parámetros

> Sabemos que estamos desarrollando código limpio cuando cada función hace exactamente lo que su nombre indica

Se recomienda limitar a 3 parámetros posicionales

```
//ok

function sendEmail(toWhom:string,from:string,body:string):boolean{}

//not ok
function sendEmail(tohHom:string,from:string,body:string,subject:string,apikey:string):boolean{}

```

Se puede mejorar haciendo uso de una interfaz

```
interface SendEmailOptions {
toWhom: string;
from: string;
body: string;
subject: string;
apiKey: string;
}
function sendEmail({tohHom,from,body,subject,apikey}:SendEmailOptions):boolean{}
```


## Ausencia de información técnica en nombres

Esto aplica principalmente para clases, interfaces, etc. Se convierte en algo redundante pues la información usualmente ya vienen en alguna de las palablas reservadas del lenguaje de programación.
Don't ❌

>class UserClass{}
>
>interface UserInterface{}

Better 🔥

>class User{}
>
>interface User{}

### Ejercicio - Refactorizar funciones

Refactorizar el siguiente código para que las funciones sean mas fáciles de entender. El resultado debe ser el mismo antes y despues de la refactorización.
```
(() => {


    // Resolver sin la triple condicional dentro del if
    // includes? arrays?
    function isRedFruit( fruit: string ): boolean {
        
        if ( fruit === 'manzana' || fruit === 'cereza' || fruit === 'ciruela' ) {
            return true;
        } else {
            return false;
        }
    }

    // Simplificar esta función
    // switch? Object literal? validar posibles colores
    function getFruitsByColor( color: string ): string[] {

        if ( color === 'red' ) {
            return ['manzana','fresa'];
        } else if ( color === 'yellow') {
            return ['piña','banana'];
        } else if ( color === 'purple') {
            return ['moras','uvas']
        } else {
            throw Error('the color must be: red, yellow, purple');
        }
    }

    // Simplificar esta función
    let isFirstStepWorking  = true;
    let isSecondStepWorking = true;
    let isThirdStepWorking  = true;
    let isFourthStepWorking = true;

    function workingSteps() {
        if( isFirstStepWorking === true ) {
            if( isSecondStepWorking === true ) {
                if( isThirdStepWorking === true ) {
                    if( isFourthStepWorking === true ) {
                        return 'Working properly!';
                    }
                    else {
                        return 'Fourth step broken.';
                    }
                }
                else {
                    return 'Third step broken.';
                }
            }
            else {
                return 'Second step broken.';
            }
        }
        else {
            return 'First step broken.';
        }
    }


    // isRedFruit
    console.log({ isRedFruit: isRedFruit('cereza'), fruit: 'cereza' }); // true
    console.log({ isRedFruit: isRedFruit('piña'), fruit: 'piña' }); // true

    //getFruitsByColor
    console.log({ redFruits: getFruitsByColor('red') }); // ['manzana', 'fresa']
    console.log({ yellowFruits: getFruitsByColor('yellow') }); // ['piña', 'banana']
    console.log({ purpleFruits: getFruitsByColor('purple') }); // ['moras', 'uvas']
    // console.log({ pinkFruits: getFruitsByColor('pink') }); // Error: the color must be: red, yellow, purple

    // workingSteps
    console.log({ workingSteps: workingSteps() }); // Cambiar los valores de la línea 31 y esperar los resultados


})();
```
#### Solución
```
(() => {

    // Resolver sin la triple condicional dentro del if
    // includes? arrays?
    function isRedFruit(fruit: string): boolean {
        const redFruits = ['manzana', 'cereza', 'ciruela'];
        return redFruits.includes(fruit);
    }

    // Simplificar esta función
    // switch? Object literal? validar posibles colores
    function getFruitsByColor(color: string): string[] {
        const availableColors = ['red', 'yellow', 'purple'];
        if (!availableColors.includes(color)) {
            throw Error('the color must be: red, yellow, purple');
        }
        switch (color) {
            case 'red':
                return ['manzana', 'fresa'];
            case 'yellow':
                return ['piña', 'banana'];
            case'purple':
                return ['moras', 'uvas']
        }
    }

    // Simplificar esta función

    let stepsStatus = [
        {
            name: 'first step',
            status: true
        },
        {
            name: 'second step',
            status: true
        },
        {
            name: 'third step',
            status: true
        },
        {
            name: 'fourth step',
            status: true
        },
    ]

    function workingSteps() {
        stepsStatus.forEach(function (step) {
            if (!step.status) {
                return `${step.name} is broken`;
            }
        });
        return 'Working properly'
    }


    // isRedFruit
    console.log({isRedFruit: isRedFruit('cereza'), fruit: 'cereza'}); // true
    console.log({isRedFruit: isRedFruit('piña'), fruit: 'piña'}); // true

    //getFruitsByColor
    console.log({redFruits: getFruitsByColor('red')}); // ['manzana', 'fresa']
    console.log({yellowFruits: getFruitsByColor('yellow')}); // ['piña', 'banana']
    console.log({purpleFruits: getFruitsByColor('purple')}); // ['moras', 'uvas']
    // console.log({ pinkFruits: getFruitsByColor('pink') }); // Error: the color must be: red, yellow, purple

    // workingSteps
    console.log({workingSteps: workingSteps()}); // Cambiar los valores de la línea 31 y esperar los resultados
    
})();
```



