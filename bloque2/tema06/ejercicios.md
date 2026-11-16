# Ejercicios — Tema 6: `else if` y anidación

---

## Ejercicio 1 — Signo
Pide un entero y muestra `Positivo`, `Negativo` o `Cero`.


---

## Ejercicio 2 — Etapa de la vida
Pide la edad: `Niño` (0–11), `Adolescente` (12–17), `Adulto` (18–64), `Mayor` (65 o más).


---


## Ejercicio 3 — IRPF por tramos
Pide el sueldo anual y muestra el porcentaje de retención: hasta 12 000 → 0 %; hasta 25 000 → 10 %; hasta 40 000 → 20 %; más → 30 %.


---

## Ejercicio 4 — Descuentos acumulables
Pide el importe y dos preguntas (`s`/`n`): ¿eres socio? (−5 %) ¿pagas en efectivo? (−2 %). Los descuentos se **suman**. Muestra el % total.
*Pista: ¿son excluyentes? → `if` independientes.*

---

## Ejercicio 4.1 -  Descuentos acumulables

```java
if (socio == 's') {
    descuento += 5;
} else if (efectivo == 's') {
    descuento += 2;
}
```

Explica la diferencoia con el código anterior. Si es socio y tiene efectivo cuanto descuento se le aplica?

---

## Ejercicio 4.2 -  Descuentos acumulables
Pide si el cliente es socio (s/n) y si paga en efectivo (s/n): socio y efectivo, 7 %; solo socio, 5 %; no socio pero efectivo, 2 %; ninguno, 0 %. Muestra Descuento total: X%.

---

## Ejercicio 5 — Tarifa de autobús

Menores de 4 años: gratis. 4–12: 0,50 €. 13–64: 1,20 €. 65 o más: gratis.


