# Seoul Bikes: bicicletas para mañana

Página web que predice la demanda horaria de bicicletas en Seúl y recomienda cuántas tener disponibles.
Las predicciones usan los pipelines entrenados que están en `artifacts/` (cargados con joblib, sin reentrenar).

## Estructura

```
app/servidor.py        servidor HTTP (biblioteca estándar) + API
app/index.html         interfaz web
artifacts/             seoul_pipeline_prep.joblib, seoul_pipeline_modelo.joblib, seoul_metadata.json
requirements.txt       versiones exactas del entrenamiento
.python-version        Python 3.12.16 (el mismo del entrenamiento)
```

## Ejecutar en local

```
pip install -r requirements.txt
python app/servidor.py
```

Abrir http://localhost:8000.

## Despliegue en Render (Web Service, Python, plan Free)

- Build Command: `pip install -r requirements.txt`
- Start Command: `python app/servidor.py`

Render define la variable `PORT`; el servidor la lee y escucha en `0.0.0.0`.

## API

- `GET /api/modelo`: información del modelo cargado.
- `POST /api/prediccion` con JSON, por ejemplo:
  `{"fecha":"2026-07-15","tmin":22,"tmax":22,"humedad":55,"lluvia":0,"nieve":0,"festivo":false}`
