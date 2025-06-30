# Phase 1 - Operations
After determine the data in each modules requirement, let's build the rule for the operations.

## Customer operations

<details>
<summary>Operations details</summary>

### 1. Submit customer acquisition
When submitting the customer acquisitions, the data should be validated.

| Field              | Validations                                                              |
|--------------------|--------------------------------------------------------------------------|
| KTP                | Cannot be null or empty, Should be valid Indonesian identifier number    |
| Name               | Cannot be null or empty                                                  |
| Address            | Cannot be null or empty                                                  |
| City               | Cannot be null or empty, Should aligned with available options on system |
| Province           | Cannot be null or empty, Should aligned with available options on system |
| Phone number       | Cannot be null or empty, Should represent phone number (mobile or home)  |
| Mother name        | Cannot be null or empty                                                  |
| Marital status     | Cannot be null or empty, Should aligned with available options on system |
| Gender             | Cannot be null or empty, Should aligned with available options on system |
| Date of birth      | Cannot be null or empty                                                  |
| Place of birth     | Cannot be null or empty                                                  |
| Occupation         | Cannot be null or empty                                                  |
| Income range       | Cannot be null or empty, Should aligned with available options on system |
| Email address      | Should aligned with real email format                                    |
| Residential status | Should aligned with available options on system                          |
| Officer            | Cannot be null or empty, Should aligned with available options on system |
| Office             | Cannot be null or empty                                                  |

Also, please check the business requirement when processing the data:
* Officer should be in the same with the submitted office
* Customer ages should be between 17 and 55
* CIF number should be generated if process success
* The customer state should be PENDING if process success
* KTP should be unique compared to ACTIVE customer
* The state should be log in customer state history

## 2. Inquiry customer information
The system should capable to searching customer information.\
The system should accept some parameter to filter the search results.
* Filter by CIF number
* Filter by office
* Filter by customer name
* Filter by KTP
* Filter by state

The data output should be all customer information including the officer and office information.\
But excluding the photo, there would be another operations to handle it.\
**Also, available pagination is a must.**

## 3. Update customer information
The system should capable to update customer information.\
Some fields may be prohibited to update.

| Field              | Can updated? |
|--------------------|--------------|
| Name               | Yes          |
| Address            | Yes          |
| City               | Yes          |
| Province           | Yes          |
| Phone number       | Yes          |
| Mother name        | Yes          |
| Marital status     | Yes          |
| Occupation         | Yes          |
| Income range       | Yes          |
| Email address      | Yes          |
| Residential status | Yes          |

The date output should be the same as data output in section Inquiry Customer Information.

## 4. Change customer status
The system should capable to change status customer.
Here is the states flow:

* **PENDING** to **ACTIVE**
* **PENDING** to **CLOSED**
* **ACTIVE** to **CLOSED**

Please check the business requirement to change status:
* The changed states should follow the flow above
* The customer KTP should be unique compared to ACTIVE customer
* The state should be log in customer state history

</details>
