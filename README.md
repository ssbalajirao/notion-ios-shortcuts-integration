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
(Add images)

## Privacy
No scraping, no automatic transaction access.
