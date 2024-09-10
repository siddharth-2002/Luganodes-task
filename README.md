# Luganodes_task_21bce5172
This project is designed to monitor and record Ethereum (ETH) deposits on the Beacon Deposit Contract, tracking deposits in real-time. The tracker establishes an RPC connection to an Ethereum node and captures details like deposit amount, sender address, timestamp, and more.


The Ethereum Deposit Tracker is designed to:

Monitor the Beacon Deposit Contract (0x00000000219ab540356cBB839Cbe05303d7705Fa) for incoming ETH deposits.
Handle and store multiple deposits within a single transaction, including internal transactions.
Provide robust error handling and logging mechanisms.
Optional: Set up a Grafana dashboard and Telegram notifications for alerting.
Prerequisites:
Before you begin, ensure you have met the following requirements:

Node.js (version 14 or above)
npm or yarn
An Ethereum node provider (e.g., Alchemy, Infura)
Docker (if you intend to Dockerize the application)
An Ethereum wallet (e.g., MetaMask) for testing purposes
Installation
Clone the Repository:

bash
Copy code
git clone https://github.com/your-username/eth-deposit-tracker.git
cd eth-deposit-tracker
Install Dependencies:

Use npm or yarn to install the required dependencies:

bash
npm install
 or
yarn install
Run the Application:
npm start
Start the Ethereum deposit tracker:

bash
Copy code
npm start
 or
yarn start
