
# Lab Notes
## <i>09.12.2025</i>

## CLASS NOTES AND README IN PROGRESS
### HTTPS gave me issues with tokens on Mac so I nuked my repo and got help from ChatGPT and GitHub docs to use SSH keys instead. Using GitHub official docs to help note the process for future reference.
<br>
<br>

### Check for existing SSH keys
https://docs.github.com/en/authentication/connecting-to-github-with-ssh/checking-for-existing-ssh-keys

```sh
ls -al ~/.ssh
```


#### Generate a new SSH key and add it to the SSH agent.
#### Press enter to save to the default location.
https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent

```sh
ssh-keygen -t ed25519 -C "your_email@example.com"
```


#### Enter a file to save the key

```sh
/Users/YOU/.ssh/id_github_key
```

#### When prompted for a password, press enter for no password or type a password for additional security.
#### Press enter again for no password, or type password again to confirm.

#### Start the ssh-agent
```sh
$ eval "$(ssh-agent -s)"
```



#### If using macOs, modify ~/.ssh/config file to automatically load keys into the ssh-agent and store passwords in your keychain

```sh
$ open ~/.ssh/config
```


#### If the file doesn't exist, create the file.
```sh
touch ~/.ssh/config
```


Open ~/.ssh/config file and modify the file to contain the following lines. If your SSH key has a different name or path, modify the filename or path to match your current setup

Host github.com
  AddKeysToAgent yes
  UseKeychain yes
  IdentityFile ~/.ssh/id_ed25519

#### Start SSH Agent
eval "$(ssh-agent -s)"

#### Create a public key
#### ed255199
ssh-add ~/.ssh/id_ed25519

ssh-keygen -t 

#### Check status of git repo
git status

#### Check branch name
git branch

git remote add


#### Link local repo to GitHub Rep
git remote add origin git@github.com:USERNAME/REPO.git

#### Ignore .DS_Store files globally on mac
#### Create global ignore file
git config --global core.excludesfile ~/.gitignore_global

#### Pipe ignore rule to file
echo .DS_Store >> ~/.gitignore_global

# Ignore files (.DS_Store and other unneccessary user config files or clutter)
.gitignore

# Remove files you don't want to track that have already been added to the repo (user config giles on Linux broke some settings on Mac. This command prevents this from happening again)
git rm --cached = “actually stop tracking the ones that already slipped in.”

### HEADING
Ipsum lorem. Ipsum lorem. Ipsum lorem. Ipsum lorem. Ipsum lorem. Ipsum lorem.
Ipsum lorem. Ipsum lorem. Ipsum lorem.Ipsum lorem. Ipsum lorem. Ipsum lorem.

#### Subheading
1. Ipsum lorem.
2. Ipsum lorem.
3. Ipsum lorem.