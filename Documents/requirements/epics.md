{
  "epics": [
    {
      "id": "EP-1",
      "name": "User Management",
      "description": "Implement user management features including user registration, authentication, and profile management.",
      "acceptance_criteria": [
        "Users can register with a unique username and password.",
        "Users can log in and log out successfully.",
        "Users can update their profile information.",
        "Users can reset their password."
      ]
    },
    {
      "id": "EP-2",
      "name": "Contact Management",
      "description": "Develop features for creating, editing, viewing, and deleting contacts.",
      "acceptance_criteria": [
        "Users can create a new contact with required fields.",
        "Users can edit existing contacts.",
        "Users can view a list of all contacts.",
        "Users can delete a contact."
      ]
    },
    {
      "id": "EP-3",
      "name": "Company Management",
      "description": "Implement functionality to manage companies associated with contacts.",
      "acceptance_criteria": [
        "Users can create a new company.",
        "Users can edit company details.",
        "Users can view a list of all companies.",
        "Users can delete a company."
      ]
    },
    {
      "id": "EP-4",
      "name": "API Development",
      "description": "Create a RESTful API using Spring Boot for user, contact, and company models.",
      "acceptance_criteria": [
        "API endpoints for user registration and authentication are functional.",
        "API endpoints for CRUD operations on contacts are functional.",
        "API endpoints for CRUD operations on companies are functional.",
        "API responses are in JSON format."
      ]
    },
    {
      "id": "EP-5",
      "name": "Frontend Development",
      "description": "Build a React UI that interacts with the backend API for user, contact, and company management.",
      "acceptance_criteria": [
        "The UI allows users to register and log in.",
        "The UI displays a list of contacts and companies.",
        "The UI provides forms for creating and editing contacts and companies.",
        "The UI handles API errors gracefully."
      ]
    },
    {
      "id": "EP-6",
      "name": "Database Integration",
      "description": "Set up SQLite database to store user, contact, and company data.",
      "acceptance_criteria": [
        "Database schema is created for users, contacts, and companies.",
        "Data is persisted in the SQLite database.",
        "Database can be queried for user, contact, and company information."
      ]
    }
  ]
}