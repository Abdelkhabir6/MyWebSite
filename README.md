# Projet de Contrôle d'Automate Modbus avec Interface PyQt5

Ce projet consiste en la création d'une interface graphique pour contrôler des sorties d'un automate via le protocole Modbus. L'interface est développée en utilisant **PyQt5** pour l'interface utilisateur, et **pymodbus** pour la communication avec l'automate. L'application permet de connecter un automate Modbus, d'afficher l'état des sorties et de les contrôler.

## Fonctionnalités
- Connexion à un automate Modbus.
- Affichage de l'état des sorties dans une interface graphique (écran de contrôle avec des boutons pour chaque sortie).
- Gestion des sorties via des boutons pour allumer ou éteindre chaque sortie.
- Suivi des erreurs et des événements dans un fichier log (log des actions effectuées et des erreurs survenues).

## Structure du Projet

### 1. Interface Utilisateur
L'interface est construite avec **PyQt5** et comprend :
- Un titre pour l'application.
- Un statut de connexion pour afficher si l'application est connectée à l'automate.
- Une grille de sorties représentant l'état de chaque sortie.
- Des boutons de contrôle pour interagir avec les sorties.

### 2. Modbus
La communication avec l'automate se fait via **Modbus TCP** :
- **Lire** les états des sorties.
- **Écrire** les états des sorties.
- **Mettre à jour** l'état des sorties sur l'interface.

### 3. Logging
Le projet utilise un système de **log** pour suivre l'exécution et les erreurs. Les événements sont enregistrés dans un fichier `app.log`.

### 4. Chargement Dynamique du Fichier XML de Configuration
Le fichier XML de configuration des sorties n'est plus codé en dur. Un fichier de configuration JSON est utilisé pour spécifier le chemin du fichier XML, permettant de le modifier sans toucher au code.

### 5. Fichier JSON de Configuration
Le fichier `config.json` permet de définir l'emplacement du fichier XML à utiliser, avec la structure suivante :

```json
{
    "xml_file_path": "CFLogS_API.xml"
}
Installation
Prérequis
Python 3.x

PyQt5

Installer avec pip : pip install pyqt5

pymodbus

Installer avec pip : pip install pymodbus

Étapes d'installation
Cloner ou télécharger le projet sur votre machine.

Installer les dépendances avec pip :

bash
Copier
pip install -r requirements.txt
Assurez-vous que le fichier XML CFLogS_API.xml est situé dans le même répertoire que l'exécutable ou spécifiez son emplacement dans le fichier config.json.

Pour créer un fichier exécutable :
Utilisez PyInstaller pour générer un exécutable à partir du fichier Python :

bash
Copier
pyinstaller --onefile --windowed IHM_Modbus.py
Cela générera un fichier .exe dans le dossier dist.

Utilisation
Exécutez l'application :

bash
Copier
python IHM_Modbus.py
L'interface s'ouvrira et vous pourrez vous connecter à l'automate en cliquant sur le bouton "Connecter Modbus".

Vous pourrez ensuite interagir avec les sorties de l'automate via l'interface graphique.

Composants Principaux
Modbus : Utilisé pour lire et écrire les états des sorties.

PyQt5 : Utilisé pour l'interface graphique.

Logging : Enregistre les événements de l'application dans un fichier app.log.

Exemple de fichier config.json
Le fichier config.json doit être structuré comme suit :

json
Copier
{
    "xml_file_path": "CFLogS_API.xml"
}
Le chemin du fichier XML est spécifié ici, ce qui permet de changer le fichier XML sans avoir à modifier le code.

Aide et Dépannage
Erreur de connexion Modbus : Vérifiez que l'automate est bien connecté au réseau et que l'adresse IP et le port sont corrects dans le fichier XML.

Problèmes d'affichage des sorties : Assurez-vous que le fichier XML contient des informations valides pour les sorties et que le fichier est accessible par l'application.

Conclusion
Ce projet permet de contrôler efficacement un automate Modbus via une interface simple et intuitive. Le système de logs fournit une trace complète des actions et des erreurs pour faciliter le dépannage et le suivi des événements.
