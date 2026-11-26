# Organizador de Descargas

Toma una carpeta desordenada y mueve cada archivo a una subcarpeta según su tipo: Imagenes, Documentos, Videos, Musica, Comprimidos, Instaladores y Otros.

## ¿Qué problema resuelve?

La carpeta de Descargas se llena rápido: fotos de WhatsApp, PDFs de la clase, instaladores, videos, archivos .zip… todo revuelto en un solo lugar. Encontrar algo ahí toma tiempo, y ordenarlo a mano es aburrido.

Este script lo hace por ti en menos de un segundo: revisa la extensión de cada archivo (`.jpg`, `.pdf`, `.exe`…) y lo mueve a la carpeta que le corresponde.

## Cómo usarlo

Solo necesitas Python. No hay que instalar nada, ni crear un entorno virtual.

```
python crear_desorden.py      # crea una carpeta de prueba revuelta
python organizador.py         # la ordena
```

Si `python` no funciona en tu computador, usa `py`.

Al terminar, muestra el total de archivos que movió y cuántos fueron a cada categoría:

```
¡Listo! Organicé 56 archivos en 0.025 segundos.
Imagenes: 12 · Documentos: 16 · Videos: 7 · Musica: 6 · Comprimidos: 6 · Instaladores: 4 · Otros: 5
```

`crear_desorden.py` se puede ejecutar las veces que quieras: siempre deja la carpeta revuelta otra vez. Así pruebas sin riesgo, sin tocar tus archivos reales.

## Ejemplo de lo que muestra en pantalla

Mientras trabaja, el script dice a dónde mueve cada archivo. Al final muestra el total y el detalle por categoría:

```
Organizando 'descargas_de_prueba'...

  acceso_directo.lnk  ->  Otros/
  archivo_raro.xyz  ->  Otros/
  atardecer.jpg  ->  Imagenes/
  base_de_datos_clientes.csv  ->  Documentos/
  ...
  setup_vscode.exe  ->  Instaladores/
  ...

¡Listo! Organicé 56 archivos en 0.026 segundos.
Imagenes: 12 · Documentos: 16 · Videos: 7 · Musica: 6 · Comprimidos: 6 · Instaladores: 4 · Otros: 5
```

Y la carpeta queda así:

```
descargas_de_prueba/
├── Comprimidos/
├── Documentos/
├── Imagenes/
├── Instaladores/
├── Musica/
├── Otros/
└── Videos/
```

## Categorías

| Carpeta | Extensiones |
|---|---|
| Imagenes | `.jpg` `.jpeg` `.png` `.gif` `.webp` |
| Documentos | `.pdf` `.docx` `.xlsx` `.pptx` `.txt` `.csv` |
| Videos | `.mp4` `.mov` `.avi` `.mkv` |
| Musica | `.mp3` `.wav` `.m4a` |
| Comprimidos | `.zip` `.rar` `.7z` |
| Instaladores | `.exe` `.msi` |
| Otros | Todo lo que no está en ninguna de las anteriores |

Para agregar una categoría nueva solo hay que sumar una línea al diccionario `CATEGORIAS` en `organizador.py`.

## Lo que vas a aprender con este script

| Concepto | Dónde está en el código | Qué hace |
|---|---|---|
| **Variable** | `CARPETA = Path("descargas_de_prueba")` | Guarda un dato para usarlo después |
| **Diccionario** | `CATEGORIAS = { "Imagenes": [...], ... }` | Relaciona cada categoría con su lista de extensiones |
| **Lista** | `[".jpg", ".jpeg", ".png"]` | Guarda varios valores en orden |
| **Función** | `def categoria_de(archivo):` | Un bloque de código con nombre, que se puede usar muchas veces |
| **Ciclo `for`** | `for archivo in carpeta.iterdir():` | Repite lo mismo con cada archivo de la carpeta |
| **Condicional `if`** | `if extension in extensiones:` | Decide qué hacer según una condición |
| **Contador** | `movidos += 1` | Suma uno cada vez que mueve un archivo |
| **Diccionario como contador** | `conteo[categoria] = conteo.get(categoria, 0) + 1` | Lleva la cuenta de cuántos archivos van a cada categoría |
| **Módulos** | `import shutil`, `import time` | Herramientas que ya trae Python: mover archivos y medir el tiempo |
| **f-string** | `f"Organicé {movidos} archivos"` | Arma un texto con valores adentro |

## Cómo está organizado el código

1. **Configuración** (arriba): la carpeta a ordenar y las categorías. Casi todos los cambios empiezan aquí.
2. **`categoria_de()`**: mira la extensión de un archivo y decide su categoría.
3. **`organizar()`**: recorre la carpeta, mueve cada archivo y cuenta cuántos movió y cuánto se demoró.
4. **`if __name__ == "__main__":`**: lo que se ejecuta cuando corres `python organizador.py`.

## Equipo

- **David Valencia** ([@davidvalenciadiosa-ux](https://github.com/davidvalenciadiosa-ux))
- **José Daniel Cruz** ([@KuitaPanadero](https://github.com/KuitaPanadero))

## ¿Qué más automatizaríamos?

- **David Valencia:** las grabaciones de mis partidas y los videos que edito para YouTube se amontonan en una sola carpeta. Usaría la misma idea del organizador para moverlos a carpetas por juego y por mes, según el nombre y la fecha del archivo.
- **José Daniel Cruz:** los correos de marcas que me escriben para patrocinios de mi canal. Los clasificaría automáticamente por marca y por estado (nuevo, en negociación, contenido por entregar, entregado) y me avisaría cuando se acerque una fecha de entrega, para que ninguno se quede sin respuesta.
