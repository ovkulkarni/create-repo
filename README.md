#Repo Creation Command Line Tool
**This tool requires python3**

If you do not have virtualenv installed, install it by running `sudo pip install virtualenv`

##Set Up
1. Create a virtual environment by doing `virtualenv venv -p python3`
2. Activate the virtual environment by doing `source venv/bin/activate`
3. Clone this repository onto your computer by doing `git clone https://github.com/ovkulkarni/create-repo.git`
4. Change into the directory by doing `cd create-repo`
5. Move config.example.yml to config.yml by doing `mv config.example.yml config.yml`
6. Edit config.yml to have a similar structure to the one below
```yaml
    username: ovkulkarni
    paid: false
    ssh: false
```
##Install Dependencies
1. Install all the dependencies by doing `pip install -r requirements.txt`
2. Make the python program executable by doing `chmod +x create`

##Create a Repo
1. Create a repository by running `create`. It should look something like this:
```
    $ ./create
    Enter your Github password: 
    Enter the name of the repo: create-repo
    Enter a description for the repo: Create Github Repositories From the Command Line
    Add a homepage url for more info about the repo (OPTIONAL):
    Do you want this repo to have issues enabled? (y or n): y
    Do you want this repo to have the wiki enabled? (y or n): y
    Do you want this repo to have downloads enabled? (y or n): y
    Do you want this repo be initialized with an empty README? (y or n): n
    [=] Sending request to Github...
    [+] Repository 'create-repo' Created
    To initialize this repository in an existing folder, do `git init` and then `git remote add origin https://github.com/ovkulkarni/create-repo.git`
    To access this repository online, go to https://github.com/ovkulkarni/create-repo in your web browser
```

****This repository was created using this tool****
