LTS DRIVER MESSENGER — SETUP

This is a separate support app. It does NOT change FleetControl.

FILES
- LTS_Driver_Messenger.xlsx : contact database template with 220 current driver IDs/names
- Code.gs                  : Google Apps Script backend
- Index.html               : web app
- README.txt               : this file

1) CREATE THE GOOGLE SHEET
Upload LTS_Driver_Messenger.xlsx to Google Drive.
Open it with Google Sheets and save/convert it as a Google Sheet.

The workbook contains:
- Contacts
- Send History
- Settings

There is intentionally NO Active column.
When somebody leaves, delete them from Contacts.
When someone starts, add them.

2) ADD APPS SCRIPT
From that Google Sheet:
Extensions -> Apps Script

Replace Code.gs with the supplied Code.gs.
Create a new HTML file named exactly:
Index

Paste the supplied Index.html into it.

Save.

3) INITIALIZE
In Apps Script, select:
setupMessenger

Click Run once and approve permissions.

This stores the spreadsheet ID and ensures the formatting/sheets are ready.

4) QR FOLDER FOR CURRENT USE
Unzip your driver QR PNG package with names.
Upload all PNGs to ONE Google Drive folder.

Files should be named by Driver ID:
2022.png
6196.png
4634.png
...

Open the Drive folder and copy its folder ID from the URL.

In the Settings sheet, paste it next to:
QR_FOLDER_ID

Now "Each driver's QR" automatically matches Driver ID 2022 to 2022.png, etc.

5) CONTACT DATA
In Contacts, fill:
- Email
- WhatsApp Phone

Cells wrap and fit content. Missing contact cells are highlighted.

6) DEPLOY THE WEB APP
Apps Script:
Deploy -> New deployment -> Web app

Execute as:
Me

Who has access:
Choose the access level appropriate for your company/account.

Deploy and open the /exec URL.

7) HOW TO USE
You can:
- search
- Select All Visible
- select only a few drivers
- write one global message and apply it
- change any driver's personal message
- send each selected driver a different message
- send each driver's own QR
- send each driver's own personal Drive file
- send the same Drive file to everyone
- send message only
- add/delete drivers
- see every attempt in Send History

Placeholders supported:
{name}
{id}
{email}
{phone}

Example:
Hello {name},

Your Driver ID is {id}. Your personal QR is attached.

8) EMAIL
Email works through Google Apps Script / MailApp.
Google account daily recipient quotas apply.
The app shows the remaining Apps Script email quota.

9) WHATSAPP
Automatic WhatsApp requires a WhatsApp Business Cloud API setup.

Fill these Settings only if you have it:
WHATSAPP_PHONE_NUMBER_ID
WHATSAPP_ACCESS_TOKEN
WHATSAPP_GRAPH_VERSION

Important:
WhatsApp/Meta rules can require an approved message template for
business-initiated messages outside the permitted customer-service window.
The included direct text/image function is intended for conversations where
your Meta setup allows that message type. Failed sends are recorded in history.

Keep the Settings sheet PRIVATE because an access token is a secret.

10) SAFETY
Test with 1-2 drivers before selecting everyone.
Check the Send History after the test.
