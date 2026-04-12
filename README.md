# 🗺️ Mapa de Calidad de Vida en España

Proyecto open source para visualizar el **estado real de cada municipio en España** en función de su acceso a servicios, conectividad, coste de vida y calidad de vida.

---

## 🎯 Objetivo

Crear un mapa interactivo que permita responder preguntas como:

* ¿Cuánto se tarda realmente en llegar a un hospital?
* ¿Qué pueblos tienen buena conectividad (fibra, 5G)?
* ¿Dónde se vive mejor combinando servicios + coste de vida?
* ¿Qué zonas rurales tienen mejor calidad de vida real?

👉 Todo basado en **tiempos reales por carretera**, no distancias teóricas.

---

## 🧠 Concepto clave

El proyecto calcula un **índice de calidad de vida por municipio** basado en:

### 🔴 Servicios esenciales (35%)

* Hospital (urgencias 24h)
* Centro de salud
* Educación (IES, FP)

### 🟣 Conectividad y energía (28%) ⭐

* Fibra óptica (Mbps reales)
* Cobertura móvil (4G / 5G)
* Potencial autoconsumo energético

### 🟢 Ocio, deporte y naturaleza (20%)

* Instalaciones deportivas
* Piscinas, gimnasios
* Senderismo, BTT, río
* Vida social (bares)

### 🟡 Coste de vida (17%)

* Vivienda (€/m²)
* Impuestos locales
* Costes básicos (alimentación, ocio)
* Aparcamiento

### 🎉 Bonus: Ocio cultural

* Fiestas patronales
* Eventos anuales

---

## 📍 Ejemplo real

Municipio: Santacara (Navarra)

* Hospital: ~45-55 min
* IES: ~12 min (transporte gratuito)
* Fibra: 1000 Mbps
* Piscina cubierta: 12 min
* Coste de vida: bajo
* Ocio local: alto

👉 Resultado: buena calidad de vida relativa en entorno rural

---

## 🏗️ Arquitectura del proyecto

### 🔧 Backend (procesado de datos)

* Python
* Geopandas
* OSRM (routing engine)
* Tippecanoe (vector tiles)

#### Pipeline:

1. Cargar límites municipales (CNIG)
2. Extraer POIs (OpenStreetMap)
3. Calcular tiempos reales por carretera
4. Normalizar métricas
5. Generar índice por municipio
6. Exportar a GeoJSON / PMTiles

---

### 🗺️ Frontend (mapa web)

* MapLibre GL JS
* Visualización por capas:

  * Sanidad
  * Conectividad
  * Coste de vida
  * Índice global

#### Funcionalidades:

* Selector de capas
* Popups por municipio
* Buscador
* Escalas de color (verde → rojo)
* Ajuste de pesos (futuro)

---

## 📊 Estructura de datos (GeoJSON)

Ejemplo:

```json
{
  "municipio": "Santacara",
  "poblacion": 870,

  "tiempo_hospital_min": 48,
  "tiempo_ies_min": 12,

  "fibra_mbps": 1000,
  "tiempo_5g_min": 12,

  "indice_coste_vida": 0.3,
  "indice_ocio": 0.8,

  "indice_global": 0.72
}
```

---

## 🌍 Fuentes de datos

* CNIG / IGN → límites municipales
* OpenStreetMap → carreteras y servicios
* Ministerio de Transformación Digital → fibra y cobertura
* INE → población y datos socioeconómicos
* Datos autonómicos → sanidad, educación, instalaciones

---

## 🚀 Estado del proyecto

🔨 En desarrollo (fase inicial)

### Roadmap:

* [ ] MVP Navarra
* [ ] Pipeline Python básico
* [ ] Primer GeoJSON funcional
* [ ] Mapa web inicial
* [ ] Escalado a toda España
* [ ] Optimización con tiles vectoriales
* [ ] Sistema de actualización automática

---

## 📦 Estructura del repositorio

```
/data
  /raw
  /processed

/scripts
  process_data.py
  routing.py

/web
  index.html
  app.js
  styles.css

/tiles
README.md
```

---

## ⚡ Cómo empezar

```bash
git clone https://github.com/domoprac/mapa-calidad-vida
cd mapa-calidad-vida

pip install -r requirements.txt
```

---

## 🤝 Contribuir

Este proyecto está abierto a:

* Desarrolladores Python / JS
* Expertos GIS
* Analistas de datos
* Conocimiento local (validación real)

---

## 💡 Visión

Crear el mapa más preciso de calidad de vida en España:

* útil para ciudadanos
* útil para políticas públicas
* útil contra la despoblación

---

## 📜 Licencia

MIT License

---

## 📬 Contacto

Proyecto impulsado por domoprac
https://github.com/domoprac/mapa-calidad-vida

