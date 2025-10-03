# Trabajo Práctico N.º 3

**Árbol de Decisión – Empresa de Telecomunicaciones**

**Nombre:** Coral Tolazzi
**Materia:** Procesamiento de Aprendizaje Automático
**Tema:** Árbol de Decisión – Empresa de Telecomunicaciones
**Profesora:** Yanina Ximena Scudero
**Cuatrimestre y Año:** 2.º Cuatrimestre del 2025
**Instituto:** Instituto Tecnológico Beltrán

---

## 📌 Descripción

El objetivo de este trabajo práctico es construir un **árbol de decisión** que permita predecir si un cliente de una empresa de telecomunicaciones aceptará una oferta de plan de datos móviles.

Se parte de un conjunto de datos de 10 clientes que incluye los siguientes atributos:

* **Edad** (en años, agrupada en rangos: Joven ≤30, Adulto 31–50, Mayor >50)
* **Nivel de uso mensual de datos** (en GB, agrupado: Bajo ≤3GB, Medio 3.1–6GB, Alto >6GB)
* **Tiene línea fija** (Sí/No)
* **Aceptó la oferta** (Sí/No)

---

## 🎯 Objetivos del ejercicio

1. Calcular la **entropía del conjunto original**.
2. Evaluar la **ganancia de información** de los atributos:

   * Edad
   * Tiene línea fija
   * Uso de datos
3. Construir el **árbol de decisión paso a paso**.
4. Concluir cuál es el mejor atributo para iniciar el árbol y cómo usarlo para la predicción.

---

## 🧮 Desarrollo

### 1. Entropía inicial

Con 10 clientes (5 aceptaron, 5 no):
[
H(S) = 1.0
]

---

### 2. Ganancia de información

* **Tiene línea fija:** Gain = **0.278**
* **Edad:** Gain = **0.676**
* **Uso de datos:** Gain = **0.725**

👉 El atributo más informativo es **Uso de datos**.

---

### 3. Construcción del árbol

* **Nodo raíz:** Uso de datos

  * **Bajo (≤3GB):** Todos No → hoja = No
  * **Alto (>6GB):** Todos Sí → hoja = Sí
  * **Medio (3.1–6GB):** Mezcla → subdividir

En la rama **Medio**:

* **Edad ≤30:** No
* **Edad 31–50:** subdividir por línea fija

  * Línea fija = Sí → Sí
  * Línea fija = No → No

---

## 🌳 Árbol resultante

```
Uso de datos?
├── Bajo (≤3GB) → No
├── Alto (>6GB) → Sí
└── Medio (3.1–6GB)
     ├── Edad ≤30 → No
     └── Edad 31–50
          ├── Línea fija = Sí → Sí
          └── Línea fija = No → No
```

---

## ✅ Conclusiones

* El **uso de datos** es el factor más determinante:

  * Bajo → No aceptan
  * Alto → Sí aceptan
* En el rango **medio**, se requiere analizar edad y línea fija para mejorar la predicción.
* El modelo permite segmentar clientes de forma eficiente:

  * Jóvenes con bajo uso → No
  * Mayores con alto uso → Sí
  * Adultos con uso medio → depende de la línea fija

---

¿Querés que este README te lo prepare también en **formato PDF o Word** para que lo presentes directo junto con el TP, corazón?
