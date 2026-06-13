# Prueba Técnica — Científico de Datos
**Autor:** Daniel Ferrer  
**Empresa:** Naowee S.A.S  
**Modalidad:** Take-home + sustentación técnica

---

## Datos

Los datasets **no están incluidos** en el repositorio. Deben descargarse desde Kaggle antes de ejecutar los notebooks.

### Opción A — Kaggle API (recomendada)

Instalar la CLI de Kaggle y configurar credenciales:

```bash
pip install kaggle

# Colocar el archivo kaggle.json en ~/.kaggle/
# Descargarlo desde: https://www.kaggle.com/settings → API → Create New Token
mkdir -p ~/.kaggle
mv kaggle.json ~/.kaggle/
chmod 600 ~/.kaggle/kaggle.json
```

Descargar los datasets:

```bash
# Caso 1
kaggle datasets download -d jessemostipak/hotel-booking-demand -p data/caso1/ --unzip

# Caso 2
kaggle datasets download -d blastchar/telco-customer-churn -p data/caso2/ --unzip
```

### Opción B — Descarga manual

| Caso | Dataset | URL |
|---|---|---|
| Caso 1 | Hotel Booking Demand | https://www.kaggle.com/datasets/jessemostipak/hotel-booking-demand |
| Caso 2 | Telco Customer Churn | https://www.kaggle.com/datasets/blastchar/telco-customer-churn |

Colocar los archivos descargados en:
```
data/caso1/hotel_bookings.csv
data/caso2/WA_Fn-UseC_-Telco-Customer-Churn.csv
```

### Opción C — kagglehub (en notebook)

```python
import kagglehub

# Caso 1
path = kagglehub.dataset_download("jessemostipak/hotel-booking-demand")

# Caso 2
path = kagglehub.dataset_download("blastchar/telco-customer-churn")
```

---

## Instalación y entorno

### Requisitos previos

- Python 3.10 o superior
- pip 23 o superior

### Instalación local

```bash
# 1. Clonar el repositorio
git clone https://github.com/Dferrer2405/Prueba-tecnica-naowee--Daniel-Ferrer.git
cd Prueba-tecnica-naowee--Daniel-Ferrer

# 2. Crear entorno virtual
python -m venv venv
source venv/bin/activate        # Linux / Mac
venv\Scripts\activate           # Windows

# 3. Instalar dependencias
pip install -r requirements.txt

# 4. Lanzar Jupyter
jupyter notebook
```

### Instalación en Google Colab

Cada notebook incluye una celda inicial de instalación de dependencias. Ejecutarla antes de continuar:

```python
# Celda 1 de cada notebook — ejecutar primero
!pip install -r requirements.txt
```

---

## Dependencias

```
pandas==2.2.2
numpy==1.26.4
matplotlib==3.9.0
seaborn==0.13.2
scikit-learn==1.5.0
statsmodels==0.14.2
scipy==1.13.1
jupyter==1.0.0
kaggle==1.6.14
kagglehub==0.2.9
imbalanced-learn==0.12.3
```

> Las versiones están fijadas para garantizar reproducibilidad. El archivo `requirements.txt` en la raíz del repositorio contiene esta lista completa.
