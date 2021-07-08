〽️ AutoRclone is a python script built do copy google drives files and folders.



⚙️ Installation :
Download and extract this GitHub repo
Download and install Python and pip
cd to the autorclone folder and run : pip install -r requirements.txt
Create service account (tutorial here)
Download the Rclone and extract it to the AutoRclone Folder (ex : for windows users, put the .exe file into the AutoRclone Folder).


🛠 Usage :
To duplicate team drives or copy files from public folders to team drive, run : py autorclone.py -s SourceID -d DestinationID -b 1 -e 100 
Change SourceID by the id of the source folder. 

Change DestinationID by the id of the destination folder. 

Change 100 with the number of sa you have.

The minimum authorization needed for the source ID is : reader  and for the destination folder : contributor
How to get the ID : 

Google drive link : https://drive.google.com/drive/folders/1mh5mZxmQCvtoVdc_eDHawpxgHfkghTXO?usp=sharing , the id is : 1mh5mZxmQCvtoVdc_eDHawpxgHfkghTXO





To upload files from your computer  run : py autorclone.py -sp LocalPath -d DestinationID -b 1 -e 100 
Change LocalPath with the path of the folder you want to upload. 

Change DestinationID by the id of the destination folder. 

Change 100 with the number of sa you have.

Note : you can add the  --crypt  tag to encrypt your uploads (not recommended)
