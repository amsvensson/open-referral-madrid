Workshop [Visualizar'15 Commoning Data](http://medialab-prado.es/article/tallervisualizar15proyectos)
=======================================

Thursday, 7 May 2015
--------------------
After two initial [conference days](http://medialab-prado.es/article/visualizar15-seminario) with interesting talks about open data, project introductions and many more topics, today was the first day of actual work! After an initial session of info and general guidelines, I met up with the other team mates of the [CityAPI](http://comunidad.medialab-prado.es/en/groups/cityapi-dashboard-madrid) project to talk about the whats, hows, and minimum viable project/product/prototype. After an intense brainstorming session, we decided on looking into [CKAN](http://ckan.org), to find out if it would work as our general framework.

Inspired by Greg Bloom's talk on [Open Referral](http://openreferral.org/) and previous chats with him about the project, I also spent some time thinking about how/if the Open Referral framework could fit into the cityAPI project. At the end of the day we had a 'Critical Session' with the workshop mentors, to discuss the ideas and scope of the cityAPI project. We got some good ideas, and they suggested that we should to try to ask for statistical data from the Instituto Nacional de Estadistica, INE (Spanish National Institute for Statistics), to complement the data from the city of Madrid's [open data portal](http://datos.madrid.es).


Friday, 8 May 2015
------------------
After a night to reflect on the progress and the comments of the workshop mentors, we came back the next morning and continued our research. We would not have a full team until the afternoon, so I continued to read up on the Open Referral data model/schema, and on requirements and install notes for the [Ohana API](https://github.com/codeforamerica/ohana-api) and the [Ohana Web Search](https://github.com/codeforamerica/ohana-web-search). I got further inspired - read: convinced - to try to implement the Open Referral platform as Greg brought back good news from his morning meeting with a social services foundation. Not only were they going to be able to share data with us, but there were also an awareness about the need for increased data sharing in the sector, data sharing standards, and platforms like these!

After lunch we gathered to define the project, and decided on a work scheme where we could work somewhat in parallel. My team mates would implement the CityAPI with ckan as base, pulling 'all' data from the open data portal, and develop a dashboard, while I would work specifically with the health and social services part of the data, try to set up the Ohana API and Web Search. To harmonize the projects, we decided to ask the INE (National Institute for Statistics) for data regarding health in particular (as we had been advised to pick an area), and that the general dashboard they will create can pull data from both the CityAPI and the Ohana API. 

This organizational decision was not obvious - the initial idea was rather that either i) the Ohana API would pull data from the CityAPI, or ii) that that the Ohana Web Search might be able to be implemented on top of the CityAPI directly. Taking into account the expressed need for a platform for data sharing among the health and social services, however, I realized that the Ohana API is much better suited for this than the general model ckan offers. So it would make sense for the Ohana API to 'exist' and it would also make sense that this would be the hub for this kind of information. So with that in light, we decided that it would make more sense for the CityAPI to pull from Ohana than the other way around.

In the afternoon I was introduced to Lorena, who work at Media-lab Prado. She researches community services in the area, and will be a huge help, I reckon. To start with, she's agreed to help me with the translation of the site!


 
Saturday, 9 May 2015
--------------------
This morning I woke up with tons of ideas on how to start tackling the data transformation tasks, but instead today ended up being mostly about 'maintenance' - forking, cloning, setting up repos; printing, doing to-do lists, writing the documentation/daily logs for the previous days, etc, etc. I also read some more on the Open Referral site, the FAQ and other things, which I feel has helped me to get a better grasp on what's needed and how to affront the data transformation task ahead.
 
Regarding the repos, I decided to divide the work into 2 repos - plus the 2 repos from the ohana platform - so 4 in total. My two repos are the following:
- [visualizar15-commoning-data](https://github.com/amsorribes/visualizar15-commoning-data): This is where I will keep my logs/updates about my progress on this project, including files and ideas, to-dos, etc.
 
- [ohana-importer-madrid](https://github.com/amsorribes/ohana-importer-madrid): This is where I will strictly keep the source code for the scripts for the data that will be imported into the Ohana API. This will include downloading files from the datos.madrid.es site, transformations so they adhere to the Open Referral schema (the Human Service Data Specification, HSDS), and loading it all into Ohana via the API (hopefully).
 
Looking forward to days ahead when I will start checking out the data!
 
 
Monday, 11 May 2015
-------------------
Installed PuTTY and WinSCP to connect to the virtual machine Gabriel set up for us. 
Decided to first install the Ohana API on my local machine, to try it out easier.
Following install instructions on: https://github.com/codeforamerica/ohana-api/blob/master/INSTALL.md, and more specifically: https://github.com/codeforamerica/ohana-api-dev-box/wiki/Ohana-API-virtual-machine-installation-guide-for-Windows
Steps:
- [x] Install VirtualBox
- [x] Install Vagrant
- [x] Clone ohana-api-dev-box
- [x] Clone ohana-api-madrid into ohana-api-dev-box directory
- [x] Configure the database
- [x] Set up the environment variables
- Had to redo these steps, installing ruby and rails, to manage to launch the Ohana API
	- [x] Log in to the virtual machine via SSH
	- [x] Bootstrap Ohana API in the VM
- [] ~~Launch Ohana API~~ - Unable to get it to work. Get the rails server up and running, but nothing on http://localhost:8080

Commands to run for setting it up:
> with git bash, navigate to ohana-api-dev-box
vagrant up
vagrant ssh
cd /vagrant/ohana-api-madrid
script/bootstrap
rails s -p 8080

Trying.....googling.... trying....googling.... trying, ugh.

* Will try to install it on my computer without the VirtualBox instead!
Ugh..
- [x] Install [Ruby 2.1.6](http://rubyinstaller.org/downloads/) (32 bit version)
- [x] Install RubyGems: >> gem update --system
- [x] Download and extract corresponding DevKit from same page (DevKit-mingw64-32-4.7.2-20130224-1151-sfx.exe)
	- [x] [Install DevKit](https://github.com/oneclick/rubyinstaller/wiki/Development-Kit): 
	- [x] ruby dk.rb init
	- [x] ruby dk.rb install

With *git bash* (not window's command window!)
Following commands from https://github.com/codeforamerica/howto/blob/master/Ruby.md
	- [x] Install RVM with the latest version of Ruby: curl -L https://get.rvm.io | bash -s stable --autolibs=enabled --ruby
```
% Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100   184  100   184    0     0    152      0  0:00:01  0:00:01 --:--:--   206
100 22721  100 22721    0     0  13341      0  0:00:01  0:00:01 --:--:-- 13341
BASH 3.2.25 required (you have 3.1.0(1)-release)
```

- [x] skip downloading of documentation for each gem by adding a global no-document configuration to the .gemrc file: echo "gem: --no-document" >> ~/.gemrc
- [x] Install rails: >> gem install rails

```
Successfully installed rails-4.2.1
```

* Now following https://github.com/codeforamerica/howto/blob/master/PostgreSQL.md
There are no instructions for windows, so I went to the PostgreSQL page instead.
- [x] Download & Install  [PostgreSQL](http://www.enterprisedb.com/postgresql-941-installers-win32?ls=Crossover&type=Crossover)

Now, clone the Ohana API and set up:
- [x] git clone https://github.com/<your GitHub username>/ohana-api.git && cd ohana-api
- [x] bin/setup
- [x] add "C:\Program Files (x86)\PostgreSQL\9.4\bin\psql.exe" to Windows PATH (Environment variables)
Nope, still not working. Have to install puma...

* Now following instructions on: https://github.com/hicknhack-software/rails-disco/wiki/Installing-puma-on-windows
Doesn't work either.

###..Giving up..###
Going to ask for help, ideally if someone could set it up for me on heroku.

Uninstall:
- [x] Ruby
- [x] DevKit
- [x] PostgreSQL

(_Oh, my poor registry_..)

---

###Datos###
~~Going to start downloading and looking at the data instead. Hopefully while I work on the data transformations, I can get help setting up Ohana API!~~
Went to get help to install it on the linux virtual machine that we have access to here at media-lab prado. We're still at it, but permissions are getting in the way..

###Late Night update!###
My issue on github was heard, and with a simple change of command
~~```rails s -p 8080```~~ --> ```puma -p 8080``` 
I can now reach http://localhost:8080 correctly and see the developer and admin interfaces!!


Tuesday, 12 May 2015
--------------------
Adolfo tugged on, trying to get it to work on the linux (debian) virtual machine here at media-lab prado. After much struggle, and help from another person, we (they) finally got it to work! I finally got access to (two!) working copies of the Ohana API, and will go on to i) quickly look at some customizations, and ii) get cracking on the data!

Finished tasks from ToDo:
- [x] Customize Ohana API - read through, no customizations needed at this point
- [x] Send translation files to Lorena
- [x] Change Settings for Ohana API (config/settings.yml)  <-- **important! more to do here for later!**

- Added a bunch of tasks to ToDo


Wednesday, 13 May 2015
----------------------
At the other branch of the project, they have been trying to get ckan up and running, and ran into problems as well - to the point that Gabriel has now set up an Ubuntu virtual machine, in addition to the Debian we had been using. Seeing that I now have access to an Ubuntu machine, and that it seemed that a lot of the problems we ran into with the installation was due to Debian, I will probably try to install the Ohana API on the Ubuntu machine later on. However, first I am going to start on the data, which I foresee will take me quite some effort to get right...

###Populating the database - Steps taken###
- Copy all csv-files in the ```ohana-api-madrid/data/sample-csv``` directory to my project directory ```ohana-importer-madrid/data/csv-templates```
- File by file, go in and delete all the data - leave only the headers (except for the 'taxonomy.csv' file).

####[Info about the files](https://github.com/codeforamerica/ohana-api/wiki/Populating-the-Postgres-database-from-the-Human-Services-Data-Specification-%28HSDS%29-compliant-CSV-files) (reorganized according to requirement)####
- organizations.csv (required)
- locations.csv (required)
- addresses.csv (required)
- phones.csv (required)
- services.csv (required)
- regular_schedules.csv (recommended)
- holiday_schedules.csv (recommended)
- contacts.csv (optional)
- mail_addresses.csv (optional)
- programs.csv (optional)
- taxonomy.csv (optional)

####Download and Inspect Files from datos.madrid.es####
- Go to CATALOGO
- On the right there's a box with "FILTRAR POR..."
  - Select "Salud" and press the Filtrar button, download interesting files
  - Select "Sociedad y bienestar", press Filtrar button, download interesting files
- Downloaded files to ```ohana-api-madrid/datos-madrid```
- First, I chose csv-files to download, as they would be easiest to process from python. However, upon inspection, there are line breaks within single entries, making a loop over lines problematic... Will look into it further, maybe it will be easier with the excel files after all..
- After careful inspection of the different file formates available (xlsx, csv, rdf, xml), I have chosen to go wih XML. I was tempted to choose RDF, since this is an emerging standard - but there were data fields that had been merged (e.g. Transportation into Description), which makes it less useful. Conclusion, thus: Will use XML to get the information!
- Looked into the lxml library in python

#####First test of populating the database#####
First, will do a test with just one organization, to test how to build the database and if my format is working.
I will work with the first organization in the "Centros de dia" directory.
- Download file from http://datos.madrid.es/egob/catalogo/200342-0-centros-dia.xml

- Got an excel file from Manu will several xslx files put together. Gone through them to understand the structure and relationships between orgnaizations and locations/services.

- Idea for implementation: Create a dictionary for each csv file; Keep lists of dicts to represent entries.
- I am going to need to do custom import scripts for each file, especially to sort out what organization each entry belongs to (Municipal or Concertado --> splits into several, some have more than one location!).

- After lunch, with time to ponder on the organization of all of this, I have decided to create the organizational structure for the Municipal centers in Madrid. 
- Found the Organigrama, now in ```ohana-importer-madrid/organization-madrid/```

- Have added one Centro de dia, with all the required info in the csv files. Going to try to see if it works, trying on my local virtual machine.
- [x] copy cvs-files to ```ohana-api-dev-box/ohana-api-madrid/data```
- [x] open up git shell, navigate to ohana-api-dev-box
- [x] run 
	- [x] ```vagrant up```
	- [x] ```vagrant ssh```
	- [x] ```cd /vagrant/ohana-api-madrid```
	- [x] ```script/reset```
	- [ ] ```script/import``` --> ERROR
	- [x] make changes to files
	- [x] ```vagrant reload```
	- [x] ```cd /vagrant/ohana-api-madrid```
	- [x] ```script/reset```
	- [x] ```script/import``` 
	- [x] ```puma -p 8080``` --> SUCCESS!

-Install the web search
	- [x] clone the web search: ```git clone https://github.com/amsorribes/ohana-web-search-madrid.git && cd ohana-web-search-madrid```
	- [ ] ```bin/setup``` --> ```command not found```

- Run bin/setup commands manually
- [x] ```cp config/application.example.yml config/application.yml```
- [x] ```gem install bundler --conservative```
- [x] ```bundle check || bundle install```
- [x] ```rm -f log/*```
- [x] ```rm -rf tmp/cache```
- [ ] ```touch tmp/restart.txt``` --> ERROR: touch: cannot touch `tmp/restart.txt': No such file or directory. Probably not needed, ignoring error :D

- [x] Try to run the web search, get error and 'Unable to find server' on ```http://localhost:4000```

```
vagrant@ohana-api-dev-box:/vagrant/ohana-web-search-madrid$ puma -p 4000
[1805] Puma starting in cluster mode...
[1805] * Version 2.11.1 (ruby 2.2.1-p85), codename: Intrepid Squirrel
[1805] * Min threads: 5, max threads: 5
[1805] * Environment: development
[1805] * Process workers: 2
[1805] * Preloading application
[1805] * Listening on tcp://0.0.0.0:4000
[1805] * Listening on tcp://0.0.0.0:3000
/home/vagrant/.rvm/gems/ruby-2.2.1@ohana-web-search/gems/puma-2.11.1/lib/puma/binder.rb:210:in `initialize': Address already in use - b
ind(2) for "0.0.0.0" port 3000 (Errno::EADDRINUSE)
        from /home/vagrant/.rvm/gems/ruby-2.2.1@ohana-web-search/gems/puma-2.11.1/lib/puma/binder.rb:210:in `new'
        from /home/vagrant/.rvm/gems/ruby-2.2.1@ohana-web-search/gems/puma-2.11.1/lib/puma/binder.rb:210:in `add_tcp_listener'
        from /home/vagrant/.rvm/gems/ruby-2.2.1@ohana-web-search/gems/puma-2.11.1/lib/puma/binder.rb:96:in `block in parse'
        from /home/vagrant/.rvm/gems/ruby-2.2.1@ohana-web-search/gems/puma-2.11.1/lib/puma/binder.rb:82:in `each'
        from /home/vagrant/.rvm/gems/ruby-2.2.1@ohana-web-search/gems/puma-2.11.1/lib/puma/binder.rb:82:in `parse'
        from /home/vagrant/.rvm/gems/ruby-2.2.1@ohana-web-search/gems/puma-2.11.1/lib/puma/runner.rb:119:in `load_and_bind'
        from /home/vagrant/.rvm/gems/ruby-2.2.1@ohana-web-search/gems/puma-2.11.1/lib/puma/cluster.rb:301:in `run'
        from /home/vagrant/.rvm/gems/ruby-2.2.1@ohana-web-search/gems/puma-2.11.1/lib/puma/cli.rb:512:in `run'
        from /home/vagrant/.rvm/gems/ruby-2.2.1@ohana-web-search/gems/puma-2.11.1/bin/puma:10:in `<top (required)>'
        from /home/vagrant/.rvm/gems/ruby-2.2.1@ohana-web-search/bin/puma:23:in `load'
        from /home/vagrant/.rvm/gems/ruby-2.2.1@ohana-web-search/bin/puma:23:in `<main>'
        from /home/vagrant/.rvm/gems/ruby-2.2.1@ohana-web-search/bin/ruby_executable_hooks:15:in `eval'
        from /home/vagrant/.rvm/gems/ruby-2.2.1@ohana-web-search/bin/ruby_executable_hooks:15:in `<main>'
vagrant@ohana-api-dev-box:/vagrant/ohana-web-search-madrid$ puma -p 4000
[1813] Puma starting in cluster mode...
[1813] * Version 2.11.1 (ruby 2.2.1-p85), codename: Intrepid Squirrel
[1813] * Min threads: 5, max threads: 5
[1813] * Environment: development
[1813] * Process workers: 2
[1813] * Preloading application
[1813] * Listening on tcp://0.0.0.0:4000
[1813] * Listening on tcp://0.0.0.0:3000
[1813] Use Ctrl-C to stop
[1813] - Worker 0 (pid: 1816) booted, phase: 0
[1813] - Worker 1 (pid: 1820) booted, phase: 0
```

- [x] Write Moncef (again..) about this, and 'location' problems with requirements of State and number of digits in the phone number, since this is different in the US and Spain.


Thursday, 14 May 2015
---------------------
- Woke up to a response from Moncef (thank you, thank you, _thank you_)!
- Will start implementing the solutions:
* Update ohana-api:
	- [x] ```cd /ohana-api-madrid``` with Git Bash
	- [x] ```git fetch codeforamerica```
	- [x] ```git checkout master```
	- [x] ```git merge codeforamerica/master```
	- [x] ```git push origin master```
	
* Remove phone regex check (I was thinking of changing the regex, but it is not 'easy', since in Madrid, people tend to write phone numbers either as 912 345 678, 912 34 56 78, 91 23 45 678 (and maybe more ways!). Decided to remove the check altogether.
	- [x] disable the validation by commenting this line: https://github.com/amsorribes/ohana-api-madrid/blob/master/app/models/phone.rb#L16, 
	- [x] and the comma at the end of line 15.
	- [x] commit to master and push to github

* Change postal code requirement to 5 digits, starting by 28 (28xxx)
	- [x] make change in regex in ```ohana-api-madrid\app\validators\zip_validator.rb```
	- [x] push to github

* Get the vagrant virtual machine to work for both the API and the web search:
	Response from Moncef:
	"The ohana web search issue is because the Vagrantfile is only forwarding one port from the Vagrant machine to your computer. That means that only port 8080 will be accessible from your browser. I added port 4000 to the Vagrantfile, so please pull the latest code for ohana-api-dev-box, then run “vagrant halt”, and “vagrant up” to pick up the changes."
	- [x] pull from ohana-api-dev-box
	- [x] ```vagrant halt```
	- [x] ```vagrant up```
	
	"To point ohana-web-search to your local Ohana API, you need to set the OHANA_API_ENDPOINT environment variable to "http://localhost:8080/api", which you can do in your “config/application.yml”: https://github.com/codeforamerica/ohana-web-search/blob/master/config/application.example.yml#L149"
	- [x] make changes in ```config/application.yml```
	- [x] ```vagrant halt```
	- [x] ```vagrant up```
	- [x] ```rails s -p 4000 -b 0.0.0.0``` --> SUCCESS!!

* Lorena me ha mandado la traduccion del portal de admin del API tambien!
	- ToDo: Una vez que la API y el web search funcionen, introducir las traducciones!
	

---

SOOOooOooOoo much trouble getting it all to work. I tried to implement the changes, it looked like everything was working, and then all of the sudden it wasn't. I've now redone all the steps with the dev-box twice, first with clones from the codeforamerica github account, and then from my amsorribes account. It is working again, but without any of the modifications I had done. Let's see what is breaking it....

In the meantime, while stuff has been installing, I have been manually filling out the Google Spreadsheet template with data from the Centros de Dia, to see if I will be able to populate the database with this.

---
Some notes about the translation - after formatting the yml-files correctly (with help from a yml consistently check website), and several iterations of trying, I got it through the Ohana API start-up process without any errors or warnings. So, good to go I thought, until I logged into the admin interface and got (database?) errors which had not been there before. Decided that I will have to wait to get the translations working for now, will center on populating the database first of all, and then deal with getting the translations to work..


Sunday, 17 May
--------------
After a few lovely days with friends visiting, it's back to work! The steps I am planning on taking are:
- [x] Run Ohana API, log into admin, see that all is working
- [x] ctrl+c, ctrl+d, vagrant halt
- [x] ~~Remove phone number formatting check~~ <-- Already in code cloned from github (I pushed it previously)
- [x] ~~Remove postal code formatting check~~ <-- Already in code cloned from github (I pushed it previously)
- [x] Try to run and log into the admin interface to confirm that it is still working and didn't break
- [x] Export the data I filled into the Google Spreadsheet template to csv
- [x] Run the csv's through CSV Lint
- [ ] Follow [instructions](https://github.com/codeforamerica/ohana-api/blob/master/INSTALL.md#uploading-and-validating-your-own-data) on how to build the database
	- [x] Put the csv's in the data folder
	- [x] vagrant up, vagrant ssh, cd /vagrant/ohana-api-madrid
	- [x] script/reset
	- [ ] script/import --> Error:
	```
	...Importing your organizations...
	rake aborted!
	ActiveRecord::StatementInvalid: PG::StringDataRightTruncation: ERROR:  value too long for type character varying(255)
	```
	Ugh.. which means I will have to (manually!) search and find too long entries... :(
	- [x] organizations.csv: Shortened the description of first line, removed some invisible whitespaces, removed website
	- [x] organizations OK, now complain that no 'programs.csv' present, even though it says "programs.csv (optional)" on the [instructions](https://github.com/codeforamerica/ohana-api/wiki/Populating-the-Postgres-database-from-the-Human-Services-Data-Specification-%28HSDS%29-compliant-CSV-files) page!
	- [x] Add programs.csv
	- [x] Needs taxonomy.csv too (even though this file also is specified as 'optional')
	- ```rake aborted! Geocoder::OverQueryLimitError: Geocoder::OverQueryLimitError```
	- [x] Try to find where in settings I change the bounding box --> it is in 'config/settings.yml' . I've lost all the changes I made to it a while back.
		New bounding box: SW: 39.906410, -4.623211  ; NE: 41.173322, -3.027446
	- ```rake aborted! Geocoder::OverQueryLimitError: Geocoder::OverQueryLimitError```
		- Tried different delays with script/import 0.2 , 0.5 , 1 - still OverQueryLimitError
		- Found [this](https://github.com/codeforamerica/ohana-api/issues/136) thread from last year, where solution was to comment out line 178 in location.rb . Line 178 does however not exist in the present day location.rb , so searched back in time March 8, 2014 to see what line it was. It corresponds to present-day line 64. Commented out that!
	- [x] Push to github/ohana-api-madrid comment at  https://github.com/amsorribes/ohana-api-madrid/blob/master/app/models/location.rb#L64
	- Complains about no contacts.csv file (again, when it is 'optional'). This is more problematic becuase I don't have that contact information.
	- [x] Create in 'contact' info by putting the service name as contact name in template, and download as csv.
	- Complains about no regular_schedule and holiday_schedule as well. Download the defaults..
	- SUCCESS !
	- [x] Export the database:  ```script/export_prod_db```
	- [x] To restore your local database from your clean data: ```script/restore_prod_db```

Revv it up!
- [x] ```puma -p 8080```
- [x] accessible at localhost:8080/admin -- However, can't log in with development accounts!
- Going to try to get the web search up, see if I can see the database entries I made
	- [x] open new Git Bash
	- [x] vagrant ssh
	- [x] ```rails s -p 4000 -b 0.0.0.0```
	- [ ] Can't get the database data to show up in the web search interface...

...HOWEVER - trying out the Ohana **API** at localhost:8080/api **WORKS**!! Woohoo, The database is populated with my entries and we can get at them from the API!! 
Now I "just" have to figure out why they aren't showing up in the web search, but that is less worrying at the moment. 

Next, try translation:
- [x] Implement translation file (es.yml) in ohana-web-search-madrid !
It worked! 
But much more needs to be able to be translated! Adding to to-do list for later, raise issue on ohana-web-search


Remembered one thing - I put "MA" as state for all the addresses, before the State requirement was removed for addresses outside of USA and Canada. I should change this to see if it helps with the entries showing up in the web search.
- [x] Remove "MA" from all addresses
- [x] Download the csv file
- [x] Shut down web service and API service
- [x] Copy new 'addresses.csv' to /data
- [x] script/reset
- [x] script/import
- [x] script/export_prod_db
- [x] script/restore_prod_db
- [x] puma -p 8080 ==> API is working well!

### OHOY!! ###
I figured out why my database entries weren't showing up in the web search! I had lost the change I made in the ```config/application/yml``` (because it isn't version controlled) so:
- [x] Change line 149 to: ```OHANA_API_ENDPOINT: http://localhost:8080/api``` for local testing!!

####SUCCESS!!!####
I've now got a working copy of the web search, showing up with entries from the database I built with Day Centers in Madrid - running locally on my (virtual) machine! It still looks terrible - even though the translation is in place, most of the text on the page is still in English. Thinking about deploying it to heroku so I can send a link to the Ohana development team (Moncef, but maybe more people?) to see if they can help making more of the page 'translatable'. 
- I've spent some time reading the config/settings.yml of the Web Search application. Here can and will have to do a lot of customizations and translations. Have begun, but more to be done.


To modify the front page boxes with search terms, I will look into which data is available from the datos.madrid.org, and organize these boxes accordingly.

Draft of categories:

* Attencion y Gestiones
	- Centros de salud
	- Farmacias
	- Centros de Servicios Sociales Municipales

* Menores, Familia & Mujeres
	- Centros de Atención para Menores y Familia
	- Puntos de atención a mujeres
	
* Centros de Inclusion Social
	- Mayores: Centros de Día ; Centros Municipales de Mayores
	- Centros para personas con discapacidad
	- Centros para personas sin hogar

* Entidades de participación ciudadana
	- Federaciones
	- Asociaciones
	- Centros municipales de enseñanzas artísticas

OR

* Attencion y Gestiones
	- Centros de salud
	- Farmacias
	- Centros de Servicios Sociales Municipales

* smth
	- Centros para personas sin hogar
	- Puntos de atención a mujeres

* smth
	- Centros de Atención para Menores y Familia
	- Mayores: Centros de Día ; Centros Municipales de Mayores
	- Centros para personas con discapacidad

* Entidades de participación ciudadana
	- Federaciones
	- Asociaciones
	- Centros municipales de enseñanzas artísticas


==> For now, go with the first one, but ask Lorena what she thinks!


###Avaliable Files at http://datos.madrid.es####

####Salud####
* [Madrid Salud: relación de centros municipales](http://datos.madrid.es/portal/site/egob/menuitem.c05c1f754a33a9fbe4b2e4b284f1a5a0/?vgnextoid=9613e34983c73410VgnVCM2000000c205a0aRCRD&vgnextchannel=374512b9ace9f310VgnVCM100000171f5a0aRCRD)
	Centros de Salud Municipales
    Centros de Atención a Drogodependencias
    Centros especializados
    Centros monográficos
	Datos de ubicación, transporte, contacto, horario y servicios. Referencias a Barrios y Distritos de ubicación del centro y su área de influencia de servicios.
	File URL: http://datos.madrid.es/egob/catalogo/201544-0-centros-salud.xml

* [Farmacias](http://datos.madrid.es/portal/site/egob/menuitem.c05c1f754a33a9fbe4b2e4b284f1a5a0/?vgnextoid=edae2c7220107410VgnVCM1000000b205a0aRCRD&vgnextchannel=374512b9ace9f310VgnVCM100000171f5a0aRCRD) (?)
	Relación de Farmacias ubicadas en la ciudad de Madrid.  
	La información procede del Colegio Oficial de Famaceúticos de Madrid. En los enlaces se puede acceder directamente a su web y a su buscador de Farmacias de Guardia.
	File URL: http://datos.madrid.es/egob/catalogo/207619-0-farmacias-madrid.xml

* [Farmacias de guardia](http://datos.madrid.es/portal/site/egob/menuitem.c05c1f754a33a9fbe4b2e4b284f1a5a0/?vgnextoid=c383f3e3fbefc410VgnVCM1000000b205a0aRCRD&vgnextchannel=374512b9ace9f310VgnVCM100000171f5a0aRCRD) (Only with periodic, automatic data fetching scripts)

####Sociedad y bienestar####


---

Monday, 18 May
--------------
Priorities today:
- Deploy Ohana API to Heroku
- Deploy Web Search to Heroku
- Start populating the database (won't have time to finish in a day, will take considerably longer)
- Try to get the search to work (will I need to implement taxonomies?)
	- Especially the 'Boxes' on the home screen
	- The search by Postal Code is not working
	- Search by partial keyword ("Qua" should give hits for Quavitae)

ToDo, not forget:
- Pull new changes from codeforamerica/ohana-api and /ohana-web-search !
- Uncomment (reactivate) the geocoding line since this seems to have been fixed now
- Maybe raise and issue on github regarding import script requiring optional csv files
- Solve admin login to the API - add new super admin user?

###Tasks today###
- [x] Filed [issue](https://github.com/codeforamerica/ohana-web-search/issues/810) on ohana-web-search about partial searches not working in the Organization name search
- [x] Try to get the forking and branching of the two projects right (not easy..)
	- [ ] Still to do: fetch and merge (or rebase?) new changes from ohana-api <-- LATER, now everything is finally working again!
- [x] Filed [issue](https://github.com/codeforamerica/ohana-api/issues/340) on ohana-api for help on how to reach the admin interface after having populated the database.

###Deploy Ohana API to Heroku###
- [x] Create account at Heroku
- [x] inside vagrant, run ```wget -qO- https://toolbelt.heroku.com/install-ubuntu.sh | sh```
- [x] log in: ```heroku login```
- [x] Create my app: ```heroku apps:create ohana-api-madrid```
- have redone these steps as I can't seem to find the "color url"
	- [x] Deploy the app: ```script/setup_heroku ohana-api-madrid```
	- [x] Save all the heroku configuration in ```heroku setup response.txt```
- [x] Put the database dump file somewhere accessible by HTTP
	- Decided to try from dropbox (instead of setting up a trial account at AWS), found [this](http://dirk.haage.info/post/40674698476/this-is-not-the-dropbox-link-youre-looking-for) on how to link to the file
- [ ] Get your Heroku database name: ```heroku config -a ohana-api-madrid```


- [x] Manually do steps from script/setup_heroku, add database, mail and 
- [x] Add heroku remote: ```git remote add heroku git@heroku.com:ohana-api-madrid.git```

- [x] restore database from url: ```heroku pg:backups restore 'http://dl.dropboxusercontent.com/u/2754289/ohana_api_production.dump' DATABASE -a ohana-api-madrid```

####SUECCESS!####
ohana-api-madrid is now avaliable at https://ohana-api-madrid.herokuapp.com  !!

---
Later at night, want to see if I can get the web search up on heroku as well!

Here's the session (edited to only the commands that worked):
```
	Welcome to your Vagrant-built virtual machine.
	Last login: Mon May 18 18:50:44 2015 from 10.0.2.2
	vagrant@ohana-api-dev-box:~$ cd /vagrant/
	vagrant@ohana-api-dev-box:/vagrant$ cd ohana-web-search-madrid/
	vagrant@ohana-api-dev-box:/vagrant/ohana-web-search-madrid$ script/setup_heroku -a socisalud-madrid
	-o https://ohana-api-madrid.herokuapp.com/api/
	-bash: script/setup_heroku: /bin/sh^M: bad interpreter: No such file or directory
	vagrant@ohana-api-dev-box:/vagrant/ohana-web-search-madrid$ heroku login
	Enter your Heroku credentials.
	Email: 
	Password (typing will be hidden):
	Authentication successful.
	vagrant@ohana-api-dev-box:/vagrant/ohana-web-search-madrid$ heroku config:set CANONICAL_URL=socisalu
	d-madrid.herokuapp.com --app socisalud-madrid
	Setting config vars and restarting socisalud-madrid... done, v3
	CANONICAL_URL: socisalud-madrid.herokuapp.com
	vagrant@ohana-api-dev-box:/vagrant/ohana-web-search-madrid$ heroku config:set DOMAIN_NAME=socisalud-
	madrid.herokuapp.com --app socisalud-madrid
	Setting config vars and restarting socisalud-madrid... done, v4
	DOMAIN_NAME: socisalud-madrid.herokuapp.com
	vagrant@ohana-api-dev-box:/vagrant/ohana-web-search-madrid$ heroku config:set OHANA_API_ENDPOINT=htt
	ps://ohana-api-madrid.herokuapp.com/api --app socisalud-madrid
	Setting config vars and restarting socisalud-madrid... done, v5
	OHANA_API_ENDPOINT: https://ohana-api-madrid.herokuapp.com/api
	vagrant@ohana-api-dev-box:/vagrant/ohana-web-search-madrid$ token=$(python -c 'import uuid; print uu
	id.uuid4()')
	vagrant@ohana-api-dev-box:/vagrant/ohana-web-search-madrid$ heroku config:set SECRET_TOKEN=$token --
	app socisalud-madrid
	Setting config vars and restarting socisalud-madrid... done, v6
	SECRET_TOKEN: (_not shown_)
	vagrant@ohana-api-dev-box:/vagrant/ohana-web-search-madrid$ heroku addons:create mandrill -a socisal
	ud-madrid
	Creating helping-stably-2562... done
	Adding helping-stably-2562 to socisalud-madrid... done
	Setting MANDRILL_APIKEY, MANDRILL_USERNAME and restarting socisalud-madrid... done, v7
	Use `heroku addons:docs mandrill` to view documentation.
	vagrant@ohana-api-dev-box:/vagrant/ohana-web-search-madrid$ heroku addons:create memcachier -a socis
	alud-madrid
	Creating grinning-patiently-3934... done
	Adding grinning-patiently-3934 to socisalud-madrid... done
	Setting MEMCACHIER_PASSWORD, MEMCACHIER_SERVERS, MEMCACHIER_USERNAME and restarting socisalud-madrid... done, v8
	Please allow up to three minutes for MemCachier credentials to sync.
	Use `heroku addons:docs memcachier` to view documentation.
	vagrant@ohana-api-dev-box:/vagrant/ohana-web-search-madrid$ git push heroku dev
```

Ugh, I don't know why, but heroku won't deploy neither my dev branch, nor the master branch (which is identical to codeforamerica/ohana-web-search)! I've saved the log file with the failed attempts at deployment and written to Moncef to see if he can help me figure it out. That's about all I can do for tonight, and hoping for good news tomorrow!


Tuesday, 19 May
---------------
It suddenly occurred to me when already in bed, that I had read something about an issue with deployment - but since I hadn't deployed ever, I didn't quite understand it or was able to remember the details. 

I looked into it first thing this morning, and HOORAY, it was the same problem I was having - and most importantly - the proposed fix worked for me too! So now we have a ohana web search working at: https://socisalud-madrid.herokuapp.com/

####Tasks today:####
- [x] New logo for the search page
- [x] Email to Greg
- [x] Documentation stuff for the project presentation tomorrow
- [x] Looking for more data to add - Familiy and infancy b/c it fits with other visualization in the project
- [x] New logo: SociSalud Madrid
- [x] Implemente info-box for Centros de dia!
- [x] Instead of populating the database with new data, I decided to improve the data already in there, both for it to be better formatted and more complete, and to know what works and what gives errors on import, for other, new data.
- [x] Get new data into the database:
	- [x] Update the information in the Google Spreadsheet
	- [x] Download the data in csv format with the rakefile script
	- [x] ```script/reset```
	- [x] ```script/import```
	- [x] ```script/export_prod_db```
	- [x] ```script/import_prod_db```
	- [x] ```heroku login```
	- [x] ```heroku config -a ohana-api-madrid```
	- [x] move production dump file to dropbox and get URL
	- [x] restore database from url: ```heroku pg:backups restore https://dl.dropboxusercontent.com/u/2754289/ohana-db/ohana_api_production.dump DATABASE -a ohana-api-madrid```
- DONE! New database in place! (Starting to get the hang of this! xD)

- Now: trying to fix things with the translation, I will probably have to extend the es.yml file beyond what was in the English one. I get this (ugly) error e.g.: "translation missing: es.time.am"
* Ok, made it work, by introducing changes to es.yml:
	- [x] Add time: am: '' ; pm: ''
	- [x] Change time format for regular schedule to ```schedules_hours: '%-H:%M'```

###Family and Youth Info###
- [x] Add several info-boxes for family and youth services
- [x] Add family and youth services to Google spreadsheet
- [x] Get new data into the database:
	- [x] Update the information in the Google Spreadsheet
	- [x] Download the data in csv format with the rakefile script
	- [x] ```script/reset```
	- [x] ```script/import```
	- [x] ```script/export_prod_db```
	- [x] ```heroku login```
	- [x] ```heroku config -a ohana-api-madrid```
	- [x] move production dump file to dropbox and get URL
	- [x] restore database from url: ```heroku pg:backups restore https://dl.dropboxusercontent.com/u/2754289/ohana-db/ohana_api_production.dump DATABASE -a ohana-api-madrid```
- DONE! New database in place! (Starting to get the hang of this! xD)
- Also SUCCESS, the info-boxes work well! Try them:
	- 'centros de día para mayores'
	- caf
	- cai
	- pef
	- 'centros de día para menores'


Wednesday, 20 May
-----------------
Last day of the workshop. I got everything up and running, and now what is missing is more data. I have been thinking about how to automate this, but I know it would take my several days, and I don't have the time to start that right now. The good news is however, that it can be done manually as well, using the Google Spreadsheet, so it doesn't have to be automated right now, anyone interested in taking this project further could continue with the data input until we have all that is available on the datos.madrid.es site. I think it wouldn't take more than a few days of dedicated work, or a few hours a day for a week(ish). 

Today I have been doing mostly wrap-up things - an interview for the exposition and giving feedback to Manuel on the prints. This afternoon I will prepare my part of our groups final talk, that will happen this afternoon. Now, I will look into hosting our project page on github. OK, Done! Our project page is now at http://medialab-prado.github.io/visualizar15-cityapi

Tasks:
- [x] Add myself as admin
- [x] Add myself as superadmin
- [x] Fix typo on front page (doh, hehe)


####Tasks, to-dos, from talks about how to take this project forward:####
- [x] Add Adolfo as superadmin at ohana-api-madrid.herokuapp.com
- [x] Add Lorena from Medialab Prado as admin
- [x] Add Lorena as superadmin at ohana-api-madrid.herokuapp.com
- [x] Clean up my ToDo list, only leave things yet to be done (i.e. 'for later' section)
- [x] Organize ToDo list into Technical tasks, Project Management, Data Input tasks
- [x] Write Lorena --> Meeting next week
- [x] Add to ToDo list, add remaining data from datos.madrid.es
- [x] Add to ToDo's, ask for help in where/how to translate the remaining words on the web page
- [ ] Go through this log book and distil instructions, orphan ToDo's and issues/fixes/pull requests to be filed to the different ohana projects.
- [x] Clean up the file directories
- [ ] Implement translation of admin interface
- [ ] Things needed: documentation in Spanish. E.g. translation of the FAQ on the Open Referral web page.
- [ ] Clean up github branches (?)


Thursday, 21 May
----------------
Although the workshop officially ended yesterday, I've come in to Medialab Prado today as well, to do some final wrap-up work and try to meet up with people here from Medialab Prado about the continuity of the project.

---

In the end it wasn't possible to meet today due to another meeting running over, so we've decided on meeting up sometime next week, and try to get all interested parties together. 

Tasks today:
- [x] Clean up my ToDo list, only leave things yet to be done (i.e. 'for later' section)
- [x] Read Greg's Madrid memo draft
- [x] Looked into changing over the ohana-api and socisalud-madrid apps to OpenShift instead of Heroku. Possible upsides would be *no credit card* (as I am a bit nervous about 'accidentally' being billed at Heroku, and that OpenShift is very welcoming to open source and open data initiatives. Downsides are that I'm not entirely sure I would manage to get it to work (no detailed instructions), Mandrill (e-mailing service) seems like it doesn't work (well?) on OpenShift, and that all the application names would have *my* user name in it, e.g.: socisalud-madrid.amsorribes.rhcloud.com  (which I guess would "look good" for me, but this project isn't about me, so having my username in the namespace feels a little wrong and extra cumbersome when demoing the Admin interface, API and web search to potentially interested parties). So for these reasons, I decided to stay on Heroku (and cross my fingers that I won't get billed..!).
- [x] Finished the new big ToDo list!
- [x] Clean up the file directories
- [x] Clean up github repos about the project (added several files to visualizar15-commoning-data, and deleted ohana-importer-madrid)







