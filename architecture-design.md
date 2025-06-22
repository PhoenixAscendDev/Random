```mermaid
flowchart TD
    UI["📱 Frontend UI<br/>(Web, Mobile, Console, etc)"]
    API["🌐 API Layer<br/>(Controllers, Routes)"]
    DomainFacade["📦 DomainFacade (DLL)<br/>Use Case & Workflow Orchestration"]
    Microservices["🧩 Microservices<br/>(External or Self-Hosted)"]
    Managers["📦 Managers (DLL)<br/>Core Business Logic"]
    Grove["📦 GroveModules (DLL)<br/>Creative Feature Logic"]
    Core["📦 Core (DLL)<br/>Business Objects"]
    Data["📦 DataAccess (DLL)<br/>Persistence + Queries"]

    UI --> API
    API --> DomainFacade
    API --> Microservices
    DomainFacade --> Managers
    Microservices --> DomainFacade
    DomainFacade --> Grove
    Managers --> Core
    Grove --> Core
    Core --> Data
