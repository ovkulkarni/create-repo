#!/usr/local/bin/python3
import requests
import yaml
import sys
import json
import getpass

with open('config.yml', 'r') as f:
    config = yaml.load(f.read())

password = getpass.getpass("Enter your Github Password: ")
repo_name = str(input("Enter the name of the repo: "))
repo_desc = str(input("Enter a description for the repo: "))
repo_homepage = str(input("Add a homepage url for more info about the repo (OPTIONAL): "))
valid = ['y', 'n']
repo_priv = 'n'
if config["paid_account"]:
    repo_priv = str(input("Do you want this repo to be private? (y or n): "))
    if not repo_priv in valid:
        repo_priv = str(input("Please enter either y or n: "))
    if not repo_priv in valid:
        print("Invalid Input! Exiting...")
    sys.exit()
if repo_priv == 'n':
    private = False
else:
    private = True

repo_issues = str(input("Do you want this repo to have issues enabled? (y or n): "))
if not repo_issues in valid:
    repo_issues = str(input("Please enter either y or n: "))
if not repo_issues in valid:
    print("Invalid Input! Exiting...")
    sys.exit()

if repo_issues == 'n':
    issues = False
else:
    issues = True

repo_wiki = str(input("Do you want this repo to have the wiki enabled? (y or n): "))
if not repo_wiki in valid:
    repo_wiki = str(input("Please enter either y or n: "))
if not repo_wiki in valid:
    print("Invalid Input! Exiting...")
    sys.exit()

if repo_wiki == 'n':
    wiki = False
else:
    wiki = True

repo_downloads = str(input("Do you want this repo to have downloads enabled? (y or n): "))
if not repo_downloads in valid:
    repo_downloads = str(input("Please enter either y or n: "))
if not repo_downloads in valid:
    print("Invalid Input! Exiting...")
    sys.exit()

if repo_downloads == 'n':
    downloads = False
else:
    downloads = True

repo_init = str(input("Do you want this repo be initialized with an empty README? (y or n): "))
if not repo_init in valid:
    repo_init = str(input("Please enter either y or n: "))
if not repo_init in valid:
    print("Invalid Input! Exiting...")
    sys.exit()

if repo_init == 'n':
    init = False
else:
    init = True

session = requests.Session()
session.auth = (config["username"], password)
data = {
        "name": repo_name,
        "description": repo_desc,
        "homepage": repo_homepage,
        "private": private,
        "has_issues": issues,
        "has_wiki": wiki,
        "has_downloads": downloads,
        "auto_init": init
        }
url = 'https://api.github.com/user/repos'
print('[=] Sending request to Github...')
r = session.post(url, json.dumps(data))
if r.status_code == 201:
    returned = json.loads(r.text)
    html_url = returned["html_url"]
    if config["ssh"]:
        clone_url = returned["ssh_url"]
    else:
        clone_url = returned["clone_url"]
    name = returned["name"]
    print("[+] Repository '{}' Created".format(name))
    if init:
        print('To clone this repository to your computer, do `git clone {}`'.format(clone_url))
    else:
        print('To initialize this repository in an existing folder, do `git init` and then `git remote add origin {}`'.format(clone_url))
    print("To access this repository online, go to {} in your web browser".format(html_url))
else:
    print("[-] The repository was unable to be created. Github returned an error of {}".format(r.status_code))
    print("[-] Here is the full content Github returned: {}".format(json.loads(r.text)["message"]))
