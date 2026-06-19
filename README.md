# turismo
En mi trabajo final de la materia Laboratorio de Datos, realizamos un modelo predictivo para inferir la cantidad de turistas argentinos que viajarían a cada región del mundo según parámetros económicos con el fin de determinar si éstos se relacionan con el flujo turístico.
Utilizamos un dataset de turismo internacional de datos.gob.ar y datasets de valores de dólar blue, dólar oficial, índice big mac e inflación obtenidos de diversas fuentes online. Estos datasets cubrían el período 2016-2025.
En el preprocesamiento de datos, calculamos la brecha cambiaria en porcentaje del dólar oficial, asignamos con un criterio adecuado valores de índice big mac a las regiones que no coincidían entre ambos datasets y extendimos sus valores a los meses contiguos a la publicación del índice.
Al inspeccionar los datos, observamos que la cantidad de turistas a cada región depende fuertemente del mes del año. También vimos que durante la pandemia hubo un decrecimiento significativo del turismo, como se puede ver en el 1er gráfico, por lo que no consideramos esos datos.

<img width="325" height="260" alt="pandemia" src="https://github.com/user-attachments/assets/64fa9189-39c9-4d08-88c3-91f1fa40497b" />

Definimos los features: mes, región, inflación, brecha cambiaria e índice big mac relativo y como target a la cantidad de turistas.
Utilizamos una Random Forest Regression. Dividimos los datos en grupos de entrenamiento y de prueba estratificando según una combinación del mes y la región. A las columnas numéricas le aplicamos un Robust Scaler. A la columna de región, un One Hot Encoder y a la columna de mes un encoding trigonométrico.
Aplicamos la regresión y comparamos la predicción con los valores reales como se ve en el 2do gráfico.

<img width="300" height="400" alt="lineal" src="https://github.com/user-attachments/assets/22b3a807-0b44-4580-9821-824e64514cca" />

Realizamos una validación cruzada de 5 pliegues con la misma estratificación y obtuvimos un score de 0.88 ± 0.02, lo que indica que el modelo predice y generaliza bien.
También vimos que las variables económicas son relevantes y su grado de importancia, como se ve en el 3er gráfico, lo que prueba que hay una relación entre la cantidad de turismo al exterior y estas variables económicas.

<img width="328" height="375" alt="Importancia" src="https://github.com/user-attachments/assets/9286f536-e05f-401f-b43e-79a1a070998e" />
