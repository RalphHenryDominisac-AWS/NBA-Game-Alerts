# NBA Game Day Notifications / Sports Alerts System

## Overview

The NBA Game Day Notifications system provides real-time game updates and notifications to subscribed users via SMS or Email. This project integrates **Amazon SNS**, **AWS Lambda**, **Amazon EventBridge**, and **NBA APIs**, showcasing the power of cloud computing for real-time alert systems.

Subscribers receive up-to-date game scores, statuses, and other critical details directly in their preferred communication channel.

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
