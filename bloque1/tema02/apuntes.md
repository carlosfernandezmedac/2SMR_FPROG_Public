# Tema 2 — Variables y operadores

RA1 (CE d, e, f, g)

## Índice
1. [Variables: cajas con nombre](#1-variables-cajas-con-nombre)
2. [Tipos de datos básicos](#2-tipos-de-datos-básicos)
3. [Operadores aritméticos](#3-operadores-aritméticos)
4. [Operadores de comparación](#4-operadores-de-comparación)
5. [Comparar texto: `equals()`, no `==`](#5-comparar-texto-equals-no-)
6. [Errores típicos](#6-errores-típicos)

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

## 2. Tipos de datos básicos

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

De momento vamos a trabajar con valores **fijos**, escritos directamente en el código.
Pedirlos por teclado lo vemos en el Tema 3, con `Scanner`.

---

## 3. Operadores aritméticos

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

## 4. Operadores de comparación

El resultado siempre es `boolean` (`true`/`false`):

| `>` | `<` | `==` | `!=` | `>=` | `<=` |
|---|---|---|---|---|---|
| mayor | menor | igual a | distinto de | mayor o igual | menor o igual |

```java
int a = 7, b = 2;
System.out.println(a > b);    // true
System.out.println(a == b);   // false
```

---

## 5. Comparar texto: `equals()`, no `==`

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

## 6. Errores típicos

| Error | Causa |
|---|---|
| `variable edad might not have been initialized` | Usaste la variable antes de darle un valor |
| `incompatible types: possible lossy conversion` | Metes un `double` en una variable `int` sin conversión (Tema 4) |
| `7 / 2` da `3` en vez de `3.5` | División entre dos `int` — no es un error, es cómo funciona |

---

Casos prácticos y ejercicios: [`casos-practicos.md`](casos-practicos.md) · [`ejercicios.md`](ejercicios.md)
