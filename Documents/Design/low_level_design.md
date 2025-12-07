# Low-Level Design for Contact Management System (CMS)

## 1. Detailed Sequence Diagrams

### Create Contact Flow
```mermaid
sequenceDiagram
    participant User
    participant Frontend
    participant ContactController
    participant ContactService
    participant ContactRepository

    User->>Frontend: Fill contact form
    Frontend->>ContactController: POST /contacts
    ContactController->>ContactService: createContact(contactDTO)
    ContactService->>ContactRepository: save(contact)
    ContactRepository-->>ContactService: contactSaved
    ContactService-->>ContactController: contactCreated
    ContactController-->>Frontend: 201 Created, contact
    Frontend-->>User: Display success message
```

### List Contacts with Pagination
```mermaid
sequenceDiagram
    participant User
    participant Frontend
    participant ContactController
    participant ContactService
    participant ContactRepository

    User->>Frontend: Request contact list
    Frontend->>ContactController: GET /contacts?page=1&size=10
    ContactController->>ContactService: listContacts(page, size)
    ContactService->>ContactRepository: findAll(page, size)
    ContactRepository-->>ContactService: contactsList
    ContactService-->>ContactController: contactsList
    ContactController-->>Frontend: 200 OK, contactsList
    Frontend-->>User: Display contacts
```

### Update Contact
```mermaid
sequenceDiagram
    participant User
    participant Frontend
    participant ContactController
    participant ContactService
    participant ContactRepository

    User->>Frontend: Edit contact form
    Frontend->>ContactController: PUT /contacts/{id}
    ContactController->>ContactService: updateContact(id, contactDTO)
    ContactService->>ContactRepository: findById(id)
    ContactRepository-->>ContactService: contact
    ContactService->>ContactRepository: save(updatedContact)
    ContactRepository-->>ContactService: contactUpdated
    ContactService-->>ContactController: contactUpdated
    ContactController-->>Frontend: 200 OK, updatedContact
    Frontend-->>User: Display success message
```

### Delete Contact
```mermaid
sequenceDiagram
    participant User
    participant Frontend
    participant ContactController
    participant ContactService
    participant ContactRepository

    User->>Frontend: Request to delete contact
    Frontend->>ContactController: DELETE /contacts/{id}
    ContactController->>ContactService: deleteContact(id)
    ContactService->>ContactRepository: deleteById(id)
    ContactRepository-->>ContactService: contactDeleted
    ContactService-->>ContactController: 204 No Content
    ContactController-->>Frontend: 204 No Content
    Frontend-->>User: Display success message
```

### Add Tag to Contact
```mermaid
sequenceDiagram
    participant User
    participant Frontend
    participant ContactController
    participant ContactService
    participant TagService
    participant ContactRepository

    User->>Frontend: Request to add tag
    Frontend->>ContactController: POST /contacts/{id}/tags
    ContactController->>ContactService: addTagToContact(id, tagDTO)
    ContactService->>TagService: findTagById(tagId)
    TagService-->>ContactService: tag
    ContactService->>ContactRepository: findById(id)
    ContactRepository-->>ContactService: contact
    ContactService->>ContactRepository: save(contactWithTag)
    ContactRepository-->>ContactService: contactUpdated
    ContactService-->>ContactController: contactUpdated
    ContactController-->>Frontend: 200 OK, updatedContact
    Frontend-->>User: Display success message
```

## 2. Detailed Class Diagrams

### Contact Class Diagram
```mermaid
classDiagram
    class Contact {
        +Long id
        +String name
        +String email
        +String phone
        +List<Tag> tags
    }

    class ContactDTO {
        +String name
        +String email
        +String phone
    }

    class ContactService {
        +Contact createContact(ContactDTO contactDTO)
        +List<Contact> listContacts(int page, int size)
        +Contact updateContact(Long id, ContactDTO contactDTO)
        +void deleteContact(Long id)
        +Contact addTagToContact(Long id, Long tagId)
    }

    class ContactController {
        +ResponseEntity<Contact> createContact(ContactDTO contactDTO)
        +ResponseEntity<List<Contact>> listContacts(int page, int size)
        +ResponseEntity<Contact> updateContact(Long id, ContactDTO contactDTO)
        +ResponseEntity<Void> deleteContact(Long id)
        +ResponseEntity<Contact> addTagToContact(Long id, Long tagId)
    }

    class ContactRepository {
        +Contact save(Contact contact)
        +Optional<Contact> findById(Long id)
        +void deleteById(Long id)
        +List<Contact> findAll(Pageable pageable)
    }

    ContactController --> ContactService
    ContactService --> ContactRepository
```

### Tag Class Diagram
```mermaid
classDiagram
    class Tag {
        +Long id
        +String name
    }

    class TagDTO {
        +String name
    }

    class TagService {
        +Tag createTag(TagDTO tagDTO)
        +Tag findTagById(Long id)
    }

    class TagController {
        +ResponseEntity<Tag> createTag(TagDTO tagDTO)
        +ResponseEntity<Tag> getTag(Long id)
    }

    class TagRepository {
        +Tag save(Tag tag)
        +Optional<Tag> findById(Long id)
    }

    TagController --> TagService
    TagService --> TagRepository
```

### Frontend Components Class Diagram
```mermaid
classDiagram
    class ContactList {
        +render()
        +fetchContacts()
    }

    class ContactForm {
        +render()
        +handleSubmit()
    }

    class ContactService {
        +createContact(contactDTO)
        +listContacts(page, size)
        +updateContact(id, contactDTO)
        +deleteContact(id)
        +addTagToContact(id, tagDTO)
    }

    ContactList --> ContactService
    ContactForm --> ContactService
```

## 3. Module Structure and Package Organization
```
com.example.cms
├── controller
│   ├── ContactController.java
│   └── TagController.java
├── service
│   ├── ContactService.java
│   └── TagService.java
├── repository
│   ├── ContactRepository.java
│   └── TagRepository.java
├── model
│   ├── Contact.java
│   ├── ContactDTO.java
│   ├── Tag.java
│   └── TagDTO.java
└── exception
    ├── ResourceNotFoundException.java
    └── GlobalExceptionHandler.java
```

## 4. Complete Database Schema with SQL DDL
```sql
CREATE TABLE contacts (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    name TEXT NOT NULL,
    email TEXT NOT NULL UNIQUE,
    phone TEXT
);

CREATE TABLE tags (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    name TEXT NOT NULL UNIQUE
);

CREATE TABLE contact_tags (
    contact_id INTEGER,
    tag_id INTEGER,
    PRIMARY KEY (contact_id, tag_id),
    FOREIGN KEY (contact_id) REFERENCES contacts(id),
    FOREIGN KEY (tag_id) REFERENCES tags(id)
);
```

## 5. Detailed API Endpoint Specifications

### Create Contact
- **Path**: `/contacts`
- **Method**: `POST`
- **Parameters**: 
  - Body: `ContactDTO`
- **Request Schema**:
```json
{
  "name": "John Doe",
  "email": "john.doe@example.com",
  "phone": "1234567890"
}
```
- **Response Schema**:
```json
{
  "id": 1,
  "name": "John Doe",
  "email": "john.doe@example.com",
  "phone": "1234567890",
  "tags": []
}
```
- **HTTP Status Codes**: 
  - 201 Created
  - 400 Bad Request (if validation fails)

### List Contacts
- **Path**: `/contacts`
- **Method**: `GET`
- **Parameters**: 
  - Query: `page`, `size`
- **Response Schema**:
```json
{
  "content": [
    {
      "id": 1,
      "name": "John Doe",
      "email": "john.doe@example.com",
      "phone": "1234567890",
      "tags": []
    }
  ],
  "totalPages": 1,
  "totalElements": 1
}
```
- **HTTP Status Codes**: 
  - 200 OK

### Update Contact
- **Path**: `/contacts/{id}`
- **Method**: `PUT`
- **Parameters**: 
  - Path: `id`
  - Body: `ContactDTO`
- **Request Schema**: Same as Create Contact
- **Response Schema**: Same as Create Contact
- **HTTP Status Codes**: 
  - 200 OK
  - 404 Not Found (if contact does not exist)

### Delete Contact
- **Path**: `/contacts/{id}`
- **Method**: `DELETE`
- **Parameters**: 
  - Path: `id`
- **HTTP Status Codes**: 
  - 204 No Content
  - 404 Not Found (if contact does not exist)

### Add Tag to Contact
- **Path**: `/contacts/{id}/tags`
- **Method**: `POST`
- **Parameters**: 
  - Path: `id`
  - Body: `TagDTO`
- **Request Schema**:
```json
{
  "name": "Friend"
}
```
- **Response Schema**: Same as Update Contact
- **HTTP Status Codes**: 
  - 200 OK
  - 404 Not Found (if contact or tag does not exist)

## 6. Validation Rules and Constraints
- **Contact**:
  - `name`: Not null, max length 100
  - `email`: Not null, must be a valid email format, unique
  - `phone`: Optional, max length 15
- **Tag**:
  - `name`: Not null, unique, max length 50

## 7. Error Handling Strategy
- Use a global exception handler to catch exceptions and return appropriate HTTP status codes and messages.
- Custom exceptions for resource not found, validation errors, etc.

## 8. Security Considerations
- Implement authentication (e.g., JWT) for API access.
- Validate user input to prevent SQL injection and XSS attacks.
- Use HTTPS for secure data transmission.
- Implement role-based access control if needed (e.g., admin vs. user permissions). 

This low-level design provides a comprehensive overview of the Contact Management System, detailing the interactions, data structures, and architectural considerations necessary for implementation.