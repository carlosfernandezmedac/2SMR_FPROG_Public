# Ejercicios — Tema 4: Conversión de tipos

---

## Ejercicio 1 — Truncar vs. redondear

Declara una variable `double` con el valor `7.89`. Muestra por pantalla el resultado
de truncarla con `(int)` y el de redondearla con `Math.round()`, para comparar.

---

## Ejercicio 2 — De texto a número

Un programa recibe la edad como texto (`String edadTexto = "17";`). Conviértela a
`int` y muestra si esa persona es mayor de edad (`true` o `false`).

---

## Ejercicio 3 — Media con decimales

Pide dos números enteros por teclado y muestra su media **con decimales**. Por ejemplo,
con 7 y 4 la media es 5.5.

---

## Ejercicio 4 — La letra siguiente

Pide una letra por teclado y muestra su código y la letra siguiente del alfabeto. Con
la `a`, debe mostrar `97` y `b`.

---

## Ejercicio 5 — Suma de dos números escritos como texto

Pide dos números leyéndolos con `sc.nextLine()` (que devuelve texto), conviértelos con
`Integer.parseInt` y muestra su suma. Comprueba qué pasa si no conviertes y sumas el
texto directamente (`"12" + "30"`).

---

## Ejercicio 6 — Predice el resultado

Sin ejecutar, di qué mostrará cada línea y luego compruébalo:

```java
boolean a = true;
boolean b = false;

System.out.println(a && b);
System.out.println(a || b);
System.out.println(!a);
System.out.println(!a || b);
System.out.println(a && !b);
```

---

## Ejercicio 7 — ¿Puede sacarse el carnet?

Guarda en variables la edad (`int`) y si ha aprobado el teórico (`boolean`). Calcula en un `boolean` si puede sacarse el carnet: tiene **18 años o más Y** ha aprobado el teórico. Muestra el resultado.

---

## Ejercicio 8 — Descuento de cine

Una entrada tiene descuento si la persona tiene **menos de 12 años O más de 65**. Guarda la edad en una variable (por ejemplo `70`), calcula en un `boolean` si tiene descuento y muéstralo. Después muestra también `!tieneDescuento`.

---

## Ejercicio 9 — Completa la tabla

Sin ejecutar, completa el resultado de cada fila y luego comprueba tus respuestas escribiendo el código:

| `a` | `b` | `a && b` | `a \|\| b` | `!a` |
|---|---|---|---|---|
| `true` | `true` | ? | ? | ? |
| `true` | `false` | ? | ? | ? |
| `false` | `true` | ? | ? | ? |
| `false` | `false` | ? | ? | ? |

