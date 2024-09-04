-------------------------------------------------------------
Training of EEG Emotion classifiers with SEED-V Data Tutorial
-------------------------------------------------------------
 
# PROCESAMIENTO_SEEDV.

1) Descargar el dataset SEED-V. El link de acceso para solicitar los datos se encuentra en el archivo 'SEEDV_Dataset.txt'.

2) Ejecutar '0.Segments_SEEDV' definiendo el directorio en el que se encuentran los archivos .cnt descargados. Definir directorio de salida en el que se guardaran los archivos generados en este paso. Este script segmenta los datos en crudo para utilizar solo aquellos intervalos de interés, en los que se ha recogido señal EEG mientras el individuo estaba viendo un video. Se genera un dataset por cada video visto en cada sesión por cada individuo. 

3) El script '1.Preprocessing' lee los archivos .set generados en el paso anterior en el directorio en el que se encuentran, aplica el algoritmo de preprocesamiento y guarda los nuevos archivos en el directorio definido. Para ejecutar este script se requiere especificar el directorio en el que se encuentra el archivo con las localizaciones de los electrodos, este archivo lo proporciona el BCMI cuando se solicitan los datos del SEED-V.

4) Una vez se tiene la señal preprocesada se pasa a la extracción de características y la creación del dataset final, que se utilizará para entrenar y testear los modelos de clasificación. El script '2.FEATURES_LABELS_CONCAT.ipynb' define inicialmente funciones de utilidad, para la carga de datos EEG, la computación de canales faltantes por la media y la aplicación de la STFT y cálculo de la Diferencia de Entropía. 

Este script integra tres partes importantes, en primer lugar, la extracción de características, después el añadido de etiquetas y finalmente la concatenación de los datasets. En cada uno de estos tres pasos, hay que definir el directorio de entrada y de salida. 

Para el paso de añadir las etiquetas, el BCMI proporciona los detalles del experimento con los que se puede conocer que estímulo emocional se ha llevado a cabo en cada momento, y así asignar la etiqueta a cada dataset. 

La ejecución de este script genera un .csv que será utilizado para entrenar los modelos de clasificación.

5) El dataset generado es el siguiente:

 'procesado_eeglab.csv' -> https://upvedues-my.sharepoint.com/:x:/g/personal/jpbolbal_upv_edu_es/Ef4jpGVlWIVMh4Urp_XYzmMBBELZfS7I4EjGHl4vnBuflw?e=9kLOGw

6) También se ha generado un dataset en el que el paso 3) ha sido obviado. Es decir, es un dataset sin el preproceso de la señal. Esto se ha realizado para estudiar el efecto del preprocesamiento en la calidad de la clasificación. 

 'procesado.csv' -> https://upvedues-my.sharepoint.com/:x:/g/personal/jpbolbal_upv_edu_es/EU5lm9Zr81hMoY9YggPDiIMBPGiLdy1-vAR7wWP0480y_Q?e=ksDDvr


7) Con estos archivos se pueden probar los diferentes modelos diseñados en el script '3.CLASSIFIERS.ipynb'. Aquí se han probado los diferentes clasificadores y se estudia la comparativa entre ambos datasets. 



--------------------------------------------------------------------------------------------
Preparacion del experimento de Reconocimiento de Emociones a partir de EEG con los modelos desarrollados.
--------------------------------------------------------------------------------------------

# TRAINING_DATA

La preparación de los datos de Training es muy similar al procedimiento ya comentado. La principal diferencia es que para este experimento disponemos de 16 canales en lugar de 62, por tanto el parametro de canales y localizaciones en el preprocesamiento es diferente. 

1) Se define el directorio en el que se tienen los datos del SEED-V segmentados y el directorio de salida, y se ejecuta el archivo '1.Preprocessing_16_Channels'. Aquí también hay que definir el directorio en el que se encuentra el archivo 'channel_16_pos', que contiene las localizaciones de los 16 canales utilizados.

2) Ejecutar el archivo 2.FEATURES_LABELS_CONCAT_TrainingData.ipynb'. La unica modificación con respecto al primer archivo de extracción de características es la función de añadido de canales faltantes con la media, ya que en este archivo se realiza la comprobación para que todos los datasets tengan 16 canales, en lugar de 62, el resto es igual.

La ejecución de este script genera un .csv que será utilizado para entrenar los modelos de clasificación.

3) El archivo se encuentra en la siguiente ruta:

- 'training_combinado.csv' -> https://upvedues-my.sharepoint.com/:x:/g/personal/jpbolbal_upv_edu_es/Ed3Dx77S5Y1GhfMDr-tlUsQBNIUoZueq--5qrZb4LiT11g?e=B8NtbH



# TEST_DATA

1) En primer lugar, descargar los archivos con la señal registrada en crudo en el experimento. Los datos están disponibles en el siguiente enlace:

https://upvedues-my.sharepoint.com/:f:/g/personal/jpbolbal_upv_edu_es/Egh4AurTKVBAqTJMgZ0gHM0B8NQJcCaw-79A7uW_Tw4uUw?e=kr9fc0

2) Ejecutar el script '0.TXT_TO_FIF.ipynb' sobre cada archivo de datos en crudo txt para convertir a un formato adecuado para el preprocesado. 

3) Al igual que se realizaba en los datos del SEED-V, se segmenta los datos en un dataset para cada video de cada individuo. Para esto ejecutar el script '1.Segment_FIFs' sobre el directorio en el que se encuentren los archivos .FIF. Se define el directorio de salida que se leera en el paso siguiente.

4) Ejecutar el script '2.Preprocessing', que contiene el algoritmo de preprocesamiento adaptado para 16 canales. 

5) Ejecutar el script '3.FEATURES_LABELS_CONCAT_E.ipynb' ya comentado anteriormente. Se ha modificado el añadido de etiquetas, ya que el experimento realizado aunque sigue la metodología del realizado para el SEED-V, no es el mismo. El orden de los estímulos emocionales se encuentra en el archivo 'Linea Temporal de la Inducción'.

6) El archivo generado se encuentra en la siguiente ruta:

- 'archivo_combinado.csv': https://upvedues-my.sharepoint.com/:x:/g/personal/jpbolbal_upv_edu_es/EUDQmSyfvcpKm3JQ8XFTVnABASsZRsSGMAtLnFkqcCViVg?e=glKbo6


