# Ejercicios — Tema 3: Entrada de datos y constantes

---

## Ejercicio 1 — Lectura de una cadena

Pide al usuario su nombre por teclado y muéstralo.


---

## Ejercicio 2 — Lectura de un número entero

Pide un número entero y muéstralo.

---

## Ejercicio 3 — Suma de dos enteros

Pide dos números enteros y muestra su suma.

---

## Ejercicio 4 — Suma, resta, multiplicación y división

Pide dos números y muestra el resultado de las cuatro operaciones básicas.

---

## Ejercicio 5 — Área de un rectángulo

Pide la base y la altura de un rectángulo y calcula su área. Se calcula con base * altura

---

## Ejercicio 6 — Área de un triángulo

Pide la base y la altura de un triángulo y muestra su área. Se calcula con (base * altura) / 2

---

## Ejercicio 7 — Salario semanal

Pide el número de horas trabajadas y el precio por hora, y calcula el salario semanal.

---

## Ejercicio 8 — Euros a pesetas

Pide una cantidad en euros y muestra su equivalente en pesetas. Guarda el cambio
(1 € = 166,386 pesetas) en una **constante**.

---

## Ejercicio 9 — Pesetas a euros

Pide una cantidad en pesetas y muestra su equivalente en euros, usando la misma
constante.

---

## Ejercicio 10 — Factura con IVA

Pide una base imponible y calcula el total de la factura aplicando el IVA del 21 %.
Guarda el IVA en una constante.

---

## Ejercicio 11 — Área de un círculo

Pide el radio de un círculo y calcula su área. Define una constante `PI` con el valor
`3.14159`. El área se cálcula con la fórmula: (PI * radio * radio)

---


## Ejercicio 12 — Precio con descuento

Una tienda aplica siempre un descuento del 10 %. Define el descuento como constante,
pide el precio de un producto y muestra el precio final. El precio final se cálcula con **precioFinal = precio * (1 - DESCUENTO)**

---

## Ejercicio 13 — Euros a dólares

Supón que 1 € = 1,10 $. Define el cambio como constante, pide una cantidad en euros y
muestra los dólares. Después imagina que el cambio sube a 1,15: ¿cuántas líneas hay que
tocar?

---

## Ejercicio 14 — Encuentra el error

Este programa no compila. ¿Por qué? ¿Cómo lo arreglarías?

```java
public class ErrorConstante {
    public static void main(String[] args) {
        final double IVA = 0.21;
        IVA = 0.10;
        System.out.println(IVA);
    }
}
```
---


## Ejercicio 15 — Ficha de alumno (edad y nombre)

Pide primero la **edad** (un número) y después el **nombre** (un texto), y muestra una
frase como `Ana tiene 16 años`.

> 💡 Pista: ¿qué pasa si no pones nada entre `nextInt()` y `nextLine()`?

---

## Ejercicio 16 — Edad dentro de 5 años

Pide la edad y muestra la que tendrás dentro de 5 años.

**Ejemplo:** entrada `17` → salida `En 5 años tendrás: 22`

---

## Ejercicio 17 — Doble y triple

Pide un número entero y muestra su doble y su triple en dos líneas.

**Ejemplo:** entrada `8` → salida:
```
El doble de 8 es 16.
El triple es 24.
```

---

## Ejercicio 18 — Conversor de tiempo

Pide los minutos y muestra cuántos segundos son. Guarda los segundos que tiene un
minuto (60) en una **constante**.

---

## Ejercicio 19 — Media de tres notas

Pide tres notas por teclado (pueden tener decimales) y muestra su media.

---

## Ejercicio 20 — Leer una letra

Pide una letra por teclado y muestra `La letra es: X` (con la letra que se haya escrito).

> 💡 Pista: `Scanner` no tiene `nextChar()`. Mira la tabla de métodos de los apuntes.


