# Tema 2 — Variables y operadores

## Índice
1. [Variables: cajas con nombre](#1-variables-cajas-con-nombre)
2. [Nombres de variables](#2-nombres-de-variables)
3. [Tipos de datos básicos](#3-tipos-de-datos-básicos)
4. [Operadores aritméticos](#4-operadores-aritméticos)
5. [Operadores de comparación](#5-operadores-de-comparación)
6. [Precedencia: qué se calcula primero](#6-precedencia-qué-se-calcula-primero)
7. [Comparar texto: `equals()`, no `==`](#7-comparar-texto-equals-no-)
8. [Errores típicos](#8-errores-típicos)
---

## 1. Variables: cajas con nombre

Una variable es una **caja con nombre** donde se guarda un dato para usarlo después.
Regla de oro: **antes de usarla hay que declararla**, indicando su tipo.

```java
int edad;              // declaración (sin valor todavía)
edad = 16;              // asignación

int cursoActual = 2;   // declaración + asignación en una línea
```

- El **tipo** no cambia nunca (una `int` siempre guarda enteros).
- El **valor** sí puede cambiar a lo largo del programa.
- Una variable sin valor asignado no se puede usar — el compilador da error.

---

## 2. Nombres de variables

| Nombre | ¿Válido? | Por qué |
|---|---|---|
| `edad` | ✅ | Claro y en minúscula |
| `nombreCompleto` | ✅ | Varias palabras: la segunda empieza en mayúscula |
| `precio2` | ✅ | Puede llevar números, pero no empezar por uno |
| `2precio` | ❌ | No puede empezar por un número |
| `mi edad` | ❌ | No puede tener espacios |
| `precio-total` | ❌ | No puede llevar guiones |
| `class` | ❌ | Es una palabra reservada de Java |

Java distingue mayúsculas: `edad` y `Edad` son dos variables distintas.

---


## 3. Tipos de datos básicos

| Tipo | Guarda | Ejemplos |
|---|---|---|
| `int` | Números enteros | `5`, `-3`, `100` |
| `double` | Números con decimales | `3.14`, `-7.89` |
| `char` | Un solo carácter (comillas simples) | `'a'`, `'+'`, `'1'` |
| `boolean` | Verdadero o falso | `true`, `false` |
| `String` | Cadena de texto (comillas dobles) | `"Hola"`, `"Celia"` |

```java
int edad = 18;
double precio = 9.99;
char inicial = 'A';
boolean aprobado = true;
String nombre = "Juan";
```

> ⚠️ `char` va con comillas **simples** y un solo carácter. `String` va con comillas
> **dobles** y puede tener cualquier longitud.

De momento vamos a trabajar con valores **fijos**, escritos directamente en el código. A esos valores (18, 9.99, 'A', "Juan", true) se les llama **literales**.
Pedirlos por teclado lo vemos en el Tema 3, con `Scanner`.

---

## 4. Operadores aritméticos

| `+` | `-` | `*` | `/` | `%` |
|---|---|---|---|---|
| suma | resta | multiplicación | división | resto (módulo) |

```java
int a = 7;
int b = 2;

System.out.println(a + b);   // 9
System.out.println(a - b);   // 5
System.out.println(a * b);   // 14
System.out.println(a / b);   // 3  (división entera: se pierden los decimales)
System.out.println(a % b);   // 1  (resto de 7 entre 2)
```

> ⚠️ Si **los dos operandos son `int`**, la división descarta los decimales. Para
> obtener el resultado decimal, hace falta que al menos uno sea `double`
> (`(double) a / b` → `3.5`). Lo veremos a fondo en el Tema 4.

**Concatenar texto con `+`:**

```java
String nombre = "Ana";
int edad = 16;
System.out.println("Me llamo " + nombre + " y tengo " + edad + " años");
```

---

## 5. Operadores de comparación

El resultado siempre es `boolean` (`true`/`false`):

| `>` | `<` | `==` | `!=` | `>=` | `<=` |
|---|---|---|---|---|---|
| mayor | menor | igual a | distinto de | mayor o igual | menor o igual |

```java
int a = 7, b = 2;
System.out.println(a > b);    // true
System.out.println(a == b);   // false
```

> Existen también los operadores **lógicos** (`&&`, `||`, `!`) y los de **incremento**
> (`++`, `+=`). Los veremos con el `if` y los bucles.

---

## 6. Precedencia: qué se calcula primero

Igual que en matemáticas: primero `*`, `/`, `%` y después `+`, `-`. Los **paréntesis**
mandan sobre todo, y a igual prioridad se va de izquierda a derecha.

```java
System.out.println(2 + 3 * 4);     // 14  (primero 3 * 4)
System.out.println((2 + 3) * 4);   // 20  (primero el paréntesis)
System.out.println(10 - 4 - 3);    // 3   (de izquierda a derecha: (10 - 4) - 3)
```

> 💡 Ante la duda, usa paréntesis.

---

## 7. Comparar texto: `equals()`, no `==`

```java
String a = "Hola";
String b = "Hola";

System.out.println(a == b);        // ⚠️ no fiable para comparar contenido
System.out.println(a.equals(b));   // ✅ true — esta es la forma correcta
System.out.println(a.equals("hola"));   // false — distingue mayúsculas/minúsculas
```

> 💡 **Para memorizar:** los `String` se comparan con `.equals()`. El `==` en números
> y `char` sí funciona bien; en `String` no es fiable.

---

## 8. Errores típicos

| Error | Causa |
|---|---|
| `variable edad might not have been initialized` | Usaste la variable antes de darle un valor |
| `incompatible types: possible lossy conversion` | Metes un `double` en una variable `int` sin conversión (Tema 4) |
| `7 / 2` da `3` en vez de `3.5` | División entre dos `int` — no es un error, es cómo funciona |




