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








