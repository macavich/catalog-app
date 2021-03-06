# About
This project is the fourth project for Udacity's Fullstack Web Development Nanodegree.  The goal of this project is to create a webserver that handles secure CRUD functionality, OAuth2 login handling, and JSON endpoints to serve data for a client.

The project is called Catalog App.  It's database stores very categories, and associated items for each category.  For example, the item 'Shinguard' is associated with the category 'Soccer'.

An OAuth2 authenicated user is allowed to create new Items for whatever Category they choose.  Users are also allowed to Edit items, but only items which they have created.  The project supports login from both Facebook and Google+ so it should securely cover most potential users.

Finally, for those looking to receive JSON from the server, JSON endpoints are provided for just about all of the data available on the page.  See further documentation below for endpoint information.


# Getting Started
#### Virtual Machine for Ubuntu
To recreate my environment, you will need to install [Viritual Box](https://www.virtualbox.org/wiki/Downloads) first, and afterwards [Vagrant](https://www.vagrantup.com/downloads.html).  This will be how we will install the Ubuntu virtual machine.  Please feel free to skip these to the python dependencies if you would like to try execution in your current environment.  

In the folder named vagrant in the project repo, you'll find a file call Vagrantfile.  Please don't alter this, it will configure the Ubuntu virtual machine and download the python dependencies listed below for your virtual machine.

Create a folder in your desired location and fork the repo.  If pulled directly from this repo, the following commands in terminal will set things up as you'll want them for the virtual machine.
```
$ mkdir vagrant/catalog
$ mv * vagrant/catalog
```
(you'll get a friendly message from bash saying you can't move vagrant into itself!)
```
$ cd vagrant
```

Now you're in your newly made vagrant directory.  Time to get the virutal machine running.
Execute the following:
```
$ vagrant up
```
This may take up to 15 or so minutes depending on your internet connection; you are downloading the entire Ubuntu operating system.
```
$ vagrant ssh
```
Now you should see the Ubuntu virtual machine up and running!  Move into our vagrant folder.
```
$ cd /vagrant
```

and finally
```
$ cd Sports-Project.
```
Time to set up the project!

# Execution
You need to run the following python files first to set up the database and add sample items to your newly made database.  As of the time of my writing this, I am using the following version of python:
```
$ python --version
Python 2.7.12
```
Now run the following commands from the bash terminal.
```
$ python database_setup.py
$ python sample_items.py
```

And finally:
```
$ python application.py
```

You'll see a response in your terminal saying "* Running on http://0.0.0:8000/ (Press CTRL+C to quit)".  At this point you'll know your server is running, and can be accessed from a browser after hitting enter in the search bar filled with http://localhost:8000/.

*** Please note that this project uses client_secrets from both facebook and google.  You'll have to make a new project on their developer websites found ([here](https://developers.facebook.com/) and [here](https://developers.google.com/oauthplayground/)) and populate the following files `client_secrets.json` and `fb_client_secrets.json` and place them in the Sports-Project directory for successful execution.  The 'client_secrets' file from each of the OAuth2 providers is the Credential JSON download that will be available for you after making a new project.

### Python Library Dependencies

Successful execution requires the standard python library for python2.  I am using Ubuntu version 16.04.  I am running this in a virtual machine, installed with Vagrant and Virtual Box.  Please see the above if you want to see replicate my environment. The following dependencies are also required and will be already installed if running the virtual machine indicated as above.

For users not running the virtual machine, I will list out the packages and the versions that I have installed as of the time of me writing this.  To install any of the following packages, simply open a new bash terminal and write `$ pip install {package}`, of course replacing `{package}` with whatever you desire, like so `$ pip install flask`.  Depending on your user permissions, you may need to try to following to successfully install packages. `$ pip install {package} --user`.  If that doesn't work, one may need to use the following: `$ sudo pip install {package}`.
```
>>> flask.__version__
'1.0.2'
>>> httplib2.__version__
'0.11.3'
>>> requests.__version__
'2.18.4'
>>> oauth2client.__version__
'4.1.2'
>>> sqlalchemy.__version__
'1.2.7'
```

If you're having issues with a particular library, you can install any library's version with the following command. The below example is installing a specific version of flask, please change the package name to whatever suits your needs, and note that if you needed `--user` or `sudo` in the install, you'll need it down here too.

```
$ pip install flask==1.0.2 --user
```

# JSON API Endpoints:
To view all of the categories and their associated IDs (which will be helpful for further endpoints), send a GET request to:
```
localhost:8000/sports/JSON/
```

To view all of the items for a category of id '#', send a GET request to:
```
localhost:8000/sports/#/JSON/
```

To view all a single item of id '##' for a category of id '#', send a GET request to:
```
localhost:8000/sports/#/items/##/JSON/
```

As one can see, navigation of the API is contingent on a client's ability to identify the 'id' property of categories and items.  Happy requesting!

# Contributing
I am not looking for contributors as of the time of me writing this.
# Bugs
Please reach out to the project's author Jack Dealtrey at github@macavich for issues!
