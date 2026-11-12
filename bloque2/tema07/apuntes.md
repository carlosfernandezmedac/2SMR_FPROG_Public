# Tema 7 — Elegir entre muchos casos: `switch`

RA2 · RA3 — correspondencia con el libro: Tema 8 apartado 5 (estructuras de selección complejas)

## Índice
1. [¿Para qué sirve `switch`?](#1-para-qué-sirve-switch)
2. [Sintaxis y `break`](#2-sintaxis-y-break)
3. [Agrupar casos](#3-agrupar-casos)
4. [`switch` con `char` y `String`](#4-switch-con-char-y-string)
5. [¿`if` o `switch`?](#5-if-o-switch)
6. [Errores típicos](#6-errores-típicos)

---

## 1. ¿Para qué sirve `switch`?

Cuando comparas **una misma variable** con **muchos valores concretos**, una cadena de `else if`
queda larga. El libro lo llama "selección compleja": **no añade nada nuevo**, solo hace el código
más legible.

```java
// con else if
if (dia == 1) { ... } else if (dia == 2) { ... } else if (dia == 3) { ... }
```

## 2. Sintaxis y `break`

```java
switch (variable) {
    case valor1:
        // código
        break;
    case valor2:
        // código
        break;
    default:
        // si no coincide ningún caso
}
```

<!--in: 3-->
```java
import java.util.Scanner;

public class DiaSemana {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        System.out.print("Día (1-7): ");
        int dia = sc.nextInt();

        switch (dia) {
            case 1:
                System.out.println("Lunes");
                break;
            case 2:
                System.out.println("Martes");
                break;
            case 3:
                System.out.println("Miércoles");
                break;
            case 4:
                System.out.println("Jueves");
                break;
            case 5:
                System.out.println("Viernes");
                break;
            case 6:
                System.out.println("Sábado");
                break;
            case 7:
                System.out.println("Domingo");
                break;
            default:
                System.out.println("Día no válido");
        }
    }
}
```

> ⚠️ **Sin `break` Java sigue ejecutando los casos siguientes** (aunque no coincidan). Es el error nº 1.

Prueba qué pasa quitando los `break`:

<!--in: 1-->
```java
public class SinBreak {
    public static void main(String[] args) {
        int dia = 1;
        switch (dia) {
            case 1:
                System.out.println("Lunes");
            case 2:
                System.out.println("Martes");
            default:
                System.out.println("Otro");
        }
    }
}
```
Salida: `Lunes`, `Martes`, `Otro`.

---

## 3. Agrupar casos

Si varios valores hacen lo mismo, déjalos **sin `break`** entre ellos a propósito:

<!--in: 7-->
```java
import java.util.Scanner;

public class LaboralFinde {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int dia = sc.nextInt();

        switch (dia) {
            case 1:
            case 2:
            case 3:
            case 4:
            case 5:
                System.out.println("Día laborable");
                break;
            case 6:
            case 7:
                System.out.println("Fin de semana");
                break;
            default:
                System.out.println("Día no válido");
        }
    }
}
```

---

## 4. `switch` con `char` y `String`

<!--in: s-->
```java
import java.util.Scanner;

public class Menu {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        System.out.println("a) Sumar   b) Restar   s) Salir");
        char opcion = sc.next().charAt(0);

        switch (opcion) {
            case 'a':
                System.out.println("Has elegido sumar");
                break;
            case 'b':
                System.out.println("Has elegido restar");
                break;
            case 's':
                System.out.println("Adiós");
                break;
            default:
                System.out.println("Opción incorrecta");
        }
    }
}
```

Con `String` funciona igual (compara con `equals` por dentro):

<!--in: rojo-->
```java
import java.util.Scanner;

public class Semaforo {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String color = sc.next();

        switch (color) {
            case "rojo":
                System.out.println("Para");
                break;
            case "amarillo":
                System.out.println("Precaución");
                break;
            case "verde":
                System.out.println("Pasa");
                break;
            default:
                System.out.println("Color desconocido");
        }
    }
}
```

---

## 5. ¿`if` o `switch`?

| Usa `switch` si… | Usa `if / else if` si… |
|---|---|
| Comparas **una variable** con **valores exactos** (1, 2, 3 · 'a', 'b' · "rojo") | Hay **rangos** (`nota >= 5`) |
| Es un **menú** de opciones | Hay condiciones compuestas con `&&`, `\|\|` |
| | Comparas variables distintas |

`switch` **no admite** `case nota >= 5`. Los rangos se hacen con `if`.

---

## 6. Errores típicos

| Error | Consecuencia |
|---|---|
| Olvidar `break` | Se ejecutan los casos siguientes |
| Olvidar `default` | Entradas inesperadas no se tratan |
| `case 1, 2:` o `case dia > 3:` | No compila (en el `switch` clásico) |
| Repetir un `case` | No compila |
| Usar `double` en el `switch` | No compila (solo `int`, `char`, `String`…) |

> 📌 Java moderno permite `case 1 -> ...` sin `break`. 
