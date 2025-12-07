{
  "stories": [
    {
      "epic_id": "EP-1",
      "id": "US-1",
      "title": "User Registration",
      "as_a": "new user",
      "i_want": "to register with a unique username and password",
      "so_that": "I can create an account to access the system",
      "acceptance_criteria": [
        "Users can register with a unique username and password.",
        "The system validates the uniqueness of the username.",
        "Users receive a confirmation message upon successful registration."
      ],
      "story_points": 5
    },
    {
      "epic_id": "EP-1",
      "id": "US-2",
      "title": "User Login",
      "as_a": "registered user",
      "i_want": "to log in to my account",
      "so_that": "I can access my profile and manage my contacts",
      "acceptance_criteria": [
        "Users can log in with their username and password.",
        "Users receive an error message for incorrect credentials.",
        "Users can log out successfully."
      ],
      "story_points": 3
    },
    {
      "epic_id": "EP-1",
      "id": "US-3",
      "title": "Profile Update",
      "as_a": "logged-in user",
      "i_want": "to update my profile information",
      "so_that": "I can keep my information current",
      "acceptance_criteria": [
        "Users can update their profile information.",
        "The system saves the updated information successfully.",
        "Users receive a confirmation message after updating."
      ],
      "story_points": 3
    },
    {
      "epic_id": "EP-1",
      "id": "US-4",
      "title": "Password Reset",
      "as_a": "user who forgot my password",
      "i_want": "to reset my password",
      "so_that": "I can regain access to my account",
      "acceptance_criteria": [
        "Users can request a password reset link.",
        "Users can set a new password using the link.",
        "Users receive a confirmation message after resetting the password."
      ],
      "story_points": 5
    },
    {
      "epic_id": "EP-2",
      "id": "US-5",
      "title": "Create Contact",
      "as_a": "user",
      "i_want": "to create a new contact",
      "so_that": "I can store important information about people",
      "acceptance_criteria": [
        "Users can create a new contact with required fields.",
        "The system validates the input fields.",
        "Users receive a confirmation message upon successful creation."
      ],
      "story_points": 5
    },
    {
      "epic_id": "EP-2",
      "id": "US-6",
      "title": "Edit Contact",
      "as_a": "user",
      "i_want": "to edit an existing contact",
      "so_that": "I can update the contact's information",
      "acceptance_criteria": [
        "Users can edit existing contacts.",
        "The system saves the updated contact information.",
        "Users receive a confirmation message after editing."
      ],
      "story_points": 3
    },
    {
      "epic_id": "EP-2",
      "id": "US-7",
      "title": "View Contacts",
      "as_a": "user",
      "i_want": "to view a list of all my contacts",
      "so_that": "I can easily find and manage them",
      "acceptance_criteria": [
        "Users can view a list of all contacts.",
        "The list displays relevant information for each contact.",
        "Users can search for contacts by name."
      ],
      "story_points": 3
    },
    {
      "epic_id": "EP-2",
      "id": "US-8",
      "title": "Delete Contact",
      "as_a": "user",
      "i_want": "to delete a contact",
      "so_that": "I can remove contacts that are no longer needed",
      "acceptance_criteria": [
        "Users can delete a contact.",
        "The system prompts for confirmation before deletion.",
        "Users receive a confirmation message after deletion."
      ],
      "story_points": 3
    },
    {
      "epic_id": "EP-3",
      "id": "US-9",
      "title": "Create Company",
      "as_a": "user",
      "i_want": "to create a new company",
      "so_that": "I can associate contacts with the company",
      "acceptance_criteria": [
        "Users can create a new company.",
        "The system validates the input fields.",
        "Users receive a confirmation message upon successful creation."
      ],
      "story_points": 5
    },
    {
      "epic_id": "EP-3",
      "id": "US-10",
      "title": "Edit Company",
      "as_a": "user",
      "i_want": "to edit company details",
      "so_that": "I can keep the company information up to date",
      "acceptance_criteria": [
        "Users can edit company details.",
        "The system saves the updated company information.",
        "Users receive a confirmation message after editing."
      ],
      "story_points": 3
    },
    {
      "epic_id": "EP-3",
      "id": "US-11",
      "title": "View Companies",
      "as_a": "user",
      "i_want": "to view a list of all companies",
      "so_that": "I can manage my associated companies",
      "acceptance_criteria": [
        "Users can view a list of all companies.",
        "The list displays relevant information for each company.",
        "Users can search for companies by name."
      ],
      "story_points": 3
    },
    {
      "epic_id": "EP-3",
      "id": "US-12",
      "title": "Delete Company",
      "as_a": "user",
      "i_want": "to delete a company",
      "so_that": "I can remove companies that are no longer relevant",
      "acceptance_criteria": [
        "Users can delete a company.",
        "The system prompts for confirmation before deletion.",
        "Users receive a confirmation message after deletion."
      ],
      "story_points": 3
    },
    {
      "epic_id": "EP-4",
      "id": "US-13",
      "title": "User API Endpoints",
      "as_a": "developer",
      "i_want": "to create API endpoints for user registration and authentication",
      "so_that": "the frontend can interact with user data",
      "acceptance_criteria": [
        "API endpoints for user registration and authentication are functional.",
        "API responses are in JSON format.",
        "Endpoints handle errors appropriately."
      ],
      "story_points": 5
    },
    {
      "epic_id": "EP-4",
      "id": "US-14",
      "title": "Contact API Endpoints",
      "as_a": "developer",
      "i_want": "to create API endpoints for CRUD operations on contacts",
      "so_that": "the frontend can manage contact data",
      "acceptance_criteria": [
        "API endpoints for CRUD operations on contacts are functional.",
        "API responses are in JSON format.",
        "Endpoints handle errors appropriately."
      ],
      "story_points": 5
    },
    {
      "epic_id": "EP-4",
      "id": "US-15",
      "title": "Company API Endpoints",
      "as_a": "developer",
      "i_want": "to create API endpoints for CRUD operations on companies",
      "so_that": "the frontend can manage company data",
      "acceptance_criteria": [
        "API endpoints for CRUD operations on companies are functional.",
        "API responses are in JSON format.",
        "Endpoints handle errors appropriately."
      ],
      "story_points": 5
    },
    {
      "epic_id": "EP-5",
      "id": "US-16",
      "title": "User Interface for Registration and Login",
      "as_a": "user",
      "i_want": "to have a user-friendly interface for registration and login",
      "so_that": "I can easily access my account",
      "acceptance_criteria": [
        "The UI allows users to register and log in.",
        "The UI provides feedback for successful and failed login attempts.",
        "The UI is responsive and accessible."
      ],
      "story_points": 5
    },
    {
      "epic_id": "EP-5",
      "id": "US-17",
      "title": "Display Contacts and Companies",
      "as_a": "user",
      "i_want": "to see a list of my contacts and companies",
      "so_that": "I can manage them effectively",
      "acceptance_criteria": [
        "The UI displays a list of contacts and companies.",
        "The list is sortable and searchable.",
        "The UI updates in real-time when changes are made."
      ],
      "story_points": 5
    },
    {
      "epic_id": "EP-5",
      "id": "US-18",
      "title": "Forms for Creating and Editing",
      "as_a": "user",
      "i_want": "to have forms for creating and editing contacts and companies",
      "so_that": "I can easily manage my data",
      "acceptance_criteria": [
        "The UI provides forms for creating and editing contacts and companies.",
        "Forms validate user input before submission.",
        "Users receive confirmation messages after successful submissions."
      ],
      "story_points": 5
    },
    {
      "epic_id": "EP-5",
      "id": "US-19",
      "title": "Error Handling in UI",
      "as_a": "user",
      "i_want": "to see error messages when something goes wrong",
      "so_that": "I can understand what needs to be fixed",
      "acceptance_criteria": [
        "The UI handles API errors gracefully.",
        "Users receive clear error messages.",
        "The UI does not crash on error."
      ],
      "story_points": 3
    },
    {
      "epic_id": "EP-6",
      "id": "US-20",
      "title": "Database Schema Creation",
      "as_a": "developer",
      "i_want": "to create a database schema for users, contacts, and companies",
      "so_that": "data can be stored and retrieved efficiently",
      "acceptance_criteria": [
        "Database schema is created for users, contacts, and companies.",
        "All required fields are included in the schema.",
        "Schema is tested for integrity."
      ],
      "story_points": 5
    },
    {
      "epic_id": "EP-6",
      "id": "US-21",
      "title": "Data Persistence",
      "as_a": "developer",
      "i_want": "to ensure data is persisted in the SQLite database",
      "so_that": "user, contact, and company information is not lost",
      "acceptance_criteria": [
        "Data is persisted in the SQLite database.",
        "Data can be retrieved accurately.",
        "Data integrity is maintained."
      ],
      "story_points": 5
    },
    {
      "epic_id": "EP-6",
      "id": "US-22",
      "title": "Database Querying",
      "as_a": "developer",
      "i_want": "to query the database for user, contact, and company information",
      "so_that": "I can retrieve data as needed",
      "acceptance_criteria": [
        "Database can be queried for user, contact, and company information.",
        "Queries return accurate results.",
        "Query performance is optimized."
      ],
      "story_points": 5
    }
  ]
}