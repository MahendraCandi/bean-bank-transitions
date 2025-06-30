# Phase 1 - Operations
After determine the data in each modules requirement, let's build the rule for the operations.

## Customer operations

<details>
<summary>Operations details</summary>

### 1. Submit customer acquisition
When submitting a new customer acquisition, all required fields must undergo validation to ensure data integrity and alignment with business rules.

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

**Business Rules**:
* The officer assigned must belong to the same office as selected in the form.
* The customer's age must be between 17 and 55 years old at the time of submission.
* A unique CIF number must be generated upon successful processing.
* The customer’s initial state must be set to PENDING.
* The KTP number must be unique among customers with ACTIVE status.
* Every state transition must be logged in the customer state history.

## 2. Inquiry customer information
The system must support searching and filtering customer information.\
The following filters should be supported:
* CIF number
* office
* customer name
* KTP
* state

**Response Expectations**:
* The response must return full customer information including associated officer and office details.
* Photo is excluded from the response; a separate operation must handle photo retrieval.
* Pagination support is required to manage large datasets.

## 3. Update customer information
The system must allow updates to customer data.\
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

**Response Expectations**:
* The response format must be consistent with the Customer Information Inquiry response format.

## 4. Change customer status
The system must allow changes to the customer’s status, following the valid status transition flow:

**Allowed State Transitions**:
* **`PENDING`** to **`ACTIVE`**
* **`PENDING`** to **`CLOSED`**
* **`ACTIVE`** to **`CLOSED`**

**Business Rule**:
* The changed states should follow the flow above
* The customer KTP should be unique compared to ACTIVE customer
* The state should be log in customer state history

</details>
