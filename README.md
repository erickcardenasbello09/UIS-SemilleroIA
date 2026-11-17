[README (1).md](https://github.com/user-attachments/files/34998540/README.1.md)
# Análisis exploratorio del puente Z24 (Grupo 4)

**Semillero de IA Aplicada a Sistemas de Ingeniería · Universidad Industrial de Santander, sede Barrancabermeja**

**Integrantes:** Erick Fabian Cárdenas Bello · Juan David Rojas Borray · Kheylor Daniel Prasca Pedraza · Mateo Lázaro

Notebook: [`EDA_Z24_Grupo4.ipynb`](EDA_Z24_Grupo4.ipynb)
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/TU_USUARIO/TU_REPO/blob/main/EDA_Z24_Grupo4.ipynb)

> Reemplazar `TU_USUARIO/TU_REPO` por los datos reales del repositorio.

## 1. Contexto
Proyecto: *Análisis y predicción del estado estructural en construcciones de concreto bajo movimiento constante mediante inteligencia artificial y captura de datos.*
Este EDA es la fase previa a entrenar una CNN 1D para clasificar el estado estructural (sano/dañado) del puente de concreto postensado Z24 (Suiza).

## 2. Pregunta de investigación del EDA
¿Qué características de las señales de aceleración (RMS, curtosis, frecuencia dominante y espectro) diferencian el estado sano del dañado, y qué tan separables son las clases antes de entrenar una CNN 1D?

## 3. Datos
- Fuente: versión procesada de Z24 en Hugging Face (`czy1215/Z24-dataset-processed`), basada en datos de KU Leuven.
- Archivos: `inputs.npy` (forma esperada `(1530, 27, 6000)` = 17 escenarios × 9 setups × 10 ventanas; 27 sensores; 6000 muestras) y `labels.npy`.
- Licencia y unidades: **por confirmar** (completar tras revisar la tarjeta del dataset).

## 4. Procedimiento
1. **Carga** de `inputs.npy` y `labels.npy` desde Hugging Face (descarga automática en Colab).
2. **Exploración**: forma de los arreglos, valores de las etiquetas y tabla escenario × etiqueta para validar la estructura.
3. **Limpieza**: NaN/inf, eliminación del offset (DC), detección de canales inactivos y segmentos inválidos.
4. **Características por segmento**: RMS, desviación estándar, curtosis, pico, frecuencia dominante, energía espectral y PSD promedio (método de Welch).
5. **Estadísticas descriptivas** por estado y por escenario, correlaciones y prueba de Mann-Whitney.
6. **Gráficos** (carpeta `figures/`).

## 5. Cómo ejecutarlo
1. Abrir el notebook en Google Colab (botón de arriba).
2. `Entorno de ejecución > Ejecutar todo`.
3. Si el notebook no encuentra los archivos, imprime la lista del repositorio; ajustar el nombre en `get_path`.

## 6. Resultados
<!-- PEGAR AQUÍ el contenido de RESULTADOS.md que genera el notebook al ejecutarse en Colab -->

### Figuras
| Figura | Qué muestra |
|---|---|
| ![g1](figures/g1_balance.png) | Segmentos por escenario y estado |
| ![g2](figures/g2_senal.png) | Señal de ejemplo sano vs. dañado |
| ![g3](figures/g3_rms.png) | RMS por escenario |
| ![g4](figures/g4_psd.png) | Espectro de potencia promedio |

## 7. Conclusiones y 8. Limitaciones
Se incluyen en el bloque de resultados pegado arriba (el notebook las genera a partir de los datos).

## 9. Siguientes pasos
Partición train/val/test **por escenario**, CNN 1D y baseline no profundo, evaluación con recall, F1 y matriz de confusión.

## 10. Referencias
Ver las referencias [1]–[6] del documento de la Actividad Semana 2 (Reynders y De Roeck, 2014; Maeck y De Roeck, 2003; dataset en Hugging Face).
