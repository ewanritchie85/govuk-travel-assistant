## Embassy Logic App

This Azure Logic App automates the retrieval and summarisation of British embassy information from GOV.UK, focusing on office name,
address, telephone number, opening times, office details URL, emergency help URL, and opening times.

### Overview

**Trigger:**
- HTTP POST request from Copliot agent with JSON body containing `country` and optional `city`.

**Workflow Steps:**
1. **Compose Query:** Combines city and country into a search string for GOV.UK (e.g., "british embassy Paris France").
2. **Search GOV.UK API:** Queries the GOV.UK Search API for embassy organisations.
3. **Parse Results:** Extracts the first relevant embassy result.
4. **Fetch Embassy Details:** Retrieves detailed content for the selected embassy.
5. **Extract Key Info:** Composes embassy name, address, telephone, office URL, and emergency help URL.
6. **Summarise Opening Times:** Sends the office URL to an Azure OpenAI endpoint, which returns a concise summary of opening times in UK English (stripping HTML, including notes like public holidays or appointment-only).
7. **Compose Response:** Combines all extracted and summarised info into a JSON response.
8. **Return Response:** Responds to the original HTTP request with the embassy details and opening times.

### Request Example

```
POST /logicapp-endpoint
Content-Type: application/json

{
  "country": "France",
  "city": "Paris"
}
```

### Response Example

```
{
  "name": "British Embassy Paris",
  "address": "35 rue du Faubourg Saint-Honoré, 75008 Paris, France",
  "telephone": "+33 1 44 51 31 00",
  "opening_hours": "Open Monday to Friday, 9am to 5pm. Closed on public holidays.",
  "office_url": "https://www.gov.uk/world/organisations/british-embassy-paris",
  "emergency_help_url": "https://www.gov.uk/world/organisations/british-embassy-paris/contact/emergency-help"
}
```

### Configuration

- The Logic App requires two parameters for Azure OpenAI:
  - `aoai_uri`: The endpoint for the OpenAI deployment.
  - `aoai_key`: The API key for authentication.

### Notes

- Only the first matching embassy result is returned.
- traditional GET request will obtain office name, address, office URL, emergency help URL
- Opening times are summarised from office URL using Azure OpenAI and may include notes about holidays or appointment-only access.
- If opening times are not present, the field will be an empty string.
