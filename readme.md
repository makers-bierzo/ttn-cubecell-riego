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

![](capturas/f1_01.png?raw=true)

![](capturas/f1_02.png?raw=true)

# Fase 2 - Cuenta en TTN 

1. Crear una cuenta en [The Things Network.](https://www.thethingsnetwork.org/)

2. Crear una aplicación. Pulsar sobre **add application** y poner un nombre al Application ID.

![](capturas/f1_03.png?raw=true)

3. Crear un dispositivo dentro de la aplicación. Pulsar sobre **register device** y poner un nombre al Device ID.

![](capturas/f1_04.png?raw=true)

4. Primeras pruebas. Heltec nos suministra mucha documentación y ejemplos con [LoRaWAN](https://github.com/HelTecAutomation/CubeCell-Arduino/tree/master/libraries/LoRa/examples/LoRaWAN)

    - Copiamos el código del ejemplo [LoRaWan_downlinkdatahandle](https://github.com/HelTecAutomation/CubeCell-Arduino/blob/master/libraries/LoRa/examples/LoRaWAN/LoRaWan_downlinkdatahandle/LoRaWan_downlinkdatahandle.ino)

    - Ponemos en él los datos de nuestro dispositivo OTAA creado. Estos valores ( devEui[], appEui[], appKey[] ) se encuentran en nuestra consola de TTN. 

    ```c
    /* OTAA para*/
    uint8_t devEui[] = { 0x22, 0x32, 0x33, 0x00, 0x00, 0x88, 0x88, 0x02 };
    uint8_t appEui[] = { 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00, 0x00 };
    uint8_t appKey[] = { 0x88, 0x88, 0x88, 0x88, 0x88, 0x88, 0x88, 0x88, 0x88, 0x88, 0x88, 0x88, 0x88, 0x88, 0x66, 0x01 };
    ```
    
    - Modificamos el archivo platformio.ini para poner nuestras preferencias de compilación añadiendo las siguientes líneas.

    ```c
    monitor_speed = 115200
    board_build.arduino.lorawan.region = EU868
    board_build.arduino.lorawan.class = CLASS_A
    board_build.arduino.lorawan.netmode = OTAA
    board_build.arduino.lorawan.adr = ON
    board_build.arduino.lorawan.debug_level = FREQ_AND_DIO
    board_build.arduino.lorawan.at_support = OFF
    board_build.arduino.lorawan.net_reserve = OFF
    board_build.arduino.lorawan.rgb = ACTIVE
    board_build.arduino.lorawan.uplinkmode = UNCONFIRMED
     ```
    - Compilamos y lo volcamos en la CubeCell.

    ![](capturas/f2_01.png?raw=true)

    - Veremos los datos enviados desde la CubeCell en consola de TTN.

    ![](capturas/f2_02.png?raw=true)

    - También podremos recibir datos en la CubeCell enviados desde la consola de TTN.

    ![](capturas/f2_03.png?raw=true)

    - Todo este tráfico se verá reflejado en el puerto serie.

    ![](capturas/f2_04.png?raw=true)


# Fase 3 - Software de envío y recepción de datos a TTN 
Programa para la CubeCell que envíe datos de un sensor cada cierto tiempo y active un relé desde TTN ...

# Fase 4 - Usar Integraciones gratuitas. 
Estudio y uso de integraciones como Ubidots o TagoIO para poder almacenar y visualizar los datos del sensor y también activar/desactivar el relé ... 
