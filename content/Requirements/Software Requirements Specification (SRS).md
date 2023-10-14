---
aliases:
  - SRS Document
  - SRS
  - SRS Doc
  - Software Requirements Specification
  - Requirements
  - requirements
---
# 1. Introduction

## 1.1 Purpose

This document specifies the software requirements for the Quoting Software intended for Gilberto Arellano Windows LLC, which aims to streamline the process of generating quotes for custom wood windows.

## 1.2 Scope

The software will provide functionalities for inputting window specifications, calculating costs, storing customer details, and generating quotes. While initially tailored for wood windows, the software aims to be scalable for all types of residential windows. Subsequent phases will include project management and analytics

## 1.3 Definitions, Acronyms, and Abbreviations

- **SRS**: Software Requirements Specification
- **CRUD**: Create, Read, Update, Delete

# 2. Overall Description
### 2.1 Product Perspective  
The Gilberto Arellano Windows LLC Quoting Software is envisioned as a comprehensive tool to streamline the quote generation process for custom wood windows. While it will initially serve the immediate needs of Gilberto Arellano Windows LLC, the software is designed with scalability in mind, anticipating future enhancements and potential use by other window companies.
### 2.2 User Classes and Characteristics

- **Administrator**: The primary user who will have full access to all features, including quote generation, project management, and analytics. This user will also have the ability to modify system settings and constants.
- **(Future) Sales Team or Staff**: Users who can generate and manage quotes but may not have access to system settings or high-level analytics.

### 2.3 Operating Environment  
The software will initially be designed for desktop environments, with potential future adaptations for mobile and tablet devices. It will be web-based, ensuring accessibility from various devices without the need for dedicated installations.

### 2.4 Design and Implementation Constraints  
Given the solo nature of the initial development, the software should prioritize simplicity and modularity. This ensures that future enhancements can be integrated seamlessly.

### 2.5 Assumptions and Dependencies  
The software assumes that the pricing constants and other foundational data provided are accurate. Any third-party integrations in future phases will depend on the compatibility and availability of external APIs or services.
# 3. System Features & Phases

## Phase 1: MVP

### 3.1.1 Quote Generation & Retrieval

**Objective**: Simplify and digitize the quote generation process.

- **Input Window Specifications**:
    - Users can input various window specifications, including dimensions, wood type, finish, hardware, glazing/glass, and custom design. Each window will have a unique identifier (`windowID`) for easy referencing.
- **Calculate Costs**:
    - The system will automatically calculate costs based on the provided specifications.
- **Generate and Display Quotes**:
    - Users can view the generated quote, which includes a detailed breakdown of costs. Each quote will have a unique identifier (`quoteID`) for easy referencing and tracking.
- **Save and Retrieve Quotes**:
    - Users can save quotes for future reference and retrieve them as needed.

## Phase 2: Project Management Light

**Objective**: Introduce basic project management capabilities to enhance the software's utility.
### 3.1.2 Customer Management

- **Manage Customer Details**:
    - Users can add, view, edit, and delete customer information.
- **Associate Quotes with Customers**:
    - Saved quotes can be linked to specific customers, providing a consolidated view of all quotes related to a particular customer. 

### 3.1.3 Project Status Tracking

- **Track Project Progress**:
    - Users can update the status of projects, marking them as "Pending", "Approved", "In Progress", "Completed", etc. Each project will have a unique identifier (`projectID`) for easy referencing and tracking.
- **Add Notes & Comments**:
    - Users can add relevant notes or comments to each project, providing context or additional information.

### 3.1.4 Attachments & Files

- **Associate Files with Projects**:
    - Users can attach relevant files or images to quotes or projects, such as sketches, designs, or photos of existing windows.

## Phase 3: Analytics & Trends

**Objective**: Provide insights into business operations and customer preferences.
### 3.1.5 Trends & Analytics Dashboard

- **View Business Insights**:
    - Users can access a dashboard that provides insights into popular wood types, finishes, and other customer preferences.
- **Track Key Metrics**:
    - The dashboard will also display metrics like average quote values, number of quotes generated, project completion rates, etc.
- **Visual Data Representation**:
    - Data will be presented using charts, graphs, and other visual tools for easy interpretation.

### 3.1.6 Historical Data Retrieval

- **Access Past Data**:
    - Users can retrieve past quotes and projects based on specific criteria, such as date range, customer, or project status.


# 4. External Interface Requirements

## 4.1 User Interfaces

### Phase 1: MVP

- **Desktop Interface**:
   - Simple, clean UI focusing on quote generation, retrieval, and detailed breakdown.
   - Basic login mechanism for user authentication.

### Phase 2: Project Management Light

- **Enhanced Desktop Interface**:
   - Additional sections/modules for customer management, project status tracking, and file attachments.
   - Improved navigation to switch between quote generation and project management seamlessly.

### Phase 3: Analytics & Trends

**Analytics Dashboard**:
   - Visual representations (charts, graphs) integrated into the UI for easier data interpretation.
   - Search and filter options for historical data retrieval.

## 4.2 Software Interfaces

### Phase 1: MVP

- **Database**: CRUD operations focused on quote generation, storage, and retrieval.
- **Backend**: Handling quote calculations, storage, and retrieval.
- **Frontend**: Quote generation form, list of saved quotes, and detailed breakdown view.

### Phase 2: Project Management Light

- **Database**: Extended CRUD operations for customer details, project status, and file attachments.
- **Backend**: Additional endpoints for customer management and project tracking.
- **Frontend**: Enhanced UI components for customer management and project tracking.

### Phase 3: Analytics & Trends

- **Database**: Queries optimized for analytics and trends.
- **Backend**: Endpoints for analytics data retrieval.
- **Frontend**: Dashboard components for visual data representation.

# 5. Non-functional Requirements

## 5.1 Performance

### Phase 1: MVP

- **Response Time**: Instant quote generation and retrieval.
- **Scalability**: Designed for a single user but keeping future scalability in mind.

### Phase 2 & 3

- **Enhanced Scalability**: As more features are added, ensure the system remains responsive and can handle additional data and users.

## 5.2 Security

### Phase 1: MVP

- **Authentication**: Basic login mechanism for user authentication.
- **Data Encryption**: Basic encryption for stored quotes.

### Phase 2 & 3

- **Enhanced Authorization**: Role-based access as more user types might be introduced, especially in the context of project management.

## 5.3 Reliability

### Phase 1: MVP

- **Data Integrity**: Ensure accurate quote calculations and storage.

### Phase 2 & 3

- **Data Backup**: As more data gets added (customer details, projects), implement more frequent data backup strategies.

## 5.4 Usability

### Phase 1: MVP

- **User-Friendly Interface**: Intuitive UI for quote generation and retrieval.

### Phase 2 & 3

- **Enhanced Navigation**: Improved UI components for seamless navigation between different modules.

## 5.5 Maintainability

### Across All Phases

- **Modularity**: Design the system in a modular fashion, allowing for easy updates and modifications.
- **Documentation**: Maintain clear documentation for each phase, detailing new features and changes.

# 6. Use Cases & User Stories

## 6.1 Use Cases

### Use Case 1: Generate a New Quote

**Primary Actor**: Administrator
**Scope**: Quote Generation Module  
**Level**: User Goal  

**Brief**:  
The user inputs window specifications and the system calculates and displays a quote.

**Flow of Events**:
1. The user logs into the system.
2. The user navigates to the "Generate Quote" section.
3. The user inputs window specifications, including dimensions, wood type, finish, hardware, glazing/glass, and special design. Each window inputted is assigned a unique `windowID`.
4. The system calculates the cost based on the provided specifications.
5. The system displays the generated quote with a detailed breakdown of costs. The generated quote is assigned a unique `quoteID`.
6. The user has the option to save the quote for future reference.

**Extensions**:
- 3a. If the user inputs invalid data, the system prompts the user to correct it.

---

### Use Case 2: Retrieve and Edit a Saved Quote

**Primary Actor**: Administrator
**Scope**: Quote Retrieval Module  
**Level**: User Goal  

**Brief**:  
The user retrieves a previously saved quote and makes edits if necessary.

**Flow of Events**:
1. The user logs into the system.
2. The user navigates to the "Saved Quotes" section.
3. The user selects a quote from the list using the `quoteID`.
4. The system displays the details of the selected quote.
5. The user edits the quote details as needed.
6. The system recalculates the quote based on the edits.
7. The user saves the updated quote.

**Extensions**:
- 5a. If the user inputs invalid data during editing, the system prompts the user to correct it.

---

## 6.2 User Stories

### User Story 1 :  
**As** an administrator,  
**I want** to input window specifications,  
**So that** I can generate a detailed quote for a customer.

**Acceptance Criteria**:  
- The system should allow input for dimensions, wood type, finish, hardware, glazing/glass, and special design.
- The system should display a quote based on the inputted specifications.
- The quote should include a detailed breakdown of costs.

---

### User Story 2:  
**As** an administrator,  
**I want** to retrieve and edit saved quotes,  
**So that** I can make necessary changes based on updated requirements or corrections.

**Acceptance Criteria**:  
- The system should list all saved quotes.
- The user should be able to select a quote and view its details using the `quoteID`.
- The user should be able to edit the quote details.
- The system should recalculate the quote based on the edits.



# 7. Appendices

## Appendix A: Glossary

**Administrator**: The primary user of the system, responsible for generating and managing quotes.

**API**: Application Programming Interface - a set of tools and protocols that allow different software applications to communicate with each other.

**CRUD**: Create, Read, Update, Delete - basic functions of persistent storage.

**Quote**: An estimated cost for a specific set of window specifications.

**Window Specifications**: The details and attributes of a window, including dimensions, wood type, finish, hardware, glazing/glass, and special design.

---

## Appendix B: References

1. San Francisco Historic Building Codes: [Link to the official website or document]
3. Window Constants Source: [Link or reference to where the window constants are derived from]

---

## Appendix C: [[Revision History]]

|Version|Date|Description of Changes|Author|
|---|---|---|---|
|1.0|10/09/2023|Initial draft|Gilberto A.|


---

# 8. Index

## A
Administrator, 2, 6  
API, 3, 7  
Appendices, 8

## C  
CRUD, 3, 7  
Customer Management, 4

## Q  
Quote, 2, 6  
Quote Generation, 3  
Quote Retrieval, 4

## W  
Window Specifications, 2, 6