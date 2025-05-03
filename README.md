## 🧱 Planned Microservices Architecture

QuickVote is being developed with a microservices architecture using Spring Boot and MySQL. I'm also integrating **Spring Cloud Config Server** and **Eureka Discovery Server** to support scalable and maintainable service communication.

### 🔌 Core Services

- **Config Server**  
  Centralized configuration for all microservices. Helps keep environment-specific settings in one place.

- **Discovery Server (Eureka)**  
  Registers all services for dynamic discovery. Makes inter-service communication more flexible and avoids hardcoding service URLs.

- **API Gateway**  
  Routes client requests to appropriate backend services. Will also handle basic request filtering and security.

### 🧩 Planned Business Services

- **Auth Service**  
  Handles user registration, login, and email verification. Will be integrated with Keycloak for advanced auth.

- **User Service**  
  Manages user roles, status, and profile details.

- **Election Service**  
  Creates and manages elections, time ranges, and custom voter forms.

- **Candidate Service**  
  Manages candidates within an election.

- **Voter Application Service**  
  Accepts and stores form submissions from prospective voters. Allows admins to approve or reject requests.

- **Voting Service**  
  Lets approved users vote (only once per election). Handles vote storage and validation.

- **Notification Service**  
  Sends approval emails, voting confirmations, and election results.

- **Result Service**  
  Tallies votes after the election ends and triggers result emails to voters.

---

## ⚙️ Tech Stack (So Far)

- Spring Boot (for all microservices)
- Spring Cloud Config
- Eureka Discovery Server
- Angular (Frontend)
- Tailwind CSS (Styling)
- MySQL (Database)
- Keycloak (Authentication)
- Docker (planned for containerization)
