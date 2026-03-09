# Detección Inteligente de Secretos Hardcodeados en Código Fuente mediante Fine-Tuning de LLMs

Este repositorio contiene el desarrollo íntegro del Trabajo Fin de Máster (TFM) para el **Máster en Inteligencia Artificial Aplicada a la Ciberseguridad (MIAC)** de la Universidad Católica de Murcia (UCAM).


El proyecto propone una solución avanzada para la identificación de credenciales, tokens y claves privadas expuestas en código fuente. A diferencia de las herramientas tradicionales basadas en expresiones regulares, esta solución emplea un modelo de lenguaje de gran escala (LLM) especializado en programación, reentrenado específicamente para comprender el contexto semántico de una filtración de datos.

---

## Objetivo del Proyecto

Demostrar la viabilidad y eficacia del uso de modelos de lenguaje (específicamente **Qwen2.5-Coder-7B**) para la detección de secretos mediante la técnica de entrenamiento eficiente **QLoRA**. El modelo es capaz de generalizar la detección a servicios no vistos previamente y discernir entre secretos reales y falsos positivos (como placeholders o variables de entorno), superando las métricas de herramientas estándares de la industria como Gitleaks.

---

## Especificaciones Técnicas

*   **Modelo Base:** Qwen2.5-Coder-7B (Alibaba Cloud).
*   **Arquitectura de Entrenamiento:** QLoRA (Quantized Low-Rank Adaptation).
*   **Cuantización:** 4-bit (NF4) para optimización de VRAM.
*   **Entorno:** Python 3.10+ ejecutado en Google Colab (GPU Tesla T4 16GB).
*   **Librería Principal:** Unsloth (para aceleración de Fine-Tuning).
*   **Datasets Utilizados:**
    *   **CredData:** Benchmark de secretos reales en repositorios de software.
    *   **CodeSearchNet:** Funciones de código real de GitHub para el entrenamiento de muestras seguras (SAFE).
    *   **Datos Sintéticos:** Generados para fortalecer patrones específicos de remediación.

---

## Estructura del Notebook y Ejecución

El núcleo del proyecto se encuentra en el notebook interactivo proporcionado. El flujo de ejecución está dividido en las siguientes fases:

1.  **Fase 0-1 (Preparación):** Instalación de dependencias críticas y carga del modelo base en memoria de video.
2.  **Fase 0.1 (Configuración):** Definición inmutable de hiperparámetros (Learning Rate, Steps, Rank de LoRA).
3.  **Fase 3 (Procesamiento de Datos):** Carga, limpieza y balanceo del dataset híbrido. Incluye un sistema de respaldo automático si no se dispone de acceso a unidades externas.
4.  **Fase 4 (Entrenamiento):** Proceso de Fine-Tuning. El modelo ajusta el 0.92% de sus parámetros (40.4M) durante 200 pasos.
5.  **Fase 6 (Evaluación):** Validación contra un conjunto de datos externo y comparación estadística mediante técnicas de *Bootstrap* contra herramientas de detección basadas en reglas.
6.  **Fases 7-9 (Análisis y Conclusión):** Pruebas de interpretabilidad, generalización multilenguaje y remediación automática.

---

## Instrucciones para la Replicabilidad

Para reproducir los resultados enunciados en la memoria técnica, siga estos pasos:

1.  Cargar el archivo `TFM_FINAL_Secret_Detector.ipynb` en una sesión de Google Colab.
2.  Asegurarse de tener activado un entorno con **GPU** (Entorno de ejecución > Cambiar tipo de entorno de ejecución > T4 GPU).
3.  Ejecutar todas las celdas de forma secuencial (`Ctrl + F9`).
4.  **Nota sobre los datos:** El notebook está configurado con una semilla aleatoria fija (Seed: 42) para garantizar que las particiones de entrenamiento y test sean consistentes en cada ejecución.

---

## Aportaciones Principales

*   **Reducción de Falsos Negativos:** El modelo identifica claves con formatos no estandarizados que las reglas fijas omiten.
*   **Comprensión Semántica:** Capacidad de distinguir entre una clave "fake" de ejemplo y una clave con entropía real.
*   **Eficiencia de Recursos:** Implementación de un modelo de 7 billones de parámetros en hardware gratuito de consumo, reduciendo el tiempo de entrenamiento a menos de 20 minutos.
*   **Soporte Multilenguaje:** Aunque entrenado mayoritariamente en Python, el modelo demuestra capacidad de transferencia a lenguajes como JavaScript, Java, Go y YAML.

---

## Autoría e Institución

*   **Autor:** Miguel Ángel Rodero Aguilar
*   **Programa:** Máster en Inteligencia Artificial Aplicada a la Ciberseguridad (MIAC)
*   **Institución:** Universidad Católica de Murcia (UCAM) / Campus Internacional de Ciberseguridad / ENIIT

---

> **Aviso Legal:** Este proyecto se ha desarrollado con fines exclusivamente académicos y de investigación en ciberseguridad. El uso de modelos de lenguaje para procesar código sensible debe realizarse siempre en entornos controlados y seguros.
