# PROJET_IPS
   PROJET IPS - Mesure de déformation par jauges - Dispositif de commande haptique.

📋 Description du Projet:
Ce projet développe un instrument de mesure intelligent qui convertit les forces appliquées sur une lame instrumentée en indication visuelle via un servomoteur. Le système propose deux modes de fonctionnement distincts : un mode automatique où le servomoteur reflète la force mesurée, et un mode manuel où l'utilisateur contrôle directement la position du servomoteur.

🎯 Objectifs:
- Concevoir le système de mesure, y compris une interface permettant de visualiser les données et les traiter.
- Etudier l’influence de la masse sur la déformation des jauges.
- Etudier l’influence de la position de la masse sur la déformation des jauges.
- Réaliser un prototype sur plaque LAB ou protoboard.
- Réaliser les logiciels du microcontrôleur d’une part, de l’IHM d’autre part.
- Router et réaliser un système de mesure sur circuit imprimé ( carte électronique avec des connecteurs adaptés pour une utilisation facile).
- Contrôler la position du servomoteur en fonction de l’effort exercé sur la lame.
- Utiliser votre IHM comme balance.
- Dépouiller, analyser, exploiter et critiquer les résultats
- Comparer les montages avec 1, 2 ou 4 jauges.


🌐 Démonstration en Ligne:
- Site Web du Projet : https://ips-groupe-c-deformation-jauge.netlify.app/


 Fonctionnalités Principales:
  Mesure et Acquisition:
- Acquisition ADC 12 bits avec moyennage sur 16 échantillons
- Filtrage numérique pour réduction du bruit électronique
- Calibration automatique (facteur de conversion : 188.68)
- Plage de mesure : 0-600g (0-5.9N)

🎮 Modes de Fonctionnement
- Mode Manuel : Contrôle direct de l'angle du servomoteur.
- Mode Automatique : Position proportionnelle à la force mesurée.

📡 Communication: 
- Protocol UART : 115200 bauds, format structuré
- Données temps réel : Tension, masse, force, angle
- Commandes bidirectionnelles avec accusé de réception
- Buffer circulaire pour réception asynchrone

 Configuration
Servomoteur MG90S : Plage 0-180° (PWM 1000-6500)
Réponse linéaire : Force → Angle de rotation
Fréquence PWM : 50Hz (standard servomoteur)

🏗️ Architecture Technique:
- Capteur Force → Tension Analogique → ADC STM32 → Valeur Numérique → Masse → Force → Angle → PWM
-   (physique)  →    (0-3.3V)   →      (12 bits) →   (0-4095)  →     (g) →  (N)  → (0-180°) → (1000-6500)

 Matériel Requis:
- Microcontrôleur : STM32 (série F411)
- Capteur : Jauge de contrainte 
- Servomoteur : MG90S 
- Interface : UART (USB/série)
- Alimentation : 5V pour servo, 3.3V pour STM32

 Périphériques Utilisés:
- ADC1 : Canal 0 (PA0) - Acquisition capteur
- TIM2 : Canal 2 (PA1) - Génération PWM
- UART2 : (PA2/PA3) - Communication série
- GPIO : PA5 - LED de statut

 Installation et Utilisation:
 Prérequis:
- STM32CubeIDE
- HAL Library STM32F4
  
Ouvrir dans STM32CubeIDE:
- Importer le projet existant
- Vérifier la configuration des pins
- Compiler le projet

Programmation:
- Connecter le STM32 via ST-Link
- Programmer le firmware
- Vérifier les connexions matérielles


Format des commandes UART :
    "Mode,Angle,e"
- 1,90,e : Mode manuel, angle 90°
 2,0,e : Mode automatique

Format des données reçues :
- V:2.456    // Tension en Volts
- M:125      // Masse en grammes  
- F:1.226    // Force en Newtons
- A:45       // Angle servomoteur

Réferences:
- Jauge de contrainte : https://web.enib.fr/~bourgeot/IPS/Datasheets/AN078-Strain_Gauge_Measurement-A_Tutorial.pdf
- Servomoteur : https://www.alldatasheet.fr/datasheet-pdf/pdf/1132104/ETC2/MG90S.html

👨‍💻 Notre équipe:
- Développeur embarqué, câblage et responsable de l'intégration système :  SOUFIANE EL MAMSAOUI
- Créateur du site web portfolio et de l'interface de visualisation 3D : AYOUB MACHKOUR
- Conception de circuits et réalisation de cartes électroniques : Antoine VERMANDER
- Conception électronique et validation des circuits : Benjamin HEYSCH

Encadrant : 
 - Mr.Jean-Matthieu BOURGEOT

Institution :
-  ENIB
