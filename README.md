# PowerBI-Dashboard
What it is?
This is custom M365 Copilot Adoption Dashboard that uses Graph API (in beta) to grab data from your M365 tenant.
Some organizations, for various reasons, found existing reports in M365 Admin Portal, Viva insights or Copilot Dashboard not suitable for the purpose of driving adoption, hence there was the need for the custom dashboard. I developed this dashboard working with organizations that were in this position and needed insights into the adoption of M365 Copilot. Feedback and requirements provided by those organizations have been used as an input for the dashboard, within restrictions that provide Graph API at the moment (this dashboard is not using Audit Logs as data source). Now you can use this dashboard for M365 Copilot Adoption analysis in your tenant or as a starting point to further develop your own custom dashboard.
Please provide your feedback or ideas via this form.

Change log
October 23rd 2026:

Graph API report functions changed in beta again, this time adding versions and change Dn period. This template is updated with latest beta/reports.
July 22nd 2026:

Graph API report functions changed in beta, so dashboard stopped working. The fix is to replace beta/reports/ with v1.0/copilot/reports/ in the URL used in each of the three queries, keeping the same period parameter and format option.
February 11th 2026:

Bug Fix - Card visual after PBI update shows larger icons than planned - this was fixed
Bug Fix - Table 'X' contains a duplicate value '(Unknown)' - fixed (for some reason some graph funcions picked up Unknown for UPN for several users and that caused relationship errors). New version is filtering those values and error is not present any more. If you customized table a lot, and don't want to re-use template fix this error on your own by filtering 4 tables (Teams User Detail, OneDrive Activity User Detail, M365 Apps User Detail and Email User Details) as shown: Unknown error fix.
June 26th 2025:

Bug Fix - Users page now shows only currently licensed users. Previous version kept users with removed license which resulted in showing incorrect total number of Copilot users with license and inconsistencies in the report.
Readiness score now includes Audio Duration for Teams.
Organizational Insights: Copilot vs Non-Copilot Users - new page that replaces previous Organization and insights page. New page contains more relevant behavioral information. Please find details below.
Semantic Model - imported email activity user detail (used for org insights).
Overview and Functionalities
This dashboard contains four pages:

Overview
Users
Readiness
Organizational Insights: Copilot vs Non-Copilot Users
1. Overview and History
Screenshot showing overview.

Card shows active users % and total number of active users in the last 30 days (Active users # is the total number of users with Copilot license in your organization who tried a user-initiated Microsoft 365 Copilot feature).
Shows user distribution per Copilot usage in different apps (Where the prompt has been triggered from, have in mind single user can run Copilot in different tools so that means same user can contribute to Word and Excel values in the chart)
Top 10 departments in the organization per number of active users (Departments are taken from Entra ID field department)
Slicer for Copilot details in Chart 7.
Slicer to show total number of licenses or not in Chart 7. (purple line)
Buttons to select if you want to see absolute or % usage values (numbers or %) in Chart 7.
6 months aggregated historical overview of active users. Axis slider enables zoom in. When using % you can drill down on daily level.
2. Users
This page shows details about users with assigned M365 Copilot license. Screenshot showing overview.

Card shows M365 Copilot enabled users (with license assigned) [*See known issues](## Known Issues)
Enabled users are distributed in 4 sub categories: a. Active Users - the ones that had at least 1 prompt in any of the M365 Copilot interfaces in the last 30 days
b. Churned Users - users that had at least 1 prompt in any of the M365 Copilot interfaces in between 30 and 60 days from last refresh time
c. Lost Users - users that had at least 1 prompt in any of the M365 Copilot interfaces 60+ days ago from last refresh time
d. Enabled but never active - number of users who were assigned M365 Copilot license but they never used it (not a single prompt)
Slicer to select mentioned categories and show the list in table 7.
Keyword filter (if you are looking for particular user by name)
Slicer to show Champion material (most engaged users by the number of apps where they use Copilot in) In essence they have maturity rating above 5 (see definition for Maturity rating on the page)
Filter per Company, Department or Country - taken from Entra ID.
Table with names and other details based on selection. You can select each user individually to see details in cards 8.
Cards that show the last date of usage for M365 Copilot in each tool (if user is active). For inactive users, card will be marked in red without any date. [*See known issues](## Known Issues)
3. Readiness
This page shows details about all users from Microsoft Entra ID (excluding service and external accounts) withouth M365 Copilot License assigned. Screenshot showing overview.

Card shows number of Entra ID users (excluding service and external accounts) without M365 Copilot License assigned.
Users are distributed in 4 sub categories based how "good" are they in using M365 services (as you want to assign Copilot license to user that is already mature user of M365 rather than to someone who is not yet there): a. Priority A - 11+ points for M365 usage (definition is provided on the page itself) b. Priority B - 4.5 to 10.5 points c. Priority C - less than 4.5 points d. Priority D - 0 points (you really don't want to assign Copilot license to these users)
Slicer to select mentioned categories and show the list in table 4.
Table with names and other details based on selection. You can select each user individually to see details in cards 5.
Cards that show per user usage of some of the M365 Features (Apps - if a user is viewing/editing files in any of apps, Teams Activity - what user does in Teams, OneDrive Activity - what users do with files in their OneDrive)
4. Organizational insights: Copilot vs Non-Copilot Users
This page shows behaviors of Copilot vs Non-Copilot users for common M365 metrics. Screenshot showing overview.

Average values of Teams activities including calls, meetings (organized), channel and chat messages and audio, video and screen share duration for the past 30 days.
Average values of OneDrive activities including viewed/edited files, synced files and shared files for the past 30 days.
Average values of Email activities including emails sent, received and read over the past 30 days.
Copilot license distribution per department - how many users is in each department with copilot license vs total number employees.
Filter for the license distribution stacked bar chart
Setup Instructions
You need to take following steps:

Register Graph API app
Install the latest version of Power BI desktop and configure it
Download and run template
1. Registration of Graph API app
Sign in to the Azure portal. (For these actions you need at least Cloud Application Administrator role.)
Go to Microsoft Entra ID > App registrations. Screenshot showing the Entra app registration.
Select + New Registration.
Enter a name. For example, use the Copilot Graph API name. Don't change any other settings and select Register.
Select API Permissions > + Add a permission. Screenshot that shows API permissions.
Select Microsoft Graph and configure permissions as follows: Screenshot showing permissions.
Don't forget to add Grant Admin Consent for (your organization).
Select Certificates and secrets.
Select + New client secret.
Add a description and expiration (in line with your organization's policies), and then select Add.
Copy and paste the Secret to a text document such as Notepad. Screenshot showing secret.
Select Overview and copy and paste the application (client) ID and Directory (tenant) ID value to the same text document. Be sure to make a note of which GUID is for which value. Screenshot showing tenant ID and client ID.
2. Get Latest Version of Power BI Desktop and configure
If you don't have it, you can download it from here
Once installed start Power BI desktop. Go to File > Options and Settings > Options
Enable Text Slicer Visual under Preview features (you will have to restart app) Screenshot showing Power BI configuration.
3. Download and run the template (.pbit)
Download template.
Start template.
Enter required parameters that you collected in step 1. of the setup. Screenshot showing template.
Wait for data to load.
Replace Insert Company Logo image with real logo of your organization. Look for how to insert image in Power BI desktop if you don't know how.
Screenshot showing logo.
REQUIRED: Save your file as PBIX. Remember this is just a template loaded with data - until you save the file as pbix.
Optional: Publish and configure daily scheduled refresh. Again, look on the internet for details. If you have credential issues, make sure they follow these settings and everything should work:
Screenshot showing credentials.
Known Issues
Due to standard report features - Copilot activity on a given day, the report becomes available within 72 hours of the end of that day (in UTC) - you might notice delays even when refreshing dashboard for some values up to 3 days from the refresh time.
On the users page you might have situation where certain user has Last Activity Date not empty, while at the same time other cards (Teams, Chat, Outlook...) show empty values. My assumption is that these are users who use Copilot Chat (web) and they don't have M365 Copilot License assigned. Why this happens I still have no confirmation or reasoning behind it, but I will update this once either more details are provided, or Graph API is updated with Copilot Chat functions.
Unknown Issues
I am not quite sure about Graph API limits to query large number of objects (if they exist). There might be some limit for data to be loaded (like I saw somewhere 10000 Entra ID entries, but I cannot confirm or deny this one) Let me know if you know.
