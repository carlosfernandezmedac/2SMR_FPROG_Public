# Casos prácticos — Tema 3

## Caso práctico 1: "El programa que se saltaba una pregunta"

Un alumno ha escrito este código, pero cuando lo ejecuta, nunca le deja escribir el
nombre — el programa termina sin pedirlo. ¿Por qué pasa esto?

```java
import java.util.Scanner;

public class Matricula {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("¿Cuántos años tienes? ");
        int edad = sc.nextInt();

        System.out.print("¿Cómo te llamas? ");
        String nombre = sc.nextLine();

        System.out.println("Te llamas " + nombre + " y tienes " + edad + " años.");
    }
}
```

<details>
<summary>✅ Solución (para corrección)</summary>

El problema es el **salto de línea pendiente**, explicado en el punto 3 de los apuntes.
Cuando el usuario escribe `16` y pulsa Enter, `nextInt()` solo lee el `16` — el `\n`
se queda esperando y lo recoge el siguiente `nextLine()` como una línea vacía.

```java
System.out.print("¿Cuántos años tienes? ");
int edad = sc.nextInt();
sc.nextLine();   // consume el salto de línea pendiente

System.out.print("¿Cómo te llamas? ");
String nombre = sc.nextLine();
```


</details>

---

## Caso práctico 2: "Cambiar el IVA en un solo sitio"

Este programa calcula el precio final de tres productos con un IVA del 21 %. El cliente
avisa de que el IVA correcto es el **10 %**. ¿Cuántos sitios tendrías que cambiar? ¿Cómo
lo harías para tener que cambiar solo uno?

```java
public class Precios {
    public static void main(String[] args) {
        System.out.println("Pan: " + 2 * 1.21);
        System.out.println("Leche: " + 5 * 1.21);
        System.out.println("Queso: " + 10 * 1.21);
    }
}
```

<details>
<summary>✅ Solución (para corrección)</summary>

Hay que cambiar **tres** sitios (cada `1.21`), y un "buscar y reemplazar" podría tocar
otro `1.21` que no sea el IVA. Con una constante, se cambia en uno solo:

```java
public class Precios {
    public static void main(String[] args) {
        final double IVA = 0.10;

        System.out.println("Pan: " + 2 * (1 + IVA));
        System.out.println("Leche: " + 5 * (1 + IVA));
        System.out.println("Queso: " + 10 * (1 + IVA));
    }
}
```

Salida:
```
Pan: 2.2
Leche: 5.5
Queso: 11.0
```


</details>
