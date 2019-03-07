# Automation with Laravel

## <a name="1. Table-of-Content"></a>Chapter 1. Table of Content

- [1. Table of Content](#1.)
- [2. Introduction](#2.)
- [3. Setting up the development tools](#3.)
- [4. Setting up the Laravel powered app](#4.)
- [5. Database component](#5.)
- [6. Routes component](#6.)
- [7. /4.3.1. Introduction to queries](#7.)
- [8. /4.3.2. Basic Queries](#8.)
- [9. /4.3.3. Queries with basic relationships](#9.)
- [10. /4.3.4. Queries with advanced relationships](#10.)
- [11. /4.3.5. Query Testing Environment](#11.)
- [12. /4.3.6. Accessors and mutators queries](#12.)
- [13. /4.4. Views](#13.)
- [14. /5. Real-World Examples](#14.)
  - [8.1. /5.1. Intro](#8.1)
  - [8.2. /5.2. Forms](#8.2)
  - [8.3. /5.3. Coming soon](##)
  - [8.4. /5.4. Coming soon](##)
  

## <a name="2. Introduction"></a>Chapter 2. Introduction

### About
- This is a place for you to learn the ins and outs of Lary Wary (Laravel).
- Laravel is a kind of development tool more specifically it is a development framework.
- Please follow this course in the order laid out in the menu -  starting from "Introductions" and ending at "Views".
- Just your luck
   - You are very privileged to be able to see this course.
   - All are welcome to venture into the land of milk and honey!

### Credits
- This course is based on a video course on Udemy.com which can be found here - [Laravel for beginners](https://www.udemy.com/php-with-laravel-for-beginners-become-a-master-in-laravel/)


##<a name="3.%20Setup"></a>3. Settup

### <a name="3.1.%20Development%20Tools"></a>Chapter 3.1 Development Tools
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
			- G
