<img width="1023" height="141" alt="image" src="https://github.com/user-attachments/assets/b01b9cb4-445d-4e6c-af71-dd2374e23fcf" /># Proyecto-Final-Seguridad

# Objetivo General
Desarrollar un sistema automatizado que detecte activos de telecomunicaciones mediante YOLO, asegure su transmisión mediante cifrado y evalúque el cumplimiento de la norma ISO 27001

Como primer paso, se debe descargar las librerias en python

<img width="1914" height="1009" alt="image" src="https://github.com/user-attachments/assets/61e125e8-b184-481e-aa2c-1af689a676a5" />

¿Qué se está instalando en este paso?
# ultralytics: 
Es el paquete oficial que contiene el framework de YOLOv8. Con esto podrás entrenar y ejecutar la inteligencia artificial para detectar los activos de telecomunicaciones (routers, switches, etc.). 
# cryptography: 
La librería de seguridad que usarás para el Módulo 2 para realizar el cifrado simétrico (AES), asimétrico (RSA) y el cálculo del Hash (SHA-256).  
# opencv-python: 
Te servirá para leer, procesar y guardar las imágenes que capture tu sistema de inventario visual.  
# pandas: 
Ideal para estructurar y guardar el inventario de activos en un formato ordenado como tablas, CSV o JSON.  


Como segundo paso, entramos a Roboflow , descargamos las imagenes 

<img width="1326" height="547" alt="image" src="https://github.com/user-attachments/assets/b3e89ea3-d8f6-4600-9547-7f496b37f9bd" />

Descargamos el archivo en yolov8 y el archivo en zip

<img width="916" height="121" alt="image" src="https://github.com/user-attachments/assets/3df9e7db-946c-467a-94bf-627508bd33ba" />

Luego en Python cargamos el archivo

<img width="1868" height="320" alt="image" src="https://github.com/user-attachments/assets/3873b76a-6cb0-4161-9032-a9ccd048ff67" />

El siguiente paso lógico es entrenar el modelo de visión artificial utilizando esos datos que acabas de bajar. Como especificamos el formato "yolov8", usaremos la librería oficial de Ultralytics para poner en marcha el entrenamiento.

# Instalar la librería de entrenamiento (YOLO)

<img width="1819" height="866" alt="image" src="https://github.com/user-attachments/assets/4425af99-3b7c-4cd8-80e8-7248c8d0b5a6" />

# Poner a correr el entrenamiento
<img width="1777" height="265" alt="image" src="https://github.com/user-attachments/assets/580574e4-438b-4097-92ba-0ce5cd90956f" />
<img width="1910" height="429" alt="image" src="https://github.com/user-attachments/assets/aaf80b12-d988-4f7d-ae0e-ca40128fa07b" />

Podemos observar que termino con exito 

<img width="1607" height="347" alt="image" src="https://github.com/user-attachments/assets/986c37f2-5731-49d0-8132-0f243bad662a" />

# Script de Detección de Prueba

<img width="1493" height="350" alt="image" src="https://github.com/user-attachments/assets/9966d4c9-c9ba-4898-90b6-a24e3ce87a1a" />

el script se ejecutará de principio a fin, leerá la foto y guardará el resultado en la carpeta `predict` dándole mucha más sensibilidad al modelo para pintar las cajas de detección

<img width="1382" height="422" alt="Captura de pantalla 2026-05-23 222203" src="https://github.com/user-attachments/assets/b438805a-d610-43e0-a465-d5135e7d01a7" />

se ve la foto limpia, significa que el modelo con el umbral actual pasó de largo sin dibujar la caja.

vamos a bajar el umbral de confianza a cero (conf=0.001). Esto forzará a YOLOv8 a pintar la caja en el lugar donde tenga así sea la más mínima sospecha de que ahí está el equipo.

<img width="387" height="249" alt="Captura de pantalla 2026-05-23 222552" src="https://github.com/user-attachments/assets/f229f137-1f7f-40b4-900b-88902085ae02" />










