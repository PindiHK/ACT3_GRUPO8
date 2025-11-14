# Proyecto FastAPI - Práctica Arquitectura Orientada a Servicios

## Descripción general

Este proyecto es una **API construida con FastAPI** y organizada siguiendo las buenas prácticas de modularización. Incluye endpoints para procesar operaciones básicas y está preparado para desplegarse fácilmente tanto localmente como en entornos de nube como AWS EC2.

## Estructura del proyecto

```
aossample/
│
├── app/
│   ├── __init__.py
│   ├── main.py
│   ├── routes/
│   │   ├── __init__.py
│   │   └── sample.py
│   ├── models/
│   │   ├── __init__.py
│   │   └── item.py
│   ├── tests/
│   │   ├── __init__.py
│   │   └── test_sample.py
│   └── requirements.txt
├── venv/ (opcional, autocreada al instalar)
└── README.md (este archivo)
```

## Instalación y ejecución - Paso a paso

**IMPORTANTE:** Si está ejecutando el proyecto en una instancia EC2, asegúrese de tener Python 3.8+ y pip instalados.

### 1. Clonar el repositorio

```bash
git clone <ruta-repositorio-o-descargar-zip>
cd aossample
```

### 2. Crear el entorno virtual y activarlo

- **Linux/macOS**:
  ```bash
  python3 -m venv venv
  source venv/bin/activate
  ```
- **Windows**:
  ```cmd
  python -m venv venv
  venv\Scripts\activate
  ```

### 3. Instalar las dependencias

```bash
pip install -r app/requirements.txt
```

### 4. Ejecutar la API

```bash
uvicorn app.main:app --reload
```
La aplicación estará disponible en http://127.0.0.1:8000

- Documentación interactiva Swagger: http://127.0.0.1:8000/docs
- Documentación ReDoc: http://127.0.0.1:8000/redoc

### 5. Probar los endpoints

#### POST `/process`
- **Descripción**: Recibe dos números enteros y devuelve la suma.
- **Ejemplo de request:**
  ```json
  {
    "value1": 10,
    "value2": 5
  }
  ```
- **Respuesta:**
  ```json
  {
    "result": 15
  }
  ```

#### GET `/concat`
- **Descripción**: Concatena dos cadenas recibidas como parámetros `param1` y `param2`.
- **Ejemplo:**
  ```
  /concat?param1=Hola&param2=Mundo
  ```
- **Respuesta:**
  ```json
  {
    "result": "HolaMundo"
  }
  ```

#### GET `/length`
- **Descripción**: Devuelve el tamaño de la cadena recibida con el parámetro `string`.
- **Ejemplo:**
  ```
  /length?string=FastAPI
  ```
- **Respuesta:**
  ```json
  {
    "length": 7
  }
  ```

### 6. Ejecutar tests (opcional)

Las pruebas unitarias están en `app/tests/test_sample.py`. Para ejecutarlas:
```bash
python -m pytest
```

## Notas
- El entorno virtual no es obligatorio pero **altamente recomendado** para evitar conflictos entre dependencias de proyectos.
- Puedes generar el archivo `requirements.txt` actualizado usando `pip freeze > app/requirements.txt` después de instalar nuevas dependencias.
- El código sigue la estructura recomendada para proyectos FastAPI: separación clara por modelos, rutas y pruebas.

## Contacto y colaboración

Si detectas errores o quieres proponer mejoras, siéntete libre de hacer un pull request o abrir una issue en el repositorio.

---

**¡Esperamos que el uso e importación del proyecto sea cómodo y accesible para todos los usuarios, tanto en local como en la nube!**