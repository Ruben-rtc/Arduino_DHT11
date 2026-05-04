# 2️⃣ Connecter et Alimenter le DHT11

## 📊 Composants Nécessaires

Pour ce projet de **station météo intelligente (Smart Plante)**, voici ce dont tu as besoin :

| Composant | Fonction |
|-----------|----------|
| **Arduino UNO** | Cerveau du système |
| **DHT11** | Capteur de température et humidité |
| **Breadboard** | Planche de connexion sans soudure |
| **Câbles de liaison** | Pour connecter les composants |
| **Résistance 10kΩ** | Optionnel, pour la stabilité |

---

## 🔧 Schéma du Composant DHT11

Avant de brancher, voici à quoi ressemble le capteur :

![Schéma du DHT11](Assets/Pasted%20image%2020260116102308.png)

*Source : [DHT11 Pin Configuration - Electronics Projects Hub](https://electronicsprojectshub.com/setup-dht11-sensor-with-arduino/screenshot-156/) (consulté le 16.01.2026)*

---

## 🔌 Branchement sur la Breadboard

Voici un exemple de configuration avec un Arduino UNO :

![Branchement DHT11 sur Breadboard](Assets/Pasted%20image%2020260116160241.png)

### Étapes de branchement :

1. **Alimenter la breadboard en énergie :**
   - Connecte le **pin 5V** de l'Arduino au rail **+** de la breadboard
   - Connecte le **pin GND** de l'Arduino au rail **-** de la breadboard

2. **Connecter le DHT11 :**
   - **VCC** → Rail + (5V)
   - **GND** → Rail - (GND)
   - **DATA** → **D2** de l'Arduino

### 📋 Table de Branchement :

| Broche DHT11 | Arduino UNO | Arduino MKR WiFi 1010 |
|--------------|-------------|----------------------|
| **VCC** | 5V | 3.3V |
| **GND** | GND | GND |
| **DATA** | D2 | D2 |

---

## ✅ Vérification

Avant de passer à l'étape suivante, vérifie :
- ✓ Tous les câbles sont bien connectés
- ✓ Pas de court-circuit
- ✓ Le DHT11 est correctement alimenté

**Prêt ?** Passons à la programmation !
