# FORENSICS CHALLENGE
## TRYHACKME CTF ROOM
*https://tryhackme.com/r/room/disgruntled*

### Description
Hey, kid! Good, you’re here!

Not sure if you’ve seen the news, but an employee from the IT department of one of our clients (CyberT) got arrested by the police. The guy was running a successful phishing operation as a side gig.

CyberT wants us to check if this person has done anything malicious to any of their assets. Get set up, grab a cup of coffee, and meet me in the conference room.

- Connect to the VM 

### Walkthrough

Lets have a poke around at the privileged commands that were run.
- cd var/log
- ls

Read the file and filter the search
- cat /var/log/auth.log | grep install

![alt text](auth.png)

#### Flag 1 : /usr/bin/apt install dokuwiki
#### Flag 2 : /home/cybert

So we're told that a user was created after this previous package was implemented. We just need to adjust the grep filter search to 'adduser'

![alt text](adduser.png)

#### Flag 3 : it-admin

Now for the next flag we are told *A user was then later given sudo priveleges. When was the sudoers file updated? (Format: Month Day HH:MM:SS)*
- Again just adjust the grep filter : cat auth.log | grep visudo
- Flag 4 : seen in image

![alt text](time.png)

*A script file was opened using the "vi" text editor. What is the name of this file?*
- Adjust the grep filter : cat auth.log | grep vi
- Flag 5 : seen in image

![alt text](vi.png)