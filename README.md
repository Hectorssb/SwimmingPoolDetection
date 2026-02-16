# Swimming Pool Detection with YOLOv4

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.18659199.svg)](https://doi.org/10.5281/zenodo.18659199)

Dataset utilizado en el artículo científico:

> **A Platform for Swimming Pool Detection and Legal Verification Using a Multi-Agent System and Remote Image Sensing**
>
> International Journal of Interactive Multimedia and Artificial Intelligence (IJIMAI), 2023
>
> DOI: [10.9781/ijimai.2023.01.002](https://doi.org/10.9781/ijimai.2023.01.002) | [Open Access](https://www.ijimai.org/journal/bibcite/reference/3240)

### Cita

```
Sánchez San Blas, H., Carmona Balea, A., Sales Mendes, A., Augusto Silva, L., and Villarrubia González, G. (2023). 
A Platform for Swimming Pool Detection and Legal Verification Using a Multi-Agent System and Remote Image Sensing. 
International Journal of Interactive Multimedia and Artificial Intelligence, 8(4), 153–165. 
https://doi.org/10.9781/ijimai.2023.01.002
```

---

## Descripción

Este repositorio contiene el dataset y la configuración del modelo YOLOv4 para evaluar el rendimiento del módulo de detección de piscinas. El sistema completo descrito en el artículo es una plataforma multiagente que integra este detector con otros componentes para la verificación legal de piscinas.

El modelo está entrenado con imágenes aéreas de 512x512 píxeles.

## Estructura del Proyecto

```
SwimmingPoolDetection/
├── dataset/
│   ├── train/                    # Imágenes y anotaciones de entrenamiento
│   │   └── _annotations.coco.json
│   └── val/                      # Imágenes y anotaciones de validación
│       └── _annotations.coco.json
├── Yolov4/
│   ├── cfg/
│   │   └── yolov4-obj.cfg        # Configuración del modelo YOLOv4
│   └── data/
│       └── obj.names             # Clases del modelo
└── README.md
```

## Dataset

- **Formato**: COCO JSON
- **Resolución de imágenes**: 512 x 512 píxeles
- **Clases**: 1 (Piscinas)
- **Fecha de creación**: 2021

## Configuración del Modelo

La configuración de YOLOv4 (`Yolov4/cfg/yolov4-obj.cfg`) incluye:

| Parámetro | Valor |
|-----------|-------|
| Batch | 64 |
| Subdivisions | 64 |
| Width | 512 |
| Height | 512 |
| Max Batches | 6000 |
| Learning Rate | 0.001 |
| Mosaic | Habilitado |

## Requisitos

- [Darknet](https://github.com/AlexeyAB/darknet) compilado con soporte GPU (recomendado)
- CUDA y cuDNN (para entrenamiento con GPU)
- OpenCV

## Uso

### Entrenamiento

```bash
./darknet detector train data/obj.data Yolov4/cfg/yolov4-obj.cfg yolov4.conv.137
```

### Inferencia

```bash
./darknet detector test data/obj.data Yolov4/cfg/yolov4-obj.cfg backup/yolov4-obj_best.weights imagen.jpg
```

## Preparación del Dataset

1. Las imágenes deben estar en formato JPG
2. Las anotaciones siguen el formato COCO JSON
3. El dataset está dividido en conjuntos de entrenamiento (`train/`) y validación (`val/`)

## Resultados

El modelo está optimizado para detectar piscinas en imágenes aéreas con alta precisión.

## Licencia

Este proyecto está disponible para uso educativo y de investigación.

## Referencias

- [YOLOv4: Optimal Speed and Accuracy of Object Detection](https://arxiv.org/abs/2004.10934)
- [Darknet Framework](https://github.com/AlexeyAB/darknet)