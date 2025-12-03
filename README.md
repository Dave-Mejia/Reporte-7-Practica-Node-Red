# Reporte-7-Practica-Node-Red

En este ejercicio realizaremos la instalación del software note red para tener comunicación mediante la red con un ESP32 conectadro a un sensor ultrasónico HC-SR04 y un sensor de temperaura DHT22 los cuales nos permitiran adquirir valores de manera remota y así poderlos monitorear mediante graficos y control de datos
## Introducción
### Descripción
Utilizaremos l plataforma WOKWI para simular la adquisición de datos de distancia mediante un sensor ultrasónico HC-SR04, un sensor de temperaura DHT22 y la programación del mismo en un microcontrolador ESP32, los datos se mostrarán en una pantalla LCD, asimismo requerimos del software Node Red para la intercomunicacion.

### Material Necesario
Para realizar esta practica necesitas lo siguiente

a. Plataforma WOKWI

b. Sofware Node Red

c. Tarjeta ESP 32

d. Sensor ultrasónico HC-SR04

e. Sensor de temperaura DHT22

f. Pantalla LCD 16x2(I2C)

## Instrucciones

### Instalación Node Red
1. Abrir el ink https://nodejs.org/es y realizar la descarga del sofwtare.
![](https://github.com/Dave-Mejia/Reporte-7-Practica-Node-Red/blob/main/Node%20Red%201.png?raw=true)

![](https://github.com/Dave-Mejia/Reporte-7-Practica-Node-Red/blob/main/Node%20Red%202.png?raw=true)

2.- Una vez descargado, realizar la instalación
![](https://github.com/Dave-Mejia/Reporte-7-Practica-Node-Red/blob/main/Node%20Red%203.png?raw=true)

3. Después de instalar colocar cmd en el buscador de windows y ejecutar como administrador
![](https://github.com/Dave-Mejia/Reporte-7-Practica-Node-Red/blob/main/Node%20Red%204.png?raw=true)
![](https://github.com/Dave-Mejia/Reporte-7-Practica-Node-Red/blob/main/Node%20Red%205.png?raw=true)

5. Colocar el siguiente codigo
```npm install -g --unsafe-perm node-red``` y presionar ENTER
![](https://github.com/Dave-Mejia/Reporte-7-Practica-Node-Red/blob/main/Node%20Red%206.png?raw=true)

6. Una vez instalado colocar node-red y presionar ENTER y despues permitir.
![](https://github.com/Dave-Mejia/Reporte-7-Practica-Node-Red/blob/main/Node%20Red%207.png?raw=true)
![](https://github.com/Dave-Mejia/Reporte-7-Practica-Node-Red/blob/main/Node%20Red%208.png?raw=true)
![](https://github.com/Dave-Mejia/Reporte-7-Practica-Node-Red/blob/main/Node%20Red%209.png?raw=true)

8. Para abrir el servidor colocar la siguiente direccion IP y presionar ENTER.
```127.0.0.1:1880```
![](https://github.com/Dave-Mejia/Reporte-7-Practica-Node-Red/blob/main/Node%20Red%2010.png?raw=true)

### Preparación Node Red
1. Ir al adminstrador de paleta e instlar note red dashboard
![](https://github.com/Dave-Mejia/Reporte-7-Practica-Node-Red/blob/main/Node%20Red%2011.png?raw=true)
![](https://github.com/Dave-Mejia/Reporte-7-Practica-Node-Red/blob/main/Node%20Red%2012.png?raw=true)

### Instalación de Broker
1. Colocar Broker MQTT en buscador e instalar
![](https://github.com/Dave-Mejia/Reporte-7-Practica-Node-Red/blob/main/Broker1.png?raw=true)
![](https://github.com/Dave-Mejia/Reporte-7-Practica-Node-Red/blob/main/Broker%202.png?raw=true)
![](https://github.com/Dave-Mejia/Reporte-7-Practica-Node-Red/blob/main/Broker%203.png?raw=true)

2. Si no funciona, intentar con otro broker y seleccionar una IP.
![](https://github.com/Dave-Mejia/Reporte-7-Practica-Node-Red/blob/main/Broker%204%20OPC%20B.png?raw=true)

### Configuración de servidor
1. Colocar un bloque MQTT IN, dar clic sobre el y configurar de acuerdo a la siguiente imagen IMPORTANTE colocar la direccion IP ```3.121.19.141``` misma que se obtuvo anteriormente
![](https://github.com/Dave-Mejia/Reporte-7-Practica-Node-Red/blob/main/Configuracion%20MQTT%201.png?raw=true)
Dar clic en Update y configurar como se muestra abajo.
![](https://github.com/Dave-Mejia/Reporte-7-Practica-Node-Red/blob/main/Configuracion%20MQTT%202.png?raw=true)

2. Coloca un bloque JSON, dar clic sobre el y configurar comp se muestra en la imagen.
![](https://github.com/Dave-Mejia/Reporte-7-Practica-Node-Red/blob/main/Configuracion%20JSON%201.png?raw=true)

3. Colocar dos bloques function Y conectar.
![](https://github.com/Dave-Mejia/Reporte-7-Practica-Node-Red/blob/main/Configuracion%20Function%201.png?raw=true)

4. Configurar. colocando el siguiente codigo en cada bloque respectivamente:
```
msg.payload = msg.payload.TEMPERATURA;
msg.topic = "TEMPERATURA";
return msg;
```
```
msg.payload = msg.payload.HUMEDAD;
msg.topic = "HUMEDAD";
return msg;
```

![](https://github.com/Dave-Mejia/Reporte-7-Practica-Node-Red/blob/main/Configuracion%20Function%202.png?raw=true)

![](https://github.com/Dave-Mejia/Reporte-7-Practica-Node-Red/blob/main/Configuracion%20Function%203.png?raw=true)

5. Agregar los bloques chart y gauge y conectar como se muestra en la imagen.
![](https://github.com/Dave-Mejia/Reporte-7-Practica-Node-Red/blob/main/Chart%20&%20Gauge%201.png?raw=true)

### Configurar Dashboard
1. Abrir la seción de dashboard
![](https://github.com/Dave-Mejia/Reporte-7-Practica-Node-Red/blob/main/Dashboard%201.png?raw=true)

2. Agregrar tabs y configurar
![](https://github.com/Dave-Mejia/Reporte-7-Practica-Node-Red/blob/main/Dashboard%202.png?raw=true)
![](https://github.com/Dave-Mejia/Reporte-7-Practica-Node-Red/blob/main/Dashboard%203.png?raw=true)

3. Agregar grupo de grafica y de indicadores y configurar
![](https://github.com/Dave-Mejia/Reporte-7-Practica-Node-Red/blob/main/Dashboard%204.png?raw=true)
![](https://github.com/Dave-Mejia/Reporte-7-Practica-Node-Red/blob/main/Dashboard%205+.png?raw=true)
![](https://github.com/Dave-Mejia/Reporte-7-Practica-Node-Red/blob/main/Dashboard%206.png?raw=true)

### Configuracion de Chart & Gauge.
1. Configurar el bloque Chart de temperatura como indica la imagen.
![](https://github.com/Dave-Mejia/Reporte-7-Practica-Node-Red/blob/main/Chart%201.png?raw=true)

2. Configurar el bloque Gauge como muestra la siguiente imagen.
![](https://github.com/Dave-Mejia/Reporte-7-Practica-Node-Red/blob/main/Gauge%201.png?raw=true)

3. Realizar el mismo paso para Chart y Gauge de Humedad.

### Confirmación de conexión
1. Presionar Deploy y confirmar que MQTT In (en este caso DavidM) se conecte
![](https://github.com/Dave-Mejia/Reporte-7-Practica-Node-Red/blob/main/Conectado%201.png?raw=true)


### Configuración de ESP32
1. Abrir la plataforma WOKWI.

### Preparación
2. Ir a la pestaña de sketch.ino y borrar el codigo e programación predeterminado
3. Abrir la terminal de programación y colocar la siguente programación:

```
#include <ArduinoJson.h>
#include <WiFi.h>
#include <PubSubClient.h>
#define BUILTIN_LED 2
#include "DHTesp.h"
const int DHT_PIN = 15;
DHTesp dhtSensor;
// Update these with values suitable for your network.

const char* ssid = "Wokwi-GUEST";
const char* password = "";
const char* mqtt_server = "3.121.19.141";
String username_mqtt="Ing.DavidMejia";
String password_mqtt="12345678";

WiFiClient espClient;
PubSubClient client(espClient);
unsigned long lastMsg = 0;
#define MSG_BUFFER_SIZE  (50)
char msg[MSG_BUFFER_SIZE];
int value = 0;

void setup_wifi() {

  delay(10);
  // We start by connecting to a WiFi network
  Serial.println();
  Serial.print("Connecting to ");
  Serial.println(ssid);

  WiFi.mode(WIFI_STA);
  WiFi.begin(ssid, password);

  while (WiFi.status() != WL_CONNECTED) {
    delay(500);
    Serial.print(".");
  }

  randomSeed(micros());

  Serial.println("");
  Serial.println("WiFi connected");
  Serial.println("IP address: ");
  Serial.println(WiFi.localIP());
}

void callback(char* topic, byte* payload, unsigned int length) {
  Serial.print("Message arrived [");
  Serial.print(topic);
  Serial.print("] ");
  for (int i = 0; i < length; i++) {
    Serial.print((char)payload[i]);
  }
  Serial.println();

  // Switch on the LED if an 1 was received as first character
  if ((char)payload[0] == '1') {
    digitalWrite(BUILTIN_LED, LOW);   
    // Turn the LED on (Note that LOW is the voltage level
    // but actually the LED is on; this is because
    // it is active low on the ESP-01)
  } else {
    digitalWrite(BUILTIN_LED, HIGH);  
    // Turn the LED off by making the voltage HIGH
  }

}

void reconnect() {
  // Loop until we're reconnected
  while (!client.connected()) {
    Serial.print("Attempting MQTT connection...");
    // Create a random client ID
    String clientId = "ESP8266Client-";
    clientId += String(random(0xffff), HEX);
    // Attempt to connect
    if (client.connect(clientId.c_str(), username_mqtt.c_str() , password_mqtt.c_str())) {
      Serial.println("connected");
      // Once connected, publish an announcement...
      client.publish("outTopic", "hello world");
      // ... and resubscribe
      client.subscribe("inTopic");
    } else {
      Serial.print("failed, rc=");
      Serial.print(client.state());
      Serial.println(" try again in 5 seconds");
      // Wait 5 seconds before retrying
      delay(5000);
    }
  }
}

void setup() {
  pinMode(BUILTIN_LED, OUTPUT);     // Initialize the BUILTIN_LED pin as an output
  Serial.begin(115200);
  setup_wifi();
  client.setServer(mqtt_server, 1883);
  client.setCallback(callback);
  dhtSensor.setup(DHT_PIN, DHTesp::DHT22);
}

void loop() {


delay(1000);
TempAndHumidity  data = dhtSensor.getTempAndHumidity();
  if (!client.connected()) {
    reconnect();
  }
  client.loop();

  unsigned long now = millis();
  if (now - lastMsg > 2000) {
    lastMsg = now;
    //++value;
    //snprintf (msg, MSG_BUFFER_SIZE, "hello world #%ld", value);

    StaticJsonDocument<128> doc;

    doc["DEVICE"] = "Ing.DavidMejia";
    //doc["Anho"] = 2025;
    //doc["Empresa"] = "Dave";
    doc["TEMPERATURA"] = String(data.temperature, 1);
    doc["HUMEDAD"] = String(data.humidity, 1);
   

    String output;
    
    serializeJson(doc, output);

    Serial.print("Publish message: ");
    Serial.println(output);
    Serial.println(output.c_str());
    client.publish("DavidM", output.c_str());
  }
}
```
2. Confirmar que la IP configurada en el codigo (const char* mqtt_server =) sea a misma que en el MQTT IN de Node Red.
![](https://github.com/Dave-Mejia/Reporte-7-Practica-Node-Red/blob/main/Codigo%201.png?raw=true)

3. Confirmar que en la programación del Json se tenga el mismo nombre en client.publish que en el MQTT In.
![](https://github.com/Dave-Mejia/Reporte-7-Practica-Node-Red/blob/main/Codigo%202.png?raw=true)

5. Ir a la pestaña "Library manager" haer clic sobre el icon "+", buscar la libreria "HCSR04 ultrasonic sensor" y agregarla
![](https://github.com/Dave-Mejia/Reporte-4-ESP32-con-sensor-ultrasonico/blob/main/libreria%20sensor%20ultrasonico.png?raw=true)

6. Ir a la pestaña "Library manager" haer clic sobre el icon "+", buscar la libreria "DHT sensor library for ESPx" y agregarla
![](https://github.com/Dave-Mejia/Reporte-5-Sensor-ultrasonico-y-de-temperatura/blob/main/Libreria%20DHT.png?raw=true)

7. De igual manera agregar la librería "LiquidCrystal I2C" para la pantalla LCD
![](https://github.com/Dave-Mejia/Reporte-5-Sensor-ultrasonico-y-de-temperatura/blob/main/Libreria%20Pantalla%20LCD%20Liquid%20cristal.png?raw=true)
  
8. De igual manera agregar la librería "Arduinjson" para la conexion.
![](https://github.com/Dave-Mejia/Reporte-7-Practica-Node-Red/blob/main/Libreria%20arduino%20json.png?raw=true)

9. Ir al esquema de simulación, dar clic al icono "+ (add new part)"

![](https://github.com/Dave-Mejia/Reporte-5-Sensor-ultrasonico-y-de-temperatura/blob/main/Add%20new%20part.png?raw=true)

8. Buscar el sensor DHT22 y agregar
   
![](https://github.com/Dave-Mejia/Reporte-5-Sensor-ultrasonico-y-de-temperatura/blob/main/Add%20new%20part%202.png?raw=true)

9. Repetir el paso anterior buscar el sensor HCSR04 y agregar 
10. De igual forma buscar la pantalla LCD 16x2(I2C) y agregar
   
11. Conectar circuito como indica la figura de abajo
![](https://github.com/Dave-Mejia/Reporte-5-Sensor-ultrasonico-y-de-temperatura/blob/main/Conexion%20Tarjeta%20ESP32,%20Sensor%20DHT22,%20sensor%20HC-SR-04%20y%20pantalla%20LCD.png?raw=true)

### Operación
12. Iniciar simulador dando clic en el icono "start simulation"

![](https://github.com/Dave-Mejia/Reporte-5-Sensor-ultrasonico-y-de-temperatura/blob/main/play.png?raw=true)


13. Visualizar los datos en el monitor serial.

## Resultados
Cuando haya funcionado, verás los valores dentro del monitor serial como se muestra en la siguente imagen.
![](https://github.com/Dave-Mejia/Reporte-5-Sensor-ultrasonico-y-de-temperatura/blob/main/resultado%20sensor%20ultrasonico%20y%20temperatura%201.png?raw=true)
![](https://github.com/Dave-Mejia/Reporte-5-Sensor-ultrasonico-y-de-temperatura/blob/main/resultado%20sensor%20ultrasonico%20y%20temperatura%202.png?raw=true)
![](https://github.com/Dave-Mejia/Reporte-5-Sensor-ultrasonico-y-de-temperatura/blob/main/resultado%20sensor%20ultrasonico%20y%20temperatura%203.png?raw=true)
![](https://github.com/Dave-Mejia/Reporte-5-Sensor-ultrasonico-y-de-temperatura/blob/main/resultado%20sensor%20ultrasonico%20y%20temperatura%204.png?raw=true)

## Créditos
Ralizado por el Ingeniero David Mejía
