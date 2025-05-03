# 🗳️ QuickVote – Online Voting Platform

QuickVote is a secure, flexible, and user-friendly online voting system designed to enable users to create customizable elections with dynamic voter registration and approval workflows. It supports email notifications, real-time election statistics, and post-election result delivery.

---

## 📘 System Overview

QuickVote allows any registered and verified user to create elections and define custom forms for voter registration. Voters apply to participate through a shareable election link, and only approved applicants are permitted to vote. The system enforces strict one-vote-per-election rules and keeps all users informed through email notifications. Results are automatically emailed to voters after the election ends.

---

## 🏗️ Entity-Relationship Model

### 1. **User**
Represents a registered platform user (Admin or Voter).

- `user_id`: Primary Key
- `username`: Display name
- `email`: Verified email address
- `password_hash`: Hashed password
- `email_verified`: Boolean flag
- `role`: 'Admin' or 'Voter'
- `created_at`: Timestamp
- `status`: 'Active' or 'Suspended'

---

### 2. **Election**
Created by a user and contains metadata, voting period, and a custom voter form.

- `election_id`: Primary Key
- `title`: Election title
- `description`: Description
- `created_by`: FK → User.user_id
- `start_time`: Start datetime
- `end_time`: End datetime
- `voter_form_schema`: JSON schema for custom voter form
- `shareable_link`: Unique URL for voter applications
- `created_at`: Timestamp
- `status`: 'Draft', 'Ongoing', 'Completed'

---

### 3. **Candidate**
Represents a candidate in a specific election.

- `candidate_id`: Primary Key
- `election_id`: FK → Election.election_id
- `name`: Candidate's name
- `description`: Information about the candidate
- `registered_at`: Timestamp

---

### 4. **VoterApplication**
Submitted by users (via shareable link) to request participation in an election.

- `application_id`: Primary Key
- `election_id`: FK → Election.election_id
- `applicant_email`: Email of the applicant
- `form_data`: JSON or text data from dynamic form
- `status`: 'Pending', 'Approved', 'Rejected'
- `decision_by`: FK → User.user_id (admin reviewer)
- `applied_at`: Timestamp
- `decision_at`: Timestamp
- `notification_sent`: Boolean

---

### 5. **Vote**
Stores a single vote cast by an approved voter.

- `vote_id`: Primary Key
- `election_id`: FK → Election.election_id
- `voter_email`: Email address of voter
- `candidate_id`: FK → Candidate.candidate_id
- `voted_at`: Timestamp

*Constraint: One vote per voter per election.*

---

### 6. **ElectionStats** *(Optional View or Computed Table)*
Summarizes key voting metrics in real-time.

- `election_id`: FK → Election.election_id
- `total_candidates`: Number of candidates
- `total_voters_approved`: Approved voters
- `total_votes_cast`: Votes already cast
- `total_pending_voters`: Applications still pending

---

### 7. **Notification**
Tracks all system email notifications.

- `notification_id`: Primary Key
- `recipient_email`: Target email
- `subject`: Email subject
- `content`: Email body
- `type`: 'Approval', 'VoteConfirmation', 'Result'
- `sent_at`: Timestamp
- `status`: 'Sent' or 'Failed'

---

### 8. **ElectionResultEmail**
Logs which voters have received results after election ends.

- `result_id`: Primary Key
- `election_id`: FK → Election.election_id
- `voter_email`: Voter’s email
- `sent_at`: Timestamp

---

## 🔄 Summary of Relationships

- A **User** can act as an **Admin** (who creates elections and approves voters) or as a **Voter** (who applies and votes).

- A **verified User** can create one or more **Elections**.

- An **Election** belongs to one **User** and contains multiple **Candidates**.

- A **VoterApplication** is submitted per **Election** and reviewed by the election creator.

- Only **approved applications** can result in a **Vote**, which is restricted to one per election per voter email.

- The voting interface shows **real-time stats**, including total candidates, votes cast, pending applications, and remaining voters.

- After the election ends, the system automatically sends **results via email** to each approved voter.

---

## ✅ Key Features

- Email-verified user registration
- Custom election creation with dynamic voter forms
- Shareable voter registration link
- Admin review and approval of voter applications
- Real-time voting statistics
- Secure one-vote-per-election enforcement
- Email notifications for approvals, voting, and results

---

