# ISEA-Lab Reflection 3b
## Lab Objective
Objective was to introduces Bash scripting for creating file backups, scheduling them using cron jobs, and exporting them to the cloud.

##Reflection

Started with testing commands within bash itself

![imgsrc](../Screenshots/3b_bashcommands.png)

followed by making a bash script to copy the contents of /Documents to /backup. There was a little fumble here as i was following the directory "/home/ubuntu/Documents" when i should have been coding it to "/home/lolabozz/Documents" instead (aka my linux username).

![imgsrc](../Screenshots/3b_testscript1.png)

![imgsrc](../Screenshots/3b_backupscript.png)

Once i had figured that out, i created another script without the hardcoded directories which had performed the same way.

![imgsrc](../Screenshots/3b_testscript2.png)

I then used bash to move testscript to the usr/bin/ and ran it again.

![imgsrc](../Screenshots/3b_test_diff_folder.png)

Then i added the date function for the filename and the zip function

![imgsrc](../Screenshots/3b_testscriptwithzip.png)
![imgsrc](../Screenshots/3b_zipexec.png)

Afterwards i edited cron to schedule the backup at every 10th minute of the hour. 

![imgsrc](../Screenshots/3b_scheduling_cron.png)

I then used key-based SSH access to access and upload the .zip file onto the cloud instance.
I had to edit the testscript again to add the keypath to the cloudIP with "/usr/bin/scp -i /home/lolabozz/Desktop/webserverkeys/aws-lab-key.pem "/home/lolabozz/${now}.zip" "ubuntu@3.24.178.81:/home/ubuntu/""

![imgsrc](../Screenshots/3b_uploading_to_cloud.png)
![imgsrc](../Screenshots/3b_checkingcloud.png)

However i realsied that this hardcoded ip would cause issues whenever i rebooted the AWS and it changed ip. So i changed the "ubuntu@3.24.178.81:/home/ubuntu/" into "ubuntu@beetest.duckdns.org:/home/ubuntu/" since my duckdns webpage already constantly updates itself with the AWS ip.

![imgsrc](../Screenshots/3b_upload2cloud2.png)

I deleted the zip file within the cloud to ensure that i was uploading the file again when i ran the updated script.

![imgsrc](../Screenshots/3b_checkingcloud2.png)
