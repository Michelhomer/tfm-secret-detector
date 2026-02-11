
# 🧠 Sistema de Detección de Secretos en Código Fuente mediante Fine-Tuning de LLMs

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/marodero/tfm-secret-detector/blob/main/TFM_V1PLUS.ipynb)
[![Python](https://img.shields.io/badge/Python-3.10%2B-blue?logo=python&logoColor=white)](https://www.python.org/)
[![Model](https://img.shields.io/badge/Model-Qwen2.5--Coder--7B-violet?logo=huggingface&logoColor=white)](https://huggingface.co/Qwen/Qwen2.5-Coder-7B)
[![License](https://img.shields.io/badge/License-Apache%202.0-green)](LICENSE)

> **Trabajo Fin de Máster - Inteligencia Artificial Aplicada a la Ciberseguridad**
> *Autor: Miguel Ángel Rodero Aguilar | Enero 2026*

---

## 📖 La Historia: Del "Detector de Metales" al "Auditor Experto"

Imagine un control de seguridad en un aeropuerto. Las herramientas tradicionales de detección de secretos (como Gitleaks o TruffleHog) funcionan como un **detector de metales antiguo**: pitan cada vez que encuentran algo metálico. No distinguen entre un arma peligrosa y las llaves de casa. En el mundo del código, esto genera miles de falsas alarmas ("fatiga de alertas") porque buscan **patrones rígidos** (expresiones regulares).

**Este proyecto propone una evolución:**

Hemos entrenado una Inteligencia Artificial para que actúe como un **Agente de Seguridad Experto**. Este modelo no busca patrones ciegamente; **lee, comprende el contexto y decide** si un fragmento de código es realmente una credencial expuesta o simplemente una variable inofensiva.

### 🎯 Lo que hemos conseguido
1.  **Comprensión Semántica:** El modelo distingue entre `API_KEY = "12345"` (Peligro 🔴) y `API_KEY = os.getenv("KEY")` (Seguro 🟢).
2.  **Cero Falsos Negativos:** En las pruebas, mientras las herramientas tradicionales dejaban pasar secretos complejos, nuestro modelo detectó el **100%** de las amenazas reales.
3.  **Democratización:** Todo esto funciona en una GPU gratuita de Google Colab. No hacen falta superordenadores.

---

## 🚀 Guía de Reproducción para el Tribunal

He diseñado el código (`TFM_V1PLUS.ipynb`) para que sea **autónomo, robusto y a prueba de fallos**. Puede ejecutarlo con total tranquilidad siguiendo estos pasos:

### 1. Abrir el Laboratorio
Haga clic en el botón **"Open in Colab"** al inicio de este documento o abra el archivo `.ipynb` incluido.

### 2. Configurar el Motor (GPU)
Para que la IA "piense" rápido, necesitamos activar la aceleración por hardware:
* En el menú superior de Colab: `Entorno de ejecución` > `Cambiar tipo de entorno de ejecución`.
* Seleccione **T4 GPU** (es gratuita y suficiente).

### 3. Ejecutar la Magia
Pulse `Ctrl + F9` o vaya a `Entorno de ejecución` > `Ejecutar todas`.

---

## 🛡️ Mecanismo de Seguridad de Datos ("Safe Mode")

**¿Qué pasa si no tengo los datos originales?**
El entrenamiento original se realizó con el dataset *CredData* (Samsung), que reside en almacenamiento privado. Soy consciente de que usted, como evaluador, no tiene acceso a esos archivos.

**Solución Implementada:**
El notebook incluye un sistema inteligente de detección de entorno:
1.  Intenta buscar los datos reales en Google Drive.
2.  🚨 **Si no los encuentra (su caso):** El código lo detecta automáticamente y activa el **"Modo Demostración"**.
3.  **Generación Sintética:** El sistema creará al vuelo un dataset sintético de alta calidad que imita los patrones reales.

> **Resultado:** Usted podrá ejecutar el entrenamiento completo (Fine-Tuning con LoRA) de principio a fin, ver cómo baja la curva de pérdida y probar el modelo, **sin necesidad de configurar ni descargar nada externo**.

---

## 🔬 Bajo el Capó: Tecnologías Clave

Para lograr resultados profesionales con recursos limitados, hemos integrado lo mejor del estado del arte:

| Tecnología | ¿Qué es? | ¿Qué conseguimos con ella? |
| :--- | :--- | :--- |
| **Qwen2.5-Coder** | El "Cerebro" | Un modelo Open Source que ya sabe programar. No empezamos de cero. |
| **Unsloth AI** | El "Acelerador" | Optimiza el entrenamiento haciéndolo 2x más rápido y consumiendo menos memoria. |
| **QLoRA (4-bit)** | La "Compresión" | Nos permite cargar un modelo gigante (7B parámetros) en una tarjeta gráfica pequeña (16GB), sin perder inteligencia. |

---

## 📊 Resultados de la Evaluación (Anexo C)

Comparamos nuestro "Auditor IA" contra el estándar de la industria (Gitleaks) en 25 casos de prueba complejos:

| Métrica | Nuestro Modelo (IA) | Gitleaks (Regex) | Análisis |
| :--- | :---: | :---: | :--- |
| **Recall** | **100%** | 50% | **Seguridad Total.** La IA no dejó escapar ningún secreto. Gitleaks perdió la mitad. |
| **F1-Score** | **90,9%** | 66,7% | **Equilibrio.** La IA combina mejor la capacidad de encontrar secretos y evitar falsas alarmas. |

---

## 📂 Estructura del Repositorio

* `TFM_V1PLUS.ipynb`: **El núcleo del trabajo.** Notebook completo y documentado.
* `DOCUMENTO_TECNICO_V12.pdf`: Memoria técnica detallada.
* `Detección_de_Secretos_Código_Fuente_LLM.pdf`: Presentación ejecutiva.
* `README.md`: Esta guía.

---

*Proyecto desarrollado con pasión por la ciberseguridad defensiva.*
*Máster en IA Aplicada a la Ciberseguridad - UCAM*

