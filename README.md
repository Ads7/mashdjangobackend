# mashdjangobackend
A opensource backend server for [MASH Poject](https://www.facebook.com/MashProject/) workforce management, leads email tracker and mass mailer.
### workforce management
Track the intern/ employees as per department and aggregate their profile info(image,scocial links etc) for future reference. 

### Mailer
A mailer task intergated as django admin function to send mails to individual and mass as a async operation.
settings used by the mailer are stored in databse table mail_settings

base settings stored in mash_backend/settings/production.py and prod settings stored in mash_backend/settings/production.py
base settings should be imported in production and thereby can overwite any key req.
imp keys 
- MAX_MAILS_PER_SEC
- AWS_ACCESS_KEY_ID
- AWS_SECRET_ACCESS_KEY

url send_mail/ links to a view that provides a template to provide html or text based body for each mail

gunicorn.sh provided to span mulitple instance of server and keep them running
- LOGFILE ->gunicorn.log
- ERRORFILE -> gunicorn-error.log

requirements provided in requirements.txt
- uses AWS boto for SESConnection sending mails
- S3BotoStorage storing profile images for users
