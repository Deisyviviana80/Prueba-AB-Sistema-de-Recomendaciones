# 📊 Análisis de Prueba A/B - Sistema de Recomendaciones

## Descripción del Proyecto

Este proyecto analiza los resultados de una prueba A/B realizada por una tienda en línea internacional para evaluar el impacto de un nuevo sistema de recomendaciones en el comportamiento de compra de los usuarios. El equipo anterior dejó los datos sin analizar correctamente, por lo que el objetivo fue retomar el trabajo, identificar problemas en los datos y extraer conclusiones válidas.

El proyecto fue desarrollado como parte del programa de formación en análisis de datos de **Practicum by Yandex**.

---

## 🎯 Objetivo de la Prueba

Determinar si el nuevo sistema de recomendaciones (Grupo B) mejora en al menos un **10%** la conversión en cada etapa del embudo dentro de los primeros 14 días tras el registro:

> `product_page` → `product_cart` → `purchase`

---

## 📋 Especificaciones Técnicas

| Parámetro | Detalle |
|-----------|---------|
| **Nombre de la prueba** | `recommender_system_test` |
| **Grupo A** | Control (experiencia actual) |
| **Grupo B** | Nuevo sistema de recomendaciones |
| **Inicio** | 7 de diciembre de 2020 |
| **Cierre de inscripciones** | 21 de diciembre de 2020 |
| **Finalización** | 1 de enero de 2021 |
| **Audiencia** | 15% de nuevos usuarios de la región EU |
| **Participantes esperados** | 6,000 |

---

## 🗂️ Datasets

| Archivo | Descripción |
|---------|-------------|
| `ab_project_marketing_events_us.csv` | Calendario de eventos de marketing 2020 |
| `final_ab_new_users_upd_us.csv` | Usuarios nuevos registrados del 7 al 21 de diciembre de 2020 |
| `final_ab_events_upd_us.csv` | Eventos de usuarios del 7 de diciembre al 1 de enero de 2021 |
| `final_ab_participants_upd_us.csv` | Participantes asignados a las pruebas A/B |

---

## 🔍 Hallazgos Principales

### Problemas identificados en los datos
Durante la exploración se detectaron irregularidades importantes que comprometen la validez del experimento original:

1. **Mezcla de dos pruebas A/B distintas** en la tabla de participantes (`recommender_system_test` e `interface_eu_test`). Fue necesario filtrar correctamente antes de analizar.
2. **Desbalance severo entre grupos**: Grupo A con 2,747 usuarios vs. Grupo B con solo 928 (~3:1), lo que sugiere problemas en la aleatorización.
3. **Contaminación externa**: la campaña *Christmas & New Year Promo* estuvo activa en EU durante la segunda mitad del experimento, introduciendo un estímulo no controlado.
4. **Tamaño muestral insuficiente**: se esperaban 6,000 participantes y solo se registraron 3,675.

### Resultados del embudo de conversión (14 días)

| Etapa | Grupo A (control) | Grupo B (nuevo sistema) | ¿Significativo? |
|-------|:-----------------:|:-----------------------:|:--------------:|
| product_page | 64.8% | 56.4% | ✅ Sí (p < 0.001) |
| product_cart | 30.0% | 27.5% | ⬜ No (p = 0.145) |
| purchase | 31.7% | 27.6% | ✅ Sí (p = 0.018) |

El Grupo B (nuevo sistema) obtuvo tasas de conversión **menores** que el control en todas las etapas. La mejora esperada del 10% no fue alcanzada en ninguna etapa.

---

## 💡 Conclusión

No se recomienda implementar el nuevo sistema de recomendaciones con los resultados actuales. Los datos no muestran mejora, y el experimento presenta múltiples problemas de diseño que impiden extraer conclusiones confiables. Se recomienda rediseñar la prueba con grupos balanceados, fuera de temporadas de alta actividad comercial y alcanzando el tamaño muestral previsto.

---

## 🛠️ Tecnologías Utilizadas

- **Python 3**
- **pandas** — manipulación y análisis de datos
- **scipy** — prueba estadística Z de proporciones
- **matplotlib / seaborn** — visualización de datos
- **Jupyter Notebook** — entorno de desarrollo

---

## 📁 Archivos del Repositorio

```
📦 ab-test-recommender-system
 ┣ 📓 AB_mejorado.ipynb                      # Notebook principal con el análisis completo
 ┣ 📄 ab_project_marketing_events_us.csv     # Calendario de marketing
 ┣ 📄 final_ab_new_users_upd_us.csv          # Usuarios nuevos
 ┣ 📄 final_ab_events_upd_us.csv             # Eventos de usuarios
 ┣ 📄 final_ab_participants_upd_us.csv       # Participantes de la prueba
 ┗ 📄 README.md                              # Este archivo
```

---

## ▶️ ¿Cómo ejecutar el proyecto?

```bash
# Instalar dependencias
pip install pandas scipy matplotlib seaborn jupyter

# Abrir el notebook
jupyter notebook AB.ipynb
```

---

## 👩‍💻 Autora

Proyecto desarrollado como parte del programa de **Análisis de Datos — TRIPLETEN**.

---

*Este repositorio forma parte de mi portafolio de proyectos de análisis de datos.*
