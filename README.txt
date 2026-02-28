# Detección de Secretos Hardcodeados en Código Fuente mediante Fine-Tuning de LLMs

[![Abrir en Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/marodero/tfm-secret-detector/blob/main/TFM_FINAL_Secret_Detector.ipynb)
[![Python 3.10+](https://img.shields.io/badge/Python-3.10%2B-blue?logo=python&logoColor=white)](https://www.python.org/)
[![Modelo Base](https://img.shields.io/badge/Modelo-Qwen2.5--Coder--7B-violet?logo=huggingface&logoColor=white)](https://huggingface.co/Qwen/Qwen2.5-Coder-7B)
[![Licencia](https://img.shields.io/badge/License-Apache%202.0-green)](LICENSE)

> **Trabajo Fin de Máster — Máster en Inteligencia Artificial Aplicada a la Ciberseguridad (MIAC)** > Universidad Católica de Murcia (UCAM) · Campus Internacional de Ciberseguridad · ENIIT  
> **Autor:** Miguel Ángel Rodero Aguilar | Febrero 2026

---

## 🎯 De qué trata este trabajo, en una frase

Hemos enseñado a un modelo de lenguaje a leer código fuente y decidir si una credencial está expuesta de forma peligrosa — algo que las herramientas tradicionales basadas en patrones rígidos (expresiones regulares) no pueden hacer porque reconocen la *forma* de una clave, pero no su *significado*.

La diferencia práctica: una herramienta clásica necesitaría una GPU de gama alta o varias horas de cómputo. Nosotros lo hemos logrado de forma eficiente.

---

## ⚙️ Instrucciones de Ejecución y Reproducibilidad

Este proyecto ha sido diseñado para ser **100% reproducible** en un entorno gratuito de Google Colab. No necesitas descargar nada localmente ni configurar dependencias complejas en tu máquina. 

Para ejecutar el experimento y replicar los resultados de la memoria técnica, sigue estos pasos:

1. **Abrir el entorno:** Haz clic en el botón azul de arriba `Abrir en Colab` o abre directamente el archivo `TFM_FINAL_Secret_Detector.ipynb` en Google Colab.
2. **Configurar el Hardware:** En el menú superior de Colab, ve a `Entorno de ejecución` > `Cambiar tipo de entorno de ejecución`. Asegúrate de que el **Acelerador por hardware** esté configurado en **GPU T4** (disponible en la capa gratuita).
3. **Gestión de Datos:** No es necesario subir ningún archivo manual a tu Google Drive. El propio *notebook* se encarga de descargar los *datasets* necesarios y clonar los repositorios de evaluación de forma automática en la máquina virtual.
4. **Ejecución:** Ve a `Entorno de ejecución` > `Ejecutar todo` (o presiona `Ctrl + F9`).
5. **Tiempo estimado:** El proceso completo de instalación de dependencias, preparación de datos, *fine-tuning* (QLoRA) y evaluación final toma aproximadamente **entre 60 y 90 minutos**.

> **Nota de replicabilidad:** El *notebook* incluye una configuración estricta de semillas de aleatoriedad (*seeds*) en la Fase 0 para garantizar que la partición de datos y la inicialización de pesos produzcan resultados deterministas en cada ejecución.

---

## 📂 Estructura del repositorio

```text
tfm-secret-detector/
│
├── TFM_FINAL_Secret_Detector.ipynb   # El experimento completo. Ejecuta esto.
├── DOCUMENTO_TECNICO_V27.docx        # Memoria técnica con toda la evidencia científica.
├── AI_Secret_Detection.pdf           # Presentación ejecutiva (6 slides).
└── README.md                         # Esta guía.
```

---

## 📚 Referencia académica

Si este trabajo te resulta útil para tu investigación o proyecto, por favor, cítalo de la siguiente manera:

```text
Rodero Aguilar, M. Á. (2026). Detección de Secretos en Código Fuente
mediante Fine-Tuning de Modelos de Lenguaje. Trabajo Fin de Máster,
Máster en Inteligencia Artificial Aplicada a la Ciberseguridad (MIAC),
Universidad Católica de Murcia (UCAM).
```

**Principales fuentes citadas en el trabajo:**

* GitGuardian (2025). *State of Secrets Sprawl 2025*. https://www.gitguardian.com/state-of-secrets-sprawl
* Hu, E. J. et al. (2022). *LoRA: Low-Rank Adaptation of Large Language Models*. ICLR 2022.
* Qwen Team, Alibaba Cloud (2024). *Qwen2.5-Coder Technical Report*. arXiv:2409.12186.
* Saha, R. et al. (2024). *HasSecret: A Benchmark for Detecting Hardcoded Secrets in Source Code*. IEEE SANER 2024.