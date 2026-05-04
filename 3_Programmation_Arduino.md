# 3️⃣ Configuration Arduino IDE & Programmation

## 3.1 Installer la Carte Arduino UNO

Dans Arduino IDE, la première étape consiste à installer la carte **Arduino UNO**. Cela permet au logiciel de la reconnaître correctement et de pouvoir compiler puis téléverser du code dessus par la suite.

![Installation Arduino UNO](Assets/Pasted%20image%2020260504152346.png)

---

## 3.2 Installer une Librairie du Composant DHT11

Installer les librairies permet à Arduino IDE de compiler correctement le code C++ et de communiquer avec les différents composants. Chaque librairie fournit des fonctions déjà prêtes à l'emploi, ce qui évite d'avoir à tout programmer depuis zéro et facilite la récupération et la lecture des données des capteurs.

### 3.2.1 DHT11 (Capteur de Température et Humidité)

Pour le composant DHT11, nous avons choisi d'installer la **librairie de Dhruba Saha** :

![Librairie DHT11](Assets/Pasted%20image%2020260116091738.png)

---

## 3.3 Charger un Exemple de Code

Pour trouver un exemple de code afin de lire les données du DHT11, nous allons utiliser un exemple prêt à l'emploi.

### Étapes :

1. Appuie sur les **3 petits points** (more actions)
2. Puis dans **Example** choisis **ReadTempAndHumidity**

![Menu Examples Arduino IDE](Assets/Pasted%20image%2020260504152906.png)

Cela ouvre un fichier `.ino` dans Arduino IDE. Voici le code C/C++ (utilisé en électronique embarquée) :

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

### 🔍 Explication du Code :

La ligne clé est :

```cpp
DHT11 dht11(2);
```

Cela dit à Arduino de lire les données sur le **pin digital 2** (D2), ce que nous avons déjà configuré dans le branchement matériel.

![Vérification du branchement](Assets/Pasted%20image%2020260116160241.png)

---

## 3.4 Tester le Capteur

Maintenant que tout est mis en place, nous pouvons faire un test pour vérifier si on peut lire les informations du DHT11.

### 📤 Upload du Code

Il faut **upload** le code pour le compiler et l'envoyer sur l'Arduino :

![Bouton Upload](Assets/Pasted%20image%2020260116095942.png)

### 📊 Afficher le Serial Monitor

Pour voir les résultats affichés en temps réel, affiche le **Serial Monitor** :

![Menu Serial Monitor](Assets/Pasted%20image%2020260116110944.png)

### ✅ Résultat Final

Si tout fonctionne bien, tu devrais voir des données apparaître dans le Serial Monitor :

![Données du DHT11 en temps réel](Assets/Pasted%20image%2020260116111136.png)

**Bonne nouvelle, le DHT11 marche parfaitement !** 🎉

Tu vois maintenant la température et l'humidité en temps réel. Ces données peuvent maintenant être utilisées pour :
- 📱 Afficher sur un écran LCD/TFT
- ☁️ Envoyer vers le cloud (IoT)
- 🤖 Déclencher des actions automatiques

---

## 🎓 Prochaines Étapes

Félicitations ! Tu as réussi à :
✅ Installer Arduino IDE  
✅ Brancher le DHT11  
✅ Programmer et tester le capteur  

**Tu es maintenant prêt pour des projets plus avancés !**
