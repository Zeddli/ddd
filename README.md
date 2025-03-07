# Decentralized Health Data Exchange on Vanar Chain

## Overview

This project is a decentralized healthcare data exchange platform built on Vanar Chain—a high-performance, low-fee, eco-friendly blockchain solution designed for mass market adoption. Our platform leverages Vanar's innovative infrastructure to auto-generate and deploy dedicated smart contracts for each new user and health record, ensuring data integrity, transparency, and security through immutable on-chain audit trails.

**Key Features:**
- **Automated Smart Contract Deployment:**  
  - **User Contracts:** Each new user registration triggers the deployment of a dedicated User contract via a factory (UserFactory).
  - **Health Record Contracts:** Each health record submission triggers the deployment of a dedicated HealthRecord contract via a factory (HealthRecordFactory).
- **Immutable Audit Trail:**  
  On-chain events capture user registrations and health record submissions for complete transparency.
- **Low Transaction Fees & High Throughput:**  
  Built on Vanar Chain, the platform offers fast transactions and minimal fees, making it ideal for critical healthcare interactions.
- **User-Friendly Frontend:**  
  A React-based interface with intuitive navigation allows users to register, log in, submit health records, and view audit logs and deployed contracts.

## Architecture

### Smart Contracts
- **User.sol & UserFactory.sol:**  
  Each user is represented by a dedicated contract deployed automatically through the UserFactory.
- **HealthRecord.sol & HealthRecordFactory.sol:**  
  Each health record is encapsulated in its own contract deployed via the HealthRecordFactory.
- **Audit Trail:**  
  Both factory contracts emit events (`UserCreated` and `RecordCreated`) which are captured and displayed via our audit endpoints.


### Deployment and verification
- **User.sol**
https://explorer-vanguard.vanarchain.com/address/0xb7DaaE00D00b7e0A760bd59450CCD9a9847702ff?tab=contract

- **HealthRecord.sol**
https://explorer-vanguard.vanarchain.com/address/0xc3cbD37ed2bd47e1E0F4E82C71B19C75B2035217?tab=contract

- **UserFactory.sol**
https://explorer-vanguard.vanarchain.com/address/0x9F627028A097b05a6229D7a16a37585A6d48D283?tab=contract

- **HealthRecordFactory.sol**
https://explorer-vanguard.vanarchain.com/address/0xa55aB855bA295106aAb4f095b7BB9e4c3d6e541b?tab=contract

### Backend
- **Express Server:**  
  Provides RESTful API endpoints for:
  - Deploying new User contracts (`POST /user`)
  - Deploying new HealthRecord contracts (`POST /healthrecord`)
  - Retrieving audit logs for user registrations (`GET /audit/user`)
  - Retrieving audit logs for health record submissions (`GET /audit/record`)
  - Fetching a list of deployed HealthRecord contract addresses (`GET /deployed-records`)
- **Blockchain Interaction:**  
  Uses ethers.js to interact with the Vanar network, leveraging environment variables for configuration.

### Frontend
- **React Application:**  
  - **Routing:** Implemented using React Router.
  - **Pages:**  
    - **Landing Page:** Initial page offering options to log in or register.
    - **Login & Register Pages:** Allow users to authenticate and create new accounts.
    - **SubmitRecord:** Form for submitting health records (includes patient NRIC, diagnosis, description, date, treatment, hospitalisation).
    - **AuditTrail:** Dashboard displaying user registration and health record submission events.
    - **DeployedRecords:** Page listing deployed HealthRecord contract addresses.
- **API Integration:**  
  Axios is used to call the Express backend endpoints from the React frontend.

## Getting Started

### Prerequisites
- [Node.js](https://nodejs.org/) (v14+ recommended)
- [npm](https://www.npmjs.com/)
- [Hardhat](https://hardhat.org/)
- A Vanar Chain RPC endpoint and valid account credentials

### Installation

1. **Clone the Repository:**
   ```bash
   git clone <repository_url>
   cd deheal


**Future Enhancements**
Enhanced Authentication:
Implement secure login and authentication with token-based sessions.

Advanced UI/UX:
Improve styling and add responsive design using a UI library such as Bootstrap or Material-UI.

Additional Audit Features:
Enable real-time updates and filtering of audit logs.

Automated Verification for Deployed Contracts:
Integrate with Vanar’s explorer verification if available in the future.

Scalability:
Incorporate off-chain storage (e.g., IPFS) for larger health record data.


License
This project is licensed under the MIT License.
