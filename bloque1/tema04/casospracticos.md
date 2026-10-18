# Casos prácticos — Tema 4

## Caso práctico 1: "El redondeo que no redondeaba"

Un alumno quiere redondear `9.75` al entero más cercano (esperando `10`), pero este
código le da `9`:

```java
double nota = 9.75;
int notaRedondeada = (int) nota;
System.out.println(notaRedondeada);
```

<details>
<summary>✅ Solución (para corrección)</summary>

El casting `(int)` **trunca** (se queda solo con la parte entera), no redondea
matemáticamente. Para redondear de verdad, hay que usar `Math.round()`:

```java
double nota = 9.75;
long notaRedondeada = Math.round(nota);   // 10
```

> `Math.round()` devuelve `long`, no `int` — si quieres un `int`, añade un casting
> extra: `(int) Math.round(nota)`.

**Puntos a valorar:** que distinga truncar (`(int)`) de redondear (`Math.round()`), y
que sepa cuándo usar cada uno.

</details>

---

## Caso práctico 2: "La letra que se convirtió en número"

Un alumno quiere mostrar la letra siguiente a `'A'` (es decir, `B`), pero el programa
muestra `66`. ¿Por qué? ¿Cómo se arregla?

```java
char letra = 'A';
System.out.println(letra + 1);
```

<details>
<summary>✅ Solución (para corrección)</summary>

Al sumar un número a un `char`, Java calcula con el **código** de la letra (`'A'` es
`65`), así que `65 + 1 = 66` y el resultado es un número, no una letra.

Para volver a obtener una letra hay que hacer un *casting* a `char`:

```java
char letra = 'A';
System.out.println((char) (letra + 1));   // B
```

**Puntos a valorar:** que entienda que cada letra tiene un código y que `(char)` hace
la conversión de vuelta.

</details>

---

## Caso práctico 3: "¿Puede entrar al cine?"

Lee este programa y **predice** qué mostrará cada línea antes de ejecutarlo. Después
compáralo con la salida real.

```java
public class Cine {
    public static void main(String[] args) {
        int edad = 15;
        boolean vaConAdulto = true;
        boolean tieneEntrada = false;

        boolean puedeEntrar = edad >= 18 || vaConAdulto;
        boolean puedeSentarse = puedeEntrar && tieneEntrada;

        System.out.println("Puede entrar: " + puedeEntrar);
        System.out.println("Puede sentarse: " + puedeSentarse);
        System.out.println("No tiene entrada: " + !tieneEntrada);
    }
}
```

Responde: ¿qué cambiaría si `vaConAdulto` fuera `false`?

<details>
<summary>✅ Solución (para corrección)</summary>

```
Puede entrar: true
Puede sentarse: false
No tiene entrada: true
```

- `puedeEntrar`: `15 >= 18` es `false`, pero `vaConAdulto` es `true`; con `||` basta una, así que `true`.
- `puedeSentarse`: `&&` necesita las dos; `tieneEntrada` es `false`, así que `false`.
- `!tieneEntrada` invierte `false` y da `true`.
- Si `vaConAdulto` fuera `false`: `false || false` da `false`, y `puedeEntrar` y `puedeSentarse` serían `false`.

**Puntos a valorar:** que distinga `&&` (las dos) de `||` (basta una) y que sepa cuándo `!` invierte.

</details>
