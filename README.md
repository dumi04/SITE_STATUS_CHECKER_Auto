🌐 Website Uptime Monitor with Alerts & Google Sheets Integration
This project is an automated workflow in n8n that monitors the availability of websites listed in a Google Sheet, performs health checks, sends status email alerts via Gmail, and updates the sheet accordingly.

📋 Features
⏰ Scheduled Monitoring (daily at 8 AM)
📊 Read URLs and email addresses from a Google Sheet
🌐 HTTP requests to test website availability
🔀 Conditional logic to determine site status
📧 Email notifications sent for both online and offline states
📝 Google Sheets update for current site status (OK / PICAT)

🛠 Workflow Steps Overview
Schedule Trigger

Runs every day at 08:00 AM.

Get row(s) in sheet

Fetches domain names and associated email addresses from a Google Sheet.

Edit Fields

Formats a URL using the domain field from the sheet.

HTTP Request

Sends a GET request to the constructed URL to check site availability.

If

Evaluates whether an error was returned by the HTTP request:

If site is down:

Sends an email with the subject ❌ Status: site-ul nu răspunde.

Updates the Status column in the Google Sheet to PICAT.

If site is online:

Sends an email with the subject ✅ Site ul functioneza in parametrii

Updates the Status column to OK.

🧩 Dependencies
n8n

Google Sheets (OAuth2 credentials)

Gmail (OAuth2 credentials)

🧾 Google Sheet Format
Domeniu	Email	Status
example.com	user@example.com	OK/PICAT

✉️ Email Notification Samples
If site is DOWN:
❌ Status: site-ul nu răspunde.
În urma verificării automate efectuate la data de {{$now}}, vă informăm că site-ul {{ Domeniu }} nu a putut fi accesat.
Vă recomandăm să verificați starea serverului sau conexiunea rețelei cât mai curând posibil.

If site is ONLINE:
✅ Site-ul functionează în parametrii
În urma verificării automate efectuate la data de {{$now}}, vă informăm că site-ul {{ Domeniu }} este activ și răspunde în mod corespunzător.

📌 Customization
Modify the scheduled time in the Schedule Trigger node.
Adjust the sheet structure or add additional logic as needed.
Personalize email templates for branding or localization.

🔐 Credentials Required
Ensure these accounts are connected in n8n:
Google Sheets account (OAuth2)
Gmail account (OAuth2)

🚀 Usage
Import the workflow JSON into your n8n instance.

Set up Google Sheets and Gmail credentials.

Replace placeholder DOC_ID, sheet_namea, etc. with your actual sheet info.

Activate the workflow.

📞 Support
If you need help with deployment or customization, feel free to reach out!
