ToDo List: Open Referral Madrid
===============================

###Introduction and Overview###
To start with, before I start enumerating tasks, I want to point out that this list is a dynamic document which mostly reflects the current state of the project, and in no way do I pretend for it to be universal and all-inclusive. I will center here mostly on the technical aspects of the project, although there obviously will be some overlap with more conceptual aspects of implementing open data sharing standards in our community. 

This list could potentially be huge, but I will try to break it down in four main categories:
- **Project Management**
	- _Contact with stakeholders, organization of project and people, meetups, events_
- **Core Conceptual Ideas**
	- _Ideas that need to be discussed with stakeholders and documented: Schemas, taxonomy, infrastructure_
- **Data & Translation**
	- _Input (and updating(?)) of remaining available data, translation of documents / web site / taxonomy?, etc_
- **Technical Implementation**
	- _Updating the site, implementing translations, managing Admins, etc._
	- _For now, all referring to the prototype project._

---


###Project Management###
Not really in my scope. Hopefully we can determine more of this at the meeting next week (last week of May).

Raise:
- [ ] Can we / should we change the contact e-mail address to a medialab one? (config/settings.yml)

---

###Core Conceptual Ideas###
Same as above, not really in my scope, at least not right now (possibly later, when I come back).

---


###Data & Translation###

####Data Input####
- [ ] Input the remaining pertinent files from http://datos.madrid.es manually with Google Spreadsheet
- [ ] _Input data from other service providers (find and input?)_

####Translation####
- [ ] Write more info-boxes about new data, in ```ohana-web-search-madrid/config/settings.yml```

---


###Technical Implementation###

####Back End####
- [ ] Implement translation of Admin interface
	- [ ] Finish translate settings.yml (?)
	- [ ] Try to find more places that need translation (different config-files, etc)
	- [ ] Change in ```config/application.rb#40```: ```default_locale = :es```
- [ ] Change things (regions, funding bodies, etc) in config/settings.yml in the Ohana API
- [ ] Uncomment and re-implement (adapt) the regex check of phone numbers
	- adjust the regular expression here: https://github.com/amsorribes/ohana-api-madrid/blob/master/app/validators/phone_validator.rb#L5
	- enable/disable the validation by un/commenting this line: https://github.com/amsorribes/ohana-api-madrid/blob/master/app/models/phone.rb#L16, and the comma at the end of line 15.

#####Pull Requests & Issues#####
- [ ] Submit a pull request with the “config/locales/es.yml” file to the ohana-api repo
- [ ] Issue/Question - Why are my districts refused when the same valid_districts are defined in the settings file?
- [ ] Pull Request: Change deploy to heroku script: ```:create``` not ```:add```
- [ ] Pull Request, COLOR URL: 
	- [ ] Edit instructions and explain what to do if you do not get a 'COLOR URL'
	- [ ] File pull request
- [ ] Pull Request: Translation
	- [ ] Edit instructions on translation, point out all the places needed to change (settings.yml, more?)
	- [ ] File pull request
- [ ] Submit a pull request to the ohana-api repo with the “config/locales/es.yml” file, when it is/feels done

####Front End####
- [ ] Translation: Try to find more places that need translation (different config-files, etc)


#####Pull Requests & Issues#####
- [ ] Pull Request: Translation
	- [ ] Edit instructions on translation, point out all the places needed to change (settings.yml, more?)
	- [ ] File pull request
	- [ ] Possibly file Issue, asking for help to make more parts of the web site translatable
	- [ ] Issue: Ask for help in making Spanish default language in the Google translation boxes in top right corner of landing page
- [ ] Submit a pull request to the ohana-web-search repo with the “config/locales/es.yml” file, when it is/feels done


####Project Sharing####
- [ ] Clean up branches on GitHub
- [ ] Move whole dev-box directory structure to Dropbox, share link -- so someone can download whole thing and get it working


