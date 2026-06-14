# Lemoncode_Modulo_4-2-_Angular
Módulo 4.2 - Frameworks - Angular

# Master Continuo - Laboratorio - Módulo 4.2 - Frameworks - Angular

# Laboratorio

> Solamente el primer ejercicio es obligatorio.

> El resto de ejercicios son opcionales.

> Los puntos etiquetados como **"reto"** también son opcionales.

---

# OBLIGATORIO - Layout completo de mini-aplicación

## En este ejercicio se practica:

* CLI para crear componentes y servicios.
* Añadir Angular Material al proyecto.
* Diseño del layout completo de una aplicación.
* Programación de un servicio para gestionar el estado de la aplicación.
* Inyección de servicios.
* Routing.
* Formulario.

### Ejemplo modelo

https://carherco.es/curso-angular-ejercicio-final

> Este ejemplo modelo es similar pero no es exacto. Es para tener una idea. Lo que se pide realmente es lo que está escrito en el enunciado de este documento.

---

## 1. Crea un nuevo proyecto de Angular con routing y con estilos scss.

---

## 2. Añade Angular Material

https://material.angular.io/guide/getting-started

> Este punto es mejor hacerlo nada más empezar que una vez terminada la mini-aplicación.

---

## 3. Crea los componentes necesarios para crear el layout que se describe a continuación

Tendrás componentes de layout:

* Cabecera pública
* Cabecera privada
* Pie
* Menú público
* Menú privado

Y componentes enrutados:

* Home
* Login
* Acerca de
* Galería

Esta aplicación tendrá **2 menús**:

### Menú público

Se mostrará cuando el usuario todavía no haya hecho login.

#### Enlaces

* Home ⇒ Te lleva a la página de bienvenida de la aplicación
* Login ⇒ Te lleva a un formulario de login
* Acerca de ⇒ Te lleva a la página “Acerca de”

### Menú privado

Se mostrará cuando el usuario haya hecho login.

#### Enlaces

* Dashboard
* Galería
* CRUD
* Profile

Deberá aparecer un logo y el nombre de la web en la cabecera y algún contenido estático en el pie.

---

## 4. Configura el routing

Configura el routing para asignar una URL a cada una de las 7 páginas de los menús.

Puedes enseñar (de momentos) los dos menús simultáneamente en la pantalla para comprobar que funcionan.

Los componentes todavía no tienen ningún contenido.

No hay que programarlos.

En este punto basta con que existan y se muestre su contenido por defecto:

```text
xxxxxx works
```

---

## 5. Crea un formulario de login

Con 2 campos:

* username
* password

Pon validaciones y mensajes de error.

Al hacer submit del formulario, el componente invocará al método `login()` del servicio descrito en el siguiente punto.

---

## 6. Crea un servicio Auth

Gestionará el estado relacionado con la autenticación del usuario.

Debe ofrecer cuatro métodos:

```ts
login({username: string, password: string}): boolean
logout(): void
isLogged(): boolean
getUsername(): string
```

El método de login devolverá `true` para la combinación válida:

```text
username = master@lemoncode.net
password = 12345678
```

Para el resto de combinaciones devolverá `false`.

> Un simple if es suficiente para esta simulación de login.

Si la combinación válida sugerida no cumpliera las validaciones del formulario, podéis utilizar cualquier otra combinación válida que se adapte a vuestro caso.

---

## 7. Modifica el componente de login

Si al invocar al servicio de login éste devuelve `true`, el componente redirigirá al usuario al dashboard.

---

## 8. Mostrar menú según autenticación

Mostrar solamente:

* Menú público si el usuario no está logueado.
* Menú privado si el usuario sí está logueado.

---

## 9. Añade un botón de salir

En la cabecera de la web.

Solamente se mostrará si el usuario está logueado.

---

## 10. Mostrar username

También en la cabecera y solamente cuando el usuario esté logueado, mostrar el username del usuario.

---

## 11. RETO

Añade persistencia al estado de autenticación guardando el estado en el localStorage.

---

# OPCIONAL: Galería de fotos

## En este ejercicio se practica

* Binding
* Directivas estructurales
* Utilización del directorio assets

Se trata de programar una galería de fotos en el componente Galería del ejercicio anterior.

### Ejemplo modelo

https://carherco.es/curso-angular/#/galeria

> Este ejemplo modelo es similar pero no es exacto. Es para tener una idea. Lo que se pide realmente es lo que está escrito en el enunciado de este documento.

**NOTA:** Este ejercicio se puede programar en un componente del proyecto anterior o también se puede programar en un proyecto nuevo.

---

## 1. Descarga al menos 8 fotos

Ponlas en el directorio:

```text
src/assets
```

Dentro de `src/assets` puedes crear subdirectorios si así lo deseas.

Desde el HTML puedes enlazar las imágenes de la siguiente forma:

```html
<img src="assets/...." />
```

---

## 2. Crea una lista (array)

Objetos del tipo:

```ts
{
  id: number,
  src: string,
  title: string
}
```

Puedes crear la lista en:

* Un archivo
* Un servicio
* El propio componente

Pero sea como sea, al final del todo esa lista tiene que llegar a una propiedad pública del componente Galería.

---

## 3. La galería de fotos constará de 3 partes

### Imagen seleccionada

Una parte con la lista de todas las imágenes (en pequeño) de la galería.

### Listado de imágenes

Una parte en la que se muestre en grande una de las fotos.

### Botonera

Una botonera con 6 botones:

* Anterior
* Siguiente
* Aumentar
* Disminuir
* Play
* Stop

Crear la estructura HTML para mostrar esas 3 partes/bloques en pantalla.

---

## 4. Programa la galería

### Funcionalidades

* Al empezar, se mostrará una de las imágenes en la parte de Imagen seleccionada.
* Al hacer click en una imagen de la lista, la imagen correspondiente se mostrará en la parte de imagen seleccionada.
* Al hacer click en el botón siguiente, se cambiará la imagen seleccionada por la siguiente de la lista.
* Se pondrá `disabled` el botón siguiente cuando la imagen seleccionada sea la última de la lista.
* Al hacer click en el botón anterior, se cambiará la imagen seleccionada por la anterior de la lista.
* Se pondrá `disabled` el botón anterior cuando la imagen seleccionada sea la primera de la lista.
* Al hacer click en el botón Aumentar, se agrandará el tamaño de la imagen seleccionada.
* Al hacer click en el botón Disminuir, se reducirá el tamaño de la imagen seleccionada.
* Al hacer click en el botón Play, se pondrá en marcha el reproductor.
* La imagen seleccionada empezará a cambiar cada 2 segundos.
* Cuando el reproductor llegue a la última imagen volverá a empezar por la primera.
* Al hacer click en el botón Stop, se detendrá el reproductor.
* El botón Stop solamente se mostrará cuando esté en marcha el reproductor.
* El botón Play solamente se mostrará cuando el reproductor esté detenido.

### RETOS

#### Remarcar imagen seleccionada

Remarcar con estilos CSS la imagen de la lista que corresponda con la imagen actualmente seleccionada.

#### Paginación

Mostrar las imágenes de 3 en 3.

Añadir un botón:

* Anterior
* Siguiente

Para avanzar o retroceder de página.

### Ayuda

```html
<img *ngFor="let image of images | slice:3:6" />
```

La pipe slice haría return de los elementos:

```text
3, 4 y 5
```

del array `images`.

```text
slice:0:3
slice:3:6
slice:6:9
```

---

# Directiva: Rotate

## Crear una directiva para rotar imágenes

### En este ejercicio se practica

* Creación de una directiva personalizada
* Parametrización de directivas con @Input
* Binding de eventos con @HostListener
* Ciclo de vida: ngOnInit()

### Ejemplo modelo

https://carherco.es/curso-angular/#/rotate

> Este ejemplo modelo es similar pero no es exacto. Es para tener una idea. Lo que se pide realmente es lo que está escrito en el enunciado de este documento.

### Interfaz de uso

```html
<img rotate src="..." />

<img rotate="45" src="..." />

<img rotate="45" step="15" src="..." />
```

### Funcionalidad

* Al hacer click en una imagen que tenga el atributo rotate, la imagen deberá rotar los grados indicados en el atributo step.
* Por defecto rotará en pasos de 10 grados.
* Se le podrá indicar una rotación inicial en el propio atributo rotate.
* Si se hace click en la imagen con la tecla mayúsculas pulsada, la imagen rotará hacia el lado contrario.

### Ayuda

```css
img {
  transform: rotate(20deg);
}
```

Mostraría los elementos img girados 20 grados.

### RETO

* Probar la directiva en elementos que no sean imágenes.
* Modificar el selector para que solamente afecte a elementos `img`.

---

# OPCIONAL: Uso de RxJs

## 1. Modifica el método login()

El servicio quedaría así:

```ts
login({username: string, password: string}): Observable<boolean>
logout(): void
isLogged(): boolean
getUsername(): string
```

### AYUDA

```ts
import { of } from 'rxjs';

return of(true);
return of(false);
```

---

## 2. Adapta el componente de login

La respuesta de `login()` ya no llega directamente como boolean, sino como observable.

El componente tendrá que suscribirse al observable para conocer si el login ha ido bien o no.

---

## 3. Simula un delay en la respuesta del login

### AYUDA

```ts
import { delay } from 'rxjs';

return of(true).pipe(delay(2000));
return of(false).pipe(delay(2000));
```

---

## 4. Indicador de carga

Pon un indicador (un gif de loading) en el formulario de login que:

* Se muestre al darle al botón submit.
* Desaparezca cuando el método login haya emitido su respuesta.

### AYUDA

Como el observable emite un dato y acto seguido directamente la señal de completado/fin, puedes utilizar tanto la primera función del subscribe (la del next) como la tercera función del subscribe (la del completed) para esconder el gif.
