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

..Giving up..
-------------
Going to ask for help, ideally if someone could set it up for me on heroku.

Uninstall:
- [x] Ruby
- [x] DevKit
- [x] PostgreSQL

(_Oh, my poor registry_..)



 