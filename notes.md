## CLASS NOTES AND README IN PROGRESS
## HTTPS gave me issues with tokens on Mac so I nuked my repo and got help from ChatGPT and GitHub docs to use SSH keys instead.
## Using GitHub official docs to help note the process for future reference.

### Check for existing SSH keys [^1]
1. Open Terminal
2. Enter `ls -al ~/.ssh` to show existing SSH keys
3. If an error states  that ~/.ssh doesn't exist, there are no SSH key pairs in the default location.
4. Generate a new SSH key (if none exist).
<br>
<br>

### Generate a new SSH key [^2]
1. Open Terminal
2. Enter `ssh-keygen -t KEYNAME -C "your_email@example.com"`
    - Give your key a descriptive name that is descriptive. A naming system that includes the device, environment, and purpose will help you organize your keys. e.g., `macbook-macos-github-kirkaltonclass7`
    - The phrase after `-C` is a label. Feel free to label your key however you see fit. e.g., `-C "GitHub Key @KirkAlton-Class7`
3. When instructed to "Enter a file in which to save the key", press enter for the default location.
4. When prompted for a passphrase, press enter to leave blank (no passphrase). Alternatively, you can type a passphrase for added security, then press enter.
5. Press enter again (no passphrase) or type the passphrase again to confirm.
6. If you encounter issues, refer to the GitHub documentation for additional troubleshooting steps.
<br>
<br>

### Add your SSH key to the ssh-agent [^2]
1. Start the ssh agent:
``` sh
eval "$(ssh-agent -s)"
 ```
2. If using macOS,Sierra 10.12.2 or higher: edit the `~/.ssh/config` file to automatically load keys into the ssh-agent and store passphrases in your keychain.
    - Check if the `~/.ssh/config` file exists in the default location.
``` sh
open ~/.ssh/config
 ```
3. If the file doesn't exist, create it.
``` sh
touch ~/.ssh/config
```
4. Modify `~/.ssh/config` to contain the following lines:
```python
Host github.com
  AddKeysToAgent yes
  UseKeychain yes
  IdentityFile ~/.ssh/id_ed25519
```
- <b>Note:</b> You can omit the `UseKeychain` line if you did not add a passphrasae to the key.
<br>

5. If you encounter issues, refer to the GitHub documentation for additional troubleshooting steps.
<br>
<br>

### Add the SSH Key to Your GitHub Account [^3]
1. Open terminal and navigate to the
2. Copy the contents of your public SSH key:
```sh
$ pbcopy < ~/.ssh/KEYNAME.pub
```
3. If `pbcopy` doesn't work, locate the hidden `.ssh` folder in your OS file structure, then open it in a text editor and copy it to the clipboard.
4. On GitHub, click your profile and select "Settings".
5. In the "Access" sidebar, click "SSH and GPG Keys"
6. Click "New SSH Key" or "Add SSH Key".
7. Add a descriptive label for the new key.
8. Select the type of key (authentication or signing).
9. Paste the contents of your public key.
10. Click "Add SSH Key".
<br>
<br>



1. Create a new repo on GitHub

In upper lefthand corner click "repositories"
In upper right hand corner click "new"
Name your repository. Choose a naming system that helps you organize your repos. e.g., homework_09.23.2025_class7
Add a brief description of your repo.
Make public if sharing
Click "create repository"
If the quick setup screen shows, click SSH and copy the contents of the field.
If inside your repo, click "Code" select "SSH" and copy the contents of the field
e.g., `git@github.com:KirkAlton-Class7/hmwk_09.23.2025_class7.git`
This is your repo's remote. Paste it in a separate text file. It will be used in the next step.


Create a local repo:
1. Navigate to where you store your repos and creae a new directory.
2. Open terminal and navigate to the repo directory
3. create the local repo on your computer
`git init`
3. add your Github (remote) repo into your git index and name "origin"
`git remote add origin <your remote>`
4. # Rename default branch from "master" to "main" (preferred name)
git branch -M main
5. Stage files for upload
`git add <files to stage>`
6. # Save a "snapshot" of the files in staging
git commit -m "<message name>"
7. Push files to GitHub repo
# Upload commited changes from local repo
# Targets the "main" branch on the remote repo named "origin"
# -u sets the "upstream defaults" meaning after this you don't need them if you want to use the "main" branch on the remote repo "origin"
git push -u origin main

After first push, you can run `git push` to push files to the repo
You can run `git pull` to pull files from the repo and sync changes.
You an set up the repo to share the files and sync changes with multiple machines.



References
[^1] Checking for existing SSH keys: https://docs.github.com/en/authentication/connecting-to-github-with-ssh/checking-for-existing-ssh-keys
 

[^2] Generating a new SSH key and adding it to the ssh-agent: https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent

[^3] AdAdding a new SSH key to your GitHub account: https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account




d the SSH Key to Your GitHub Account




$ ls -al ~/.ssh

#### Generate a new SSH key and add it to the SSH agent.
#### Press enter to save to the default location.
ssh-keygen -t ed25519 -C "your_email@example.com"

#### Enter a file to save the key
/Users/YOU/.ssh/id_github_key

#### When prompted for a password, press enter for no password or type a password for additional security.
#### Press enter again for no password, or type password again to confirm.

#### Start the ssh-agent
$ eval "$(ssh-agent -s)"

#### If using macOs, modify ~/.ssh/config file to automatically load keys into the ssh-agent and store passwords in your keychain
$ open ~/.ssh/config

#### If the file doesn't exist, create the file.
touch ~/.ssh/config

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




MERGE BAM

git merge no ff
VIM
i = insert mode
Edit note and add merge comments

Escape to return to normal mode

: to enter command mode
wq to save and quit

git push to send changes to origin
