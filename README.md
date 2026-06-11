# NovaRetail+ — Análisis de Drivers de Comportamiento del Cliente
 
> **El factor más correlacionado con el ingreso resultó ser una trampa estadística.**
 
Proyecto de análisis exploratorio de datos desarrollado como parte del **Bootcamp de Data Analytics de TripleTen** (Sprint 8).
 
---
 
## Contexto del negocio
 
**NovaRetail+** es una plataforma de comercio electrónico en Latinoamérica con millones de usuarios. Para el cierre de 2024, el equipo de Crecimiento y Retención plantea la siguiente pregunta:
 
> ¿Qué factores del comportamiento del cliente están más fuertemente asociados con el ingreso anual generado?
 
---
 
## Hallazgos principales
 
1. **`compras_mes` no es un driver de comportamiento.** Su correlación de 0.967 con `ingreso_anual` refleja una relación mecánica: `ingreso_anual ≈ 30 × compras_mes`, donde ~30 es el precio promedio por compra. Es el ingreso en otra unidad, no una variable explicativa.
2. **El fenómeno tiene dos partes distintas:**
   - **Conversión:** el 30.45% de los usuarios nunca ha comprado y genera $0. Es el segmento decisivo.
   - **Intensidad:** entre quienes sí compran, solo la frecuencia de visitas predice débilmente el monto (r ≈ 0.28).
3. **El tráfico es el único driver de comportamiento accionable.** Las visitas mensuales (Spearman 0.33) son el único factor que distingue a compradores de no compradores. El embudo lo confirma: usuarios con >12 visitas/mes convierten al 84% vs 47% de quienes visitan ≤6 veces, triplicando el ingreso promedio.
4. **Null results relevantes:** plan premium (r = 0.09), satisfacción, edad, tipo de dispositivo y región no muestran asociación práctica con el ingreso (Kruskal p > 0.44 para las categóricas).
---
 
## Dataset
 
| Característica | Detalle |
|---|---|
| Registros | 15,000 clientes |
| Variables | 12 (numéricas, binarias y categóricas) |
| Target | `ingreso_anual` (ingreso que el cliente genera a la empresa) |
| Periodo | 2024 |
| Fuente | Dataset sintético — TripleTen |
 
---
 
## Técnicas aplicadas
 
- Análisis exploratorio de datos (EDA)
- Coeficientes según tipo de variable: Pearson, Spearman, Punto-biserial, Cramér's V
- Segmentación por embudo de conversión (binning de visitas)
- Prueba de Kruskal-Wallis (alternativa no paramétrica al ANOVA)
- Análisis de dos partes: conversión vs intensidad
- Detección y decisión documentada de outliers (criterio IQR 1.5×)
---
 
## Estructura del repositorio
 
```
novaretail-behavioral-drivers/
│
├── novaretail_drivers_comportamiento_ingreso.ipynb   # Notebook principal
├── novaretail_comportamiento_clientes_2024.csv        # Dataset
└── README.md
```
 
---
 
## Stack técnico
 
![Python](https://img.shields.io/badge/Python-3.x-blue)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange)
![pandas](https://img.shields.io/badge/pandas-2.x-lightgrey)
![scipy](https://img.shields.io/badge/scipy-stats-lightgrey)
![seaborn](https://img.shields.io/badge/seaborn-viz-teal)
 
---
 
## Limitaciones
 
- Los datos son de corte transversal (un solo periodo); no se puede inferir causalidad ni estacionalidad.
- La colinealidad entre `visitas_mes` y `gasto_publicidad_dirigida` (r = 0.58) impide tratarlas como palancas independientes.
- La relación `compras_mes` ↔ `ingreso_anual` es un artefacto del diseño del dataset (precio casi fijo), no un insight de negocio.
- Con n = 15,000 la significancia estadística es poco informativa; la interpretación se basa en tamaño del efecto.
---
 
## Próximos pasos propuestos
 
1. **Test A/B** para validar si incrementar el tráfico de usuarios inactivos aumenta su conversión.
2. **Variables faltantes:** recencia, fuente de tráfico, abandono de carrito.
3. **Modelo de clasificación** para predecir qué usuarios inactivos tienen mayor probabilidad de convertir.
---
 
## Autor
 
**Roberto Barrera García**
Ingeniero Mecánico-Automotriz | Analista de Datos en formación
Lean Six Sigma Green Belt
 
[![GitHub](https://img.shields.io/badge/GitHub-RobertoBG1111-black)](https://github.com/RobertoBG1111)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Roberto%20Barrera-blue)](https://www.linkedin.com/in/robertobarreragarcia/)
 
---
 
*Proyecto desarrollado con apoyo de herramientas de IA (Claude, Gemini) para validación de hipótesis y revisión metodológica. Declarado abiertamente como parte del proceso.*
