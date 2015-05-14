Big To Do List
==============

Overview
--------
### Ohana API ###
- [x] Install Ohana API locally
- [x] (Customize) Ohana API and set Settings
- [ ] Translate Ohana API
- [ ] Deploy to Heroku


### Data ###
_NB: In this first implementation, everything with have to be done manually, to get it done fast. Later, we could (I would want to) implement scripts to download and parse data automatically._
- [x] Download data from datos.madrid.es
- [ ] Read "[Prepare your data] (https://github.com/codeforamerica/ohana-api/wiki/Populating-the-Postgres-database-from-the-Human-Services-Data-Specification-%28HSDS%29-compliant-CSV-files)"
- [ ] Change headers to conform to the HSDS

### Ohana Web Search ###






Schedule / Specific Days
------------------------
### Tuesday ###
- [ ] Meet with Lorena
  - [x] Look into web interface, how to do translation, so she can start!


Technical issues, meta-tasks
----------------------------
- [x] Ask for a virtual machine at Media-Lab Prado
  - [x] Find Gabriel / his e-mail address
  - [x] Solved, got e-mail back with address
- [x] Set up GitHub repos
  - [x] Fork ohana-api
  - [x] Fork ohana-web-search
  - [x] Create ohana-importer-madrid
  - [x] Create visualizar15 repo
- [ ] Set up gh-pages with Jekyll for visualizar15, to blog progress

  
Data, sources, files, etc
-------------------------
- [x] Print HSDS Schema overview

First approximation:
- [ ] Download a suitable file manually
- [ ] Got through the headers, see how they fit with the HSDS schema
- [ ] _Possibly_ transform with Open Refine


Front-End
---------


Back-End, Deployment
--------------------
- [x] Sync changes in Ohana
- [x] Install PuTTY and WinSCP
- [x] Install Ohana API locally
  - [x] Ask for help (create new issue) on how access the rails server

  
  
  
Translation
-----------
- [x] Copy config/locales/en.yml to a new file called “es.yml” in the same directory, 
- [ ] Translate the values for each key.
  - [x] Send files to Lorena
  - [x] Partially translate settings.yml
  - [ ] Finish translate settings.yml (?) (Low priority at this moment)
- [x] Uncomment and change the default locale to “:es” in https://github.com/codeforamerica/ohana-api/blob/master/config/application.rb#L40
  - [ ] Ask if opening key "en:" should be changed to "es:"
- [ ] Raise issue: Add to instruction about translation that it is also needed in settings.yml file
- [ ] Submit a pull request with the “config/locales/es.yml” file to the ohana-api repo


FOR LATER, AFTER THE WORKSHOP!
------------------------------
- [ ] Change things (regions, funding bodies, etc) in config/settings.yml in the Ohana API
- [ ] /If someone takes over the project/, change contact e-mail address in config/settings.yml !
- [ ] Uncomment and re-implement (adapt) the regex check of phone numbers (but in ohana-api-madrid! not in codeforamerica/ohana-api)
	- adjust the regular expression here: https://github.com/codeforamerica/ohana-api/blob/master/app/validators/phone_validator.rb#L5
	- enable/disable the validation by un/commenting this line: https://github.com/codeforamerica/ohana-api/blob/master/app/models/phone.rb#L16, and the comma at the end of line 15.


