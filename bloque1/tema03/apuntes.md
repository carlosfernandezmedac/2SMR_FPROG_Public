# Tema 3 — Entrada de datos y constantes

## Índice
1. [Scanner: pedir datos al usuario](#1-scanner-pedir-datos-al-usuario)
2. [Leer varios datos seguidos](#2-leer-varios-datos-seguidos)
3. [El problema del `nextLine()` que se salta](#3-el-problema-del-nextline-que-se-salta)
4. [Literales](#4-literales)
5. [Constantes: `final`](#5-constantes-final)
6. [Errores típicos](#6-errores-típicos)

---

## 1. Scanner: pedir datos al usuario

Hasta ahora los valores estaban fijos en el código. Con `Scanner`, el programa **lee**
lo que escribe la persona:

```java
import java.util.Scanner;   // 1. al principio del archivo

public class PedirNombre {
    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);   // 2. crear el objeto Scanner

        System.out.print("¿Cómo te llamas? ");
        String nombre = sc.nextLine();          // 3. leer según el tipo

        System.out.println("Hola, " + nombre);
    }
}
```

| Método | Lee |
|---|---|
| `sc.nextInt()` | un número entero |
| `sc.nextDouble()` | un número decimal |
| `sc.nextLine()` | una línea de texto completa |
| `sc.next()` | una palabra (para en el primer espacio) |
| `sc.nextLine().charAt(0)` | un solo carácter (no existe `nextChar()`) |

---

## 2. Leer varios datos seguidos

```java
Scanner sc = new Scanner(System.in);

System.out.print("Nombre: ");
String nombre = sc.nextLine();

System.out.print("Edad: ");
int edad = sc.nextInt();

System.out.printf("Me llamo " + nombre + " y tengo " + edad + " años");
```

---

## 3. El problema del `nextLine()` que se salta

```java
Scanner sc = new Scanner(System.in);

System.out.print("Edad: ");
int edad = sc.nextInt();

System.out.print("Nombre: ");
String nombre = sc.nextLine();   // ⚠️ esto no espera a que escribas nada
```

Cuando escribes `16` y pulsas Enter, `nextInt()` solo lee el `16` — el salto de línea
se queda pendiente. El siguiente `nextLine()` lo recoge al instante (línea "vacía") y
el programa sigue sin dejarte escribir el nombre.

**Solución:** consumir ese salto de línea sobrante con un `sc.nextLine()` extra:

```java
int edad = sc.nextInt();
sc.nextLine();   // "limpia" el salto de línea pendiente

String nombre = sc.nextLine();   // ahora sí espera correctamente
```

> 💡 Esto **solo** pasa al mezclar `nextInt()`/`nextDouble()` con `nextLine()` justo
> después. Si solo usas `nextInt()` seguido de otro `nextInt()`, no hace falta.

---

## 4. Literales

Un **literal** es un valor escrito directamente en el código. Es solo el valor, no la
línea entera:

```java
int a = 10;
```

- `int a` → declara la variable
- `=` → le da un valor
- `10` → **el literal**

Según el tipo de dato, hay distintos literales:

| Literal | Tipo |
|---|---|
| `10` | entero (`int`) |
| `3.14` | decimal (`double`) |
| `'A'` | carácter (`char`) |
| `"Hola"` | texto (`String`) |
| `true` | lógico (`boolean`) |

Un literal también puede aparecer sin variable:

```java
System.out.println("Hola");   // "Hola" es un literal de texto
System.out.println(5 + 3);    // 5 y 3 son literales enteros
```

Dentro de un texto hay caracteres especiales que se escriben con `\`:

| Escritura | Qué hace |
|---|---|
| `\n` | Salto de línea |
| `\t` | Tabulador |
| `\"` | Comillas dentro del texto |
| `\\` | Una barra `\` |

```java
System.out.println("Linea 1\nLinea 2");
System.out.println("Ruta: C:\\Users");
```
Salida:
```
Linea 1
Linea 2
Ruta: C:\Users
```

---

## 5. Constantes: `final`

Una **constante** es como una variable, pero su valor **no puede cambiar** una vez
asignado. Se marca con `final` y, por convención, se escribe en mayúsculas.

```java
final double PI = 3.14159;
final double IVA = 0.21;
final int MAX_ALUMNOS = 30;
```

Úsalas con datos del usuario:

```java
Scanner sc = new Scanner(System.in);
final double PI = 3.14159;

System.out.print("Radio: ");
double radio = sc.nextDouble();

System.out.println("Longitud: " + (2 * PI * radio));
System.out.println("Área: " + (PI * radio * radio));
```
Con radio `5`:
```
Longitud: 31.4159
Área: 78.53975
```

Si intentas cambiarla, el programa no compila:

```java
PI = 3;   // ❌ error: cannot assign a value to final variable PI
```

**¿Por qué una constante y no escribir el número cada vez?** Si el IVA cambia, con una
constante lo cambias en **un solo sitio**. Con el `0.21` repetido por todo el código
tendrías que buscarlos todos, y un "buscar y reemplazar" podría cambiar otro `0.21` que
no era el IVA.

```java
final double IVA = 0.21;
System.out.print("Precio: ");
double precio = sc.nextDouble();
System.out.println("Con IVA: " + (precio * (1 + IVA)));   // con 100 -> 121.0
```

> 💡 Java ya trae una constante para π: `Math.PI`. Úsala cuando no quieras definir la tuya.

---

## 7. Errores típicos

| Error | Causa |
|---|---|
| `InputMismatchException` | El usuario escribió texto donde `nextInt()`/`nextDouble()` esperaba un número |
| El programa "se salta" una pregunta | Salto de línea pendiente — añade `sc.nextLine()` extra (punto 3) |
| `cannot assign a value to final variable` | Intentas modificar una constante |
| `NoSuchElementException` | Se pidió leer un dato y no había nada que leer (por ejemplo, se acabó la entrada) |


