# 🗳️ QuickVote (Work in Progress)

QuickVote is an online voting platform I'm building to make creating and managing elections easier and more flexible. The main idea is to let users sign up, create their own elections, and define how people can register to vote using custom forms. Once voters are approved by the election creator, they can cast their vote—only once!—and get notified by email when the results are out.

This project is still under active development, and things are evolving as I go.

---

## 🔍 What I'm Building

- A user system with email verification
- The ability for users to create elections
- Shareable registration links with custom forms for each election
- A review process to approve or reject voter applications
- One vote per user per election
- Real-time stats for each election (like how many voted, how many still pending)
- Email notifications for approvals, voting confirmations, and results

---

## 🏗️ Planned Entities and Relationships

### User
Users can be admins (who create elections) or voters (who apply and vote).  
Each user has:
- Username, email, password
- Role (admin or voter)
- Email verification status

### Election
Created by a user (admin), each election has:
- Title, description, start/end time
- A custom form for voters to fill before voting
- A shareable link for voter registration

### Candidate
Each election can have multiple candidates, added by the creator.

### Voter Application
When someone wants to vote, they fill out a form (custom per election).  
The election creator reviews the application and approves or rejects it.

### Vote
Only approved voters can vote, and they can vote **only once** per election.

### Notifications
Emails are sent for:
- Application approval
- Vote confirmation
- Final results

---

## 🔄 How Everything Connects

- A **user** registers → verifies their email
- A **verified user** creates an **election**
- That user adds **candidates** and defines a custom **form** for voter registration
- A **voter** fills the form via the **shareable link**
- The election creator reviews and **approves/rejects** the application
- If approved, the voter can **cast one vote**
- After the election ends, **results are emailed** to voters

---

## 🚧 Status

Right now, I’m still working on:
- Backend logic and API setup (Spring Boot)
- Database schema (MySQL)
- Authentication and authorization (Keycloak)
- Frontend (Angular + Tailwind CSS)

More updates coming soon!

