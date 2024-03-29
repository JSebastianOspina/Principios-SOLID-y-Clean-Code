# Principios-SOLID-y-Clean-Code
Notas de clase del curso de Principios SOLID y Clean Code de Fernando Herrera en Udemy

> "Nuestro código tiene que ser simple y directo, debería leerse con la misma facilidad que un texto bien escrito"
> 
> "Código limpio es el que se ha escrito con la intención de que otra persona (o tu mismo) lo entienda."

# Table of contents

- [Principios-SOLID-y-Clean-Code](#principios-solid-y-clean-code)
- [Deuda técnica](#deuda-técnica)
  - [Esquema de deuda técnica de Martin Fowler](#esquema-de-deuda-técnica-de-martin-fowler)
    - [Imprudente](#imprudente)
    - [Imprudente e Inadvertida](#imprudente-e-inadvertida)
    - [Prudente](#prudente)
    - [Prudente e inadvertida](#prudente-e-inadvertida)
- [Refactorización](#refactorizacin)
- [Clean Code](#clean-code)
  - [Nombres pronunciables y expresivos](#nombres-pronunciables-y-expresivos)
    - [Ejercicio](#ejercicio)
      - [Solución](#solucin)
  - [Ausencia de información técnica en nombres](#ausencia-de-información-técnica-en-nombres)
  - [Nombre según el tipo de dato](#nombre-según-el-tipo-de-dato)
    - [Arreglos](#arreglos)
    - [Booleanos](#booleanos)
    - [Números](#nmeros)
    - [Funciones](#funciones)
      - [Ejercicio - Refactorizar funciones](#ejercicio---refactorizar-funciones)
        - [Solución](#solucin)
    - [Ejercicio](#ejercicio)
      - [Solución](#solucin)
    - [Nombres de las clases](#nombres-de-las-clases)
      - [3 preguntas para saber si es un buen nombre](#3-preguntas-para-saber-si-es-un-buen-nombre)

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

### Funciones

> Sabemos que estamos desarrollando código limpio cuando cada función hace exactamente lo que su nombre indica

Deben representar acciones, se contruyen a partir del verbo que representa la acción seguido de un sustanivo. Deben ser descriptivos y concisos, debe expesar lo que hace especificamente sin entrar en su implementación. Esto se debe a el **principio de responsabilidad única**.

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

#### Ejercicio - Refactorizar funciones

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

##### Solución

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
        const fruitsByColor = {
            'red': ['manzana', 'fresa'],
            'yellow': ['piña', 'banana'],
            'purple': ['moras', 'uvas']
        }
        if (!Object.keys(fruitsByColor).includes(color)) {
            throw Error('the color must be: red, yellow, purple');
        }
        // @ts-ignore
        return fruitsByColor[color];
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
        // @ts-ignore
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

#### 3 preguntas para saber si es un buen nombre
- ¿Qué hace exactamene la clase?
- ¿Como exactamente esta clase realiza cierta tarea?
- ¿Hay algo específico sobre su ubicación?

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

## Principio DRY
> Don't repeat yourself

- Consiste en evitar la duplicidad de código.
- Simplifica las pruebas
- Ayuda a centralizar procesos
- Aplicar el principio DRY, usualmente lleva a refactorizar.

```
type Size = '' | 'S' | 'M' | 'XL';

class Product {
    constructor(
        public name: string = '',
        public price: number = 0,
        public size: Size = '',
    ) {
    }

    badToString() {
        //Estas validaciones deberían estar centralizadas, siempre que haya
        // una nueva propiedad se duplica el codigo. NO DRY!!
        if (this.name.length === 0) throw Error('Name is empty');
        if (this.price <= 0) throw Error('Price is zero');
        if (this.size.length === 0) throw Error('size is empty');
        return `${this.name} (${this.price}), ${this.size}`;

    }

    isProductReady(): boolean {
        for (const property in this) {
            switch (typeof this[property]) {
                case "string":
                    // @ts-ignore
                    if (this[property].length === 0) throw Error(`${property} is empty`);
                    break;
                case "number":
                    // @ts-ignore
                    if (this[property] <= 0) throw Error(`${property} is zero`);
                    break;
                default:
                    throw Error(`type of ${property} is not supported`);
            }
        }
        return true;
    }

    toString() {
        if (!this.isProductReady()) return;
        return `${this.name} (${this.price}), ${this.size}`;
    }
}

(() => {
    const bluePants = new Product('Pantalones', 10, 'M');
    console.log(bluePants.toString());
})();
```
## Comentarios
"No comentes el código mal escrito, reescríbelo"
Se deben evitar a toda costa, pues el código debe ser suficientemente autoexplicativo.  Sin embargo, cuando usamos librerías de terceros, APIS, frameworks, nos encontraremos ante situaciones en las que escribir un comentario será mejor que dejar una solución compleja o un hack sin explicación. 

Se debe comentar **¿El por qué?** en lugar del **¿Qué o ¿cómo?**

## Uniformidad en el proyecto
Ante problemas similares, hay que aplicar soluciones similares.  Esto aplica para el codigo, la estructura de las carpetas, el nombre de los archivos. También debe identarse de misma manera. 

## Clases
### Estrucura recomendada para las clases
#### Lista de propiedades
1) Las propiedades estáticas.
2) Las propiedades públicas.
3) Las propiedades privadas.

#### Lista de métodos
1) Constructores estáticos.
2) Luego el constructor.
3) Métodos estáticos.
3) Métodos privados.
5) Resto de metodos de instancia ordenados de mayor a menor importancia.
6) Finalmente getters y setters. 

![Ejemplo de correcta estrucura de una clase](https://user-images.githubusercontent.com/55632072/218136194-231f2884-562d-4665-b2df-6cad563b0476.png)

### Herencia

Es dificil cumplir con el principio de responsabilidad única cuando una clase hereda de otra, pues se vuelve ahora una nueva responsabilidad de la clase poder instanciar a su padre através de la palabra clave super. A continuación un ejemplo en typescript que muestra como la herencia termina generando un constructor de gran tamaño para las clases hijo. 

```
(() => {
    type Gender = 'M' | 'F';

    class Person {
        public name: string;
        public gender: Gender;
        public birthdate: Date;

        constructor(name: string, gender: Gender, birthdate: Date) {
            this.name = name;
            this.gender = gender;
            this.birthdate = birthdate;
        }
    }

    class User extends Person {
        public lastAccess: Date;

        constructor(
            public email: string,
            public role: string,
            name: string,
            gender: Gender,
            birthdate: Date
        ) {
            super(name, gender, birthdate);
            this.lastAccess = new Date();
        }

        checkCredentials() {
            return true;
        }

    }

    class UserSettings extends User {
        constructor(
            public workingDirectory: string,
            public lastOpenFolder: string,
            email: string,
            role: string,
            name: string,
            gender: Gender,
            birthdate: Date
        ) {
            super(email, role, name, gender, birthdate);

        }
    }

    const newPerson = new Person('Sebas', 'M', new Date('1999-06-03'));
    const userSettings = new UserSettings(
        '/usr/home',
        '/home',
        's@s.com',
        'Admin',
        'Fernando',
        'M',
        new Date(),
    )
    console.log(userSettings);
})();

```

Para solucionar esto en cierta medida, es posible enviar objetos como argumentos, pues es evidente que este gran numero de parámetros posicionales no es óptimo. 
```
(() => {

    // No aplicando el principio de responsabilidad única

    type Gender = 'M'|'F';

    interface PersonProps {
        birthdate : Date;
        gender    : Gender;
        name      : string;
    }

    class Person {
        public birthdate: Date;
        public gender   : Gender;
        public name     : string;

        constructor({ name, gender, birthdate }: PersonProps ){
            this.name      = name;
            this.gender    = gender;
            this.birthdate = birthdate;
        }
    }


    interface UserProps {
        birthdate : Date;
        email     : string;
        gender    : Gender;
        name      : string;
        role      : string;
    }

    class User extends Person {

        public email: string;
        public role : string;
        public lastAccess: Date;

        constructor({
                        birthdate,
                        email,
                        gender,
                        name,
                        role,
                    }: UserProps ) {
            super({ name, gender, birthdate });
            this.lastAccess = new Date();
            this.email = email;
            this.role  = role;
        }

        checkCredentials() {
            return true;
        }
    }


    interface UserSettingsProps {
        birthdate        : Date;
        email            : string;
        gender           : Gender;
        lastOpenFolder   : string;
        name             : string;
        role             : string;
        workingDirectory : string;
    }

    class UserSettings extends User {

        public workingDirectory: string;
        public lastOpenFolder  : string;

        constructor({
                        workingDirectory,
                        lastOpenFolder,
                        email,
                        role,
                        name,
                        gender,
                        birthdate,
                    }: UserSettingsProps ) {
            super({ email, role, name, gender, birthdate });
            this.workingDirectory = workingDirectory;
            this.lastOpenFolder   = lastOpenFolder;
        }
    }


    const userSettings = new UserSettings({
        birthdate: new Date('1985-10-21'),
        email: 'fernando@google.com',
        gender: 'M',
        lastOpenFolder: '/home',
        name: 'Fernando',
        role: 'Admin',
        workingDirectory: '/usr/home',
    });

    console.log({ userSettings });


})();
```

Sin embargo, esto aún no cumple el principio de responsabilidad única, ademas de que siempe se debe **priorizar la composición frente a la herencia**
Para solucionarlo, se pueden crear clases de tipo "composisicón" que se encarguen de relacionar estas dos clases. 


# STUPID
Hmm, huele feo... ¿Que será? es un acromico para referirse a 6 Code Smells
Singleton: patrón singleton
Tight Coupling: alto acoplamiento
Untestability: Codigo no probable (unit test) 
Premature optimization: optimizaciones prematuras
Indescriptive Naming: nombres pocos descriptivos
Duplication: duplicidad de código, no aplicar el principio DRY.

## Singleton
Hace referencia a el uso del patrón singleton.
### Pros
Garantiza una única instancia de la clase a lo largo de toda la aplicación. 
### Contras
- Vive en el contexto global.
- Puede ser modificado por cualquiera en cualquier momento, lo que lo hace no rastreable.
- Dificil de testear debido a su ubicación.

## Tight Coupling: alto acoplamiento
"Queremos diseñar componentes que sean auto-contenidos, auto suficientes e independientes. Con un objetivo y un propósito bien definido". - The pragmatic Programmer.
Lo ideal es tener bajo acoplamiento y una buena cohesión. 

**Cohesión** se refiere a lo que la clase (o modulo) puede hacer. 
La baja cohesion significaría que la clase realiza una gran variedad de acciones: es amplia: no se enfoca en lo que debe hacer. 
Alta cohesión significa que la clase se enfoca en lo que debería estar haciendo, es decir, solo métodos relacionados con la intención de la clase. 

**Acoplamiento** cuán relacionadas o dependientes son dos clases o modulos entre si. 
En **bajo acoplamiento** cambiar algo importante en una clase no debería afectar a la otra.
**En alto acoplamiento** dificultará el cambio y el mantenimiento de su código; dado que las clases están muy unidas, hacer un cambio podría requerir una renovación completa del sistema. 

![imagen](https://user-images.githubusercontent.com/55632072/218197386-ce94238d-f512-4a50-ab8f-f2888f5affb8.png)

### Desventajas
- Un cambio en un modulo por lo general rpovoca un efecto domino de los cambios en otros modulos.
- El ensamblaje de modulos puede requerir mas esfuerzo y tiempo debido a la mayor dependencia entre modulos.
- Un módulo en particular puede ser mas dificil de reutilizar y/o problar porque se deben incluir módulos dpeendientes. 

### Posibles soluciones
- A tiene un atributo que se refiere a B
- A llama a los servicios de un objeto B
- A tiene un método que hace referencia a B (a través del tipo de retorno o parámetro)
- A es una subclase de (o implementa) la clase B.
