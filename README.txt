LTS DRIVER MESSENGER — GITHUB PAGES VERSION

ARCHITECTURE
GitHub Pages index.html
        ↓
Google Apps Script /exec backend
        ↓
Google Sheet + Google Drive + Email
        ↓
Optional WhatsApp Business Cloud API

Your main FleetControl app is NOT changed.

FILES
- index.html                  -> upload to NEW GitHub repository
- Code.gs                     -> paste into Apps Script
- LTS_Driver_Messenger.xlsx   -> Google Sheet template
- README.txt                  -> setup instructions

--------------------------------------------------
1. GOOGLE SHEET
--------------------------------------------------
Upload LTS_Driver_Messenger.xlsx to Google Drive.
Open it with Google Sheets and convert/save it as a Google Sheet.

Sheets:
- Contacts
- Send History
- Settings

No Active column is used.
Delete people who leave.
Add new people when they start.

--------------------------------------------------
2. APPS SCRIPT BACKEND
--------------------------------------------------
Open the Google Sheet.

Extensions -> Apps Script

Replace the code with Code.gs from this package.

Save.

Select function:
setupMessenger

Click Run once.

Approve permissions.

--------------------------------------------------
3. QR FOLDER
--------------------------------------------------
Upload your personal driver QR PNG files to ONE Google Drive folder.

Example:
2022.png
6196.png
4634.png

In the Settings sheet, paste the Google Drive folder ID next to:
QR_FOLDER_ID

Now the app automatically matches:
Driver 2022 -> 2022.png
Driver 6196 -> 6196.png

--------------------------------------------------
4. DEPLOY APPS SCRIPT
--------------------------------------------------
Apps Script:

Deploy -> New deployment
Type -> Web app

Execute as:
Me

Who has access:
Choose the access level appropriate for your use.
For GitHub Pages access, the deployed endpoint must be accessible
to the people using the GitHub app.

Deploy.

Copy the URL ending in:
/exec

Example:
https://script.google.com/macros/s/XXXXXXXXXXXX/exec

--------------------------------------------------
5. PUT THE APPS SCRIPT LINK IN GITHUB HTML
--------------------------------------------------
Open index.html.

Near the bottom find:

const API_URL = 'PASTE_YOUR_APPS_SCRIPT_EXEC_URL_HERE';

Replace only the text between the quotes:

const API_URL =
'https://script.google.com/macros/s/XXXXXXXXXXXX/exec';

Save index.html.

--------------------------------------------------
6. GITHUB PAGES
--------------------------------------------------
Create a NEW GitHub repository, for example:

LTS-Driver-Messenger

Upload:
index.html

Commit.

Repository:
Settings -> Pages

Source:
Deploy from a branch

Branch:
main

Folder:
/ (root)

Save.

Your app will look like:

https://YOUR-USERNAME.github.io/LTS-Driver-Messenger/

--------------------------------------------------
7. CONTACTS
--------------------------------------------------
Fill these in Contacts:

Driver ID
Name
Email
WhatsApp Phone
Default Message
Personal File / Drive File ID
Notes

Phone example:
+436601234567

--------------------------------------------------
8. EMAIL
--------------------------------------------------
Select all or only some drivers.

Each driver can have a different message.

Attachment options:
- Each driver's QR
- Each driver's personal Drive file
- Same Drive file for everyone
- Message only

Then:
SEND SELECTED BY EMAIL

Email is sent by the Google account that owns/runs the Apps Script backend.

Google Apps Script / Gmail daily quotas apply.

--------------------------------------------------
9. NORMAL WHATSAPP
--------------------------------------------------
Your current normal WhatsApp account can use:

OPEN NORMAL WHATSAPP QUEUE

The app goes driver by driver and opens:
wa.me/<driver-phone>

with that driver's personalized message already filled.

A normal browser/WhatsApp account cannot automatically attach
each driver's personal PNG in bulk.

--------------------------------------------------
10. WHATSAPP CLOUD API — OPTIONAL LATER
--------------------------------------------------
If you later use the official WhatsApp Business Cloud API, fill:

WHATSAPP_PHONE_NUMBER_ID
WHATSAPP_ACCESS_TOKEN
WHATSAPP_GRAPH_VERSION

Then the button:
WHATSAPP CLOUD API

can use the backend sender.

Meta template/conversation rules still apply.

KEEP THE SETTINGS SHEET PRIVATE.
The WhatsApp access token is a secret.

--------------------------------------------------
11. PERSONALIZATION
--------------------------------------------------
Supported placeholders:

{name}
{id}
{email}
{phone}

Example:

Hello {name},

Your Driver ID is {id}.
Your personal QR is attached.

Each driver receives their own name/ID automatically.

--------------------------------------------------
12. TEST FIRST
--------------------------------------------------
Before sending to everyone:

1. Add your own email/phone to one test driver.
2. Select only that driver.
3. Send a test.
4. Check Send History.
5. Then try 2-3 drivers.
6. Only after that select everyone.
