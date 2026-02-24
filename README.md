# web-scrapping-using-n8n

The purpose of this workflow is to build a universal web scraper using n8n that can collect structured data for any topic the user enters.

The workflow contains four main nodes:
1.	Trigger Node – When Chat Message Received
2.	AI Agent Node – Responsible for scraping
3.	Chat Model Node (OpenRouter) – Provides AI model for agent
4.	Google Sheets Node – Appends scraped data
5.	Simple Memory Node – Optional memory for better context
 <img width="830" height="529" alt="image" src="https://github.com/user-attachments/assets/9deaaa95-3a1e-4bf7-83aa-f26f4cc5293d" />


•	Adding the Trigger Node -added the “When Chat Message Received” trigger node.
•	Adding the AI Agent Node- which controls all scraping logic.
 Selected Chat Model → OpenRouter Model
 Selected Tool → Google Sheets Append Row
 Added a System Message describing:
o	Interpret user topic
o	Search multiple websites
o	Scrape ALL results
o	Extract specific fields
o	Append one row per item
               This system message makes the AI behave like a multi-website scraper.
•	OpenRouter Chat Model node to provide the AI with:
o	The ability to analyze websites
o	Multi-step reasoning
o	Unlimited result scraping
o	Support for long, complex scraping tasks
o	This node is connected to the AI Agent through the Chat Model parameter.

•	Adding the Simple Memory Node
•	Adding google sheets append row node ---Google Sheets – Append Row node and connected it as a Tool in the AI Agent.
•	Writing the System Prompt
o	I created a detailed System Message for the AI Agent:
o	Understand topic
o	Select best websites automatically
o	Search multiple websites
o	Scrape ALL items, not just a few
o	Mapped 40+ fields : url, title, subtitle, category, tags, price, currency etc.
o	Call Google Sheets tool once per item

The workflow successfully functions as a universal scraper capable of:
•	Understanding any topic
•	Searching across multiple websites
•	Extracting structured data
•	Filling rows directly into Google Sheets

## SOIL TESTING LABS DATA COLLECTION USING N8N UNIVERSAL WEB SCRAPER

The objective of this task was to build and use a universal web-scraping workflow in n8n to collect detailed information about soil testing laboratories (both Government and Private) across all districts in Tamil Nadu and store the data in a structured Google Sheet.
•	Set up AI Agent with custom system prompt for soil testing labs.
•	Mapped required Google Sheets fields (Name, Address, District, Category, Contact, Email).
•	Ran the workflow with the topic “Soil testing labs in Tamil Nadu”.
•	Data was collected from multiple government and private sources.
•	Verified and cleaned up the entries in Google Sheets.
•	Ensured duplicates were removed and fields were consistently formatted.

Configured the trigger (When Chat Message Received )
            Added a trigger node to allow the workflow to start automatically when a user sends a topic or query, such as “Soil testing labs in Tamil Nadu”.

Set up the AI Agent with a custom system prompt
          Configured the AI Agent node with a detailed system message that instructs it to search multiple websites, extract complete information, and follow a fixed schema for data fields. The prompt was specifically optimized for scraping soil testing labs in Tamil Nadu (both Government and Private).

Mapped the required Google Sheets fields
         In the Google Sheets “Append Row” node, I mapped the output fields such as: Name, Address, District, Category (Government/Private), Contact, Email. These fields ensure that the scraped data is properly structured inside the sheet.

Executed the workflow by sending a chat message with the scraping topic.
          The AI Agent understood the query and started searching multiple government and private websites for soil testing lab details. The Agent extracted all available entries and appended them into Google Sheets.

