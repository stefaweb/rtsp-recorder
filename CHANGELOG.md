# Changelog recorder script

Version [3.1.1] (5-03-2024)

- Add sound file duration in email template.
- Update of musicindex.css.
- Directory email_templates has been renamed to recorder_templates.
- Localization in English and French for Email Subject and Body templates.
- Added LANG parameter in recorder.conf.
- Added Content-Type to mail header.
- Localization in English of log_message and internal messages.
- Localization of minutes and seconds in body message.
- Added SILENT_SOUND_DURATION parameter in recorder.conf. It permit to delete silent sound file if SOUND_LENGTH is smaller or equal than SILENT_SOUND_DURATION.

Version [3.1.0] (2-03-2024)

- Added SOX_CMD parameter in recorder.conf.
- Added EMAIL_TO_SUPPORT parameter. Error message will be sent to this email.
- Added DIR_WEB, DIR_LOG, DIR_PID= and DIR_TEMPLATE parameters.
- Update of musicindex.css and musicindex.conf.
- Changed naming structure of sound file name.
- Fixed a bug in deleting the silence file.
- README.md in US and FR language.
- email_template directory renamed recorder_templates.

Version [3.0.8] (1-03-2024)

- Update of musicindex.css and musicindex.conf files.
- Change of AMPLITUDE_ADJUSTMENT_SHORT in mail message to reduce number du 3 digits.

Version [3.0.7] (29-02-2024)

- INPUT_THRESHOLD now use sox "Maximum amplitude" tag to manage threshold.
- Using id3v2 to set the Artist with the prefix.
- Using id3v2 to set the Track with the volume ajustement.
- Added customized musicindex.css and musicindex.conf for Apache Musicindex module.

Version [3.0.6] (28-02-2024)

- Initial version.
