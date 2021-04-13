
## Planning

#### 1. Parsing User Stories
- [x] User Story 01
- [x] User Story 02
- [x] User Story 03
- [x] User Story 04
- [x] User Story 05
- [x] User Story 06
- [x] User Story 07
- [x] User Story 08
- [x] User Story 09
- [x] User Story 10
- [x] User Story 11
- [ ] User Story 12
- [ ] User Story 13
- [ ] User Story 14
- [ ] User Story 15
- [ ] User Story 16
- [ ] User Story 17
- [ ] User Story 18
- [ ] User Story 19
- [ ] User Story 20

#### 2. Database Domain Modelling
- [x] Users Table
- [x] Spaces Table

#### 3. MVP Planning

#### 4. Feature & Unit Testing

---

## Parsing User Stories

### Headline Specifications

Actions are *italic*. Nouns are **bold**. Attributes of nouns are **_bold italics_**.

##### User Story 01

As a user,
So that I can list my house,
I’d like to be able to *create a* **listing** of a **space**.

##### User Story 02

As a user,
So that I can make money from all of my properties,
I would like to be able to *list multiple spaces*.

##### User Story 03

As a user,
So that other users can admire my space and want to stay there,
I want to be able to _provide a **name**, **description** and **price**_ for my **space**.

##### User Story 04

As a user,
So that other users can consider when they might be able to visit,
I want to be able to **offer a range of _dates_** when the **space** is **_unoccupied_**.

##### User Story 05

As a user,
So I can rent a space,
I’d like to be able to _request_ a **space** and it to be _approved by the **owner**_.

##### User Story 06

As a user,
So that I don’t get double-booked,
I want to make sure that a **space** can’t _be **booked** more than once_.

##### User Story 07

As a user,
So that my space is still available to other prospective clients,
I would like my **space** to _not be **booked** out_ until a **user** _confirms a booking request_.

---

### 'Nice to Have' Specifications

##### User Story 08
As a user,
To confirm my account has been created,
I would like _to be sent_ an **e-mail** after _signing up_.

##### User Story 09
As a user,
To make sure my space has been registered correctly,
I would like _to be sent_ an **e-mail** after _creating a new space_.

##### User Story 10
As a user,
To make sure my space was updated correctly,
I would like _to be sent_ an **e-mail** after _updating a space_ with changes.

##### User Story 11
As a user,
To make sure I know when a user books my space,
I would like _to be sent_ an **e-mail** after a _user confirms booking_ my **space**.

---

## Database Domain Modelling

The above user stories parse into several classes. As per [Class Responsibility Collaborator](http://agilemodeling.com/artifacts/crcModel.htm) modelling, there are two obvious classes - **User** and **Space**.

Class: **Space**

Responsibility | Collaborators
--- | ---
Knows owner | User
Knows own name |
Knows own description |
Knows own price |
Knows own availability |
Knows own bookings |

Class: **User**

Responsibility | Collaborators
--- | ---
Knows own name |
Knows own username |
Knows own e-mail |
Knows own password |
~Knows own telephone number~ |
Knows own spaces | Space

Each class needs its own table, each with columns corresponding to the responsibilities of each class.

Table: **Users**

id PK | user_name | user_email | password_digest
--- | --- | --- | ---

Table: **Spaces**

id PK | space_name | description | price | user_id FK | start_date | end_date
--- | --- | --- | --- | --- | --- | ---

Table: **Bookings**

id PK | start_date | space_id FK | user_id FK | accepted
--- | --- | --- | --- | ---

---

## MVP Planning

- [x] Create a listing from form
- [x] Show listing on homepage
- [x] Homepage
- [x] Add listing form on homepage
- [x] Submit button on homepage form
- [x] POST/GET redirect cycle
- [x] Save form contents to session
- [x] Display listing on homepage
- [x] Display listings on homepage

---

## Feature & Unit Testing

Taking for example User Story 01 (`I’d like to be able to create a listing of a space.`), this presupposes the existence of a user, a space, and the ability to list it.

Creating these follows the TDD process:
1. Composition of pseudocode.
2. Composition of feature tests.
3. Composition of unit tests.
4. Composition of code.
5. Running of feature and unit tests.
6. Refactoring, and if necessary correction of code.

