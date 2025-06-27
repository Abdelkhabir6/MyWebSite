
# Projet de Contrôle d'Automate Modbus avec Interface PyQt5

Ce projet consiste en la création d'une interface graphique pour contrôler des sorties d'un automate via le protocole Modbus. L'interface est développée en utilisant **PyQt5** pour l'interface utilisateur, et **pymodbus** pour la communication avec l'automate. L'application permet de connecter un automate Modbus, d'afficher l'état des sorties et de les contrôler.

## Fonctionnalités

- **Connexion Modbus** : Se connecte à un automate Modbus et permet de récupérer ou envoyer des données de/vers l'automate.
- **Interface Utilisateur** : Affiche un tableau de contrôle pour les sorties de l'automate avec des boutons permettant d'allumer ou d'éteindre les sorties.
- **Configuration Dynamique** : Le fichier XML de configuration est désormais chargé à partir d'un fichier de configuration JSON au lieu d'être en dur dans le code.
- **Suivi des Erreurs** : Un fichier log est utilisé pour suivre les événements et les erreurs du programme.

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
```

## Installation

### Prérequis
1. **Python 3.x**
2. **PyQt5**
   - Installer avec pip : 
   ```bash
   pip install pyqt5
   ```
3. **pymodbus**
   - Installer avec pip : 
   ```bash
   pip install pymodbus
   ```

### Étapes d'installation
1. Cloner ou télécharger le projet sur votre machine.
2. Installer les dépendances avec pip :
   ```bash
   pip install -r requirements.txt
   ```
3. Assurez-vous que le fichier XML `CFLogS_API.xml` est situé dans le même répertoire que l'exécutable ou spécifiez son emplacement dans le fichier `config.json`.

### Pour créer un fichier exécutable :
1. Utilisez **PyInstaller** pour générer un exécutable à partir du fichier Python :
   ```bash
   pyinstaller --onefile --windowed IHM_Modbus.py
   ```
   Cela générera un fichier `.exe` dans le dossier `dist`.

## Utilisation
1. Exécutez l'application :
   ```bash
   python IHM_Modbus.py
   ```
2. L'interface s'ouvrira et vous pourrez vous connecter à l'automate en cliquant sur le bouton "Connecter Modbus".
3. Vous pourrez ensuite interagir avec les sorties de l'automate via l'interface graphique.

### Composants Principaux
- **Modbus** : Utilisé pour lire et écrire les états des sorties.
- **PyQt5** : Utilisé pour l'interface graphique.
- **Logging** : Enregistre les événements de l'application dans un fichier `app.log`.

## Exemple de fichier `config.json`

Le fichier `config.json` doit être structuré comme suit :

```json
{
    "xml_file_path": "CFLogS_API.xml"
}
```

Le chemin du fichier XML est spécifié ici, ce qui permet de changer le fichier XML sans avoir à modifier le code.

## Aide et Dépannage
- **Erreur de connexion Modbus** : Vérifiez que l'automate est bien connecté au réseau et que l'adresse IP et le port sont corrects dans le fichier XML.
- **Problèmes d'affichage des sorties** : Assurez-vous que le fichier XML contient des informations valides pour les sorties et que le fichier est accessible par l'application.

## Conclusion

Ce projet permet de contrôler efficacement un automate Modbus via une interface simple et intuitive. Le système de logs fournit une trace complète des actions et des erreurs pour faciliter le dépannage et le suivi des événements.
