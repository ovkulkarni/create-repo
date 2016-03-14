#Repo Creation Command Line Tool
**This tool requires python3**


##Configuration
1. Move config.example.yml to config.yml by doing `mv config.example.yml config.yml`
2. Edit config.yml to have a similar structure to the one below
```yaml
    username: ovkulkarni
    paid: false
    ssh: false
    defaults: false
```

**ONLY IF YOU WANT TO USE DEFAULTS**

1. Move defaults.example.yml to defaults.yml by doing `mv defaults.example.yml defaults.yml`
2. Edit defaults.yml to have a similar structure to the one below
```yaml
    private: false
    issues: true
    wiki: true
    downloads: true
    init: false
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
