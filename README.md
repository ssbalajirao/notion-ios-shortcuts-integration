# Notion API Integration via iOS Shortcuts

## Overview
A configurable iOS Shortcut that creates records in any Notion database
using the Notion REST API.

## Why
- Fast data entry
- Voice support via Siri
- No bank or SMS access
- Privacy-first

## How It Works
1. Siri triggers shortcut
2. User inputs data
3. Shortcut calls Notion API
4. Response is parsed
5. Siri confirms result

## Tech Stack
- iOS Shortcuts
- Siri
- Notion REST API
- Postman

## Success / Failure Logic
- object = "page" → success
- object = "error" → failure


---

## Sample Request Payload

Below is a simplified example of the request body sent to the Notion API.
All IDs and values are placeholders.

```json
{
  "parent": {
    "database_id": "<DATABASE_ID>"
  },
  "properties": {
    "Name": {
      "title": [
        { "text": { "content": "Sample Entry" } }
      ]
    },
    "Amount": {
      "number": 100
    },
    "Account": {
      "relation": [
        { "id": "<ACCOUNT_PAGE_ID>" }
      ]
    }
  }
}
```
## Example Use Case: Expense Tracking

This generic Notion API integration is demonstrated using a personal
expense tracking system.

In this implementation:
- Siri is used to trigger the iOS Shortcut
- The user manually provides expense details such as amount and account
- The Shortcut constructs a request payload based on the database schema
- A POST request is sent to the Notion API to create a new database entry
- Relations (e.g., Account) are handled using existing Notion Page IDs

During development:
- Postman was used to retrieve the Notion database ID
- Relation page IDs were fetched by querying the related databases
- Database schemas and property structures were inspected using the API
- Request payloads were validated before implementing them in iOS Shortcuts

After the API call:
- The response is parsed to extract the `object` field
- If `object = "page"`, the entry was created successfully
- If `object = "error"`, the operation failed
- Siri provides immediate voice feedback indicating success or failure

This use case was chosen because it requires:
- Fast input
- Reliable confirmation
- No automatic bank or SMS access
- Full user control over what gets recorded

The same integration can be adapted for other use cases such as
habit tracking, study logs, or workout tracking by modifying
the database ID and property mappings.


## Screenshots

### iOS Shortcut Implementation
Screenshots showing the overall flow of the iOS Shortcut, including:
- Siri trigger and user input
- Request construction for the Notion API
- Response parsing and success/failure handling

<!-- Add shortcut screenshots here -->
<img width="736" height="1600" alt="image" src="https://github.com/user-attachments/assets/9faa88e5-6614-4905-a22c-cadf46dff5e8" />

---

<img width="736" height="1600" alt="image" src="https://github.com/user-attachments/assets/cbd921d5-42b9-461c-b75c-bc3e44ed59f5" />

---

<img width="736" height="1600" alt="image" src="https://github.com/user-attachments/assets/a65922b0-5a84-4d19-82bc-9b174a6d9a69" />

---

<img width="736" height="1600" alt="image" src="https://github.com/user-attachments/assets/ae96bd8b-ecd1-4b81-9dad-de8774b69c76" />


---

### API Exploration (Postman)
Postman was used during development to explore and validate the Notion API before implementing the workflow in iOS Shortcuts.

## Fetch Accessible Databases

This request retrieves all databases that the Notion integration has access to. It was used to identify the required database ID.

**Request Headers**
     <img width="1442" height="961" alt="Get all the data base through Postman Headers" src="https://github.com/user-attachments/assets/02a9218b-37cd-4483-bd72-2e5e2d1085d0" />
**Request Body**
     <img width="1447" height="942" alt="Get all the data base through Postman Body" src="https://github.com/user-attachments/assets/d52fa2b2-506f-4be4-88cc-af484cddba8a" />

---

### Retrieve Database Schema and Relation IDs

A specific database was queried to inspect its schema and extract relation page IDs required for creating and updating entries.

**Request Headers**
    <img width="1438" height="833" alt="Getting data base Data" src="https://github.com/user-attachments/assets/991f5c2d-e925-406d-ab92-1eac06024c7c" />
**Request Body**
    <img width="1437" height="945" alt="Getting data base Data (Body)" src="https://github.com/user-attachments/assets/32920644-408c-492f-8462-7e89759a13a8" />

Postman was also used to:

- Inspect database schemas and property structures  
- Fetch database IDs and relation page IDs  
- Validate request payloads before automation  
- Verify successful responses and handle API errors  
- Ensure compatibility before implementing the logic in iOS Shortcuts  

---

### Notes

- Screenshots are included for reference and reproducibility.
- The validated API logic was later implemented using iOS Shortcuts.
## Privacy
No scraping, no automatic transaction access.
