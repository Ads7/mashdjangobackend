# mash_backend
An opensource backend server for [MASH Poject](https://www.facebook.com/MashProject/) workforce management, leads email tracker and mass mailer.
### workforce management
Track the intern/ employees as per department and aggregate their profile info(image, scocial links etc) for future reference. session middleware used for authentication and used user groups to assign editing and viewing privileges  

### Mailer
A mailer task integated as Django admin function to send emails to individual and mass as an async operation(using cerlery task).
settings used by the mailer are stored in database table mail_settings as key value pairs

base settings stored in mash_backend/settings/production.py and prod settings stored in mash_backend/settings/production.py
base settings should be imported in production and thereby can overwrite any key req.
imp keys 
- MAX_MAILS_PER_SEC
- AWS_ACCESS_KEY_ID
- AWS_SECRET_ACCESS_KEY

URL send_mail/ links to a view that provides a template to provide HTML or text-based body for each mail

gunicorn.sh provided to span multiple instance of the server and keep them running
- LOGFILE ->gunicorn.log
- ERRORFILE -> gunicorn-error.log

requirements provided in requirements.txt
- uses AWS boto for SESConnection sending emails
- S3BotoStorage storing profile images for users
