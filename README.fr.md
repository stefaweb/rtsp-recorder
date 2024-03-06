# RTSP Recorder script

Le script `recorder` permet d'enregistrer des flux audio RTSP, notamment depuis des dispositifs comme l'enregistreur audio AXIS C8110, et de les convertir en fichiers MP3. Il inclut également des fonctionnalités d'ajustement du seuil de déclenchement (threshold), de suppression des silences, et d'envoi de notifications par email.

## Prérequis

Avant de commencer, assurez-vous d'avoir installé les dépendances suivantes sur votre système :

- VLC (`cvlc`)
- Sox
- ID3v2
- libsox-fmt-mp3

## Configuration

### Fichier de Configuration

Le script fonctionne en utilisant un fichier de configuration `recorder.conf` qui doit être placé dans un dossier spécifié (par défaut, dans `/etc/recorder.conf`). Ce fichier permet de personnaliser le comportement du script selon vos besoins.

Voici les principaux paramètres à configurer :

- `LANG` : Choisir "us" ou "fr" en fonction de la langue désirée.
- `PREFIX` : préfixe pour le nommage des fichiers enregistrés.
- `URL_SERVER` : l'URL du serveur ou sont stocké les sons.
- `RTSP_URL` : l'URL du flux RTSP.
- `RTSP_SAMPLE_RATE` : fréquence d'échantillonnage (sampling rate) en Hz.
- `RTSP_BITE_RATE` : quantité de données numériques transmises par unité de temps en kbits/s.
- `RTSP_USER, RTSP_PASSWORD` : nom et mot de passe pour l'authentification RTSP.
- `DIR_WEB`: chemin du répertoire de sortie pour les fichiers MP3.
- `DIR_LOG, DIR_PID, DIR_TEMPLATE` : chemin du répertoire de sortie pour les fichiers systèmes (PID, email_templates, logs).
- `EMAIL_FROM`, `EMAIL_TO`, `EMAIL_TO_SUPPORT` : adresses email de l'expéditeur et du destinataire pour les notifications et les messages d'erreur.
- `INPUT_THRESHOLD` : paramètre pour l'ajustement du seuil de déclenchement (threshold).
- `DURATION` : durée de l'enregistrement (en secondes).
- `SILENT_SOUND_DURATION` : permet de définir la durée minimum du fichier son silencieux à conserver (en seconde).
- `DELETE_ORIGINAL` : paramètre pour supprimer le fichier sonore original.
- `REMOVE_SILENCE` : paramètre pour supprimer les silences.
- `SOX_CMD` : paramètre de la commande sox pour supprimer les silences dans les fichiers MP3.

### Lancement

Pour démarrer un enregistrement, exécutez le script dans un terminal comme suit :

```bash
./recorder
./recorder -f config-recorder.conf
```

## Utilisation

Le script `recorder` est conçu pour être exécuté en tant que tâche cron, vous permettant de capturer automatiquement l'audio à intervalles réguliers. Voici un exemple de configuration d'une tâche cron avec un cadencement de 15 minutes :

```cron
*/15 * * * * /var/www/local/recorder -f /etc/recorder.conf
```

Mettre la variable `DURATION=900` dans le fichier de configuration spécifiée dans `/etc/recorder.conf` pour caller le script sur 15 minutes.

Cette tâche cron exécute le script recorder toutes les 15 minutes, en utilisant la configuration spécifiée dans `/etc/recorder.conf`.

La coupure sonore entre chaque enregistrement est d'environ 10 à 20 ms.

