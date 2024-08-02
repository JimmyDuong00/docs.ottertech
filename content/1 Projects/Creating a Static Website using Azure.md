This post will cover how to create an Azure static web app using Quartz using Github Pages. 
This setup will allow you to write and quickly publish your blogs and projects using Markdown files. 
### (Optional) Create a Github Account
Note, a Github Account can only host a single webpage using Github Pages. If you already have an account without Pages enabled, skip this step.
Navigate to the Github website and create a free account using your preferred email.
## Clone the Quartz Repository
Navigate to Jacky Zhao's Quartz repository using this link https://github.com/jackyzha0/quartz

Click on the 'Use this template' button and select 'Create a new repository':

![[Pasted image 20240729084747.png]]

Name the repository to the domain name you purchased for the site. For example, if you purchased 'freedom.com' then enter that as the repo name. Select 'Public' or 'Private' depending on if you want your code to be readable to the public or not:

![[Pasted image 20240729085547.png]]

In your local computer, open CMD and run the command to login to authenticate through Github:
```
gh auth login
```
> Select HTTPS for the preferred protocol
> Authenticate Git with your Github credentials
> Authenticate with Github CLI through web browser

Enter your one time code to the browser that opened:
Navigate to the folder where you want the files to be located at:
Run the github pull command to pull all the files locally:
```
git pull [Insert Repo Name Here]
```

You now have successfully integrated your Github repository locally.

## Build the Application Locally
Initialize the application 
```npm i```: 
![[Pasted image 20240729091523.png]]

Create the website ```npx quartz create```:

![[Pasted image 20240729091744.png]]

Build the application ```npx quartz build```:

![[Pasted image 20240729093854.png]]

Serve the website locally ``` npx quartz build --serve```:

![[Pasted image 20240729093829.png]]

Access the website using a web browser using ```http://localhost:8080/```
Enter the address in your web browser and you will see your website appear:

![[Pasted image 20240729093744.png]]

You have successfully generated your static site and served it locally.
## Create a Static Web App in Azure
This step will go over how to connect Azure to your Github Account and use CI/CD to automatically publish new content when you commit to the repository.

Navigate to the Azure Static Web Apps portal and select the 'Create' button:

![[Pasted image 20240729100352.png]]

In this form, choose and fill out:
Resource group: Create a new resource group for this project
Name: Give the static web app a name
Hosting plan: Select free
Deployment details: Select GitHub and select the 'change account or add account' button.

![[Pasted image 20240729100823.png]]

When you select the change account button, you will give permissions to Authorize App Service:

![[Pasted image 20240729101131.png]]

After allowing Azure to connect to your Github, select the Organization, Repo, and Branch you want Azure to deploy. 
Fill in the build details:
Build presets: Custom
App location: /
Api location: leave blank
Output location: /dist

![[Pasted image 20240729101522.png]]
Select create once done.





## Configure DNS

## Writing for Your Site
### Setup Obsidian
### Setup Github Desktop
