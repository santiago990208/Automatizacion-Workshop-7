# Automatizacion Workshop 7
Santiago Botero -  Nicolas Imbachi
 - [Sensor](#sensor)
 - [Sistema Embebido](#sistema-embebido)
   - [Hardware](#hardware)
   - [Software](#software)
 - [Conectividad](#conectividad)
   - [Conectividad física](#conectividad-física)
   - [Protocolo de comunicación](#protocolo-de-comunicación)
   - [Protocolo de aplicación](#protocolo-de-aplicación)
 - [Analitica de datos](#analitica-de-datos)

## Sensor

Sensor digital de presión atmosferica, humedad y temperatura BME280. Este sensor provee interfaces de conexión SPI y I2C, cada una con un maximo de frecuencia de 3.4 MHz y 10 MHz respectivamente. Este sensor tiene un rango de operación para las tres funcionalidades:

El BME 280 es un sensor digital de humedad, presion atmosferica y tempertura, cuenta con una interfaz digital de conexion I2C y SPI.
Los rangos de comportamiento y parametros para cada modulo son:

Hhumedad:
- Humedad relativa: 0 - 100%.
- Tiempo de respuesta: 1s.
- Tolerancia de exactitud: ±3% humedad relativa.

Temperatura:
- Temperatura: -40 - +85°C.
- Exactitud de temperatura absoluta (0-65°C): ±1°C

Presión:
- Presión atmosferica: 300 - 1100 hPa.
- Exactitud absoluta (0-65°C): ±1.0hPa.
- Exactitud relativa: ±0.12hPa.

En nuestro caso se utiliza la interfaz I2C por medio de los pines GPIO2 y GPIO3 de la placa Raspberry. 

Referencia: [BME280 Datasheet](https://pdf1.alldatasheet.com/datasheet-pdf/view/1132060/BOSCH/BME280.html) 

## Sistema Embebido

Se usa la Raspberry Pi 3 Modelo B, está placa contiene las siguientes espcificaciones:

### Hardware

- CPU de 64 bits Broadcom BCM2837 de cuatro núcleos a 1,2 GHz
- 1GB RAM
- LAN inalámbrica BCM43438 y Bluetooth Low Energy (BLE) a bordo
- Ethernet 100 base
- GPIO extendido de 40 pines
- 4 puertos USB 2
- Salida estéreo de 4 polos y puerto de video compuesto
- HDMI de tamaño completo
- Puerto de cámara CSI para conectar una cámara Raspberry Pi
- Puerto de pantalla DSI para conectar una pantalla táctil Raspberry Pi
- Puerto Micro SD para cargar su sistema operativo y almacenar datos
- Fuente de alimentación Micro USB conmutada actualizada hasta 2.5A


Referencia: [Raspberry Pi 3 Model B](https://www.raspberrypi.com/products/raspberry-pi-3-model-b/)

### Software

- OS Raspberry Pi OS.
- Ejecución Node.js.
- Cliente JavaScript.
- Libreria MQTT.
- Libreria IoT Azure.
- Libreria BME280.
- Libreria Raspberry Pi.

Referencia: [Raspberry Pi Web Simulator](https://azure-samples.github.io/raspberry-pi-web-simulator/)

## Conectividad

### Conectividad física
El protocolo de capa 1 o conectividad fisica I2C.

I2C funciona mediante una arquitectura de bus, donde se conectan mediante dos hilos los circuitos integrados, este protocolo se debe usar ya que la Rasberry Pi cuenta con dos perifericos para s implementacion.

Referencia: [Protocolo I2C](https://hetpro-store.com/TUTORIALES/i2c/#:~:text=I2C%20es%20un%20puerto%20y,de%20comunicaci%C3%B3n%2C%20SDA%20y%20SCL.) 

### Protocolo de comunicación
La comunicacion se realiza por medio del protocolo MQTT el cual eusa Azure por defecto. Este protocolo de comunicacion es maquina-a-maquina, con un mensaje de tipo cola. 

La arquitectura es cliente servidor (publicadores suscriotores), estos intercambian datos con un servidor centralizado (Azure, IoT Hub)

Referencia: [MQTT Azure](https://docs.microsoft.com/es-es/azure/iot-hub/iot-hub-mqtt-support)

## Analitica de datos
Para la solución implementamos el centro de IoT brindado por Azure, el cual no solo nos permite recibir la data en tiempo real, sino que también muestra una serie de gráficos con los cuales se puede realizar la analítica de la aplicación que se está implementando

