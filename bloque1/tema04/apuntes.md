# Tema 4 — Conversión de tipos y operadores lógicos

## Índice
1. [Conversión implícita](#1-conversión-implícita)
2. [Conversión explícita (casting)](#2-conversión-explícita-casting)
3. [Letras y números: `char` ↔ `int`](#3-letras-y-números-char--int)
4. [Convertir texto a número](#4-convertir-texto-a-número)
5. [Tipo lógico: `&&`, `||`, `!`](#5-tipo-lógico----)
6. [Errores típicos](#6-errores-típicos)

---

## 1. Conversión implícita

Java convierte automáticamente un tipo "pequeño" a uno "más grande" sin que lo pidas,
porque no se pierde información:

```java
int entero = 10;
double decimal = entero;   // conversión automática: 10 → 10.0
```

```
int → double
```

---

## 2. Conversión explícita (casting)

Al revés —de "grande" a "pequeño"— Java **no** lo hace solo, porque se puede perder
información. Hay que pedirlo con un *casting*: `(tipo) valor`

```java
double decimal = 9.75;
int entero = (int) decimal;   // 9  -> se trunca, no redondea
```

Sirve también para obtener decimales en una división:

```java
int a = 7;
int b = 4;
System.out.println((a + b) / 2);            // 5    (división entera)
System.out.println((double) (a + b) / 2);   // 5.5  (casting antes de dividir)
```

> ⚠️ El *casting* de `double` a `int` **trunca**: `(int) 9.99` da `9`, no `10`.
> Para redondear: `Math.round(9.75)` da `10`.

---

## 3. Letras y números: `char` ↔ `int`

Cada letra tiene un número asociado (su código):

```java
char letra = 'A';
int codigo = letra;                       // 65  (conversión automática)
char siguiente = (char) (letra + 1);      // 'B' (hay que hacer casting)

System.out.println(codigo);               // 65
System.out.println(siguiente);            // B
System.out.println((int) 'a');            // 97
```

> ⚠️ `letra + 1` es un número, no una letra: `System.out.println(letra + 1)` muestra
> `66`. Para obtener `B` hay que hacer `(char) (letra + 1)`.

---

## 4. Convertir texto a número

Cuando lees con `sc.nextLine()` obtienes un `String`. Para operar con él, hay que
convertirlo:

```java
String texto = "25";
int numero = Integer.parseInt(texto);          // String → int
double decimal = Double.parseDouble("3.5");    // String → double

// Al revés, número → texto:
int edad = 16;
String textoEdad = String.valueOf(edad);       // int → String
```

---

## 5. Tipo lógico: `&&`, `||`, `!`

Un `boolean` solo vale `true` o `false`. Los **operadores lógicos** combinan valores
`boolean` y devuelven otro `boolean`:

| Operador | Se lee | Da `true` cuando... |
|---|---|---|
| `&&` | **y** (and) | las **dos** condiciones son `true` |
| `\|\|` | **o** (or) | **al menos una** es `true` |
| `!` | **no** (not) | invierte el valor: `true` → `false` |

**Tablas de verdad** (`V` = true, `F` = false):

| a | b | `a && b` | `a \|\| b` |
|---|---|---|---|
| V | V | V | V |
| V | F | F | V |
| F | V | F | V |
| F | F | F | F |

| a | `!a` |
|---|---|
| V | F |
| F | V |

```java
int edad = 17;
boolean tienePermiso = true;

System.out.println(edad >= 16 && tienePermiso);   // true  (las dos se cumplen)
System.out.println(edad >= 18 || tienePermiso);   // true  (basta con una)
System.out.println(!tienePermiso);                // false (lo contrario)
```

> 💡 Se usan sobre todo en el `if` y en los bucles, que veremos en el Bloque 2. Aquí
> solo practicamos a calcular su resultado.

---

## 6. Errores típicos

| Error | Causa |
|---|---|
| `incompatible types: possible lossy conversion from double to int` | Falta el casting `(int)` al pasar de `double` a `int` |
| `NumberFormatException` | `Integer.parseInt("hola")`: el texto no es un número válido |
| `(int) 9.99` da `9`, no `10` | El casting trunca, no redondea |
| `'A' + 1` da `66`, no `B` | Sumar a un `char` da un número; hay que hacer `(char)` |
| `a & b` o `a | b` en vez de `&&` / `||` | Son operadores distintos; para condiciones usa siempre los dobles |

