
# 📌 Análisis de Emociones en Tweets en Español  

Este proyecto implementa distintos enfoques de **Procesamiento de Lenguaje Natural (NLP)** para la clasificación de emociones en textos en español, utilizando el dataset [EmoEvent](https://github.com/fmplaza/EmoEvent), que contiene más de **8,000 tweets** anotados en categorías como:  
`anger, joy, sadness, fear, disgust, surprise, others`.  

---

## 🚀 Objetivo  
Evaluar y comparar el rendimiento de diferentes modelos para la **detección automática de emociones en español**, desde arquitecturas clásicas entrenadas desde cero hasta modelos de última generación preentrenados.

---

## ⚙️ Modelos implementados  

1. **🔹 LSTM (baseline entrenado desde cero)**  
   - Red neuronal recurrente con embeddings.  
   - Accuracy: **~51%**.  
   - Problemas: fuerte *overfitting* y bajo rendimiento en clases minoritarias.  

2. **🔹 DistilBERT (fine-tuning en inglés)**  
   - Modelo preentrenado en grandes corpus, ajustado para clasificación de emociones.  
   - Accuracy: **~64%**.  
   - Mejor generalización y balance entre clases.  

3. **🔹 Robertuito (pysentimiento/robertuito-emotion-analysis)**  
   - Variante de RoBERTa preentrenada en **español** y especializada en **detección de emociones**.  
   - Accuracy: **~86%**, F1 ponderado: **0.85**.  
   - Excelente en clases dominantes, aunque *disgust* sigue siendo difícil por el desbalance del dataset.  

---

## 📊 Resultados  

| Modelo      | Accuracy | F1-Score Ponderado | Observaciones |
|-------------|----------|--------------------|---------------|
| **LSTM**        | 0.51     | 0.39               | Baseline, sobreajuste, bajo desempeño en clases minoritarias. |
| **DistilBERT**  | 0.64     | 0.61               | Mejora gracias a transfer learning, más equilibrado. |
| **Robertuito**  | 0.86     | 0.85               | Mejor modelo, especializado en emociones en español. |

---

## 🔍 Conclusiones  

- Los **modelos preentrenados** superan ampliamente a modelos entrenados desde cero.  
- **Robertuito** es la opción ideal para aplicaciones reales en **análisis de emociones en redes sociales en español**, gracias a su rapidez, precisión y especialización.  
- El **desbalance de clases** sigue siendo un reto, especialmente para emociones como *disgust, fear, surprise*.  

---

## 📂 Estructura del proyecto  

