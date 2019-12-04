# Stackdriver Log Export to Datadog
## Overview

This script automates the GCP configurations required to export selected logs from Stackdriver Logging to Cloud Pub/Sub for ingestion into Datadog.  At a high level, this script automates the following tasks, as outlined in the [Datadog documentation](https://docs.datadoghq.com/integrations/google_cloud_platform/):
- The installation of the Google Cloud SDK, including initial authentication (disabled by default)
- The creation of a new service account (including the creation and storage of its private key)
- The configuration of appropriate Cloud IAM permissions for the new service account
- The creation of a new Cloud Pub/Sub topic
- The creation of a new Cloud Pub/Sub push subscription
- The creation of a Stackdriver Logging export sink (including the configuration of appropriate Cloud IAM permissions on the new Cloud Pub/Sub topic)

## Instructions

This script must be run once for each project to be monitored via Datadog:
- Set variables on lines 20-30, including:
  - Project ID
  - Service Account name
  - Service Account private key export path
  - Cloud Pub/Sub Topic name (which is also used for the Cloud Pub/Sub subcription)
  - Datadog API key
  - Stackdriver Logging Sink name
- If you have not already installed the Google Cloud SDK, uncomment lines 34-44
- Save changes, and ake "configureExportToDatadog" executable
  ```
  chmod +x /path/to/file/configureExportToDatadog
  ```
- Run the script and check output for errors
  ```
  .\/path/to/file/configureExportToDatadog
  ```
- Upload the Service Account private key (JSON file) in the **Configuration** tab of the [Datadog Google Cloud Integration tile](http://app.datadoghq.com/account/settings#integrations/google_cloud_platform)
