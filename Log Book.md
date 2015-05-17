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


Sunday, 17 May
--------------
After a few lovely days with friends visiting, it's back to work! The steps I am planning on taking are:
- [ ] Remove phone number formatting check
- [ ] Remove postal code formatting check
- [ ] Try to run and log into the admin interface to confirm that it is still working and didn't break
- [ ] Export the data I filled into the Google Spreadsheet template to csv
- [ ] Run the csv's through csvLint
- [ ] Put the csv's in the data folder
- [ ] Follow instructions on how to build the database

Some notes about the translation - after formatting the yml-files correctly (with help from a yml consistently check website), and several iterations of trying, I got it through the Ohana API start-up process without any errors or warnings. So, good to go I thought, until I logged into the admin interface and got (database?) errors which had not been there before. Decided that I will have to wait to get the translations working for now, will center on populating the database first of all, and then deal with getting the translations to work..




 