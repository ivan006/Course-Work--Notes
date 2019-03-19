Models - Defines the location of an entity types data
Controllers - Defines the associated templates for an entity type (templates for generating the view entity and edit entity pages)
Views - Defines the style of each of the entity types associated templates.

# Automation with Laravel

## <a name="1."></a>Chapter 1. Table of Content

- [1. Table of Content](#1.)
- [2. Introduction](#2.)
- Setup chapters
	- [3. Setting up the development tools](#3.)
	- [4. Setting up the Laravel powered app](#4.)
- Web app component chapters
	- [5. Database component](#5.)
	- [6. Routes component](#6.)
	- [7. Introduction to queries](#7.)
	- [8. Basic Queries](#8.)
	- [9. Queries with basic relationships](#9.)
	- [10. Queries with advanced relationships](#10.)
	- [11. Query Testing Environment](#11.)
	- [12. Accessors and mutators queries](#12.)
	- [13. Views component](#13.)
- [14. Real-World Examples](#14.)
  - [8.1. /5.1. Intro](#8.1)
  - [8.2. /5.2. Forms](#8.2)
  - [8.3. /5.3. Coming soon](##)
  - [8.4. /5.4. Coming soon](##)
  

## <a name="2."></a>Chapter 2. Introduction

### About
- This is a place for you to learn the ins and outs of Lary Wary (Laravel).
- Laravel is a kind of development tool more specifically it is a development framework.
- Please follow this course in the order laid out in the menu -  starting from "Introductions" and ending at "Views".
- Just your luck
   - You are very privileged to be able to see this course.
   - All are welcome to venture into the land of milk and honey!

### Credits
- This course is based on a video course on Udemy.com which can be found here - [Laravel for beginners](https://www.udemy.com/php-with-laravel-for-beginners-become-a-master-in-laravel/)


##<a name="3.d"></a>3. Settup

### <a name="3."></a>Chapter 3.1 Development Tools
#### Table Of Content

- [For Windows](#For_Windows)
  - [Virtual Local Server (VLS)](#Virtual_Local_Server)
  - [Package Installation Manager ](#Package_Installation_Manager)
  - [IDE](#IDE)
  - [Database Manager](#Database_Manager)
- [For Ubuntu](#For_Ubuntu)
  - [Local Server](#Local_Server)
  - [Package Installation Manager ](#Package_Installation_Manager_2)
  - [IDE](#IDE_2)
  - [Database Manager](#Database_Manager_2)


#### <a name="For_Windows"></a>For Windows
##### <a name="Virtual_Local_Server"></a>Virtual Local Server (VLS)

- This VLS system comprises of 5 parts.
  - VLS Terminal
  - VLS Engine
  - VLS Content Location
  - VLS Configuration Manager
  - VLS Configuration Package
  - VLS Environment
- VLS Terminal
	- Intro
		- Purpose: An interface to the virtual server
		- Name: Git Bash
	- Installation
		- [Git Bash](https://git-scm.com/download/win).
- VLS Engine
	- Intro
		- Purpose: Used to run the virtual server
		- Name: VirtualBox
	- Installation
		- [Virtual Box](https://www.virtualbox.org/wiki/Downloads) (then click "windows hosts").
		- Then edit your environment variables:
		  - Orientate yourself to `Control Panel\System and Security\System`
		  - Click `Advanced System Settings` and `Environment Variables`
		  - Click `User variables for Person > Path`
		  - Edit `Variable value`
		    - Add this to the beginning `C:\Program Files\Oracle\VirtualBox;`
- VLS Content Location
	- Make this folder: `c:/laravel-apps`
- VLS Configuration Manager
	- Intro
		- Purpose: Used to help configure our virtual server
		- Name: Vagrant
	- Installation
		- [Vagrant](https://www.vagrantup.com/downloads.html).
- VLS Configuration Package (Known as a "Box")
	- Intro
		- Purpose: Used to configure our virtual server so that it can facilitate the specified framework.
		- Name: Laravel Homestead
	- Installation
		- For Very Fast Connections:
		  - The file is about a gig.
		  - Open a new instance of Git Bash and run this `vargant box add laravel/homestead`.
		  - When prompted enter `2` for virtualbox installation type.
		- For Normal Connections:
		  - Installer Downloading
		    - The file is about a gig.
		    - Go to https://app.vagrantup.com/boxes/search
		    - Search for `Laravel` and choose Homestead by Laravel
		    - Either click the latest version or a version you want (only version 6 and above is able to have it's PHP version switched, which will be necessary).
		    - Then prepend the URL link with this `/providers/virtualbox.box`
		  - Installation
		    - Rename the downloaded file to `virtualbox.box`.
		    - Use Git Bash to install it
		      - By running this command `vagrant box add laravel/homestead file:///C:/Users/Ivan/Downloads/virtualbox.box`.
		    - Download  [metadata_url](https://abbasharoon.me/metadata_url) (right click this link and say "save link as"), remove its file extension and move it to your newly formed folder           
		    `%USERPROFILE%\.vagrant.d\boxes\laravel-VAGRANTSLASH-homestead`.
		    - In this same location rename the directory named “0” to the same number as the version of the box that that you installed
		      - E.g. ```6.1.0```.
	- Uninstallation
		- `vagrant box remove laravel/homestead --box-version=6.2.0`
		- Configure the box number version to your case
- VLS Environment
	- Installation
		- Part 1 (ssh keys)
			- Open a new instance of Git Bash, locate yourself with `cd .ssh/` and the run `ssh-keygen -t rsa -b 4096 -C "your@email.com"` replace the email here with your email.
			- When prompted for more detail just click enter each time (without entering any details) until it says that the keys have been "saved".
		- Part 2 (Homestead folder)
			- Open Git Bash, locate yourself with this command `cd c:`
			- Run this command `git clone https://github.com/laravel/homestead.git Homestead`.
			- From windows explorer run this file `C:\Homestead\init.bat`.
			- Homestead.yaml
			  - In this file `C:\Homestead\Homestead.yaml` configure this attributes
			     - folders:
				- \- map: `C:\laravel-apps`
		- Part 3 (homestead-7 folder)
		  - Orientate yourself to `cd c:/Homestead` and then run the command `vagrant up`
		    - Note if you are not using the latest version of Homestead you might need to clarify that
			- In the `homestead.rb` file
				- Location: - `C:\Homestead\scripts`
				- Edit: Change the version number in this line `config.vm.box_version = settings['version'] ||= '>= 6.3.0'`
			- And in the `homestead.yaml` file in the folder `C:\Homestead`
		  - If this doesn't work the first time restart Git Bash and try again.
		  - When the first launch has complete run the command `vagrant halt`
	- Uninstallation (if ever you need to)
		- Part 1 (homestead-7 folder)
			- Get environment ID by running `vagrant global-status` and checking the ID code of the specific environment
			- Run `vagrant destroy 1a1a1a1a` (replace `1a1a1a1a` with the environment ID)
		- Part 2 (Homestead folder)
			- Delete the `Homestead` folder inside `C:`
		- Part 3 (ssh keys)
			- Go to `%USERPROFILE%\.ssh`
			- Manually delete it's contents
	- Operation
		- Please note: In later sections of this course you will be editing source code for that you will need to make sure Laravel Homestead is open and to save computer resources close it when your not working.
		- Open - using Git Bash locate yourself with `cd c:/Homestead` and then run the command `vagrant up` (executing this may take a while).
		- Close - using Git Bash locate yourself with `cd c:/Homestead` and then run the command `vagrant halt`
		- Check status
		  - This just tells you if the virtual machine is running or not.
		  - Using Git Bash locate yourself with `cd c:/Homestead` and then run `vagrant global-status`.
		- Provision
		  - Orientate yourself to `cd c:/Homestead` then `vagrant up` then `vagrant provision` then if you want `vagrant halt`
		- Troubleshoot
		  - If at some point you get the message `No input file selected` either
		    - Restart homestead
		    - Provision homestead
##### <a name="Package_Installation_Manager"></a>Package Installation Manager </summary>
- We will be using Composer

- Installation
	- Installation: [Composer](https://getcomposer.org/download/)
- Operation
	- Composer functions are used through a command line interface.
- Extensions
	- Laravel Installer
		- Add the globally available "create new Laravel project" command to composer
		  - open a new instance of Git Bash and run ```composer global require "laravel/installer"```.

##### <a name="IDE"></a>IDE
- An IDE is just a souped-up code editor. The IDE we will use is called Atom. Alternatively we suggest Microsoft Visual Studio
- Core
	- Google `Atom`, download installer and install.
- <a name="Plugins/Extra_Features"></a> Plugins/Extra Features
	- Custom Code Snippets
		- Intro
		  - Code Snippets enable you to create a custom library of commonly used code samples.
		  - This means that instead of writing a full block of code (for instance `Hello Jack. How are you today?`) you can just use a shortcut (e.g. `greet` then tab key)
		- Usage
		  - Many IDEs support this either as a built-in extra feature or as an optional plugin (just search online for your IDE's variant)
		  - If your using Atom
		  - Atom Snippets comes as a built-in extra feature
		  - In atom orient yourself to the snippets settings file with `File > Snippets`
		  - At the bottom of the file add this code
		  ```
		    '.php':
		    'Greeting for php':
		    'prefix': 'greet'
		    'body': 'Hello $1. How are you today?'
		  ```
		    - Line 1: Type of code
		    - Line 2: Name
		    - Line 3: Shortcut
		    - Line 4: Sample
		    - $1, $2.. etc: Is for the cursor position (press tab to go to the next position)
		    - For multi lines samples wrap the code in two sets of these `'''`
		  - To make multiple snippet for the same code type you must structure it like this
		  ```
		    '.php':
		    'Greeting for php':
		    'prefix': 'greet'
		    'body': 'Hello $1. How are you today?'
		    'Greeting for php2':
		    'prefix': 'greet2'
		    'body': 'Hello $1. How are you today2?'
		  ```
	- Setup to work with `.blade.php`
		- To make it work with `blade` file you must install the blade syntax highlighter plugin called `language-blade` (then restart Atom)
	- Blade Snippet Library
		- This may also be useful (if your using Atom search for `blade-snippets`)
	- Laravel Snippets
		- This may also be useful (if your using Atom search for `Laravel`  by Cronos87)

##### <a name="Database_Manager"></a> Database Manager
- General: We will be using MySQL Workbench this is a MySQL tool which allows you to manage databases.
- Note: A homestead connection wont work if you have not launched your local server.
- Install: Download installer from here [https://www.mysql.com/products/workbench/](https://www.mysql.com/products/workbench/).
- Configuration
  - Setup Connection
    - General: Note that if this doesn't work the first time close the connection and try again.
    - Launch MySQL Workbench and by default you will be on the welcome page which shows the message `Welcome to MySQL Workbench`
    - Click the plus symbol in the page.
    - In the popup configure these attributes
      - Connection Name: `Local_Server`
      - Connection Method: Standard TCP/IP over SSH
      - SSH Hostname: your SSH Hostname
        - To find out what your SSH Hostname is do this:
          - Launch vagrant
          - Check the load message for a field called `SSH address` the value here is your SSH Hostname. Copy it.
      - SSH Username: `vagrant`
      - SSH Password: click store in vault then enter `vagrant`
      - MySQL Hostname: `localhost`
      - Username: `homestead`
      - Password: click store in vault then enter `secret`
    - Then your connection will be saved to the welcome page.
  - Reposition tools - Schemas tool bar
    - Run the connection
    - In the sidebar locate the schemas tool bar
    - Click its expand/collapse toggler
    - Now is will be nice and visible
- Operations
  - To open MYSQL WorkBench launch it from its launch icon.


#### <a name="For_Ubuntu"></a>For Ubuntu
##### <a name="Local_Server"></a>Local Server



- Installation and Configuration
	- Ubuntu
		- I recommend
		  - Organize a new internal hard-drive
		  - Learn how to switch it with your old hard-drive
		  - Turn off your PC and switch them
		  - Install Ubuntu onto the new drive, this will delete everything that was on the drive
	- Ngine X
		- Install
		  - `sudo apt install nginx`
		  - Type `Y` then enter
		- Configurations
		  - Uninstall apache
		    - `sudo apt autoremove apache2*`
		- Test `nginx -v`
	-PHP
		- Install
		```
		  sudo apt-get install python-software-properties
		  sudo add-apt-repository ppa:ondrej/php
		  sudo apt-get update
		  sudo apt-get install -y php7.2
		```
		- Extras
		  - For using it with Laravel
		    ```
		      sudo apt install php7.2-zip php7.2-mbstring php7.2-json php7.2-gd php7.2-mysql php7.2-xml
		    ```
	- MySQL
		- Install `sudo apt install mysql-client mysql-server mysql-common`
		- Configure - Get connection to DB server by making a user account
			- Open MySQL as admin - run `sudo mysql`
			- Set account details `GRANT ALL PRIVILEGES ON *.* TO 'user'@'localhost' IDENTIFIED BY 'password';`
			- exit MySQL - run `exit`
	- App folder
		- Make this folder: `Documents/Multimedia/laravel-apps`
- Operation
	- Run server orientate yourself in the terminal to your app inside `laravel-apps` and the run `php -S localhost`
	- After completion close the server - press `ctrl+C`


##### <a name="Package_Installation_Manager_2"></a>Package Installation Manager </summary>
- We will be using Composer

- Installation
	- Method 1
		- Run `sudo apt install composer`
		- enter your desktop password`
	- Method 2: [Composer](https://getcomposer.org/download/)
- Operation
	- Composer functions are used through a command line interface.
- Extensions
	- Laravel Installer
		- Add the globally available "create new Laravel project" command to composer
		  - open a new instance of Git Bash and run ```composer global require "laravel/installer"```.

##### <a name="IDE_2"></a>IDE
- An IDE is just a souped-up code editor. The IDE we will use is called Atom. Alternatively we suggest Microsoft Visual Studio
- Core
	- Go to `https://atom.io/`
	- Download .deb installer
- Plugins/Extra Features
	- See the Window option's section of the same name [Plugins/Extra Features](#Plugins/Extra_Features)


##### <a name="Database_Manager_2"></a> Database Manager
- General: We will be using MySQL Workbench this is a MySQL tool which allows you to manage databases.
- Note: A homestead connection wont work if you have not launched your local server.
- Installation
  - `sudo apt install mysql-workbench`
  - Click yes
- Test
  - Press start key and type workbench
- Configurations
  - Make new connection called `local` to your DB server using your database user details
- Operations
  - To open MYSQL WorkBench launch it from its launch icon. 


### <a name="4."></a>Chapter 3.2 Laravel Powered App
#### Table Of Content


- [General](#General)
- [Source Code](#Source-Code)
- [Database](#Database)

#### <a name="General"></a>General
##### Laravel Overview
- Laravel is something you install on an app by app basis.
- It determines the architecture of your apps source code and provides it with lots of useful prebuilt functions.

##### PHP artisan
- Other that all the fundamental mechanisms that we will cover in later sections you will also have access to a set of command line functions called PHP artisan.
- These commands are helpful and can assist you while you build your application.



#### <a name="Source-Code">Source Code</a>

##### Using Windows

- Installation
	- In Git Bash locate yourself using ```cd c:/laravel-apps```
	- Decide on your project name e.g. `fundamental-mechanisms-app` (this is the example name because in the next section we will be practicing using what we call fundamental mechanisms)
	- Decide if you want the latest version or and older versions
	  - For latest do this
	     - Run `composer create-project --prefer-dist laravel/laravel`. And if you have the Laravel extension for composer you can even use `laravel new fundamental-mechanisms-app`
	  - Or for old version do This
	     - Run ```composer create-project --prefer-dist laravel/laravel fundamental-mechanisms-app 5.2.29``` for specific version (in this case version 5.2.29).
	     - If you get an error try first restarting Git Bash.
- Configurations
	- Map it in Homestead - to do this you will need to update this file `Homestead.yaml`, which is located in either `C:\Homestead\resources\` or `C:\Homestead\`
	   - Configure these attributes
	      - sites:
		 - \- map: ```fundamental-mechanisms-app.test```
		 - to: ```/home/vagrant/code/fundamental-mechanisms-app/public```
	   - For multiple project running in parallel do This
	      - Duplicate the above mentioned set of attributes and configure like this
	      ```
		sites:
		    - map: fundamental-mechanisms-app.test
		      to: /home/vagrant/code/fundamental-mechanisms-app/public
		    - map: fundamental-mechanisms-app2.test
		      to: /home/vagrant/code/fundamental-mechanisms-app2/public
	      ```
	- Map it in your host file
	   - Using windows explorer locate yourself to here ```C:\Windows\System32\drivers\etc\```
	   - Temporarily move the ```host``` file to your desktop.
	   - Open the host file in a code editor and configure it so it's contents ends with (to run multiple projects duplicate one of these code lines and configure).
	   ```
	   192.168.10.10 laravel.test
	   192.168.10.10 homestead.test
	   192.168.10.10 fundamental-mechanisms-app.test
	   ```
	   - Move it back into it's original location ```C:\Windows\System32\drivers\etc\```.
	- Provision homestead
	    - Run homestead - run `cd c:/Homestead` and then `vagrant up`
	    - Run the command ```vagrant provision```.
- PHP version
	- Check
	  - Add this to your routes (see how in later sections) and
	  ```
	    Route::get('/phpversion', function () {
	      echo phpversion();
	    });
	  ```
	  - Then open the corresponding page in your browser
	- Change
	  - Open `Homestead.yaml`
	  - Add and set a php field in your site configurations. The versions available to use are limited to "5.6", "7.0", "7.1", "7.2" and "7.3" ("7.3" is default)
	   ```
	     sites:
		 - map: fundamental-mechanisms-app.test
		   to: /home/vagrant/code/fundamental-mechanisms-app/public
		   php: "5.6"
	   ```
	   - Provision homestead - Orientate yourself to `cd c:/Homestead` then `vagrant up` then `vagrant provision` then if you want `vagrant halt`
- Testing
	- Run your local server. Open your browser and enter the URL   ```fundamental-mechanisms-app.test/``` and see if a page opens with the text "Laravel".
	- After completion close Homestead - run `vagrant halt`
- Patches
	- Foreach loop error
	  - Cause
	    - Software incompatibility: If you are running a version  of PHP that is higher than 7.1 with a version of Laravel that is lower than 5.6 you will get this error
	    - Test your PHP and Laravel versions, here's how
	      - Oriented yourself with `cd C:/laravel-apps/fundamental-mechanisms-app`
	      - Run `php artisan --version` and `php -v`
	  - Fix
	    - Option 1
	      - Go to `vendor\laravel\framework\src\Illuminate\Database\Eloquent\Builder.php` (eloquent builder file)
		- Replace this: `$originalWhereCount = count($query->wheres);`
		- With this: `$originalWhereCount = is_null($query->wheres) ? 0 : count($query->wheres);`
	    - More info
	      - This error shows when you try to run certain types of foreach loops and looks like this `count(): Parameter must be an array or an object that implements Countable`
	      - See more at  https://stackoverflow.com/questions/48343557/count-parameter-must-be-an-array-or-an-object-that-implements-countable
	    - Option 2
	      - If your using Laravel version `5.2.29` revert your php version to `5.6`

##### Using Ubuntu
- Installation
	- In terminal orientate yourself to `laravel-apps`
	- Decide on your project name e.g. `fundamental-mechanisms-app` (this is the example name because in the next section we will be practicing using what we call fundamental mechanisms)
	- Decide if you want the latest version or and older versions
	  - For latest do this
	     - Run `composer create-project --prefer-dist laravel/laravel`.
	  - Or for old version do This
	     - Run ```composer create-project --prefer-dist laravel/laravel fundamental-mechanisms-app 5.2.29``` for specific version (in this case version 5.2.29).
	     - If you get an error try first restarting terminal.
- Testing
	- Run your local server. Open your browser and enter the URL `127.0.0.1` and see if a page opens with the text "Laravel".


#### <a name="Database">Database</a>
##### Installation
  - Create new DB
    - Launch MySQL WorkBench then and open your server environments connection
    - Click on the "new schema" symbol and
    - Decide on a database name (we recommend using the same name as your app) `fundamental-mechanisms-app`.

##### Configurations
- Configure .env file
	- If using Ubuntu
	  - DB_HOST= `127.0.0.1`
	  - DB_DATABASE= `fundamental-mechanisms-app`
	  - DB_USERNAME= [your username]
	  - DB_PASSWORD= [your password]
	- If using Windows
	  - DB_HOST= `192.168.10.10`
	  - DB_DATABASE= `fundamental-mechanisms-app`
	  - DB_USERNAME= `homestead`
	  - DB_PASSWORD= `secret`
- A note on security
	- The database.php file (location in the `config` folder) is used to connect to the DB.
	- But since the database login info may be sensitive it is not kept in that file.
	- Rather there are two extra files: A `.env` file and a `.env.example` file.
	- The `.env` file is used to store the database logins which the database.php file can reference to make the connection.
	- This is so that when sharing your app with other people, say if they want to have their own implementation of your app, then you can ensure your databases security.
	- This is done by leaving the `.env` file out and getting the recipient to set up their own `.env` file as per there own database settings.
	- They will still have access to the `.env.example` file which they can use to see how to structure their `.env` file.

##### Testing
- Run `cd C:/laravel-apps/fundamental-mechanisms-app` then `php artisan tinker`
- Run
`DB::connection()->getPdo();`
- If it says Unknown database then your have failed to connect
- If it shows an array called `PDO` then you managed to connect.
- To re-test first exit and re-enter tinker by running `exit` and then `php artisan tinker`
- When your done run `exit`



## <a name="5."></a>Chapter 4. Database component 

### Table Of Content
- [Database](#Database)


### General
- Definition
  - A database is where we store our "raw data" which we can display into more easy to understand report like pages. The data can be considered as raw as it has no style yet added to it.


### Managing Tables - Using Migrations
#### General
- Definition: Migrations help you to create your db tables easier.
- You get two different types of migrations
  - Table migrations that are for creating entire tables with multiple columns
  - Column migrations for adding ad hoc columns to tables that are already created
- Migration files are located here: `C:\laravel-apps\fundamental-mechanisms-app\database\migrations`
- Migration files contain migration column action functions which basically specify the details of the columns your want to create
  - E.g. `$table->string('example_column');`
- These are different depending on the column type you want to use
  - For strings (short line of text)
    - `$table->string('example_column');`
  - For text (long block of text)
    - `$table->text('example_column_2');`
  - For a column with further configurations you can append the code line with a function, for instance
    - `$table->string('example_column')->unique();`
- Artisan commands
  - To see all the artisan commands
    - In Git Bash locate yourself with `cd C:/laravel-apps/fundamental-mechanisms-app`
    - Run `php artisan`
  - Migration specific
    - Activate the migrations
      - In Git Bash locate yourself with `cd C:/laravel-apps/fundamental-mechanisms-app`
      - Run `php artisan migrate`
    - Deactivate the migrations
      - In Git Bash locate yourself with `cd C:/laravel-apps/fundamental-mechanisms-app`
      - Run `php artisan migrate:reset`
    - Deactivate recently activated migrations
      - In Git Bash locate yourself with `cd C:/laravel-apps/fundamental-mechanisms-app`
      - Run `php artisan migrate:rollback`
    - Refresh all the migrations
      - Combing the effect of deactivating and then activating the migrations causes the tables to loose all their records.
      - In Git Bash locate yourself with `cd C:/laravel-apps/fundamental-mechanisms-app`
      - Run `php artisan migrate:refresh`
    - Check the migrations activation status
      - In Git Bash locate yourself with `cd C:/laravel-apps/fundamental-mechanisms-app`
      - Run `php artisan migrate:status`
- See more info here: [https://laravel.com/docs/5.6/migrations#columns](https://laravel.com/docs/5.6/migrations#columns)

#### Handling Tables with a Migrations
- Create a table with a migration
  - Example
    - Setup the migration
      - Create migration
        - Choose the table name - make it uses underscores for spaces and ends with an "s"
        - In Git Bash locate yourself with `cd C:/laravel-apps/fundamental-mechanisms-app`
        - Run `php artisan make:migration example_objects --create="example_objects"`
      - Add a column function to the migration
        - Choose the column's names and types (e.g. string or text etc.)
        - Open the migration file in a code editor. Locate the schema function in your migration's up method.
        - Add the functions so this is the result
        ```
          Schema::create('example_objects', function (Blueprint $table) {
              $table->increments('id');
              $table->timestamps();
              $table->string('example_column');
              $table->text('example_column_2');
          });
        ```
    - Activate the migrations
      - In Git Bash locate yourself with `cd C:/laravel-apps/fundamental-mechanisms-app`
      - Run `php artisan migrate`

#### Handling Columns with a Migration
- General: These allow you to add columns to tables without interrupting the tables content/records that are already created
- Create a column with a migration
  - Example
    - Setup
      - Create migration
        - In Git Bash locate yourself with `cd C:/laravel-apps/fundamental-mechanisms-app`
        - Decide on a migration name.
        - Run `php artisan make:migration migration_name --table="example_objects"`
      - Add a column function to the migration
        - Open the migration file in a code editor.
        - Locate the schema function in your migration's up method
        - Here you will add a new line of code
        - For example
        ```
          Schema::table('example_objects', function (Blueprint $table) {
              $table->integer('example_column_3')->unsigned();
          });
        ```
      - Add a column deletion function to the migration
        - Open the migration file in a code editor.
        - Locate the schema function in your migration's down method
        - Here you will add a new line of code
        - For example here I am adding two custom columns
        ```
          Schema::table('example_objects', function (Blueprint $table) {
              $table->dropColumn('example_column_3');
          });
        ```
    - Use - Activate the migration

#### Deleting Migrations
- Unfortunately deleting a migration is quite hard
  - You cannot delete a migration without first deactivating it
  - Which you can do either by using
    - deactivate all migrations or by using
    - deactivate recent migrations
    - which will delete either all or some of your db content.  
  - After that you can delete the migration and then reactivate the migrations again.
  - If after that you try to create new migrations but get this error
  ```
  [ErrorException]
  include(blabla): failed to open stream: No such file or directory
  ```
  then solve it by running this in git bash `composer dump-autoload`
  

## <a name="6."></a> Chapter 5. Route component

### Table Of Content
- [Routes](#routes)
  - [Route Parameters](#Route-cont.-Route-Parameters)

### General
- Routes are kind of like "request handlers". This is because they define what certain URL requests do.
- They are located in `C:\laravel-apps\fundamental-mechanisms-app\app\Http\routes.php`

#### <a name="Check-All-Route-Details"></a> Check All Route Details
- Once you've created some routes you can check their details
- In Git Bash locate yourself with `cd C:/laravel-apps/fundamental-mechanisms-app`
- Run `php artisan route:list`

### Route URL Path
- This defines the URL path (the bit of the URL that comes after the top level domain i.e. .com or .org).
- Example of use:  ```Route::get('/ExampleRoute', 'ExampleController@ExampleControllerMethod');```.


### Route Content
- This defines the page content.
- Again example of use (in this case it's ExampleController@ExampleControllerMethod): ```Route::get('/ExampleRoute', 'ExampleController@ExampleControllerMethod');```.

#### Route Content Types

- Functions
  - This references contents from the same file.
  ```
    Route::get('/ExampleRoute', function(){
      return "Hello world";
    });
  ```
  - Example:
  ```
    Route::get('/ExampleRoute', function(){
      return "Hello world";
    });
  ```
- Views
  - This references contents from a view file
  ```
    Route::get('/ExampleRoute', function () {
      return view('ExampleView');
    });
  ```
  - In this case from here:  `C:\laravel-apps\fundamental-mechanisms-app\resources\views\ExampleView.blade.php`.
  - When we demonstrate an example of this in a later section.
- Controller Methods
  - This references contents from a method inside a controller file
  ```
    Route::get('/ExampleRoute', 'ExampleController@ExampleControllerMethod');
  ```
  - In this case from this file `C:\laravel-apps\fundamental-mechanisms-app\app\Http\Controllers\ExampleController.php` and this method `ExampleControllerMethod`.
  - When we demonstrate an example of this in a later section.
- CRUD Controller Method Sets
  - This you use in accordance with a CRUD type controller (mentioned later).
  - This creates not 1 but a set of pages.
  - `Route::resource('/ExampleRoute', 'ExampleController');`
  - This will give your users access to all of the CRUD methods in the controller in the route content position. Check what they are by checking all your route's details (see how here [Check All Route Details](#Check-All-Route-Details)).
  - When we demonstrate an example of this in a later section.

### Routes Names
- Names can be used to abbreviate routes making it easier for developers to reference them.
- Basic Method
  - Add a bit of code to your route
  - E.g. ` Route::get('ExampleRoute/ExamplePart/ExamplePart', array('as'=>'Example.Route', function(){ return "Hello world!"; }));`
  - This gives this name `Example.Route` to this route `ExampleRoute/ExamplePart/ExamplePart`.
- CRUD Method
  - CRUD controller route by default have names defined. Check what they are by checking all your route's details (see how here [Check All Route Details](#Check-All-Route-Details)).


### <a name="Route-cont.-Route-Parameters"></a>Route Parameters
- General: Route parameters are variables that the user can define through the address bar.
- Usefulness: You could create an exchange rate page that displays the value of a certain amount of dollars converted to pounds. You would do this by letting users to type the preferred dollar amount somewhere in the address bar.
- Put `{ExampleParameter}` in the route URL
- Example:
```
  Route::get('/ExampleRoute4/{ExampleParameter}', function($ExampleParameter){
    return "Hello ".$ExampleParameter."!";
  });
```


## <a name="7."></a>Chapter 4.3.1. Introduction

### Table Of Content


- [Concepts](#Concepts)
- [Basic Setup](#Basic-Setup)
- [Integration with Route Parameters](#Integration-with-Route-Parameters)
- [SQL Queries](#SQL-Queries)


### <a name="Concepts"></a> Concepts
#### MVC
- MVC or rather PDR-MVC (page, database, route, model, view and controller)
- ![](https://raw.githubusercontent.com/ivan006/Blue-Gem-Education/master/Laravel-For-Beginners-Notes/MVC-pattern.png)
- MVC is a programming pattern.
- It's central parts are "models", "views" and "controllers", thus how it got it's name.
- MVC is commonly used nowadays.
- MVC enables us to among other things use developer friendly ORM queries, in the past however we simply used SQL queries.


#### Controllers

##### Definition and Location
- Definition:
  - A controller handles data - both raw database data and styling data. Styling data is stored in a type of file called a "view" which we will look at later.
  - A controller is where you write your ORM queries
- Location: They are located in `C:\laravel-apps\fundamental-mechanisms-app\app\Http\Controllers`

##### Controller Methods
- Controller are what make up controllers
```
  namespace App\Http\Controllers;
  use Illuminate\Http\Request;
  use App\Http\Requests;
  class ExampleController extends Controller
  {
      public function ExampleControllerMethod()
      {
        return "Hello wolrd!";
      }
  }
```

##### Types of Controller Methods
- The normal type of controller method will use both queries and a view
- But you can also set up a controller method that doesn't use queries (and so doesn't use any models or the database), and so any desired content you have to hardcode.
- Also you can set up a controller method that doesn't use a view, and so any desired styling you have to hardcode.

#### Models

##### Definition and Location
- Definition:
  - A model is a kind of "proxy" or "go between" for your raw data (database). This is because in MVC we don't directly handle data in the database but rather through our models. This allows easier handling.
  - A model is what makes, the easy to use, ORM queries possible it also can set limitations and freedoms on the types of queries possible for it's associated table.
- Location: `C:/laravel-apps/fundamental-mechanisms-app/app`.



###  <a name="Basic-Setup"></a> Basic Setup

#### Controllers
##### Plain Type
- These are come with no default code, so are quite hard to make.
- Using a code editor or windows explorer locate yourself to `C:\laravel-apps\fundamental-mechanisms-app\app\Http\Controllers`.
- Create a new php file, the name format should be camel case e.g. `ExampleController.php`.

##### Basic Type
- These come with some default code, so are easier to make.
- Using Git Bash locate yourself using  `cd C:/laravel-apps/fundamental-mechanisms-app`.
- `php artisan make:controller ExampleController`

##### CRUD Type
- These come with a lot of default code, so are the easiest to make.
- Using Git Bash locate to your project with `cd C:/laravel-apps/fundamental-mechanisms-app`
- Run `php artisan make:controller --resource ExampleController`, note the camel casing on the controller name.

#### Models
##### Just a Model
- Example
  - Note: this model will be required in the later sections
  - Create one
    - Choose a name - use  a camel cased version of the table name and remove the "s" from the end
    - Using Git Bash locate yourself using  `cd C:/laravel-apps/fundamental-mechanisms-app`.
    - Then run `php artisan make:model ExampleModel`
  - Configure it
    - Table specifier
      - If you didn't format the name of model or the table correctly you will have to specify what table the model refers to
      - To specify a table put this into your model's class `protected $table = 'example_table_model';`
    - Primary key specifier
      - If your tables primary key is not "id" you will need to specify it.
      - To specify the primary key put this into your model class `protected $primaryKey = 'id';`
  - Importing model into the routes
    - Option 1 - Model function (this you have to do every single time you want to us that model)
      - Put this inside the route `$example_variable = App\ExampleModel;`
    - Option 2 - Model usage function (this is once off so use this one to save time)
      - Put this at the beginning of your routes file `use App\ExampleModel;`




##### A Table-Model Pair
- General: Tables and models are rarely made independently so here's how to make them simultaneously.
- Using the Shortcut
  - Create the migration and the model at the same time
    - This is the shortcut
    - Choose the models name - use camel casing and do not end it with an "s" as this will be done automatically to your table only.
    - In Git Bash locate yourself with `cd C:/laravel-apps/fundamental-mechanisms-app`
    - Run `php artisan make:model ExampleModel -m`
  - Create the table with the migration
    - Finish sitting up the migration
      - Add a column function to the migration
        - Choose the column's names and types (e.g. string or text etc.)
        - Open the migration file in a code editor. Locate the schema function in your migration's up method.
        - Add these functions so this is the result
        ```
              $table->increments('id');
              $table->timestamps();
              $table->string('example_column');
              $table->text('example_column_2');
        ```
          - Note: when editing this be sure not to remove the default "id" and timestamps functions as they are always best to keep.
    - Activate the migrations
      - In Git Bash locate yourself with `cd C:/laravel-apps/fundamental-mechanisms-app`
      - Run `php artisan migrate`
  - Configure the model
    - Primary key specifier
      - If your tables primary key is not "id" you will need to specify it.
      - To specify the primary key put this into your model class `protected $primaryKey = 'id';`
    - Allowable multiple value inserts
      - Set model to allow multiple value inserts
      - Choose the values that need allowing
      - Put this into your model's class
      ```
        protected $fillable = [
          'example_column',
          'example_column_2',
          'example_column_3',
        ];
      ```
  - Importing model into the routes
    - Option 1 - Model function (this you have to do every single time you want to us that model)
      - Put this inside the route `$example_variable = App\ExampleModel;`
    - Option 2 - Model usage function (this is once off so use this one to save time)
      - Put this at the beginning of your routes file `use App\ExampleModel;`
- Without Using the Shortcut
  - Create a table with a migration
    - Setup the migration
      - Create migration
        - Choose the table name - make it uses underscores for spaces and ends with an "s"
        - In Git Bash locate yourself with `cd C:/laravel-apps/fundamental-mechanisms-app`
        - Run `php artisan make:migration example_TableModel --create="example_table_model"`
      - Add a column function to the migration
        - Choose the column's names and types (e.g. string or text etc.)
        - Open the migration file in a code editor. Locate the schema function in your migration's up method.
        - Add the functions so this is the result
        ```
          Schema::create('example_table_model', function (Blueprint $table) {
              $table->increments('id');
              $table->timestamps();
              $table->string('example_column');
              $table->text('example_column_2');
          });
        ```
    - Activate the migrations
      - In Git Bash locate yourself with `cd C:/laravel-apps/fundamental-mechanisms-app`
      - Run `php artisan migrate`
  - Setup a new model
    - Create one
      - Choose a name - use  a camel cased version of the table name and remove the "s" from the end
      - Using Git Bash locate yourself using  `cd C:/laravel-apps/fundamental-mechanisms-app`.
      - Then run `php artisan make:model ExampleModel`
    - Configure it
      - Table specifier
        - If you didn't format the name of model or the table correctly you will have to specify what table the model refers to
        - To specify a table put this into your model's class `protected $table = 'example_table_model';`
      - Primary key specifier
        - If your tables primary key is not "id" you will need to specify it.
        - To specify the primary key put this into your model class `protected $primaryKey = 'id';`
      - Allowable multiple value inserts
        - Set model to allow multiple value inserts
        - Choose the values that need allowing
        - Put this into your model's class
        ```
          protected $fillable = [
            'example_column',
            'example_column_2',
            'example_column_3',
          ];
        ```
  - Importing model into the routes
    - Option 1 - Model function (this you have to do every single time you want to us that model)
      - Choose the same model name as the one above
      - Put this inside the route `$example_variable = App\ExampleModel;`
    - Option 2 - Model usage function (this is once off so use this one to save time)
      - Choose the same model name as the one above
      - Put this at the beginning of your routes file `use App\ExampleModel;`

### <a name="Integration-with-Route-Parameters"></a> Integration with Route Parameters
- Put `{ExampleParameter}` in the route URL
- Put `$ExampleParameter` in the ExampleControllerMethod method of the controller class.
- Example:
  - Route
    - `Route::get('/ExampleRoute5/{ExampleParameter}', 'ExampleController@ExampleControllerMethod2');`
  - Controller
    ```
      public function ExampleControllerMethod2($ExampleParameter)
      {
        return "Hello ".$ExampleParameter."!";
      }
    ```
  - Test using: `fundamental-mechanisms-app.test/ExampleRoute5/example-parameter-string`.

### <a name="SQL-Queries"></a>  SQL Queries
- There are four types of database queries and the are abbreviated with "CRUD"
  - Create
  - Read
  - Update
  - Delete
- SQL means Structure Query Language
- SQL is a language for managing values in a database.

#### Create (Insert)
  - Use `DB::insert();`
  - Example:
    - Route
    ```
      Route::get('/ExampleRoute11', function(){
        DB::insert('insert into example_models(example_column, example_column_2, example_column_3) values(?, ?, ?)', ['example_value', 'example_value2', 1]);
      });
    ```

#### Read
  - Use `DB::select();`
  - Example:
    - Route
    ```
      Route::get('/ExampleRoute12', function(){
        $example_variable = DB::select('select * from example_models where example_column  = ?', ['example_value']);
        return "<pre>".var_dump($example_variable)."</pre>";
      });
    ```

#### Update
  - Use `DB::update();`
  - Example:
    - Route
    ```
      Route::get('/ExampleRoute13', function(){
        $example_variable = DB::update('update example_models set example_column  = ? where example_column = ?', ['example_value2', 'example_value3']);
        return $example_variable;
      });
    ```

#### Delete
  - Use `DB::delete();`
  - Example:
    - Route
    ```
      Route::get('/ExampleRoute14', function(){
        $example_variable = DB::delete('delete from example_models where example_column = ?', ['example_value2']);
        return $example_variable;
      });
    ```

## <a name="8."></a> Chapter 4.3.2. Basic Queries

### Table Of Content


- [ORM Queries](#ORM-Queries)


### <a name="ORM-Queries"></a> ORM Queries



#### Query Types
##### Create types
- Insert record with one field value
  - Example
    - Route
    ```
      Route::get('/ExampleRoute15', function(){
        $example_variable = new ExampleModel;
        $example_variable->example_column = 'example_value4';
        $example_variable->save();
      });
    ```
- Insert record with multiple field values
  - Example
    - Route
    ```
      Route::get('/ExampleRoute16', function(){
        ExampleModel::create(['example_column'=>'example_value6', 'example_column_2'=>'example_value7', 'example_column_3'=>1]);
      });
    ```
    - Model
      - Make sure your model to allows this by configuring it like this, make sure all the relevant columns are listed in your model's class
      - Example
      ```
        protected $fillable = [
          'example_column',
          'example_column_2',
          'example_column_3',
        ];
      ```

##### Read types
- Find all records (and return a field's values)
  - Example
    - Route
    ```
      Route::get('/ExampleRoute17', function(){
        $example_variable = ExampleModel::all();
        foreach ($example_variable as $example_variable_part) {
            echo $example_variable_part->example_column."<br>";
        }
      });
    ```
- Find all records and sort by date created
  - Method 1
    - Route
    ```
      Route::get('/ExampleRoute17.1', function(){
        $example_variable = ExampleModel::latest()->get();
        foreach ($example_variable as $example_variable_part) {
            echo $example_variable_part->example_column."<br>";
        }
      });
    ```
  - Method 2
    - Route
    ```
      Route::get('/ExampleRoute17.2', function(){
        $example_variable = ExampleModel::orderBy('id', 'desc')->get();
        foreach ($example_variable as $example_variable_part) {
            echo $example_variable_part->example_column."<br>";
        }
      });
    ```
  - Method 3
    - Route
    ```
      Route::get('/ExampleRoute17.3', function(){
        $example_variable = ExampleModel::orderBy('id', 'asc')->get();
        foreach ($example_variable as $example_variable_part) {
            echo $example_variable_part->example_column."<br>";
        }
      });
    ```
- Find based on primary key (and return a field's values)
  - Example
    - Route
    ```
      Route::get('/ExampleRoute18', function(){
        $example_variable = ExampleModel::find(1);
        return $example_variable->example_column;
      });
    ```
- Find based on primary key (and return a field's values) or display an error
  - Example
    - Route
    ```
      Route::get('/ExampleRoute19', function(){
        $example_variable = ExampleModel::findOrFail(100);
        return $example_variable;
      });
    ```
- Find based on other conditions (and return a field's values)
  - Example
    - Route
    ```
      Route::get('/ExampleRoute19.5', function(){
        return $example_variable = ExampleModel::withTrashed()->orderBy('id','desc')->get();
      });
    ```
- Find based on other conditions (and return a field's values) or display an error
  - Example
    - Route
    ```
      Route::get('/ExampleRoute20', function(){
        $example_variable = ExampleModel::where('id','>',50)->firstOrFail();
        return $example_variable;
      });
    ```

##### Update types
- Update based on primary key
  - Example
    - Route
    ```
      Route::get('/ExampleRoute21', function(){
        $example_variable = ExampleModel::find(1);
        $example_variable->example_column = 'example_value5';
        $example_variable->save();
      });
    ```
- Update based on other conditions
  - Example
    - Route
    ```
      Route::get('/ExampleRoute22', function(){
        ExampleModel::where('id', 2)->where('example_column', 'example_value6')->update(['example_column'=>'example_value8', 'example_column_2'=>'example_value9']);
      });
    ```

##### Delete types
- Delete method 1
  - Note: this works only works when soft delete is not activated
  - Example
    - Route
    ```
      Route::get('/ExampleRoute23', function(){
        ExampleModel::find(2)->delete();
      });
    ```
- Delete method 2
  - Note: this works only works when soft delete is not activated
  - Example
    - Route
    ```
      Route::get('/ExampleRoute24', function(){
        ExampleModel::destroy(3);
      });
    ```
- Delete multiple
  - Example
    - Route
    ```
      Route::get('/ExampleRoute25', function(){
        ExampleModel::destroy([4,7]);
      });
    ```  
- Delete one or multiple based on condition
  - Example
    - Route
    ```
      Route::get('/ExampleRoute26', function(){
        ExampleModel::where('example_column','example_value6')->delete();
      });
    ```

##### Soft Delete Functionality
- General
  - Records that are deleted softly are not properly deleted but they wont display when functions like `findAll` are run.
  - Activate soft delete
    - Examples
      - Model
        - General
          - File - All of the following functions must go in the same file with this name `ExampleModel`
        - Function 1
          - Make sure this function is at beginning of the file just after a similar one but outside the class `use Illuminate\Database\Eloquent\SoftDeletes;`
        - Function 2
          - Make sure this function is at beginning of the class `use SoftDeletes;`
        - Function 3
          - Make sure this function is at beginning of the class but after the "use" functions `protected $dates = ['deleted_at'];`
      - Database
        - Add a new column handling migration called `deleted_at` with an associated table of `example_models`.
        - Edit the new migration    
          - Locate and open the files
          - In the  `up` moethod write `$table->softDeletes();`
          - In the `down` method write `$table->dropColumn('deleted_at');`
- Soft Delete
  - Example
    - Route
    ```
      Route::get('/ExampleRoute27', function(){
        ExampleModel::find(7)->delete();
      });
    ```
- Read Items That Have Been Soft Deleted
  - Find all records
    - Example
      - Route
      ```
        Route::get('/ExampleRoute27.5', function(){
          $example_variable = ExampleModel::withTrashed()->get();
          foreach ($example_variable as $example_variable_part) {
              echo $example_variable_part."<br>";
          }
        });
      ```
  - Find all trashed
    - Example
      - Route
      ```
       Route::get('/ExampleRoute28', function(){
         $example_variable = ExampleModel::onlyTrashed()->get();
         return $example_variable;
       });
      ```
- Restore All Soft Deleted items
  - Example
    - Route
    ```
      Route::get('/ExampleRoute29', function(){
        ExampleModel::onlyTrashed()->restore();
      });
    ```
- Normal Delete All Soft Deleted Items (While Soft Delete is Activated)
  - Example
    - Route
    ```
      Route::get('/ExampleRoute30', function(){
        ExampleModel::onlyTrashed()->forceDelete();
      });
    ```
    - First make sure record with id 6 is soft deleted again (using exampleroute27) before running this

####  Query Scope
- Example Model
  - Route
  ```
    Route::get('/30.1', function(){
      $example_variable = ExampleModel::latest();
      foreach ($example_variable as $example_variable_part) {
          echo $example_variable_part->example_column."<br>";
      }
    });
  ```
  - Model
  ```
    public static function scopeLatest($query){
      return $query->orderBy('id', 'desc')->get();
    }
  ```


## <a name="9."></a> Chapter 4.3.3. Basic Relationships

### Table Of Content

- [Basic Relationships](#Basic-Relationships)
  - [One to One Relationship](#One-to-One-Relationship)
  - [One to Many Relationships](#One-to-Many-Relationships)
  - [Many to Many Relationships](#Many-to-Many-Relationships)

### <a name=""></a> Basic Relationships

#### <a name=""></a> Basic Relationships

##### <a name="General-2"></a> General
- This section covers ORM queries that use tables that have interrelationships. Tables can be related like for instance records in one table can give further information about a record in another table. There are many different types of relationships though and here you'll see how to use them.




##### <a name="One-to-One-Relationship"></a> One to One Relationship
- Prerequisites
  - Parent model
    - Set Up a New Table and Model Using the Shortcut (as previously demonstrated) - use these specs
      - Table name `example_parent_models`
      - Table columns
      ```
        $table->string('example_column');
        $table->text('example_column_2');
      ```
      - Model name `ExampleParentModel`
    - Add a parent model relationship column to the example model table.
      - Configure your example_models migration by adding this to your set of column functions `$table->integer('example_parent_model_id')->unsigned();`.
      - Refresh all the tables (as shown how in previous section)
    - Add a record to the example parent model table and make sure multiple field values are filled in (use the `insert record with multiple field values` method as previously demonstrated).
      - For the route
        - Name give your route `/ExampleRoute31`.
        - Use the model usage function `use App\ExampleParentModel;`
        - Make sure your route references the right model e.g. `ExampleParentModel::`
    - Model
      - Add one of the following code blocks to the parent model's model
      - Method 1 - Specify the column to refer to for the child model's parent model id column
      ```
        public funcion ExampleModel(){
          return $this->hasOne('App\ExampleModel', 'example_parent_model_id');
        }
      ```
        - So as you can see you do it in the `hasOne()` function's second parameter.
        - Also note your if your child  models's primary key column is not simple called `id` you can specify it as the third parameter.
      - Method 2 - Use default specifier which will be the parent model's name prepended with `_id` (also note that camel case `ExampleParentModel` converts to underscored `example_parent_model` and then obviously gets prepended `example_parent_model_id`)
      ```
        public funcion ExampleModel(){
          return $this->hasOne('App\ExampleModel');
        }
      ```
        - Add this in the model's class
        - Note the name of the function (in this case "ExampleModel") doesn't matter as long as we refer to it in our route correctly, but it is easiest to base its name on the table it references.
  - Child model
  ```
    public function ExampleParentModel(){
      return $this->belongsTo('App\ExampleParentModel');
    }
  ```
    - Add this in the model's class
- Basic Queries
  - Add a record to the example model table and make sure multiple field values are filled in.
    - Add model usage function to top `use App\ExampleParentModel;`
    - For the model: Add `example_parent_model_id` to the list fillable function list.
    - Route
    ```
      Route::get('/ExampleRoute32', function(){
        ExampleModel::create(['example_column'=>'example_value6', 'example_column_2'=>'example_value7', 'example_column_3'=>1, 'example_parent_model_id'=>1]);
      });
    ```
  - View child of parent
    - Route
        ```
          Route::get('/ExampleRoute33/{id}', function($id){
            return ExampleParentModel::find($id)->examplemodel;
          });
        ```
    - Test with `fundamental-mechanisms-app.test/ExampleRoute33/1`
  - View parent of child
    - Route
        ```
          Route::get('/ExampleRoute34/{id}', function($id){
            return ExampleModel::find($id)->exampleparentmodel;
          });
        ```
    - Test with `fundamental-mechanisms-app.test/ExampleRoute34/1`
- Full CRUD
  - Create through a relative
    - Route
      ```
      Route::get('/ExampleRoute34.1', function(){
        $example_variable = ExampleParentModel::findOrFail(1);
        $example_variable_2 = new ExampleModel(['example_column'=>'example_model_value', 'example_column_2'=>'example_model_value_2', 'example_column_3'=>1, 'example_parent_model_id'=>1]);
        $example_variable->ExampleModel()->save($example_variable_2);
      });
      ```
  - Read - we already did this, see "view" above
  - Update
    - Route
      ```
      Route::get('/ExampleRoute34.2', function(){
        $example_variable = ExampleModel::whereExampleParentModelId(1)->first();
        $example_variable->example_column = "example_model_value_2";
        $example_variable->save();
      });
      ```
  - Delete
    - Route
      ```
        Route::get('/ExampleRoute34.3', function(){
          $example_variable = ExampleParentModel::findOrFail(1);
          $example_variable->ExampleModel->forceDelete();
        });
      ```
      - If soft delete is not enabled then you can replace `forceDelete()` with `delete()`

##### <a name="One-to-Many-Relationships"></a> One to Many Relationships
- Prerequisites
  - Parent model
  ```
    public function ExampleModels(){
      return $this->hasMany('App\ExampleModel');
    }
  ```
    - Add this in the model's class
    - Regarding the function's name here we added use an "s" at the end to as it is a many relationship
  - Manage records: Add a second ExampleModel record by executing `/ExampleRoute32` again.
- Basic Queries
  - Read/view
    - Route
    ```
      Route::get('/ExampleRoute35', function(){
        $example_variable = ExampleParentModel::findOrFail(1)->examplemodels;
        foreach ($example_variable as $example_variable_part){
          echo $example_variable_part."<br>";
        }
      });
    ```
- Full CRUD
  - Read
    - Route
    ```
      Route::get('/ExampleRoute35.1', function(){
        $example_variable = ExampleParentModel::findOrFail(1)->examplemodels;
        foreach ($example_variable as $example_variable_part){
          echo "My ___$example_variable_part->example_column_2 ___ brings all the boys to the ___$example_variable_part->example_column ___ I can teach you but I have to charge.<br>";
        }
      });
    ```
  - Update
    - Route
    ```
      Route::get('/ExampleRoute35.2', function(){
        $example_variable = ExampleParentModel::findOrFail(2);
        $example_variable_2 = $example_variable->examplemodels()->whereId(9);
        $example_variable_2->update(['example_column'=>'i did it!']);
      });
    ```
  - Delete
    - Route
    ```
    Route::get('/ExampleRoute35.3', function(){
      $example_variable = ExampleParentModel::findOrFail(1);
      $example_variable_2 = $example_variable->examplemodels()->whereId(8)->first();
      $example_variable_2->delete();
    });
    ```

##### <a name="Many-to-Many-Relationships"></a> Many to Many Relationships

- General
  - This is useful for things like a user can have many rolls and a roll can be occupied by many users.
  - For this you need a pivot/lookup table.
- Setup
  - Relationship model
    - Setup its table and model - using the no shortcuts method. Just follow as previously demonstrated in `Set Up a New Table-Model Pair Without Using a Shortcut` and use the following specs
      - Table migration
        - Table name
          - The naming convention here is that:
            - Must be a combo of both of the associated table names
            - The order of the name combo must be in alphabetic order  
            - Use the singular version of the table names
            - E.g. `example_grandparent_model_example_parent_model`
        - Table columns
          - Foreign keys columns
            - The naming convention here is that:
              - They must be named according to the foreign tables the refer to and then have `_id` at the end.
            - E.g.
            ```
              $table->integer('example_parent_model_id');
              $table->integer('example_grandparent_model_id');
            ```
      - Model
        - Name
          - You can use a camel cased version of the table name.
          - E.g. `ExampleGrandparentModelExampleParentModel`
        - Table specifier: `example_grandparent_model_example_parent_model`
        - Allowable multiple value inserts
          - `example_parent_model_id`
          - `example_grandparent_model_id`
  - Grandparent model
    - Setup it up - just follow as previously demonstrated in `Set Up a New Table-Model Pair Using the Shortcut` and use the following specs
      - Migration
        - Tables name `ExampleGrandparentModel`
        - Table columns
        ```
          $table->string('name');
        ```        
      - Model
        - Allowable multiple value inserts
          - `name`
        - Grandparent model
          - Add this in the model's class
          ```
            public function ExampleParentModels(){
              return $this->belongsToMany('App\ExampleParentModel');
            }
          ```
  - Parent model
    - Parent model's model
      - Regarding the function's name here we added use an "s" at the end to as it is a many relationship
      - Short method
        - If the table pivot table name and it's foreign keys columns are named according to the convention then you can use this method.
        - Add this in the model's class
        ```
          public function ExampleGrandparentModels(){
            return $this->belongsToMany('App\ExampleGrandparentModel')->withPivot('created_at');
          }
        ```
      - Long method
        - Add this in the model's class
        - If the table pivot table name and it's foreign keys columns aren't named according to the convention then you must use this method.
        ```
          public function ExampleGrandparentModels(){
            return $this->belongsToMany('App\ExampleGrandparentModel', 'example_grandparent_model_example_parent_model', 'example_parent_model_id', 'example_grandparent_model_id');
          }
        ```
- Queries
  - Create
    - 2 grandparent records
      - Do as demonstrated in `insert record with multiple field values`
      - For the route name use: `/ExampleRoute38`
      - For the referenced model use `ExampleGrandparentModel`
      - E.g.
      ```
        Route::get('/ExampleRoute38', function(){
          ExampleGrandparentModel::create(['name'=>'example_value_1']);
          ExampleGrandparentModel::create(['name'=>'example_value_2']);
        });
      ```
    - Parents
      - 2 parent records
      ```
      Route::get('/ExampleRoute40', function(){
        ExampleParentModel::create(['example_column'=>'parent_example_value_1', 'example_column_2'=>'example_value_1']);
        ExampleParentModel::create(['example_column'=>'parent_example_value_2', 'example_column_2'=>'example_value_1']);
      });
      ```
    - 3 relationship records
      - Do as demonstrated in `insert record with multiple field values`
      - For the route name use: `/ExampleRoute36`
      - For the referenced model use `ExampleGrandparentModelExampleParentModel`
      ```
        Route::get('/ExampleRoute36', function(){
          ExampleGrandparentModelExampleParentModel::create(['example_parent_model_id'=>1, 'example_grandparent_model_id'=>1]);
          ExampleGrandparentModelExampleParentModel::create(['example_parent_model_id'=>2, 'example_grandparent_model_id'=>2]);
          ExampleGrandparentModelExampleParentModel::create(['example_parent_model_id'=>2, 'example_grandparent_model_id'=>1]);
        });
      ```
    - 2 relationship records through a parent and delete any old relationships for that parent
      - Bear in mind the IDs of the grandparent models that the relationships point to go in an inside the `sync` function
      ```
        Route::get('/ExampleRoute36.1', function(){
          ExampleParentModel::findOrFail(2)->ExampleGrandparentModels()->sync([2,3]);
        });
      ```
  - Read
    - Read parents of child
      - Type 1
      ```
        Route::get('/ExampleRoute41', function(){
          $example_variable = ExampleParentModel::find(2);
          foreach ($example_variable->examplegrandparentmodels as $example_variable_part){
            echo $example_variable_part->name."<br>";
          }
        });
      ```
      - Type 2
      ```
        Route::get('/ExampleRoute41.2', function(){
          $example_variable = ExampleParentModel::find(2);
          dd($example_variable->ExampleGrandparentModels);
        });
      ```
    - Read parental relationships of child
      - Parent model's route
        ```
        Route::get('/ExampleRoute42', function(){
          $example_variable = ExampleParentModel::find(2);
          foreach ($example_variable->examplegrandparentmodels as $example_variable_part){
            echo $example_variable_part->pivot->created_at."<br>";
          }
        });
        ```
    - Read children of parent
        - Route
        ```
          Route::get('/ExampleRoute43', function(){
            $example_variable = ExampleGrandparentModel::find(1);
            foreach ($example_variable->exampleparentmodels as $example_variable_part){
              echo $example_variable_part->example_column."<br>";
            }
          });
        ```
  - Update
    - Relationship through a parent record
    ```
      Route::get('/ExampleRoute43.1', function(){
        ExampleParentModel::findOrFail(2)->ExampleGrandparentModels()->attach(1);
      });
    ```
    - Grandparent through parent record
    ```
      Route::get('/ExampleRoute43.2', function(){
        $example_variable = ExampleParentModel::find(1);
        if($example_variable->has("ExampleGrandparentModels")){
          foreach($example_variable->ExampleGrandparentModels as $example_variable2){
            if($example_variable2->name == 'example_value_1') {
              $example_variable2->name = "example_value_10";
              $example_variable2->save();
            }
          }
        }
      });
    ```
  - Delete
    - Grandparent
      - 2 grandparent records
        - Just in case you create too many records u can delete them my using the delete query as demonstrated in `Delete method 2`
        ```
          Route::get('/ExampleRoute39', function(){
            ExampleGrandparentModel::destroy(3);
          });
        ```
      - Delete grandparent through parent
      ```
        Route::get('/ExampleRoute39.2', function(){
          $example_variable = ExampleParentModel::find(1);
          foreach($example_variable->ExampleGrandparentModels as $example_variable2){
            $example_variable2->whereId(1)->delete();
          }
        });
      ```
    - Relationship record
      - Delete 1 Method 1
      ```php
        Route::get('/ExampleRoute37', function(){
          ExampleGrandparentModelExampleParentModel::destroy(1);
        });
      ```
      - Delete 1 Method 2
      ```
        Route::get('/ExampleRoute37.1', function(){
          ExampleParentModel::findOrFail(2)->ExampleGrandparentModels()->detach(1);
        });
      ```
      - Delete all for parent
      ```
        Route::get('/ExampleRoute37.2', function(){
          ExampleParentModel::findOrFail(2)->ExampleGrandparentModels()->detach();
        });
      ```



## <a name="10."></a>Chapter 4.3.4. Advanced Relationships

### Table Of Content
- [Relationship with 2 Levels of Separation](#Relationship-with-2-Levels-of-Separation)
- [Polymorphic Relationships](#Polymorphic-Relationships)




### <a name="Relationship-with-2-Levels-of-Separation"></a> Relationship with 2 Levels of Separation
- General - prerequisites
  - Grandparent2 model
    - Setup it up - just follow as previously demonstrated in `Set Up a New Table-Model Pair Using the Shortcut` and use the following specs
      - Migration
        - Tables name `ExampleGrandparent2Model`
        - Table columns
        ```
          $table->string('name');
        ```        
      - Model
        - Allowable multiple value inserts
          - `name`
        - Relationship
        ```
          public function ExampleModels(){
            return $this->hasManyThrough('App\ExampleModel', 'App\ExampleParentModel');
          }
        ```
          - The first table specifier/parameter is for the distant relative
          - The second table specifier/parameter is for the intermediate relative
          - Then if the foreign id column in your intermediary table isn't the same name as the ExampleGrandparent2Model table (converted into camel case and without the "s" at the end) with ```_id``` at the end then you can put in a third parameter specifying its name.
          - Then if the foreign id column in your distant relative table isn't the same name as the intermediary table (converted into camel case and without the "s" at the end) with ```_id``` at the end then you can put in a forth parameter specifying its name.
    - Manage records
      - Create records
        - Route
          - Create 2 records
          - Do as demonstrated in `insert record with multiple field values`
          - For the route name use: `/ExampleRoute44`
          - For the referenced model use `ExampleGrandparent2Model`
          - E.g.
          ```
            Route::get('/ExampleRoute44', function(){
              ExampleGrandparent2Model::create(['name'=>'example_value_1']);
              ExampleGrandparent2Model::create(['name'=>'example_value_2']);
            });
          ```
      - Delete records
        - Just in case you create too many records u can delete them my using the delete query as demonstrated in `Delete method 2`
        ```
        Route::get('/ExampleRoute45', function(){
          ExampleGrandparent2Model::destroy(3);
        });
        ```
  - Parent model's new column
    - Setup it up
      - Migration - As seen in the section ```Handling Columns with a Migration```
        - Use the migration name of ```parent_model_example_grandparent2_model_id_column```
        - Use the table specifier of ```example_parent_models```.
        - Table columns
        ```
          $table->integer('example_grandparent2_model_id');
        ```
        - Then activate migration      
      - Parent model
        - Allowable multiple value inserts
          - `example_grandparent2_model_id`
    - Manage records
      - Create at least 2 records
      - To create 2 records
      ```
      Route::get('/ExampleRoute46', function(){
        ExampleParentModel::create(['example_column'=>'parent_example_value_1', 'example_column_2'=>'example_value_1', 'example_grandparent2_model_id'=>'1']);
        ExampleParentModel::create(['example_column'=>'parent_example_value_2', 'example_column_2'=>'example_value_1', 'example_grandparent2_model_id'=>'2']);
      });
      ```
      - To delete records
      ```
        Route::get('/ExampleRoute47', function(){
          ExampleParentModel::destroy(1);
          ExampleParentModel::destroy(2);
          ExampleParentModel::destroy(3);
        });
      ```
- Grandchild of grandparent
  - Manage records
    - Create at least 2 records
    - To create
      - As done here ```Insert record with multiple field values```
      - Use these details
      ```
        Route::get('/ExampleRoute48', function(){
          ExampleModel::create(['example_column'=>'example_model_value', 'example_column_2'=>'example_model_value_2', 'example_column_3'=>1, 'example_parent_model_id'=>1]);
        });
      ```
        - For the ```example_parent_model_id``` value use the id of whatever record you have that also has a example_grandparent2_model_id value. In my case it's ```13``` and ```14```.
    - To delete
    ```
      Route::get('/ExampleRoute49', function(){
        ExampleModel::find(1)->forceDelete();
        ExampleModel::find(2)->forceDelete();
        ExampleModel::find(3)->forceDelete();
      });
    ```
  - View them as per grandparent
    - Parent model
    ```
      public function ExampleModels(){
        return $this->hasMany('App\ExampleModel');
      }
    ```
      - Add this in the model's class
      - Regarding the function's name here we added use an "s" at the end to as it is a many relationship
    - Route
    ```
      Route::get('/ExampleRoute50', function(){
        $example_variable = ExampleGrandparent2Model::find(1);
        foreach ($example_variable->examplemodels as $example_variable_part){
          echo "<br><br>".$example_variable_part;
        }
      });
    ```

### <a name="Polymorphic-Relationships"></a> Polymorphic Relationships
- General
  - Definition
    - A good way of understanding this is to think of it as a kind of "either-or to many relationship"
    - A polymorphic relationship means a relationship where a child table can be shared between different types of parents (or different parent tables)
- One to many polymorphic relationships
  - Prerequisites
    - Great-grand-child table-model pair
        - Setup it up - just follow as previously demonstrated in `Set Up a New Table-Model Pair Using the Shortcut` and use the following specs
            - Migration
                - Table's name `ExampleGreatGrandChildModel`
                - Table columns
                ```
                  $table->integer('parent_id');
                  $table->string('parent_type');
                  $table->string('example_column');
                ```
            - Model
                - Allowable multiple value inserts
                    - `parent_id`
                    - `parent_type`
                    - `example_column`
                - Relationship
                ```
                  public function parent() {
                    return $this->morphTo();
                  }
                ```
    - Example model
        - Migration
            - Since we will now be using polymorphic relationships this will be configured.
            - Comment this out `$table->integer('example_parent_model_id')->unsigned();`
            - Refresh all the tables
        - Model
            - Relationship
                - Add this
                ```
                  public function ExampleGreatGrandChildModels() {
                    return $this->morphMany('App\ExampleGreatGrandChildModel', 'parent');
                  }
                ```
    - Example parent model
        - Model
            - Relationship
                - Add this
                ```
                  public function ExampleGreatGrandChildModels() {
                    return $this->morphMany('App\ExampleGreatGrandChildModel', 'parent');
                  }
                ```
    - Repopulate some content
        - Since we refreshed all the tables we will need to repopulate some content.
        - Use the following routes to add content
            - For example model use `/ExampleRoute16` do not use `/ExampleRoute48`
            - For example parent model use `/ExampleRoute40` don't use `/ExampleRoute46`
            - For example grandparent model use `/ExampleRoute38`
            - For example grandparent-parent relationship model use `/ExampleRoute36`
  - Queries
    - Create
      - Create 2 great grandchild records
          - As done here `Insert record with multiple field values`
          - Use these details
          ```
            Route::get('/ExampleRoute51', function(){
              ExampleGreatGrandChildModel::create(['parent_id'=>1, 'parent_type'=>'App\ExampleModel']);
              ExampleGreatGrandChildModel::create(['parent_id'=>1, 'parent_type'=>'App\ExampleParentModel']);
            });
          ```
      - Create a great grandchild record through a parent
      ```
        Route::get('/ExampleRoute51.2', function(){
          ExampleModel::findOrFail(7)->ExampleGreatGrandChildren()->create(['example_column'=>'example_value']);
        });
      ```
    - Read
      - View the descendent polymorphically
          - Example model
              - Route
              ```
                Route::get('/ExampleRoute53', function(){
                    $example_variable = ExampleModel::find(1);
                    foreach ($example_variable->ExampleGreatGrandChildModels as $example_variable_part) {
                      echo "<br><br>".$example_variable_part;
                    }
                });
              ```
          - Example parent model
              - Route
              ```
                Route::get('/ExampleRoute54', function(){
                    $example_variable = ExampleParentModel::find(1);
                    foreach ($example_variable->ExampleGreatGrandChildModels as $example_variable_part) {
                      echo "<br><br>".$example_variable_part;
                    }
                });
              ```
      - View the ancestor polymorphically (inverse of view the descendent polymorphically)
        - Route
        ```
          Route::get('/ExampleRoute55', function(){
              $example_variable = ExampleGreatGrandChildModel::find(1);
              return $example_variable->parent;
          });
        ```
    - Update
      - Update great grandchild through it's parent
      ```
        Route::get('/ExampleRoute55.1', function(){
          $example_variable = ExampleModel::findOrFail(7)->ExampleGreatGrandChildren()->whereId(9)->first();
          $example_variable->example_column = "example_value2";
          $example_variable->save();
        });
      ```
      - Update a great grandchild's relationship through a parent
        - Give it a new parent
        ```
          Route::get('/ExampleRoute55.2', function(){
            ExampleModel::findOrFail(7)->ExampleGreatGrandChildren()->save(ExampleGreatGrandChildModel::findOrFail(2));
          });
        ```
        - Remove it's parent
        ```
          Route::get('/ExampleRoute55.3', function(){
            ExampleModel::findOrFail(7)->ExampleGreatGrandChildren()->whereId(9)->update(['parent_id'=>'', 'parent_type'=>'']);
          });
        ```
    - Delete
      - Delete great grandchild records
      ```
        Route::get('/ExampleRoute52', function(){
          ExampleGreatGrandChildModel::find(1)->forceDelete();
        });
      ```
      - Delete great grandchild record through parent
      ```
        Route::get('/ExampleRoute52.1', function(){
          ExampleModel::findOrFail(7)->ExampleGreatGrandChildren()->whereId(7)->delete();
        });
      ```
- Many to many polymorphic relationships
  - Prerequisites
    - Parent 2 table-model pair
        - Setup it up - just follow as previously demonstrated in `Set Up a New Table-Model Pair Using the Shortcut` and use the following specs
            - Migration
                - Table's name `ExampleParentModel2`
                - Table columns
                ```
                  $table->string('name');
                ```
            - Model
                - Allowable multiple value inserts
                    - `name`
                - Relationship
                ```
                  public function ExampleModels() {
                    return $this->morphedByMany('App\ExampleModel', 'example_parent_model2_relation');
                  }
                  public function ExampleGreatGrandChildModels() {
                    return $this->morphedByMany('App\ExampleGreatGrandChildModel', 'example_parent_model2_relations');
                  }
                ```
    - Bridging/relationship table-model pair
        - Setup it up - just follow as previously demonstrated in `Set Up a New Table-Model Pair Using the Shortcut` and use the following specs
            - Migration
                - Table's name `ExampleParentModel2Relationship`
                - Table columns
                ```
                  $table->string('example_parent_model2_id');
                  $table->integer('example_parent_model2_relation_id');
                  $table->string('example_parent_model2_relation_type');
                ```
            - Model
                - Allowable multiple value inserts
                ```
                  protected $fillable = [
                  'example_parent_model2_id',
                  'example_parent_model2_relation_id',
                  'example_parent_model2_relation_type',
                  ];
                ```
    - Example model
      - Model
          - Relationship
              - Add this
              ```
                public function ExampleParentModel2s() {
                  return $this->morphToMany('App\ExampleParentModel2', 'example_parent_model2_relation');
                }
              ```
    - Example Great Grand Child model
      - Model
          - Relationship
              - Add this
              ```
                public function ExampleParentModel2s() {
                  return $this->morphToMany('App\ExampleParentModel2', 'example_parent_model2_relation');
                }
              ```
  - Queries
    - Create
      - Create 2 parent 2 records
          - As done here `Insert record with multiple field values`
          - Use these details
          ```
            Route::get('/ExampleRoute56', function(){
              ExampleParentModel2::create(['name'=>'grand-child2.1']);
              ExampleParentModel2::create(['name'=>'grand-child2.2']);
            });
          ```
      - Create 2 relationship records
        - As done here `Insert record with multiple field values`
        - Bear in mind you can use either the `save()` function of the `attach()` function
        ```
          Route::get('/ExampleRoute58', function(){
            ExampleParentModel2Relationship::create(['example_parent_model2_id'=>'1', 'example_parent_model2_relation_id'=>1, 'example_parent_model2_relation_type'=>'App\ExampleModel']);
            ExampleParentModel2Relationship::create(['example_parent_model2_id'=>'2', 'example_parent_model2_relation_id'=>1, 'example_parent_model2_relation_type'=>'App\ExampleGreatGrandChildModel']);
          });
        ```
      - Create relationship records through a child
      ```
        Route::get('/ExampleRoute58.1', function(){
          $example_variable = ExampleParentModel2::findOrFail(1);
          ExampleModel::findOrFail(7)->ExampleParentModel2s()->save($example_variable);
        });
      ```
      - Create relationship records through a child and delete any old relationships for that child
      ```
        Route::get('/ExampleRoute58.2 ', function(){
          ExampleModel::findOrFail(7)->ExampleParentModel2s()->sync([2]);
        });
      ```
    - Read
      - View polymorphic parents of children
        - While specifying child type 1
          - Route
          ```
          Route::get('/ExampleRoute60', function(){
              $example_variable = ExampleModel::find(1);
              foreach ($example_variable->ExampleParentModel2s as $example_variable_part) {
                echo "<br><br>".$example_variable_part;
              }
          });
          ```
        - While specifying child type 2
          - Route
          ```
          Route::get('/ExampleRoute61', function(){
              $example_variable = ExampleGreatGrandChildModel::find(1);
              foreach ($example_variable->ExampleParentModel2s as $example_variable_part) {
                echo "<br><br>".$example_variable_part;
              }
          });
          ```
        - Read the parent through child
        ```
          Route::get('/ExampleRoute61.1', function(){
            $example_variable = ExampleModel::findOrFail(7);
            foreach($example_variable->ExampleParentModel2s as $example_variable2){
              echo $example_variable2;
            }
          });
        ```
      - View child of a specified child type of the polymorphic parent (inverse of above). Polymorphic means shared between different tables/types of data.
        - While specifying child type 1
          - Route
          ```
            Route::get('/ExampleRoute62', function(){
              $example_variable = ExampleParentModel2::find(1);
              foreach ($example_variable->ExampleModels as $example_variable_part) {
                echo "<br><br>".$example_variable_part;
              }
            });
          ```
        - While specifying child type 2
          - Route
          ```
          Route::get('/ExampleRoute63', function(){
            $example_variable = ExampleParentModel2::find(1);
            foreach ($example_variable->ExampleGreatGrandChildModels as $example_variable_part) {
              echo "<br><br>".$example_variable_part;
            }
          });
          ```
    - Update
      - Update parent through child
      ```
        Route::get('/ExampleRoute63.1', function(){
          $example_variable = ExampleModel::findOrFail(7)->ExampleParentModel2s->first()->update(['name'=>'updated']);
        });
      ```
    - Delete
      - Delete parent 2 records
      ```
        Route::get('/ExampleRoute57', function(){
          ExampleParentModel2::find(1)->forceDelete();
        });
      ```   
      - Delete parent through child
      ```
        Route::get('/ExampleRoute57.1', function(){
          $example_variable = ExampleObject::findOrFail(7)->ExampleParentModel2s->first()->delete();
        });
      ```
      - Delete parent 2 records
      ```
        Route::get('/ExampleRoute59', function(){
          ExampleParentModel2Relationship::find(1)->forceDelete();
        });
      ```  



## <a name="11."></a>Chapter 4.3.5. Query Testing Environment

### Table Of Content
- [Query Testing Environment](#Query-Testing-Environment)

### <a name=""></a>  Query Testing Environment

#### <a name=""></a> Query Testing Environment
- General
  - A queries testing environment is a place to test your controller queries before you add them to your script. The one that comes with Laravel is called Tinker.
- To open it
  - In git bash command line and run `cd C:/laravel-apps/fundamental-mechanisms-app` then `php artisan tinker`
- To close it
  - Run the command `exit`
- Basic ORM queries
  - Create a record
    - In one go
      - Run the command `$example_variable = App\ExampleModel::create(['example_column'=>'example_value6', 'example_column_2'=>'example_value7', 'example_column_3'=>1]);`
    - In multiple steps
      - To create a pseudo-form that will send the record data to the db - run `$example_variable = new App\ExampleModel`
      - To add something to that pseudo-form run `$example_variable->example_column = "example_value6"`
      - To check what the pseudo-form holds so far run `$example_variable`
      - To submit your pseudo-form run `$example_variable->save()`
      - To view the information is has been given while being saved to the db run `$example_variable`
  - To view a record
    - Just filtered by id - run `$example_variable = App\ExampleModel::find(1);`
    - Using other filters
      - Where filter
        - Run `$example_variable = App\ExampleModel::where("id", "<", 6)->orderBy('id','desc')->first();`
      - WhereId
        - Run `$example_variable = App\ExampleModel::whereId(2)->first();`
  - To update a record
    - First find the records
      - Run `$example_variable = App\ExampleModel::find(1);`
    - Run `$example_variable->example_column = "example_value6";`
    - Run `$example_variable->save()`
  - To delete a record
    - If soft-delete isn't activated
      - First find the records
        - Run `$example_variable = App\ExampleModel::find(2);`
        - Run `$example_variable->delete()`
    - If soft-delete is activated
      - Soft delete
        - Same method as shown is `To delete a record - If soft-delete isn't activated`
      - Restore
        - Run `$example_variable->restore()`
      - Hard delete
        - First soft delete item
        - Then empty your
          - Run `$example_variable = App\ExampleModel::onlyTrashed();`
          - Run `$example_variable->forceDelete()`
- ORM queries with relationships
  - View
    - Run `$example_variable = App\ExampleModel::find(1);`
    - Run `$example_variable->ExampleGreatGrandChildModels`
  - Create, update, delete just like u do in the `Query Testing Environment- Basic ORM Queries` section
  
  
  

## <a name="12."></a>Chapter 4.3.6. Accessors and Mutators

### Table Of Content
- [Dates](#Dates)
- [Accessors](#Accessors)
- [Mutators](#Mutators)

### <a name="Dates"></a> Dates
#### Basic Dates
- Route
```
  Route::get('/64', function (){
    $date = new DateTime('+1 weeks');
    echo $date->format('m-d-Y');
  });
```

#### With Human Readable Accessors
- Setup
  - Laravel comes with a library called Carbon that helps with this
  - This the following code at the top of your route file
  ```
    use Carbon\Carbon;
  ```
- Usage  
  - Now (non-human readable)
    - Route
    ```
      Route::get('/65', function (){
        echo Carbon::now();
      });
    ```
  - Now
    - Route
    ```
      Route::get('/66', function (){
        echo Carbon::now()->diffForHumans();
      });
    ```
  - Ten Days from now
    - Route
    ```
      Route::get('/67', function (){
        echo Carbon::now()->addDays(10)->diffForHumans();
      });
    ```
  - 5 Months Ago
    - Route
    ```
      Route::get('/68', function (){
        echo Carbon::now()->subMonths(5)->diffForHumans();
      });
    ```
  - Yesterday
    - Route
    ```
      Route::get('/69', function (){
        echo Carbon::now()->yesterday()->diffForHumans();
      });
    ```

### <a name="Accessors"></a> Accessors
- Query without an accessor
  - Route
  ```
    Route::get('/70', function(){
      $example_variable = ExampleModel::find(7);
      echo $example_variable->example_column;
    });
  ```
- Query With an accessor
  - Example Model
    - Route: Reuse route `70` for this
    - Model
      - Upper Case First Letter
      ```
        public function getExampleColumnAttribute($value) {
          return ucfirst($value);
        }
      ```
      - Or Upper Case All Letters
        - Change the returned value to
        ```
          strtoupper($value);
        ```

### <a name="Mutators"></a> Mutators
- Example Model
  - Route
  ```
    Route::get('/71', function(){
      $example_variable = ExampleObject::find(7);
      $example_variable->example_column = $example_variable->example_column;
      $example_variable->save();
    });
  ```
  - Model
  ```
    public function setExampleColumnAttribute($value) {
      $this->attributes['example_column'] = strtoupper($value);
    }
  ```
  - Database
    - The check your DB data has changed



## <a name="13."></a>Chapter 4.4. Views component

### Table Of Content
- [Views](#)

### Definition
  - Views are what  handle style. This is because they give style to your data.
- They are located here `C:\laravel-apps\fundamental-mechanisms-app\resources\views`.

### How to Create Them
- Using a code editor or windows explorer locate yourself to `C:\laravel-apps\fundamental-mechanisms-app\resources\views`.
- Create a new .blade.php file, the name format should be camel case e.g. `ExampleView.blade.php`.
- Example:
  - Route
  ```
    Route::get('/ExampleRoute2', function () {
      return view('ExampleView');
    });
  ```
  - View
    - Name `ExampleView.blade.php`
    - Content
    ```
      Hello world!
    ```

### Template Inheritance
- This enables parent templates to give default content to their assigned child templates.
- A common example for this is to wrap all your html in html tags and to insert a generic head block.
- Example:
  - Route
  ```
    Route::get('/ExampleRoute9', function () {
      return view('ExampleView6');
    });
  ```
  - Parent template
    - Location: `C:\laravel-apps\fundamental-mechanisms-app\resources\views\layouts` (you will need to create the "layouts" folder).
    - Name: `ExampleParentView.blade.php`.
    - Content:
    ```
      <!DOCTYPE html>
      <html>
      <head>
        <meta charset="UTF-8">
        <title>Example Title</title>
      </head>
      <body>
      <div class="container">
        @yield('content')
      </div>
        @yield('footer')
      </body>
      </html>
    ```
  - Child template
    - Location: `C:\laravel-apps\fundamental-mechanisms-app\resources\views`
    - Name: `ExampleView6.blade.php`.
    - Content:
    ```
      @extends('layouts.ExampleParentView')
      @section('content')
        <h1>Example content</h1>
      @stop
      @section('footer')
        <script>alert('Hello world')</script>
      @stop
    ```


### Accepting Route Parameters
#### Only One Parameter
- Example:
  - Route
    - `Route::get('/ExampleRoute6/{ExampleParameter}', 'ExampleController@ExampleControllerMethod3');`
  - Controller method
    - Method 1
    ```
      public function ExampleControllerMethod3($ExampleParameter)
      {
        return view('ExampleView3')->with('ExampleParameter',$ExampleParameter);
      }
    ```
    - Method 2 (this method can also be used in controller that have multiple parameters)
    ```
      public function ExampleControllerMethod3($ExampleParameter)
      {
        return view('ExampleView3', compact('ExampleParameter'));
      }
    ```
  - View
    - Name `ExampleView3.blade.php`
    - Content
    ```
      Example message with {{$ExampleParameter}}.
    ```
  - Test using something like: `fundamental-mechanisms-app.test/ExampleRoute6/example-parameter-string`.

#### Multiple Parameters
##### As a set of variables
- Example:
  - Route
  ```
  Route::get('/ExampleRoute7/{ExampleParameter}/{ExampleParameter2}/{ExampleParameter3}', 'ExampleController@ExampleControllerMethod4');
  ```
  - Controller method
  ```
    public function ExampleControllerMethod4($ExampleParameter, $ExampleParameter2, $ExampleParameter3)
    {
      return view('ExampleView4', compact('ExampleParameter','ExampleParameter2','ExampleParameter3'));
    }
  ```
  - View
    - Name `ExampleView4.blade.php`
    - Content
    ```
      Example message with {{$ExampleParameter}}, {{$ExampleParameter2}} and {{$ExampleParameter3}}.
    ```
  - Test URL: `fundamental-mechanisms-app.test/ExampleRoute7/1/2/3`.


##### As an array
- Example:
  - Route
  ```
    Route::get('/ExampleRoute8/{ExampleParameter}/{ExampleParameter2}/{ExampleParameter3}', 'ExampleController@ExampleControllerMethod5');
  ```
  - Controller Method
  ```
    public function ExampleControllerMethod5($ExampleParameter, $ExampleParameter2, $ExampleParameter3)
    {
      $ExampleParameters = [$ExampleParameter,$ExampleParameter2,$ExampleParameter3];
      return view('ExampleView5', compact('ExampleParameters'));
    }
  ```
  - View
    - Name `ExampleView5.blade.php`
    - Content
    ```
      Example message with {{$ExampleParameters[0]}}, {{$ExampleParameters[1]}} and {{$ExampleParameters[2]}}.
    ```
  - Test URL: `fundamental-mechanisms-app.test/ExampleRoute8/1/2/3`.

### Control Structures - Foreach Loop
- Example:
  - Route (same as in `Multiple Parameters - As an array`)
  ```
    Route::get('/ExampleRoute10/{ExampleParameter}/{ExampleParameter2}/{ExampleParameter3}', 'ExampleController@ExampleControllerMethod6');
  ```
  - Controller (same as in `Multiple Parameters - As an array`)
  ```
    public function ExampleControllerMethod6($ExampleParameter, $ExampleParameter2, $ExampleParameter3)
    {
      $ExampleParameters = [$ExampleParameter,$ExampleParameter2,$ExampleParameter3];
      return view('ExampleView7', compact('ExampleParameters'));
    }
  ```
  - View
    - Name `ExampleView7.blade.php`
    - Content
    ```
      Example message with:
      @if (count($ExampleParameters))
        <ul>
        @foreach($ExampleParameters as $ExampleParameter)
          <li>{{$ExampleParameter}}</li>
        @endforeach
        </ul>
      @endif
    ```
  - Test URL: `fundamental-mechanisms-app.test/ExampleRoute10/1/2/3`

## <a name="14."></a>Chapter 5. Real world examples
### <a name="5.1.%20Intro"></a>Chapter 5.1. Intro

#### Make a new laravel powered app
##### Install
- Called it `real-world-examples-app` the method was previously demonstrated.

##### Make table-model pairs
- Create them
	- posts
	  - Command:
	    - Orientate with `cd C:/laravel-apps/real-world-examples-app`
	    - Run `php artisan make:model Post -m`
	- users
	  - Already made
	- role_user
	  - Commands:
	    - Table/Migration: `php artisan make:migration role_user --create="role_user"`
	    - Model: `php artisan make:model RoleUser`
	- roles
	  - Command: `php artisan make:model Role -m`
	- countries
	  - Command: `php artisan make:model Country -m`
	- photos
	  - Command: `php artisan make:model Photo -m`
	- videos
	  - Command: `php artisan make:model Video -m`
	- tags
	  - Command: `php artisan make:model Tag -m`
	- tag_relationships
	  - Command: `php artisan make:model TagRelationship -m`
- Configure them
	- General: Add the following column functions (to the migrations) and model methods (to the models)
	- posts
	  - Similar to
	    - Model: example_models
	    - From the section on: Database 	
	    - Video course's section: 41s
	  - Columns
	  ```
			$table->string('title');
			$table->text('content');
			$table->integer('user_id')->unsigned();    
			$table->softDeletes();
	  ```
	  - Model methods
	    - Part 1 (put this underneath the other `use` function)
	    ```
	      use Illuminate\Database\Eloquent\SoftDeletes;
	    ```
	    - Part 2
	    ```
		use SoftDeletes;
		protected $dates = ['deleted_at'];
		protected $table = 'posts';
		protected $fillable = [
		  'title',
		  'body',
		  'user_id',
		];
		public function User(){
		  return $this->belongsTo('App\User');
		}
		public function Roles(){
		  return $this->belongsToMany('App\Role')->withPivot('created_at');
		}
		public function Photos() {
		  return $this->morphMany('App\Photo', 'photo_relative');
		}
		public function Tags() {
		  return $this->morphToMany('App\Tag', 'tag_relative');
		}
	    ```
	- users
	  - Similar to
	    - Model: example_parent_models
	    - From the section on: Basic Relationships - One to One 	
	    - Video course's section: 62
	  - Columns: Already set
	  - Model methods
	  ```
	      public function Post(){
		return $this->hasOne('App\Post');
	      }
	      public function Posts(){
		return $this->hasMany('App\Post');
	      }
	      public function Roles(){
		return $this->belongsToMany('App\Role')->withPivot('created_at');
	      }
	      public function Photos() {
		return $this->morphMany('App\Photo', 'photo_relative');
	      }
	  ```
	- role_user
	  - Similar to
	    - Model: example_grandparent_model_example_parent_model
	    - From the section on: Basic Relationships - Many to many 	
	    - Video course's section: 66-67
	  - Columns
	  ```
			$table->integer('user_id');
			$table->integer('role_id');
	  ```
	  - Model methods
	  ```
	      protected $table = 'role_user';
	      protected $fillable = [
		'user_id',
		'role_id',
	      ];
	  ```
	- roles
	  - Similar to
	    - Model:  example_grandparent_models
	    - From the section on: Basic Relationships - Many to many  	
	    - Video course's section: 	66-67
	  - Columns
	  ```
			$table->string('name');
	  ```
	  - Model methods
	  ```
	      protected $fillable = [
	      'name'
	      ];
	      public function Users(){
		return $this->belongsToMany('App\User');
	      }
	  ```
	- countries
	  - Similar to
	    - Model:  example_grandparent2_models
	    - From the section on: Advanced Relationships - Relationship with 2 Levels of Separation 	
	    - Video course's section: 68-70
	  - Columns
	  ```
			$table->string('name');
	  ```
	  - Model methods
	  ```
	      protected $fillable = [
	      'name',
	      ];
	      public function Posts(){
		return $this->hasManyThrough('App\Post', 'App\User');
	      }
	  ```
	- photos
	  - Similar to
	    - Model:  example_great_grand_child_models (although due to a mistake it's equivalent is relatively different)
	    - From the section on: Advanced Relationships - Polymorphic Relationships - One to many 	
	    - Video course's section: 71-73
	  - Columns
	  ```
			$table->integer('photo_relative_id');
			$table->string('photo_relative_type');
			$table->string('file');
	  ```
	  - Model methods
	  ```
	      protected $fillable = [
		'photo_relative_id',
		'photo_relative_type',
		'file',
	      ];
	      public function photo_relative() {
		return $this->morphTo();
	      }
	  ```
	- videos
	  - Similar to
	    - Model:  example_great_grand_child_models (although due to a mistake it's equivalent is relatively different)
	    - From the section on: Advanced Relationships - Polymorphic Relationships - One to many 	
	    - Video course's section: 71-73
	  - Columns
	  ```
			$table->string('file');
	  ```
	  - Model methods
	  ```
	      protected $fillable = [
		'file',
	      ];
	      public function Tags() {
		return $this->morphToMany('App\Tag', 'tag_relative');
	      }
	  ```
	- tags
	  - Similar to
	    - Model:  example_parent_model2s
	    - From the section on: Advanced Relationships - Polymorphic Relationships - Many to many  	
	    - Video course's section: 	74-77
	  - Columns
	  ```
			$table->string('name');
	  ```
	  - Model methods
	  ```
	      protected $fillable = [
	      'name',
	      ];
	      public function Posts() {
		return $this->morphedByMany('App\Post', 'tag_relative');
	      }
	      public function Photos() {
		return $this->morphedByMany('App\Video', 'tag_relative');
	      }
	  ```
	- tag_relationships
	  - Similar to
	    - Model:  example_parent_model2_relation
	    - From the section on: Advanced Relationships - Polymorphic Relationships - Many to many 	
	    - Video course's section: 74-77
	  - Columns
	  ```
			$table->string('tag_id');
			$table->integer('tag_relative_id');
			$table->string('tag_relative_type');
	  ```
	  - Model methods
	  ```
	      protected $fillable = [
	      'tag_id',
	      'tag_relative_id',
	      'tag_relative_type',
	      ];
	  ```
- Impliment them
	- Orientate yourself with `cd C:/laravel-apps/real-world-examples-app`
	- Run `php artisan migrate`

##### Create a layout view file
- Orientate yourself to you views folder
- Create and orientate yourself to a subfolder called `layouts`
- Create the file `app.blade.php`
- Add this to its contents
```
  <!DOCTYPE html>
  <html>
  <head>
    <meta charset="UTF-8">
    <title>App</title>
  </head>
  <body>
  <div class="container">
    @yield('content')
  </div>
    @yield('footer')
  </body>
  </html>
```



### <a name="5.2.%20Forms"></a>Chapter 5.2. Forms

#### Table Of Content
- [Basics](#Basics)
- [LC Form Builder](#LC-Form-Builder)
- [Validation](#Validation)


#### <a name="Basics"></a> Basics
##### Setup

- Controller: `php artisan make:controller --resource PostsController`
- Route  
```
  Route::resource('/posts','PostsController');
```
  - Check all the resultant routes
    - Orientate yourself `cd C:/laravel-apps/real-world-examples-app`
    - Run `php artisan route:list`
- Views
  - Orientate yourself to you views folder
  - Create and orientate yourself to a subfolder called `posts`
  - Create the following files
    - `index.blade.php`
    - `create.blade.php`
    - `show.blade.php`
    - `edit.blade.php`

##### Fine tuning
- Create Post page
	- Part 1
	  - View
	    - Orientate yourself to `create.blade.php`
	    ```
	      @extends('layouts.app')
	      @section('content')
	      <h1>Create Post</h1>
	      <form class="" action="/posts" method="post">
		<input type="text" name="title" value=""  placeholder="Enter title">
		{{csrf_field()}}
		<input type="submit" name="submit" value="Submit">
	      </form>
	      @endsection
	    ```
	  - Controller
	    - This goes in the posts controller's "create" method
	    ```
	      return view('posts.create');
	    ```
	- Part 2
	  - Controller
	    - Add a model usage namespace
	      - Orientate yourself to your posts controller file
	      - Add the model usage namespace `use  App\Post;`  at the top directly underneath the "namespace" function.
	    - This goes in the posts controller's "store" method
	      - Part A
		- Option 1
		```
		  Post::create($request->all());
		```
		- Option 2
		```
		  $input = $request->all();
		  $input['title'] = $request->title;
		  Post::create($request->all());
		```
		- Option 3
		```
		  $post = new Post;
		  $post->title = $request->title;
		  $post->save();
		```
	      - Part B
	      ```
		return redirect('/posts');
	      ```
	- Test URL: `../posts/create`
- Lists Posts page
	- View
	  - Orientate yourself to `index.blade.php`
	  ```
	    @extends('layouts.app')
	    @section('content')
	    <h1>List Posts</h1>
	    <ul>
	      <li><a href="{{route('posts.create')}}">Create post</a></li>
	      @foreach($posts as $post)
	      <li><a href="{{route('posts.show',$post->id)}}">{{$post->title}}</a></li>
	      @endforeach
	    </ul>
	    @endsection
	  ```
	- Controller
	  - This goes in the posts controller's "index" method
	    - Part 1
	    ```
	      $posts = Post::all();
	    ```
	    - Part 2
	    ```
	      return view('posts.index', compact('posts'));
	    ```
	- Test URL: `../posts`
- View Posts page
	- View
	  - Orientate yourself to `show.blade.php`
	  ```
	    @extends('layouts.app')
	    @section('content')
	    <h1>View Post</h1>
	    <h2><a href="{{route('posts.edit',$post->id)}}">{{$post->title}}</a></h2>
	    @endsection
	  ```
	- Controller
	  - This goes in the posts controller's "show" method
	  ```
	    $post = Post::findorfail($id);
	    return view('posts.show', compact('post'));
	  ```
	- Test URL: `../posts/4`
- Edit/Delete Posts page
	- Part 1
	  - View
	    - Orientate yourself to `edit.blade.php`
	    ```
	    @extends('layouts.app')
	    @section('content')
	    <h1>Edit Post</h1>
	    <form class="" action="/posts/{{$post->id}}" method="post">
	      {{csrf_field()}}
	      <input type="hidden" name="_method" value="PUT">
	      <input type="text" name="title" value="{{$post->title}}"  placeholder="Enter title">
	      <input type="submit" name="submit" value="Update">
	    </form>
	    <form class="" action="/posts/{{$post->id}}" method="post">
	      <input type="hidden" name="_method" value="DELETE">
	      {{csrf_field()}}
	      <input type="submit" value="Delete">
	    </form>
	    @endsection
	    ```
	  - Controller
	    - This goes in the posts controller's "edit" method
	    ```
	      $post = Post::findOrFail($id);
	      return view('posts.edit', compact('post'));
	    ```
	- Part 2
	  - Controller
	    - This goes in the posts controller's "update" method
	    ```
	      $post = Post::findOrFail($id);
	      $post->update($request->all());
	      return redirect('/posts');
	    ```
	- Part 3
	  - Controller
	    - This goes in the posts controller's "delete" method
	    ```
	      $post = Post::whereId($id)->first()->delete();
	      return redirect('/posts');
	    ```
	- Test URL: `../posts/4/edit`

####  <a name="LC-Form-Builder"></a> LC Form Builder
##### Setup
- If you like you can see more info about the Laravel Collective Form Builder at https://laravelcollective.com/docs/5.2/html

- Install packages
	- Configure composer
	  - Oriented yourself to `composer.json` and paste `"laravelcollective/html":"^5.2.0"` as a new line in the `"require"` section. Make sure to put a comma after the previous item.
	  - If your using a Laravel version that doesn't fit into the `5.2` range then you will need to adapt the code.
	- Run composer
	  - Orientate yourself `cd C:/laravel-apps/real-world-examples-app`
	  - Run `composer update`
- Configure package
	- Configure `app.php`
	  - Part 1
	    - Orientate yourself to `config/app.php`
	    - Paste the following code directly above the existing comment
	      - The code
	      ```
	      Collective\Html\HtmlServiceProvider::class,
	      ```
	      - The comment
	      ```
		/*
		 * Application Service Providers...
		 */
	      ```
	  - Part 2
	    - Orientate yourself to `config/app.php` and paste the following code as a new line in the `'aliases'` section. Make sure to put a comma after the previous item.
	    ```
	      'Form' => Collective\Html\FormFacade::class,
	      'Html' => Collective\Html\HtmlFacade::class,
	    ```

##### Usage
- Create Post page
	- View
	  - Orientate yourself to `create.blade.php`
	  - Edit the file to look like this
	  ```
	    @extends('layouts.app')
	    @section('content')
	    <h1>Create Post</h1>
	    {!! Form::open(['method'=>'POST', 'action'=>'PostsController@store']) !!}
	      <div class="form-group">
		{!! Form::label('title', 'Title:') !!}
		{!! Form::text('title', null, ['class'=>'form-control']) !!}
	      </div>
	      <div class="form-group">
		{!! Form::submit('Create Post', ['class'=>'btn btn-primary']) !!}
	      </div>
	    {!! Form::close() !!}
	    @endsection
	  ```
- Lists Posts page
	- View
	  - Orientate yourself to `index.blade.php`
	  - Edit the file to look like this
	  ```
	  ```
- View Posts page
	- View
	  - Orientate yourself to `show.blade.php`
	  - Edit the file to look like this
	  ```
	  ```
- Edit/Delete Posts page
	- View
	  - Orientate yourself to `edit.blade.php`
	  - Edit the file
	    - Final result
	    ```
	      @extends('layouts.app')
	      @section('content')
	      <h1>Edit Post</h1>
	      {!! Form::model($post, ['method'=>'PATCH', 'action'=>['PostsController@update', $post->id]]) !!}
		<div class="form-group">
		  {!! Form::label('title', 'Title:') !!}
		  {!! Form::text('title', null, ['class'=>'form-control']) !!}
		</div>
		<div class="form-group">
		  {!! Form::submit('Update', ['class'=>'btn btn-primary']) !!}
		</div>
	      {!! Form::close() !!}
	      {!! Form::open(['method'=>'DELETE', 'action'=>['PostsController@destroy', $post->id]]) !!}
		<div class="form-group">
		  {!! Form::submit('Delete', ['class'=>'btn btn-danger']) !!}
		</div>
	      {!! Form::close() !!}
	      @endsection
	    ```
	    - How we got the final result
	      - Edit part
		- Replaced the first form with the same form content as we used in the recent `create.blade.php`
		- Adaptions
		  - but used the method `PATCH` not `POST`
		  - and used the action `PostsController@update` not `PostsController@store`
		  - Used the submit text `Update` not `Create Post`
		  - For the opening form function
		    - Used the opening form function `model` not `open` and add a new parameter of `$post` which goes first
		    - Made the action an array so that it can also include `$post->id`
		    - So it looks like this
		    ```
		    {!! Form::model($post, ['method'=>'PATCH', 'action'=>'PostsController@update']) !!}
		    ```
	      - Delete part
		- Replaced the second form also with the same form content as we used in the recent `create.blade.php`
		- Adaptions
		  - but used the method `DELETE` not `POST`
		  - and used the action `PostsController@destroy` not `PostsController@store`
		  - Used the submit text `Delete` not `Create Post`
		  - Used the css class text `btn-danger` not `btn-primary`
		  - And removed the title text, title label and their form group
		  - For the opening form function
		    - Made the action an array so that it can also include `$post->id`
		    - So it looked like this
		    ```
		    {!! Form::open(['method'=>'DELETE', 'action'=>['PostsController@destroy', $post->id]]) !!}
		    ```

##### LC Form Builder Snippets
- Intro
  - To make the writing of commonly used LC Form Builder code samples easier we will make them into snippets
  - If you're using the Atom IDE the method of doing this was demonstrated in the Development Tools part of this course
- Submit button
  - Type of code: `php`
  - Name: `LC Form Builder Sumbit Button`
  - Shortcut: `LCsumbit`
  - Sample:
  ```
    '''
      <div class="form-group">
        {!! Form::submit('$1', ['class'=>'btn btn-$2']) !!}
      </div>
    '''
  ```
- Text input
  - Type of code: `php`
  - Name: `LC Form Builder Text input`
  - Shortcut: `LCtextinput`
  - Sample:
  ```
    '''
      <div class="form-group">
        {!! Form::label('$1', '$2:') !!}
        {!! Form::text('$1', null, ['class'=>'form-control']) !!}
      </div>
    '''
  ```
- Form
  - Type of code: `php`
  - Name: `LC Form Builder Form`
  - Shortcut: `LCform`
  - Sample:
  ```
    '''
    {!! Form::open(['method'=>'$1', 'action'=>'PostsController@$2']) !!}
      <div class="form-group">
        {!! Form::label('$3', '$4:') !!}
        {!! Form::text('$3', null, ['class'=>'form-control']) !!}
      </div>
      <div class="form-group">
        {!! Form::submit('$5', ['class'=>'btn btn-$6']) !!}
      </div>
    {!! Form::close() !!}
    '''
  ```

#### <a name="Validation"></a> Validation
#####

- Intro
  - We will use Laravel's automatic validation errors messages (e.g. "please enter a password with more that 5 characters")
  - This is thought of as setting constraints to the type of requests the user is allowed to make
- Validation message plus basic request validator
  - Create Post page
    - "Store" controller
      - Add the `basic request validator` code below to the store method and make sure it goes above it's sibling functions
      ```
        $this->validate($request, [
          'title'=>'required|max:50',
        ]);
      ```
        - This code we will just use temporarily to demonstrate how it works
    - View
      - Orientate yourself to `create.blade.php`
      - Add the following code after the form
      ```
        @if(count($errors) > 0)
          <div class="alert alert-danger">
            <ul>
              @foreach($errors->all() as $error)
                <li>{{$error}}</li>
              @endforeach
            </ul>
          </div>
        @endif
      ```
- Prebuilt request validator
  - Request
    - Make new one
      - Orientate with
      ```
        cd C:/laravel-apps/real-world-examples-app
      ```
      - Run
      ```
        php artisan make:request CreatePostRequest
      ```
    - Edit it
      - Orientate yourself to
      ```
        app\Http\Requests\CreatePostRequest.php
      ```
      - In the authorize method set the return value to
        - `true`
        - This sets it so that everyone can make request with the form (not just privileged members)
      - In the rules method add the following to the returned array
        - `'title'=>'required'`
  - Controller Method (Create Posts Page Store Controller Method)
    - Remove the `basic request validator` code
    - Using the request
      - Option 1
        - Change the first part of the store method's parameter (the `Request` part) to `Requests\CreatePostRequest` so it looks like
        ```
          public function store(Requests\CreatePostRequest $request)
        ```
      - Option 2
        - Change the first part of the store method's parameter (the `Request` part) to `CreatePostRequest` so it looks like
          ```
            public function store(CreatePostRequest $request)
          ```
        - Add the usage function to the top of this file (directly under the "namespace" function)
        ```
          use App\Http\Requests\CreatePostRequest;
        ```
