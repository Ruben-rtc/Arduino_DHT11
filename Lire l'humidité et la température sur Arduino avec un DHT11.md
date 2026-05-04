# 1 Installer le Logiciel Arduino IDE

Installer le logiciel Arduino : [arduino.cc/en/software/](https://www.arduino.cc/en/software/)

![](Assets/Pasted%20image%2020260116092019.png)

# 2 Brancher le DHT11 sur le breadboard

Les capteurs dont nous avons besoin pour notre projet de Smart Plante sont les suivants : 


|Composant|Fonction|
|---|---|
|ILI9341 TFT breakout|Afficher des données sur un écran|

Pour la création des schémas des capteur, j'ai utilisé **Circuit Canvas** https://circuitcanvas.com/ et le logiciel **KiCad** https://www.kicad.org/ (plus professionnel).

---

## 2.1 Le DHT11

Schéma du composant : 
![](Assets/Pasted%20image%2020260116102308.png)

image trouvé sur : [DHT11 Pin Configuration - Electronics Projects Hub](https://electronicsprojectshub.com/setup-dht11-sensor-with-arduino/screenshot-156/) (consulté le 16.01.2026)

Voici un exemple de comment configurer les cables pour le DHT11 sur une breadboard avec un Arduino Uno :

![](Assets/Pasted%20image%2020260116160241.png)

1. Alimenter le breadboard en énergie
- sur la bande horizontale + du breadboard connecter un pin avec l'entrée 5V sur l'Arduino UNO
- sur la bande horizontale - du breadboard connecter un pin avec l'entrée GND (ground) sur l'arduino UNO
- Connecter le pin Data sur l'entrée D2 de l'Arduino

**Branchement :**

|DHT11 Pin|Arduino UNO|Arduino MKR WiFi 1010|
|---|---|---|
|VCC|5V|3.3V|
|GND|GND|GND|
|DATA|D2|D2|

---

# 3 Sur Arduino IDE

## 3.1 Installer le board Arduino

Dans l’Arduino IDE, la première étape consiste à installer la carte **Arduino UNO**. Cela permet au logiciel de la reconnaître correctement et de pouvoir compiler puis téléverser du code dessus par la suite.

![](Assets/Pasted%20image%2020260504152346.png)


## 3.2 installer une librairie du composant DHT11 
Installer les librairies permet à l’Arduino IDE de compiler correctement le code C++ et de communiquer avec les différents composants. Chaque librairie fournit des fonctions déjà prêtes à l’emploi, ce qui évite d’avoir à tout programmer depuis zéro et facilite la récupération et la lecture des données des capteurs.

### 3.2.1 DHT11 (capteur de température et humidité)
Pour le composant DHT11 on a choisi d'installer la librairie de Dhruba Saha
![](Assets/Pasted%20image%2020260116091738.png)

Pour trouver un exemple de code afin de lire les données du DHT11, on va prendre un exemple de code pour lire la température et l'humidité. 

Pour ce faire il faut appuyer sur les 3 petits points (more actions), puis dans **example** choisir **ReadTempAndHumidity**

![](Assets/Pasted%20image%2020260504152906.png)

Cela ouvre un fichier .ino dans le logiciel Arduino IDE et on voit ce code C/C++ (utilisé en électronique embarquée)

```cpp
// Include the DHT11 library for interfacing with the sensor.
#include <DHT11.h>  
// Create an instance of the DHT11 class.
// - For Arduino: Connect the sensor to Digital I/O Pin 2.
// - For ESP32: Connect the sensor to pin GPIO2 or P2.
// - For ESP8266: Connect the sensor to GPIO2 or D4.
DHT11 dht11(2);
void setup() {
    // Initialize serial communication to allow debugging and data readout.
    // Using a baud rate of 9600 bps.
    Serial.begin(9600);
    // Uncomment the line below to set a custom delay between sensor readings (in milliseconds).
    // dht11.setDelay(500); // Set this to the desired delay. Default is 500ms.
}
void loop() {
    int temperature = 0;
    int humidity = 0;
    // Attempt to read the temperature and humidity values from the DHT11 sensor.
    int result = dht11.readTemperatureHumidity(temperature, humidity);
    // Check the results of the readings.
    // If the reading is successful, print the temperature and humidity values.
    // If there are errors, print the appropriate error messages
    if (result == 0) {
        Serial.print("Temperature: ");
        Serial.print(temperature);
        Serial.print(" °C\tHumidity: ");
        Serial.print(humidity);
        Serial.println(" %");
    } else {
        // Print error message based on the error code.
        Serial.println(DHT11::getErrorString(result));
    }
}
```

Dans cet exemple on peut voir que l'Arduino lit les information sur le 2e pin dans digital, nous avons déjà connecté le pin d'information sur la 2e entrée de data sur Arduino.

```cpp
DHT11 dht11(2);
```

![](Assets/Pasted%20image%2020260116160241.png)

Maintenant que tout est mis en place on peut faire un test pour voir sur on peut lire les information du DHT11 avec le logiciel Arduino IDE. 


Pour ce faire, il faut **upload** le code pour le compiler : 

![](Assets/Pasted%20image%2020260116095942.png)

Ensuite, pour voir les résultats affichés. Il faut afficher le **Serial Monitor** : 

![](Assets/Pasted%20image%2020260116110944.png)

Dans le Serial Monitor on observe que les données renvoyées concernent les valeurs de température et d'humidité. Bonne nouvelle, le DHT11 marche bien !

![](Assets/Pasted%20image%2020260116111136.png)