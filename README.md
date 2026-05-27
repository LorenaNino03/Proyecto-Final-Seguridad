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


## Módulo 2 – Cifrado de la Información (Criptografía)
**Norma aplicada:** ISO 27001:2022 - Control A.10 (Cryptography)

**Concepto:** Se simula el envío seguro de una imagen capturada en campo 
(zona no segura) hacia un servidor central de auditoría. Si la imagen es 
interceptada, no puede ser leída.

### Paso 1 – Hash SHA-256 (Integridad)
Se calcula el hash de la imagen original antes de enviarla.
Si alguien la altera en tránsito, el hash no coincidirá al verificar.

<img width="1087" height="245" alt="image" src="https://github.com/user-attachments/assets/476c5d45-1b59-4e30-8c4d-b5e4d97865f1" />


### Paso 2 – Cifrado AES-256 (Confidencialidad)
Se genera una clave aleatoria de 256 bits y se cifra la imagen completa.
Sin la clave, la imagen es ilegible.

<img width="990" height="139" alt="image" src="https://github.com/user-attachments/assets/235d1bf7-fd2f-468f-8afe-71c0a7df21b4" />


### Paso 3 – Cifrado híbrido RSA + AES (Intercambio seguro de clave)
La clave AES se cifra con RSA-2048. Solo quien tenga la clave privada 
puede recuperarla.

<img width="1124" height="372" alt="image" src="https://github.com/user-attachments/assets/64637486-23a2-4746-b02b-7763bbb0b0a6" />


### Resultado en el servidor
- Clave AES recuperada: ✅ SÍ  
- Imagen descifrada correctamente: ✅ SÍ  
- Integridad verificada (SHA-256 coincide): ✅ SÍ

<img width="1118" height="506" alt="image" src="https://github.com/user-attachments/assets/a65ea294-39d5-462e-83f3-c8f3f8f8e482" />

## Módulo 3: Auditoría y Normativa ISO 27001

# Pregunta 1.¿El modelo YOLO logró listar todos los routers y switches ¿Ayuda a mantener un inventario actualizado?

Respuesta: El modelo YOLOv8 entrenado detecta visualmente dispositivos de red (routers, switches, firewalls, servidores, hubs) y genera un registro con marca de tiempo. Esto contribuye a mantener un inventario visual actualizado de activos físicos. Sin embargo, el inventario es visual y no reemplaza un CMDB (base de datos de gestión de configuración) completo.
Tema ISO 27001: Organizacional

# Pregunta 2: (Uso aceptable de activos) ¿El software de detección solo se usa para inventario?

Respuesta:Sí, cumplido. El sistema desarrollado tiene un único propósito definido: detectar y registrar visualmente activos de telecomunicaciones para fines de inventario y auditoría. No se utiliza para vigilancia de personas ni para ningún otro fin fuera del alcance del proyecto.
Tema ISO 27001: Organizacional

# Pregunta 3: (Transferencia de información) ¿Se aplicó el cifrado (Módulo 2 al enviar los datos?

Respuesta: Sí, cumplido.
El Módulo 2 implementa cifrado híbrido (AES-256 + RSA-2048) para proteger la imagen y sus metadatos durante la transmisión. Adicionalmente se calcula el hash SHA-256 para verificar integridad. Cualquier imagen interceptada en tránsito resulta ilegible sin la clave privada RSA.

# Pregunta 4: (Etiquetado de activos) ¿Las fotos sirven como etiqueta visual del equipo?

Respuesta: Las imágenes capturadas con las cajas de detección de YOLO (bounding boxes) y sus metadatos (tipo de dispositivo, coordenadas, hora) funcionan como etiqueta visual del activo. No reemplazan etiquetas físicas (código QR, número de serie), pero complementan el inventario con evidencia fotográfica fechada.

# Pregunta 5: (Protección contra malware) ¿El ordenador donde corre YOLO tiene antivirus?

Respuesta:Sí, cumplido.
El equipo donde se ejecuta el sistema cuenta con Windows Defender activo (antivirus nativo de Windows 11), lo cual proporciona protección base contra malware. Se recomienda complementar con análisis periódicos y mantener el sistema operativo actualizado.
