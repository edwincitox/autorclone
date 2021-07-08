〽️ AutoRclone is a python script built do copy google drives files and folders.

⚙️ Installation :
> Download and extract this GitHub repo<br>
> Download and install Python and pip https://www.python.org/downloads/<br>
> cd to the autorclone folder and run :<br>
> sudo pip install -r requirements.txt<br>

Create service account (tutorial here)<br>
https://drive.google.com/file/d/1K7rM7Y7lZxQyJmf4G1d-wqO0w7cUzWnv/view?usp=sharing<br>

The service accounts can be used to bypass the 750Gb/day upload limit set by google in google drive. It means that you can use them to upload more than 750Gb per day, duplicate hundreds of files...

Each service account has a 750Gb upload limit per day. You can create up to 100 service account per google cloud project. So, with only one project you can upload/duplicate up to 75Tb a day! 

> Go to the Google Cloud Console and if you don't have an existing project, create a new one https://console.cloud.google.com/<br>
> Then, enable the google drive api https://console.developers.google.com/apis/library/drive.googleapis.com?q=drive<br>
> Go to the OAuth Consent Screen and select "External" and click on "Create" https://console.cloud.google.com/apis/credentials/consent<br>
> Fulfill all required informations (the one with a red *) and click on "Save and Continue" 3 times (the "Scopes" and "Test users" parts do not require any inputs)<br>
> Click on publish and validate<br>
> On the credentials tab, click on "Create Credentials" then "OAuth client ID", select "Desktop app" https://console.cloud.google.com/apis/credentials<br>
> Click on the download button on the right of your OAuth Client IDs and save the file with the following name :  credentials.json<br>

If you want to create some service accounts using existing projects (do not create more projects)
run :
> py sa.py --quick-setup -1 <br>
⚠️ This will overwrite the existing service accounts. 

To create service accounts by creating a new project
run :
> py sa.py --quick-setup 1 replace "1" with the number of projects you want<br>
⚠️This command creates services accounts in all existing projects even the projects that will be deleted. 

After executing the code, follow the instructions...

Now, to get the email adresses of the service accounts, there is multiple ways to do it :
Windows users
> Open PowerShell and cd into folder the where you have the sa (the .json files)<br>
> Run : $emails = Get-ChildItem .\**.json |Get-Content -Raw |ConvertFrom-Json |Select -ExpandProperty client_email >>emails.txt<br>
Linux / MacOs users
> Run : grep -oPh '"client_email": "\K[^"]+' *.json > emails.txt<br>

Open the emails.txt file, copy all the email adresses and add them into the google group you've just created.

🛠 Usage :
> To duplicate team drives or copy files from public folders to team drive<br>
> run : py autorclone.py -s SourceID -d DestinationID -b 1 -e 100<br>

Change SourceID by the id of the source folder.<br>
Change DestinationID by the id of the destination folder.<br>
Change 100 with the number of sa you have.<br>

The minimum authorization needed for the source ID is : reader  and for the destination folder : contributor

> How to get the ID : <br>
> Google drive link : https://drive.google.com/file/d/1K7rM7Y7lZxQyJmf4G1d-wqO0w7cUzWnv/view?usp=sharing<br>
> the id is : 1K7rM7Y7lZxQyJmf4G1d-wqO0w7cUzWnv<br>

To upload files from your computer  run : py autorclone.py -sp LocalPath -d DestinationID -b 1 -e 100 

Change LocalPath with the path of the folder you want to upload.<br>
Change DestinationID by the id of the destination folder.<br>
Change 100 with the number of sa you have.<br>

Note : you can add the  --crypt  tag to encrypt your uploads (not recommended)
