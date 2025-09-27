
# Lab Notes
## <i>09.12.2025</i>

### Budgets
Budgets help you stay aware of costs. Setting up a monthly cost budget and zero spend budget can help prevent surprise bills.

#### Setting up a Monthly Budget
1. Search for "Billing and Cost Management" in the search bar.
2. Click "Budgets" and select "Create Budget".
3. Use a template (or select "customized" to set up threshold ntifications and other additional features.)
4. Choose the "Monthly cost budget" type.
5. Enter the budget name, budgeted amount, and specify email recipients.
6. Click create budget.

#### Setting up a Zero Spend Budget
1. In the Billing and Cost management console, create another budget.
2. Use a template or set up a customized budget.
3. Select the "Zero spend" budget type.
4. Enter the budget Name, budgeted amount, and specify email recipients
5. Click create budget.
<br>
<br>

### AWS Regions
#### Regions and Availability Zones
- AWS Regions are deployed depending on existing infrastructure in a geographical region. AWS deploys only in geographical locations that have the infrastructure to support AWS services.
- All regions contain a minimum of 3 availability zones.
- Some regions have more. For example, the North Virginia region is one of the oldest and most developed AWS regions. It contains 6 availability zones.
- You can choose to work in any AWS Region. The cost is generally the same.

#### Requesting Access to a Region
1. Click your current region name in the overhead display (or click "Global" if currently on a page for a global service.)
2. In the drop down menu scroll to the bottom and select "manage regions."
3. In the AWS Regions pane, select the regions you want access to and click "Enable" to request access to the region.
4. Regions can also be disabled by selecting a region and clicking "Disable."

#### A Note about Employers and Regions
Many organizations prefer to work out of regions that are closest to their customers. When on the job, make sure you are aware of these preferences and any best practices. Set your region(s) accordingly so you comply with the requirements of your employer.
<br>
<br>

### EC2 Instances, Launch Templates, and Template Versions
#### Launching an EC2 Instance
1. Follow the instructions from Week 1 for creating a security group and launching an EC2 instance.

#### Creating a Launch Template from an instance
1. In the EC2 console click "Instances" >> "Actions" >> "Image and templates" >> "Create template from instance."
2. Name the Launch Template
3. Add a description
4. Click create launch template

#### Launching an Instance From Template 
1. In the EC2 console click "Instances" >> "Action" >> "Image and templates" >> "Launch instance from template."
2. Double check configurations and launch the instance

#### Modifying a Launch Template
1. IN EC2 console click "Launch Templates" and click the ID of a launch template.
2. Click "Actions" >> "Modify template."
3. Add a template version description
4. Modify the template by editing the script in "Advanced Details."
5. Edit the HTML line that contains:
```html
<img src="IMAGE URL LINK" alt="image description">
```
6. Replace the image url with any link you want, then edit the image description.
7. Click "Create template version."

#### Launch an EC2 Instance from a Template Version
1. Launch a new EC2 instance from the template.
2. Template versions can be selected in the "Select a launch template version" drop down menu.

### Clean Up
- <b>Terminate all instances and clean up clutter from lab</b>
- Follow EC2 Teardown instructions from Week 1 if needed.
- Deleting templates is optional.







## CLASS NOTES AND README IN PROGRESS
## HTTPS gave me issues with tokens on Mac so I nuked my repo and got help from ChatGPT and GitHub docs to use SSH keys instead.
## Using GitHub official docs to help note the process for future reference.

#### Check for existing SSH keys
https://docs.github.com/en/authentication/connecting-to-github-with-ssh/checking-for-existing-ssh-keys
$ ls -al ~/.ssh

#### Generate a new SSH key and add it to the SSH agent.
#### Press enter to save to the default location.
https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent
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

