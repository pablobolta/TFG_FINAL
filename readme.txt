SEEDV FOLDER:

1. SEEDV_Dataset.txt: Link para solicitar acceso a los datos SEED-V del BCMI.

2. 0.Segments_SEEDV.mlx: Dividir los archivos de datos EEG en crudo de SEED-V en datasets. Cada dataset generado contiene las señales EEG generadas mientras un individuo estaba viendo un video en una de las sesiones. Genera un dataset por cada video, en cada sesion por cada individuo. 16 individuos, por 3 sesiones cada uno, por 15 videos en cada sesion; 720 archivos generados. Descarta los segmentos de datos en los que se registra señal EEG pero el individuo no tenía estimulo emocional. 

3. 1.Preprocessing.mlx: Algoritmo de preprocesamiento para señales EEG. Lee los datasets y genera nuevos datasets con la señal limpia.

4. 2.FEATURES_LABELS_CONCAT.ipynb: Calcula las features para cada archivo, añade las etiquetas correspondientes y concatena en un único csv.

5. 3.CLASSIFIERS.ipynb: Pruebas de diferentes modelos de clasificación. Obtiene diferentes métricas para los modelos. Comparativas de clasificación cuando el archivo había sido preprocesado previamente y no. 

Procesado.csv: Archivo final sin preprocesar con EEGLAB. https://upvedues-my.sharepoint.com/:f:/g/personal/jpbolbal_upv_edu_es/ErhSWXqCA6BNo01nx9BC5AQB7ROlHbzeqzBqiI9rJoz3PQ?e=n7iRjm

Procesado_eeglab.csv: Archivo final con el preprocesamiento de EEGLAB.  https://upvedues-my.sharepoint.com/:f:/g/personal/jpbolbal_upv_edu_es/ErhSWXqCA6BNo01nx9BC5AQB7ROlHbzeqzBqiI9rJoz3PQ?e=n7iRjm


TEST FOLDER:

-TEST DATA:

1. Archivos OpenBCI_RAW.txt: Datos recogidos en el experimento realizado. Uno por cada individuo. https://upvedues-my.sharepoint.com/:f:/g/personal/jpbolbal_upv_edu_es/ErhSWXqCA6BNo01nx9BC5AQB7ROlHbzeqzBqiI9rJoz3PQ?e=n7iRjm

2. Linea Temporal de la Induccion: Experimento realizado, tiempos de cada video mostrado con la emoción correspondiente. 

3. channel_16_pos: Localizaciones de los canales utilizados en el experimento.

4. 0.TXT_TO_FIF_.ipynb: Script para convertir los archivos en crudo generados a archivos .FIF utilizables en EEGLAB.

5. 1.Segment_FIFs: Segmentar los archivos en un dataset por cada video por cada individuo. 

6. 2.Preprocessing: Algoritmo de procesamiento para señales EEG. Adaptado para 16 canales. 

7. 3.FEATURES_LABELS_CONCAT_E.ipynb: Calcula las features para cada archivo, añade las etiquetas correspondientes y concatena en un único csv.

Archivo_combinado.csv: Archivo generado tras el proceso. Se utiliza como test en el experimento. https://upvedues-my.sharepoint.com/:f:/g/personal/jpbolbal_upv_edu_es/ErhSWXqCA6BNo01nx9BC5AQB7ROlHbzeqzBqiI9rJoz3PQ?e=n7iRjm


-TRAINING DATA:

1. 1.Preprocessing_16_Channels: Algoritmo de procesamiento para señales EEG. Adaptado para 16 canales.

2. 2.FEATURES_LABELS_CONCAT_E.ipynb: Calcula las features para cada archivo, añade las etiquetas correspondientes y concatena en un único csv.

Training_combinado.csv: Archivo generado tras el proceso. Se utiliza como training en el experimento. https://upvedues-my.sharepoint.com/:f:/g/personal/jpbolbal_upv_edu_es/ErhSWXqCA6BNo01nx9BC5AQB7ROlHbzeqzBqiI9rJoz3PQ?e=n7iRjm
