# IoTAuthStorage — Secure Blockchain-Based Authentication & Trusted Data Logging for IoT Sensor Networks

A lightweight, Ethereum-based smart contract that enables **secure IoT device registration**, **authenticated data submission**, **nonce-based replay protection**, and **tamper-proof event logging**.  
Designed for real-world IoT and sensor network environments while remaining simple enough for academic and research use.

---

## 🔍 Overview

Traditional IoT sensor networks depend on centralized authentication servers that suffer from:

- Single points of failure  
- Weak auditability and mutable logs  
- Replay attacks using old sensor data  
- Device impersonation vulnerabilities  
- Tampering with recorded measurements  

**IoTAuthStorage** addresses these challenges using blockchain technology.  
It introduces a decentralized and verifiable approach to IoT authentication and data integrity through:

- On-chain device identity binding  
- Role-based ownership and auditor control  
- Nonce-based replay resistance  
- Immutable event logging of hashed data  
- Off-chain data integrity verification (e.g., IPFS hashes)  

---

## ✨ Key Features

### ✔️ Secure Device Registration
- System owner registers IoT devices and auditors.
- Each device is bound to a unique Ethereum address.
- Revoked devices are immediately disabled.

### ✔️ Authenticated Data Submission
- Devices submit data using their Ethereum address.
- Transactions are signed cryptographically — no passwords required.
- Only active devices can record data.

### ✔️ Nonce-Based Replay Protection
- Every device submission includes an incrementing nonce.
- Prevents replays of previously valid transactions.
- Enforces strict transaction order per device.

### ✔️ Tamper-Evident Logging
- Sensor data stored as `keccak256`-derived hashes.
- On-chain `DataRecorded` events ensure immutable audit trails.
- Off-chain data integrity verified by recomputing hashes.

### ✔️ Auditor Role
- Owner can assign trusted auditor accounts.
- Auditors monitor device and data activity via emitted blockchain events.

### ✔️ Gas-Efficient Architecture
- Uses mappings and events instead of arrays for minimal gas cost.
- Supports thousands of devices with constant-time lookups.

---

## 🧱 Architecture Summary

**Actors**
- **Owner** – Registers and revokes devices or auditors.
- **Devices** – Represent IoT sensors submitting hashed readings.
- **Auditors** – Monitor all transactions and verify logs.

**Core Modules**
- Device Registry  
- Nonce Management System  
- Data Recording Module  
- Auditor Management Module  
- Event-Based Logging System  

---

## ⚙️ Installation & Usage

### 1️⃣ Clone the Repository

git clone https://github.com/mostafa-hatem/blockchain-proj.git

cd proj.git

### 2️⃣ Install Dependencies (Hardhat Users)
npm install

### 3️⃣ Compile the Smart Contract
npx hardhat compile

### 4️⃣ Deploy (Example Local Deployment)
npx hardhat run scripts/deploy.js --network localhost

🧪 Testing
✔️ Using Remix IDE (Beginner-Friendly)

Open Remix IDE

Upload IoTAuthStorage.sol

Compile with Solidity 0.8.19

Deploy using Injected Web3 (MetaMask)

Simulate the following roles:

Owner → registers devices and auditors

Device → submits data with increasing nonces

Auditor → monitors event logs

✔️ Hardhat Tests (Optional)

Example test file (test/IoTAuthStorage.test.js):

describe("IoTAuthStorage", function () {
    it("Should register a new device and record data", async function () {
        // test logic here
    });
});


Run tests:

npx hardhat test

🔐 Security Properties

✅ Impersonation Prevention: Transactions validated via sender’s Ethereum address.

✅ Modification Resistance: Logged data cannot be altered after recording.

✅ Replay Protection: Nonce check ensures unique, sequential submissions.

✅ Auditable Transparency: Every action is permanently logged on-chain.

✅ Owner-Restricted Control: Only owner can register or revoke devices/auditors.

📈 Performance Summary

Gas-Efficient: Mappings and events minimize on-chain storage cost.

Latency: Sub-millisecond execution in Remix VM; few seconds on testnet confirmation.

Scalability: Supports thousands of devices with constant gas per transaction.

Reliability: Immutable event logs ensure complete traceability.

🔮 Future Enhancements

🌐 IPFS integration for off-chain sensor data storage

⚡ Layer-2 deployment (Polygon, Optimism, Arbitrum)

🔑 Signature-based authentication (ECDSA validation)

🧩 Multi-owner governance and hierarchical policies

🧠 Formal verification of nonce correctness and access logic

🕵️ Zero-knowledge proofs for private device data submissions


README.md

👥 Contributors

Mohamed Ahmed Samy — 221005759

Mostafa Hatem Mostafa — 221007552

Saad-El-Din Sayed — 221006143
Arab Academy for Science and Technology

📜 License

Released under the MIT License
