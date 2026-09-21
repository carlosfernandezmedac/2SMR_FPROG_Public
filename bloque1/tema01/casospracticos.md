# Casos prácticos — Tema 1

## Caso práctico 1: "La clase que no compilaba"

Un alumno ha escrito este código en un archivo llamado `Presentacion.java` y no consigue
que compile. ¿Cuántos errores encuentras y cómo los corregirías?

```java
public class presentacion {

    public static void Main(String[] args) {
        System.out.println("Me llamo Marcos")
        System.out.println("Estudio SMR");
    }
}
```

<details>
<summary>✅ Solución (para corrección)</summary>

Hay **tres errores**:

1. La clase se llama `presentacion` (minúscula) pero el archivo es `Presentacion.java`
   (mayúscula). En Java, el nombre de la clase pública y el del archivo deben coincidir
   **exactamente**, respetando mayúsculas y minúsculas.
2. El método se llama `Main` con mayúscula. La JVM busca literalmente `main`, en
   minúsculas — con `Main` el programa no se puede ejecutar como aplicación porque no
   encuentra el punto de entrada.
3. Falta el `;` al final de la primera instrucción.

Código corregido:

```java
public class Presentacion {

    public static void main(String[] args) {
        System.out.println("Me llamo Marcos");
        System.out.println("Estudio SMR");
    }
}
```

</details>

---

## Caso práctico 2: "Un programa con datos personales"

Escribe un programa `Ficha.java` que muestre por consola, en líneas separadas:
- Tu nombre.
- El nombre del ciclo formativo.
- El nombre del módulo.

Usa al menos un comentario de una línea explicando qué hace el programa.

<details>
<summary>✅ Solución (para corrección)</summary>

```java
// Programa que muestra una ficha de datos básicos por consola
public class Ficha {

    public static void main(String[] args) {
        System.out.println("Nombre: Laura");
        System.out.println("Ciclo: Sistemas Microinformáticos y Redes");
        System.out.println("Módulo: Fundamentos de Programación");
    }
}
```

**Puntos a valorar en la corrección:**
- Que el comentario esté antes de la clase y explique el propósito, no el "cómo".
- Tres líneas de salida independientes, correspondientes a los tres datos pedidos.

</details>
