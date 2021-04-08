# Introducción

El objetivo de este proyecto es la creación de un nodo final usando una placa Heltec CubeCell HTCC-AB01 que sea capaz de enviar y recibir datos usando LoRaWAN con The Things Network. 

El caso de uso que se pretende es detectar la falta de humedad del suelo de un césped y poder actuar sobre una bomba para su riego.
 

# Fase 1 - Primeros Pasos 

## Instalar el editor de código [Visual Studio Code](https://code.visualstudio.com/).
Usaremos este programa como editor de código fuente desarrollado por Microsoft para Windows, Linux y macOS. 

## Instalar la extensión [PlatformIO](https://platformio.org/)
Necesitamos esta extensión  de visual Studio Code para poder crear y volcar programas para Arduino, Esp8266, Esp32 o CubeCell en este caso. 

## Crear un primer proyecto y volcar un primer programa.  

Esta placa se programa igual que un Arduino, así que la idea es hacer nuestro primer "hola mundo" con cualquiera de los ejemplos que hay en el github de [HelTecAutomation](https://github.com/HelTecAutomation/CubeCell-Arduino/tree/master/libraries).  

Crear el proyecto, compilarlo y enviarlo a la placa. 

![](capturas/cap_01.png?raw=true)

# Fase 2 - Cuenta en TTN 
Crear una cuenta, una aplicación, un dispositivo en The Things Network...

# Fase 3 - Software de envío y recepción de datos a TTN 
Programa para la CubeCell que envíe datos de un sensor cada cierto tiempo y active un relé desde TTN ...

# Fase 4 - Usar Integraciones gratuitas. 
Estudio y uso de integraciones como Ubidots o TagoIO para poder almacenar y visualizar los datos del sensor y también activar/desactivar el relé ... 
