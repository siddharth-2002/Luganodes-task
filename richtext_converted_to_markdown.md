ETH Deposit Tracker - Documentation
===================================

Objective
---------

The objective of this project is to create an ETH deposit tracker that monitors deposits made to the Ethereum 2.0 deposit contract, extracts relevant data, and saves it into a defined schema. The application will also include error handling, logging mechanisms, and an optional alerting system using Grafana, Prometheus, and Telegram notifications.

Purpose
-------

This application is designed to:

-   Track ETH deposits by monitoring Ethereum 2.0 deposit events.
-   Save deposit details into a specified schema.
-   Provide an alerting mechanism to notify users in case of issues or significant deposits via Telegram, Grafana dashboards, and Prometheus alerts.

Tech Stack to be Used
---------------------

-   **Node.js** (version 14 or above)
-   **npm** or **yarn** (for package management)
-   **Ethereum Node Provider** (e.g., Alchemy, Infura)
-   **Docker** (optional, for containerization)
-   **Grafana** (for monitoring and visualization)
-   **Prometheus** (for metrics collection and alerting)
-   **Telegram Bot** (for notifications)
-   **Ethereum Wallet** (e.g., MetaMask, for testing)

* * * * *

Installation and Setup
----------------------

### Prerequisites

Ensure you have the following installed on your machine:

-   **Node.js** (version 14 or above)
-   **npm** or **yarn**
-   **Docker** (optional, if containerizing the application)
-   **MetaMask** (for Ethereum wallet testing)
-   **Prometheus** (for metrics collection)
-   **Grafana** (for visualization)

### Step 1: Clone the Repository

bash

Copy code

`git clone https://github.com/your-repo/eth-deposit-tracker.git
cd eth-deposit-tracker`

### Step 2: Install Dependencies

Use **npm** or **yarn** to install the required packages:

bash

Copy code

`npm install
# or
yarn install`

### Step 3: Configure Environment Variables

Create a `.env` file in the root of the project. You'll need the following environment variables:

bash

Copy code

`ETHEREUM_NODE_URL=<Your_Ethereum_Node_URL>   # Get from Alchemy or Infura
TRACKING_CONTRACT_ADDRESS=<Ethereum_2.0_Contract_Address>   # The contract address of Ethereum 2.0 deposit contract
GRAFANA_URL=<Your_Grafana_Instance_URL>
PROMETHEUS_URL=<Your_Prometheus_Instance_URL>
TELEGRAM_BOT_TOKEN=<Your_Telegram_Bot_Token> # From BotFather on Telegram
TELEGRAM_CHAT_ID=<Your_Chat_ID> # The chat ID to send notifications`

### Step 4: Setup Telegram Bot for Notifications

1.  Open **Telegram** and search for **BotFather**.
2.  Use `/newbot` to create a new bot, follow the instructions, and get the **Bot Token**.
3.  Store the **Bot Token** in the `.env` file as `TELEGRAM_BOT_TOKEN`.
4.  Use the following commands to configure your bot:
    -   `/setprivacy` to disable privacy mode, allowing your bot to see messages.
    -   Send a message to your bot to generate a **Chat ID**.
    -   You can get the **Chat ID** by visiting `https://api.telegram.org/bot<Your_Bot_Token>/getUpdates`.

### Step 5: Run the Application

Once the environment variables are set, you can run the tracker:

bash

Copy code

`npm start`

To run with Docker:

1.  Build the Docker image:

    bash

    Copy code

    `docker build -t eth-deposit-tracker .`

2.  Run the Docker container:

    bash

    Copy code

    `docker run -d --env-file .env eth-deposit-tracker`

### Step 6: Setting up Grafana for Monitoring

1.  Install and set up a Grafana instance using the official Grafana documentation.
2.  Create a dashboard for monitoring ETH deposits.
3.  Configure Grafana alerts and integrate them with your Telegram bot via the **Alert Notification** section in Grafana.

### Step 7: Setting up Prometheus for Metrics Collection

1.  Install and set up a Prometheus instance using the official Prometheus documentation.

2.  Configure Prometheus to scrape metrics from your ETH deposit tracker application by adding it to the `prometheus.yml` configuration file:

    yaml

    Copy code

    `scrape_configs:
      - job_name: 'eth-deposit-tracker'
        static_configs:
          - targets: ['localhost:3000']  # Replace with your application's address`

3.  Define custom metrics in your application for Prometheus to scrape. Add metrics to `tracker.js` and expose them using an HTTP endpoint.

4.  Set up alerts in Prometheus based on your custom metrics and configure alerting rules to notify via Grafana or other channels.

* * * * *

Code Structure
--------------

-   **`app.js`**: Entry point for the application.
-   **`utils.js`**: Utility functions like error handling, formatting, etc.
-   **`tracker.js`**: Core logic for monitoring the Ethereum 2.0 deposit contract.
-   **`alerts.js`**: Logic for sending Telegram and Grafana alerts.
-   **`metrics.js`**: Custom Prometheus metrics and exposure.
-   **`models/Deposit.js`**: Schema for saving deposit data (block number, timestamp, fee, hash, and public key).

* * * * *

Usage Instructions
------------------

1.  **Start Tracking**: Once the app is running, it will continuously track deposits to the Ethereum 2.0 contract.

2.  **Deposit Schema**:

    javascript

    Copy code

    `{
      blockNumber: Number,
      blockTimestamp: Date,
      fee: Number,
      hash: String,
      pubkey: String
    }`

    -   Each deposit event will save data to this schema, ensuring consistency.
3.  **Alerts and Notifications**:

    -   Telegram alerts are triggered based on predefined conditions like large deposits or errors.
    -   Grafana dashboards provide real-time monitoring of the application status and tracked deposits.
    -   Prometheus metrics allow for detailed monitoring and alerting based on application performance.

* * * * *

Future Work
-----------

-   **Integration with Other Ethereum Networks**: Extend support to monitor deposits on Ethereum testnets or Layer 2 solutions.
-   **Improved Alerting**: Add more advanced alerts, such as Slack or email notifications.
-   **Automated Scaling**: Implement auto-scaling features using cloud services like AWS or Google Cloud.
-   **Performance Optimization**: Improve deposit tracking speed for higher throughput.
