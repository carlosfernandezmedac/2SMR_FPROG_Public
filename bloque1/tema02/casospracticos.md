# Casos prácticos — Tema 2

## Caso práctico 1: "¿Por qué la división da 3 y no 3.5?"

Un alumno espera que este código imprima `3.5`, pero le imprime `3`. ¿Qué está pasando?

```java
int a = 7;
int b = 2;
System.out.println(a / b);
```

<details>
<summary>✅ Solución (para corrección)</summary>

Cuando **los dos operandos son `int`**, Java hace **división entera**: descarta la
parte decimal, no redondea. `7 / 2` da `3`, no `3.5`.

Para obtener el resultado decimal, hay que forzar a que al menos uno de los dos sea
`double`, con un *casting*:

```java
System.out.println((double) a / b);   // 3.5
```

**Puntos a valorar:** que entienda que es un comportamiento del tipo de dato, no un
error — y que sepa la solución del *casting* (lo veremos a fondo en el Tema 4).

</details>

---

## Caso práctico 2: "Factura con IVA, bien alineada"

Se pide un programa que calcule el total de una factura aplicando un 21% de IVA, con
el resultado alineado a dos decimales.

```java
double baseImponible = 150.0;
double iva = baseImponible * 0.21;
double total = baseImponible + iva;

System.out.print("Base imponible: " + baseImponible);
System.out.println("IVA (21%): " + iva);
System.out.println("Total: " + total);
```

<details>
<summary>✅ Solución (para corrección)</summary>

Salida:
```
Base imponible:   150,00 €
IVA (21%):         31,50 €
Total:            181,50 €
```

</details>


## Caso práctico 2: "Factura con IVA, bien alineada"

Se pide un programa que calcule el total de una factura aplicando un 21% de IVA, con
el resultado alineado a dos decimales.

```java
double baseImponible = 150.0;
double iva = baseImponible * 0.21;
double total = baseImponible + iva;

System.out.print("Base imponible: " + baseImponible);
System.out.println("IVA (21%): " + iva);
System.out.println("Total: " + total);
```

<details>
<summary>✅ Solución (para corrección)</summary>

Salida:
```
Base imponible:   150,00 €
IVA (21%):         31,50 €
Total:            181,50 €
```

</details>


## Caso práctico 3: "Operadores en un lenguaje de programación

https://vimeo.com/846296102/9bc2cc29b8?share=copy
