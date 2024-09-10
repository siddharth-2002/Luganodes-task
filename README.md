# Luganodes Task - Ethereum Deposit Tracker

This project aims to monitor and record Ethereum (ETH) deposits on the Beacon Deposit Contract in real-time. The Ethereum Deposit Tracker provides an efficient solution to track deposits, capture detailed information such as the deposit amount, sender address, timestamp, and more, while offering advanced features like monitoring dashboards and alert systems.

## Scope

The Ethereum Deposit Tracker is designed to:

- Monitor the Beacon Deposit Contract (`0x00000000219ab540356cBB839Cbe05303d7705Fa`) for incoming ETH deposits.
- Handle and store multiple deposits within a single transaction, including internal transactions.
- Provide real-time tracking and logging mechanisms to ensure robust performance.
- Optional: Set up a Grafana dashboard and Telegram notifications for real-time alerting and monitoring.

This tool is especially useful for developers working with Ethereum staking, financial auditors, blockchain analytics platforms, and anyone who needs to monitor ETH deposits in real-time.

## Tech Stack

- **Node.js**: Backend logic, interaction with the Ethereum network, and capturing deposit data.
- **Express.js**: Server setup and API routes.
- **PostgreSQL**: Persistent storage for deposit data.
- **Docker**: Containerization for consistent deployment environments.
- **Grafana**: Real-time monitoring and visualization of deposit data.
- **Prometheus**: Metrics collection and alerting mechanisms.
- **cAdvisor**: Container resource usage tracking.
- **Telegram Bot API**: Real-time alerts via Telegram.

## Prerequisites

Before you begin, ensure you have met the following requirements:

- **Node.js** (version 14 or above)
- **npm** or **yarn**
- An Ethereum node provider (e.g., **Alchemy**, **Infura**)
- **Docker** (for Dockerized deployment)
- An Ethereum wallet (e.g., **MetaMask**) for testing purposes
## Future Scope


-Automated Report Generation: Integrate a feature to automatically generate reports for daily, weekly, or monthly deposits.
-Advanced Analytics: Incorporate analytics capabilities for deeper insights into deposit trends and behaviors.
-Multi-chain Support: Expand the tracker to monitor deposits on other Ethereum-compatible chains, such as Binance Smart Chain (BSC) and Polygon.
-Enhanced Security: Implement additional security layers, such as encryption for sensitive data and access controls.

## Installation

# Clone the repository
git clone https://github.com/siddharth-2002/Luganodes-task.git
cd Luganodes-task

# Install Dependencies
# Use npm or yarn to install the required dependencies
npm install
# or
yarn install

# Running the Application
# Start the Ethereum Deposit Tracker
npm start
# or
yarn start

# The tracker will establish an RPC connection to your Ethereum node provider and start monitoring deposits on the Beacon Deposit Contract.

# Docker Deployment
# If you prefer to run the application using Docker:

# Create a Docker Network
docker network create grafana-net

# Run the Monitoring Stack
# Navigate to the monitoring-stack folder and start the stack
cd monitoring-stack
docker compose up -d

# Run the Tracker App
# Enter the tracker-stack folder and start the application
cd ../tracker-stack
ALCHEMY_API_KEY=<YOUR_ALCHEMY_API_KEY> docker compose up -d
