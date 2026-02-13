[![en](https://img.shields.io/badge/lang-en-red.svg)](https://github.com/stefaweb/rtsp-recorder-dev/tree/main)
[![fr](https://img.shields.io/badge/lang-fr-yellow.svg)](https://github.com/stefaweb/rtsp-recorder-dev/blob/main/README.fr.md)

# RTSP Recorder Script

The `recorder` script is designed for recording RTSP audio streams, especially from devices like the AXIS C8110 or P8221 audio recorder, and converting them into MP3 files. It also features functionalities for adjusting the trigger threshold, silencing removal, and sending email notifications.

## Prerequisites

Before starting, ensure you have installed the following dependencies on your system:

- VLC (`cvlc`)
- SoX
- ID3v2
- libsox-fmt-mp3

## Configuration

### Configuration File

The script operates using a `recorder.conf` configuration file, which should be placed in a specified folder (by default, in `/etc/recorder.conf`). This file allows you to customize the script's behavior according to your needs.

Here are the main parameters to configure:

- `LANG`: Choose "us", "de" or "fr" depending of the desired language.
- `PREFIX`: Prefix for naming the recorded files.
- `URL_SERVER`: The URL of the server where the sounds are stored.
- `RTSP_URL`: The RTSP stream URL.
- `RTSP_SAMPLE_RATE`: Sampling rate in Hz.
- `RTSP_BIT_RATE`: Amount of digital data transmitted per unit of time in kbits/s.
- `RTSP_USER, RTSP_PASSWORD`: Username and password for RTSP authentication.
- `DIR_WEB`: Path to the output directory for MP3 files.
- `DIR_LOG, DIR_PID, DIR_TEMPLATE`: Paths to the output directory for system files (PID, email_templates, logs).
- `EMAIL_FROM`, `EMAIL_TO`, `EMAIL_TO_SUPPORT`: Email addresses of the sender and recipient for notifications and error messages.
- `INPUT_THRESHOLD`: Parameter for adjusting the trigger threshold.
- `DURATION`: Recording duration (in seconds).
- `SILENT_SOUND_DURATION`: Allows you to define the minimum duration of the silent sound file to keep (in seconds).
- `KEEP_ORIGINAL`: Parameter to keep original sound file.
- `KEEP_PROCESSED_FILE`: Parameter to keep silenced sound file. Warning: this option may generate unreadable empty audio file if the original audio file contains only silence.
- `REMOVE_SILENCE` : Parameter to remove silences from sound file
- `SOX_CMD`: SoX command parameter to remove silences in MP3 files.
- `SOX_GAIN`: Gain applied by SoX during final MP3 conversion (Value in dB).

### Launching

To start a recording, execute the script in a terminal as follows:

```bash
./recorder
./recorder -f config-recorder.conf
```

## Usage

The `recorder` script is designed to be run as a cron job, allowing you to automatically capture audio at regular intervals. Here is an example of a cron job configuration with a 15-minute schedule:

```cron
*/15 * * * * /var/www/local/recorder -f /etc/recorder.conf
```

Set the variable `DURATION=900` in the specified configuration file in `/etc/recorder.conf` to align the script with 15 minutes.

This cron job executes the recorder script every 15 minutes, using the configuration specified in `/etc/recorder.conf`.

The sound cut between each recording is approximately 10 to 20 ms.


