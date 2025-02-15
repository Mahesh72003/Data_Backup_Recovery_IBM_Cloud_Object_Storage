# Cloud Storage Monitoring and Backup Automation

## Overview

This project is a cloud storage monitoring and backup automation system. It continuously checks the status of IBM Cloud Object Storage and ensures efficient usage by monitoring storage space, sending alerts, and managing backups.

## Features

- **Storage Monitoring**: Regularly checks the storage bucket to monitor available space.
- **Alert System**:
  - Sends email notifications when storage exceeds 70%, 80%, and 90%.
  - Sends Telegram alerts when storage crosses 90%.
  - Stops uploads when storage reaches 95%.
- **Automated Backup Handling**:
  - Switches to a backup storage if the main storage fails.
  - Runs `auto_upload_monitoring_backup_to_main.py` if all checks pass.
  - Executes `main_to_backup_10m.py` every 10 minutes for parallel monitoring.
- **Logging**: Stores logs of all operations for auditing and troubleshooting.

## Requirements

- Python 3.x
- IBM Cloud Object Storage account
- Required Python libraries:
  - `ibm_boto3` (for IBM Cloud Object Storage integration)
  - `requests` (for Telegram alerts)
  - `smtplib` (for email notifications)
  - `logging` (for log management)

## Installation

1. Clone the repository:
   ```sh
   git clone https://github.com/your-repo/cloud-storage-monitor.git
   cd cloud-storage-monitor
   ```
2. Install dependencies:
   ```sh
   pip install -r requirements.txt
   ```
3. Set up environment variables for IBM Cloud credentials, email SMTP settings, and Telegram bot details.

## Usage

1. Run the main script:
   ```sh
   python monitor_storage.py
   ```
2. To enable auto-upload monitoring, execute:
   ```sh
   python auto_upload_monitoring_backup_to_main.py
   ```
3. To continuously monitor storage and run parallel backups every 10 minutes:
   ```sh
   python main_to_backup_10m.py
   ```

## Configuration

Modify the configuration settings in `config.py`:

- IBM Cloud Object Storage bucket name and API keys
- Email SMTP server details
- Telegram bot token and chat ID

## Logging

All events and errors are logged for auditing. Logs are stored in `logs/monitor.log`.

## Error Handling

- If the bucket is not found, an error notification is sent.
- If storage usage crosses thresholds, appropriate warnings and alerts are triggered.
- If the main storage fails, the system automatically switches to the backup storage and notifies the user.

## Future Enhancements

- Add a web dashboard for real-time monitoring.
- Implement AI-based anomaly detection for better predictive alerts.
- Introduce multi-cloud support for redundancy.

## Authors
This project was developed by:
- A V Mahesh 
- Manoj V 
- Rohan T Y 
- Abhishek G

## License

This project is licensed under the MIT License.

