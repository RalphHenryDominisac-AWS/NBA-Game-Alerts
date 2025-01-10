# NBA Game Day Notifications / Sports Alerts System

## Overview

The NBA Game Day Notifications system delivers real-time game updates and alerts to subscribed users through SMS and email. This project leverages **Amazon SNS**, **AWS Lambda**, **Amazon EventBridge**, and **NBA APIs**, demonstrating the capabilities of cloud computing in enabling real-time notification systems.

Subscribers gain instant access to game scores, statuses, and other essential information via their preferred communication channels.
---

## Features

- **Real-Time Notifications**: Get instant updates on NBA game scores, schedules, and statuses.
- **Multi-Channel Support**: Notifications delivered via SMS or Email using **Amazon SNS**.
- **Comprehensive Game Data**: Includes scores by quarter, current status, and other key details.
- **Efficient Cloud Design**: Built with AWS services to ensure scalability and reliability.

---

## Architecture

1. **AWS Lambda**: Handles fetching data from the NBA API and publishing notifications to SNS.
2. **Amazon SNS**: Distributes notifications to subscribers.
3. **Amazon EventBridge**: Schedules and triggers Lambda functions for daily game updates.
4. **NBA APIs**: Provides real-time NBA game data.


![Image Alt](https://github.com/RalphHenryDominisac-AWS/NBA-Game-Alerts/blob/e891c2e244f8bf6bdc8d9c4d3bcc2d708f60d137/Architecture.png)
---

## Installation and Setup

### Prerequisites

1. AWS Account with permissions to manage **Lambda**, **SNS**, and **EventBridge**.
2. An active subscription to the [SportsData.io NBA API](https://sportsdata.io/).
3. Python 3.8+ installed locally for development.

### Steps

1. **Clone the Repository**:

   ```bash
   git clone https://github.com/yourusername/nba-game-day-notifications.git
   cd nba-game-day-notifications
   ```

2. **Environment Variables**:

   - `NBA_API_KEY`: Your NBA API key from SportsData.io.
   - `SNS_TOPIC_ARN`: ARN of your Amazon SNS topic.

3. **Deploy AWS Resources**:

   - Create an SNS topic and configure the policy:
     ```json
     {
       "Version": "2012-10-17",
       "Statement": [
         {
           "Effect": "Allow",
           "Action": "sns:Publish",
           "Resource": "arn:aws:sns:REGION:ACCOUNT_ID:gd_topic"
         }
       ]
     }
     ```
   - Deploy the Lambda function and attach the required environment variables.

4. **Schedule the Lambda Function**:

   - Use Amazon EventBridge to trigger the function daily to fetch game updates.

5. **Test the System**:
   - Subscribe to the SNS topic via Email/SMS.
   - Manually trigger the Lambda function to ensure proper notifications.

---

## Usage

1. **Real-Time Notifications**:
   - Subscribe to the SNS topic to start receiving alerts.
2. **Daily Updates**:
   - Notifications are sent daily for all games, including:
     - Scheduled games
     - Games in progress
     - Final scores and summaries

---

## Code Overview

### Lambda Function

```python
import os
import json
import urllib.request
import boto3
from datetime import datetime, timedelta, timezone

# Function details omitted for brevity. See the repository for the full implementation.
```

### SNS Policy

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "sns:Publish",
      "Resource": "arn:aws:sns:REGION:ACCOUNT_ID:gd_topic"
    }
  ]
}
```

---

## Technologies Used

- **AWS Lambda**
- **Amazon SNS**
- **Amazon EventBridge**
- **NBA APIs**
- **Python**

---

## License

This project is licensed under the [MIT License](LICENSE).

---
