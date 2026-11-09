# Tema 6 — Varias decisiones: `else if` y anidación

## Índice
1. [Cuando hay más de dos caminos: `else if`](#1-cuando-hay-más-de-dos-caminos-else-if)
2. [El orden importa](#2-el-orden-importa)
3. [`if` dentro de `if` (anidación)](#3-if-dentro-de-if-anidación)
4. [¿`else if` o anidar? ¿Son excluyentes los casos?](#4-else-if-o-anidar-son-excluyentes-los-casos)
5. [Errores típicos](#5-errores-típicos)

---

## 1. Cuando hay más de dos caminos: `else if`

```java
if (condición1) {
    // camino 1
} else if (condición2) {
    // camino 2
} else if (condición3) {
    // camino 3
} else {
    // ninguna se cumplió
}
```

Java prueba las condiciones **de arriba abajo**; en cuanto una es `true`, ejecuta su bloque y
**se salta todo lo demás**.

<!--in: 6.5-->
```java
import java.util.Locale;
import java.util.Scanner;

public class Calificacion {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        sc.useLocale(Locale.US);

        System.out.print("Nota: ");
        double nota = sc.nextDouble();

        if (nota < 5) {
            System.out.println("Suspenso");
        } else if (nota < 7) {
            System.out.println("Aprobado");
        } else if (nota < 9) {
            System.out.println("Notable");
        } else {
            System.out.println("Sobresaliente");
        }
    }
}
```

Fíjate: no hace falta escribir `nota >= 5 && nota < 7`. Si llegamos al segundo `else if`, ya sabemos que `nota >= 5`.

---

## 2. El orden importa

```java
int nota = 9;
if (nota >= 5) {
    System.out.println("Aprobado");       // ← sale esto
} else if (nota >= 9) {
    System.out.println("Sobresaliente");  // ← nunca se llega aquí
}
```

Regla: pon primero la condición **más restrictiva** (o usa rangos que no se solapen).

---

## 3. `if` dentro de `if` (anidación)

Un `if` puede estar dentro del bloque de otro. Se usa cuando la 2ª pregunta **solo tiene sentido
si se cumplió la 1ª**.

<!--in: 20 8-->
```java
import java.util.Scanner;

public class Cine {
    public static void main(String[] args) {
        final int PRECIO = 10;
        Scanner sc = new Scanner(System.in);

        System.out.print("Edad: ");
        int edad = sc.nextInt();
        System.out.print("Dinero: ");
        int dinero = sc.nextInt();

        if (edad >= 18) {
            if (dinero >= PRECIO) {
                System.out.println("Puedes entrar");
            } else {
                System.out.println("Te falta dinero");
            }
        } else {
            System.out.println("Eres menor");
        }
    }
}
```

> 💡 Sangra (tabula) cada nivel. Si el código "se va muy a la derecha", piensa si se puede simplificar con `&&`.

El mismo programa **sin anidar**, con `&&`, si solo importa "entra / no entra":

```java
if (edad >= 18 && dinero >= PRECIO) {
    System.out.println("Puedes entrar");
} else {
    System.out.println("No puedes entrar");
}
```

---

## 4. ¿`else if` o anidar? ¿Son excluyentes los casos?

Antes de escribir el código, pregúntate:

| Situación | Estructura |
|---|---|
| Los casos son **excluyentes** (solo uno puede darse): tramos de nota, días, categorías | cadena `else if` |
| La 2ª pregunta **depende** de la 1ª | `if` anidado |
| Los casos **no son excluyentes** (pueden darse varios a la vez) | **`if` independientes**, uno detrás de otro |

<!--in: 20 1-->
```java
import java.util.Scanner;

public class Descuentos {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int edad = sc.nextInt();
        int hijos = sc.nextInt();

        int descuento = 0;
        if (edad < 26) {            // joven
            descuento += 10;
        }
        if (hijos > 0) {            // familia: se puede cumplir TAMBIÉN
            descuento += 5;
        }
        System.out.println("Descuento: " + descuento + "%");
    }
}
```

Con `else if` aquí se perdería el segundo descuento: son casos **no excluyentes**.

> `+=` suma y asigna: `descuento += 10` equivale a `descuento = descuento + 10`.

---

## 5. Errores típicos

| Error | Consecuencia |
|---|---|
| Poner `else if` donde los casos no son excluyentes | Se pierden resultados |
| Condiciones en mal orden | Una rama nunca se ejecuta |
| Llaves mal cerradas en anidación | No compila / el `else` se emparejó con otro `if` |
| Un `else` sin `if` | No compila |
| Repetir comprobaciones ya implícitas (`nota >= 5 && nota < 7` tras `nota < 5`) | Funciona, pero sobra |
