# Principios-SOLID-y-Clean-Code
Notas de clase del curso de Principios SOLID y Clean Code de Fernando Herrera en Udemy

> "Nuestro código tiene que ser simple y directo, debería leerse con la misma facilidad que un texto bien escrito"
> 
> "Código limpio es el que se ha escrito con la intención de que otra persona (o tu mismo) lo entienda."
# Deuda técnica

Falta de calidad en alguna parte de del código de nuestra aplicación. Esto genera un costo económico a futuro, que termina pagándose con mas tiempo invertido tratando de comprender el codigo, refactorizarlos, transferencia del código y solucionar los problemas generados en etapas mas tempranas del desarrollo. 

## Esquema de deuda técnica de Martin Fowler

Caer en deuda técnicas es normal y a menudo es inevitable. Un buen programador es consciente de ella y se preocupa por pagarla. La deuda técnica se paga **refactorizando** el código. 

La mala calidad en el software siempre la acaba asumiendo alguien, ya sea el cliente, el proveedor con recusos o el propio desarrollador dedicando tiemp oa refactorizar o malgastando tiempo programando sobre un sistema frágil.

### Imprudente

El desarrollador actua de forma consciente e imprudente, genera un rpoyecto de mala calidad y poco tolerante al cambio. "No hay tiempo, solo copia y pega eso"

### Imprudente + Inadvertida 

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
const write = = true;
const fruit = true;
const active = true;
const voValues = true;
const notEmpty = true;
```

Better 🔥

```
const isOpen = true;
const canWrite = = true;
const hasFruit = true;
const isActive = true;
const hasValues = true;
const isEmpty = true;
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





