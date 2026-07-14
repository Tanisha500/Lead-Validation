# Lead-Validation

An end-to-end lead validation workflow built using **n8n**. The workflow receives a CSV file through a webhook, validates email addresses, and stores valid and invalid leads into separate Airtable tables.

---

##  Project Overview

This automation demonstrates how to build a no-code/low-code data processing pipeline using n8n.

### Workflow Steps

1. Receive a CSV file through an HTTP Webhook.
2. Parse the CSV into individual records.
3. Validate email addresses using a Regular Expression (Regex).
4. Separate records into:
   - Approved Leads
   - Quarantined Leads
5. Store each category in separate Airtable tables.

---

## Tech Stack

- n8n
- Airtable
- Webhooks
- CSV Parser
- Regular Expressions (Regex)
- Postman (Testing)

---

## Workflow

```text
Receive CSV Upload
        │
        ▼
Parse CSV File
        │
        ▼
Validate Email
     ┌───────┴────────┐
     ▼                ▼
Approved         Quarantined
Leads              Leads
     │                │
     ▼                ▼
Airtable         Airtable
```

---

## Features

- Receive CSV files via Webhook
- Parse CSV automatically
- Validate email format using Regex
- Separate valid and invalid leads
- Store approved leads in Airtable
- Store quarantined leads in a separate Airtable table
- End-to-end automation using n8n

---

## Email Validation Rule

The workflow validates email addresses using the following Regular Expression:

```regex
^[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,}$
```

Examples:

| Email | Status |
|--------|--------|
| john@gmail.com | ✅ Valid |
| alice@yahoo.in | ✅ Valid |
| bobwilsongmail.com | ❌ Invalid |
| john@ | ❌ Invalid |
| @gmail.com | ❌ Invalid |
| Empty Email | ❌ Invalid |

---

## Output

### Approved Leads

Stored in:

```
Approved_Leads
```

Fields:

- Name
- Email
- Company


### Quarantined Leads

Stored in:

```
Quarantined_Leads
```

Fields:

- Name
- Email
- Company

---

##  Testing

The workflow was tested using **Postman**.

### Request

- Method: **POST**
- Body: **form-data**
- Key: `data`
- Type: `File`

Upload:

```
leads_list.csv
```

##  Screenshots

Add screenshots here:

- Workflow
- Approved Leads Table
- Quarantined Leads Table
- Successful Execution

