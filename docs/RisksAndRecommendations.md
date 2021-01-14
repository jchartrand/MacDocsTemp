## Possible problems - risk planning 

### Context

The covid situation has made it difficult to issue normal paper diplomas, and even then, paper diplomas - at a time of social distancing - are less useful than a verifiable digital diploma that can be emailed.  

The digital diplomas system is effectively therefore moving from a limited prototype that explicitly provided no guarantees, to the primary form of diploma for the whole university 
until paper can be issued.  The concern is that there is limited technical support for the system, and that the system is fragile -- the prototype was built extremely quickly
with less time available for detailed testing or to build in safeguards and features.  

Herein we try to identify possible problems and provide recommendations to help limit disruptions.

### Overview

This document is a list of possible problems or needs, written kind of like a FAQ (e.g., how do I send an emergency email).  For each one we need to list:

- *who* should be contacted (e.g., for problems with the mail system who best to fix that)
- suggested trouble shooting steps, including things like where to find log files (file location on specific server)
- parts of the system that are involved (e.g., php files/classes, python code )

**RECOMMENDATION:** There also has to be a single point person for the whole project, who triages and delegates as needed.

It would be ideal if we could describe exactly the steps someone would need to do to fix some part of the code - both for a hot fix and for a development fix, so:
	- where on the system to find the file to change.
	- how to login to the system, or who to ask to get a login and permission.
	- at least one way to edit the code, e.g., eclipse, with basic instructions on how to set that up, i.e., how to enable a hot fix.

The idea is that in a critical emergency, we want to make it as easy as possible for someone to fix the problem quickly.  We want to save whatever time we can by giving them help so they don't have to figure everything out (either on their own or by talking to people)

#### Mail

How do I change the templates, e.g., correct a spelling mistake, or add a new field, or change the logos?  So again, where are the specific files (source or live), e.g., Source: /usr/local/digitaldiploma/src/private/mail/template.php Live: /www/apache/home/mail/template.php

How do i fix broken mail (e.g., students aren't getting their notifications)
	- contact: who?
	- any description of the system that is used.

How do I send an emergency email to all graduates for a given batch (e.g., telling them there has been a problem with a batch and giving them instructions or a new date, etc.)

**RECOMMENDATION:**  This is a very good feature to add - a form in the system that can be used to send out an emergency (or otherwise unplanned) email to a given batch of graduates.  The text of the email can be entered in the form. 
	
#### Issuance

Problem with upload?  

**CRITICAL RECOMMENDATION:**  NEED TO DEFINE THE FIELDS IN THE CSV IN EXACT ORDER AND WITH THE EXACT FORMATTING NEEDED

Bitcoin transaction fails
	- who?
	- where in code to look.  troubleshooting 
	
Cron job fails
	- where is this set?
	- how can we check to see if it ran, or what errors happened.
	- how could this be reset or retriggered?  How could we manually rerun something that was supposed to run through cron, but didn't?
	
Students can't download their certificate
	- who deals with this?
	- suggested troubleshooting steps (logs, tests, etc.)

Students can't install the Blockcerts app

Students can't 'register' using the opt-in link

How would I change the blockcert template?  (what php file to change?  where on server, or how to recompile)

How do I update the python issuing code if there is a new version put out by Learning Machine?  (where should the file go, what needs to be compiled)

How might one fix the python code directly?  

**RECOMMENDATION:**  IF THIS IS MEANT TO BE A PRODUCTION APP WITH LITTLE COMFORT FOR FAILURE, SOMEONE AT MCMASTER SHOULD BECOME MORE FAMILIAR WITH THE PYTHON LIBRARIES - THERE IS NO GUARANTEE THAT LEARNING MACHINE WILL RESPOND TO REQUESTS.
	
#### Web verification

Who deals with site disruptions (page not avaiable, problems with web page, e.g., with updates to browsers)

Verifier fails (e.g., if bitcoin lookups disappear)
	- where is the source code???
	- how to change code, recompile, and where to put it in the server.

#### Wallet

Wallet app fails
	- who will contact Learning Machine.
	
**RECOMMENDATION:** IF THIS IS MEANT TO BE A PRODUCTION APP WITH LIMITED COMFORT FOR FAILURE, SOMEONE AT MCMASTER HAS TO BECOME MORE FAMILIAR WITH THE LIBRARIES FOR THE WALLET - THERE IS NO GUARANTEE THAT LEARNING MACHINE WILL RESPOND TO REQUESTS.

#### Backup

What system is used for this?  Who can restore the backup?  We need detailed steps for doing this, so it can be done quickly.

**RECOMMENDATION:** we should do a test restore to make sure backups work as expected and that we are all clear on who does what.

#### General Admin

How are new issuers(organizations?) added?

Is there anything else done outside of the admin app that should be documented?  Any direct changes to files, permissions, crontab, etc.?

How would we revoke a full batch if something went wrong?  How would we most quickly reissue that batch once the problem was fixed?

