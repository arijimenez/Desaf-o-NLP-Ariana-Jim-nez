
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
## Matrices de confusión
La matriz de confusión del modelo LSTM revela que las clases con mayor cantidad de datos, como *others*, *joy* y *sadness*, alcanzan un rendimiento aceptable con 437, 201 y 130 aciertos respectivamente, aunque presentan confusiones relevantes: *others* se confunde en 200 casos con *joy*, esta última en más de 100 casos con *others* y en 25 con *sadness*, mientras que *anger*, con 63 aciertos, suele confundirse con *sadness* (40 casos) y *others* (23 casos). En el caso de las clases minoritarias, el desempeño es muy bajo: *fear* apenas logra 6 aciertos y 9 confusiones en *others*, *disgust* también 6 aciertos pero dispersos en varias clases, y *surprise* solo 13 aciertos con 34 errores hacia *others*. En conjunto, esto muestra que el modelo funciona razonablemente bien en las clases dominantes, pero fracasa en distinguir emociones minoritarias y confunde emociones cercanas semánticamente, lo que explica su bajo rendimiento general (\~50% de accuracy) y confirma sus limitaciones frente al desbalance de datos.
<img width="785" height="624" alt="image" src="https://github.com/user-attachments/assets/c83daf4b-0d49-4683-ac6e-4541215fb0b1" />

La matriz de confusión muestra que tu modelo DistilBERT fine-tuneado tiene un buen desempeño en clases mayoritarias como others, joy y sadness, pero presenta un fuerte sesgo hacia la clase others, absorbiendo muchos errores de las demás categorías. Emociones minoritarias como disgust, fear y surprise casi no son reconocidas, lo que refleja un claro desbalance en el dataset. En general, el modelo distingue razonablemente bien emociones frecuentes, pero necesita estrategias como balanceo de datos, ponderación de clases o data augmentation para mejorar el reconocimiento de las clases menos representadas.
<img width="554" height="468" alt="image" src="https://github.com/user-attachments/assets/51a010cb-f176-454f-9dc2-21d75f715c36" />

En esta tercera matriz de confusión, del modelo pysentimiento/robertuito-emotion-analysis entrenado en español, se observa un rendimiento más equilibrado que en tu modelo DistilBERT fine-tuneado y en el LSTM. La clase others sigue siendo la más dominante (3736 aciertos), pero a diferencia del anterior, aquí las emociones principales como joy (1562), sadness (876) y anger (757) se reconocen con mucha mayor precisión y menos confusión hacia others. Además, emociones difíciles como surprise (220), disgust (132) y fear (75) también son identificadas, aunque con menor volumen de datos. En general, este modelo presenta mejor capacidad para distinguir entre emociones, mostrando menos sesgo hacia la clase mayoritaria y una cobertura más amplia de las categorías minoritarias.
<img width="751" height="590" alt="image" src="https://github.com/user-attachments/assets/fe9ef47f-fa4c-4cc2-8cd9-b64b38227061" />


## 🔍 Conclusiones  

- Los **modelos preentrenados** superan ampliamente a modelos entrenados desde cero.  
- **Robertuito** es la opción ideal para aplicaciones reales en **análisis de emociones en redes sociales en español**, gracias a su rapidez, precisión y especialización.  
- El **desbalance de clases** sigue siendo un reto, especialmente para emociones como *disgust, fear, surprise*.  

---

## 📂 Puede revisar el código en el siguiente enlace:
https://colab.research.google.com/drive/1UnVamXla36SLW6J9ciOkfXipQI2AmuDi?usp=sharing  

