# Bean Bank Requirement

> Bean Bank is a dummy bank transitioning from paper-based operations to a digital system. The following modules must be supported.

## 1. Customer
### Overview
Stores detailed information about individual retail banking customers.
Customers are typically individual locals (not foreigners or companies).
### Data Field
| No | Field              | Description                                                                                                                              |
|----|--------------------|------------------------------------------------------------------------------------------------------------------------------------------|
| 1  | CIF number         | Represent customer business key.<br/>Formatted by [4 digit office code] + [5 increment customer ID]. Example: 000100001                  |
| 2  | KTP                |                                                                                                                                          |
| 3  | Name               |                                                                                                                                          |
| 4  | Address            | Represent the detail home address like street, building, residential, etc.                                                               |
| 5  | City               | Represent the city customer is living in.<br/>Like Jakarta, Tangerang, Bandung, etc.                                                     |
| 6  | Province           | Represent the province of the city.<br/>For Jakarta should be Jakarta, for Tangerang should be Banten, for Bandung should be Jawa Barat. |
| 7  | Phone number       |                                                                                                                                          |
| 8  | Mother name        |                                                                                                                                          |
| 9  | Marital status     | Is it Single, Married, Widowed, Divorced?                                                                                                |
| 10 | Gender             |                                                                                                                                          |
| 11 | Date of birth      |                                                                                                                                          |
| 12 | Place of birth     | Represent the city                                                                                                                       |
| 13 | Occupation         |                                                                                                                                          |
| 14 | Income range       | Is it less than 3.000.000, between 3.000.000 and 8.000.000, between 8.000.000 and 20.000.000, more than 20.000.000?                      |
| 15 | Email address      |                                                                                                                                          |
| 16 | Residential status | Is it Owned, Rented, Living with Parents, Company Housing?                                                                               |
| 17 | Photo              | The clear face photo                                                                                                                     |
| 18 | Officer            | The officer that acquisitioned the customer                                                                                              |
| 19 | Office             | The office information of customer                                                                                                       |
| 20 | State              | To maintain customer states. Available states are PENDING, ACTIVE, CLOSED                                                                |


## 2. Office
### Overview
Represents the organizational structure of the banks physical locations. Offices may operate at different levels (e.g., Head Office, Branch Office).
### Data field
| No | Field        | Description                                                                                                          |
|----|--------------|----------------------------------------------------------------------------------------------------------------------|
| 1  | Office code  | Formatted by 4-digit padded auto-increment of table ID.<br/>Example: 0001 → 1 is the auto-increment ID of the office |
| 2  | Name         |                                                                                                                      |
| 3  | Office Level | Represent Head Office or Branch Office                                                                               |
| 4  | Address      |                                                                                                                      |
| 5  | City         |                                                                                                                      |
| 6  | Province     |                                                                                                                      |
| 7  | Phone number |                                                                                                                      |


## 3. Officer
### Overview
Captures data about personnel employed at branch offices. 
### Data field
| No | Field         | Description                                                                                                                                                             |
|----|---------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1  | Officer code  | Represent 5 or more digits formatted by [4-digit office code] + [1 or more alphabet letters]. <br/>Example: 0001A (1st officer in Jakarta branch), 0001Z (26th officer) |
| 2  | Name          |                                                                                                                                                                         |
| 3  | Gender        |                                                                                                                                                                         |
| 4  | Date of birth |                                                                                                                                                                         |
| 5  | Office code   |                                                                                                                                                                         |
| 6  | Active status |                                                                                                                                                                         |
| 7  | Join date     |                                                                                                                                                                         |


## 4. City and Province
### Overview
Master data for geographic coverage of Bean Bank operations. Used to validate and standardize customer and office location inputs across modules.
### Data Field
| No | Field          | Description |
|----|----------------|-------------|
| 1  | City code      |             |
| 2  | City name      |             |
| 3  | Parent code    |             |
| 4  | Province code  |             |
| 5  | Province name  |             |


## 5. Master data
### Overview
Generic lookup table for enumerated values used across the system (e.g., gender, marital status, income range). Centralizes label management to ensure consistency in validation and UI display.
### Data Field
| No | Field            | Description                                                                                                                   |
|----|------------------|-------------------------------------------------------------------------------------------------------------------------------|
| 1  | ID               |                                                                                                                               |
| 2  | Entity type ID   | Example: 1 for Gender, 2 for Residential Status, 3 for Marital Status                                                         |
| 3  | Entity type name | Example: <br/>if entity type ID is 1 → `gender`,<br/>if entity type ID is 3 → `marital-status`                                |
| 4  | Label            | Represent the label name for FE translations. Example: if value is "Living with Parents" then put it as `living-with-parents` |
| 5  | Description      | The master data descriptions. Example: Male, Female, Living with Parents, Single, Married, etc...                             |
| 6  | Status           | Activation status                                                                                                             |

