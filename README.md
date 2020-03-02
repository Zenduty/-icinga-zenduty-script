# Icinga2 - Zenduty Integration
Scripts for Icinga2-Zenduty integration

## Setup instructions 
1. Install Icinga2 on your system. After this, add an integration on your zenduty account. Not the integration key automatically provided to you.
2. Download the Zenduty-Icinga2  files by following the steps given below:
```
cd /tmp
git clone https://github.com/Zenduty/icinga-zenduty-script.git
cd icinga-zenduty-script
```
3. Open zenduty-icinga2.conf file and enter the integration key provided into the “key” field.
4. Move the files into their respective folders inside /etc/icinga2/. The zenduty-icinga2.conffile must go to the conf.d folder (or the objects.d folder, whichever exists),
```
mv zenduty-icinga2.conf /etc/icinga2/conf.d/
OR
mv zenduty-icinga2.conf /etc/icinga2/objects.d/
```
and the zenduty-webhook-notification.py file must go to the scripts folder,
```
mv zenduty-webhook-notification.py /etc/icinga2/scripts/
```
5. Make sure ‘icingaadmins’ as a user group exists. Else define it as follows in the users.conf file in conf.d  folder.
```
object UserGroup "icingaadmins" { 
display_name = "Icinga 2 Admin Group"
}
```
6. Add the custom attribute enable_zenduty to your configuration’s host and service configuration objects: 
```
vars.enable_zenduty = true
```
If you have a large number of such objects, you can just add the above line to the generic-host and generic-service templates in the templates.conf file in the conf.d folder. Then just import this template to your objects.
7. Restart Icinga 2 service
```
/etc/init.d/icinga2 restart
```
