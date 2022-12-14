# MailboxDashboard
The purpose of this project is to build a dashboard that tracks key information and summary from the email tracker kept by the Epi Team of the Monkeypox Response unit in the Division of Global Migration and Response. With CDC's centerwide activation of the Monkeypox response, the Epi Unit's functional email box was then adapted to primarily receive and transmit information about Contact Investigations and Travel Restrictions whereas prior served as the main mailbox for all Monkeypox related inquiries and questions. 
The Epi Team requested to capture the summary of all the emails they have received before and after role changes to the mailbox in order to present findings to leadership for decision makings. After the creation of an email summary dashboard, the team lead requested for an additional tracker that will calculate the rate of contact investigations conducted by the team, if the team meets 24-24-24 hour process window. 

The data source is a Sharepoint List (needed to build connections with sharepoint and Power Automate to ensure daily updates at 6 AM of dashboard) where the team members had recorded daily entries to keep track of emails that they have received and answered or been placed on hold for further follow-up. In addition, the same workbook contains the daily entry tracking for their contact investigations. 

**Note: To maintain confidentiality, all information have been updated to have mock data: real names replaced with fictional characters, locale and catergories replaced with random data** 

### View Interactive Dashboard Here: https://app.powerbigov.us/reportEmbed?reportId=96b2254e-3918-40ff-9433-e7c3121bced9&autoAuth=true&ctid=9ce70869-60db-44fd-abe8-d2767077fc8f

### Documents
* PowerBI DAX: DAX measure to create weekly chart of emails received in the mailbox and calculating rate for contact investigations. 

### Requirements 
* PowerBI Desktop
