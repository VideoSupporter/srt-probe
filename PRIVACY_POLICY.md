# Privacy Policy for SRT Probe

**Last Updated: November 26, 2025**

## Introduction

This Privacy Policy describes how SRT Probe ("we", "our", or "the application") handles user information. We are committed to protecting your privacy and being transparent about our data practices.

## Information Collection

**SRT Probe does not collect, transmit, or store any personal information.**

The application operates entirely on your local computer and does not:
- Collect personal data
- Track user behavior
- Send analytics or telemetry data
- Connect to external servers for data collection
- Share information with third parties

## Local Data Storage

SRT Probe stores the following data **locally on your computer only**:

### Application Settings
- User interface preferences (language, theme, etc.)
- Network test configurations (IP addresses, ports, test parameters)
- Test history and results

This data is stored locally using Electron's built-in storage mechanisms and never leaves your device.

### Test Results
- SRT network test results are saved as JSON files on your local computer
- You have full control over these files and can delete them at any time
- These files are not transmitted to any external servers

## Network Activity

SRT Probe performs network testing by:
- **Sender Mode**: Sending SRT protocol data streams to IP addresses and ports **you specify**
- **Receiver Mode**: Listening on a port **you specify** and accepting SRT connections from any IP address
- All network communication is limited to the SRT testing functionality
- No data is sent to our servers or any third-party services

The application only communicates with:
- **Sender Mode**: IP addresses and ports that **you explicitly configure** for testing purposes
- **Receiver Mode**: Listens on the port you configure and accepts SRT connections from all incoming IP addresses
- No other network connections are made outside of SRT testing

## Third-Party Services

SRT Probe does not integrate with or use any third-party analytics, tracking, or advertising services.

## Data Security

Since all data is stored locally on your computer:
- You are responsible for the security of your device
- We recommend following standard security practices (antivirus software, firewall, etc.)
- Test results containing sensitive network information should be handled according to your organization's security policies

## Children's Privacy

SRT Probe does not knowingly collect any information from anyone, including children under the age of 13.

## Changes to This Privacy Policy

We may update this Privacy Policy from time to time. Any changes will be reflected in the application documentation with an updated "Last Updated" date.

## Contact Information

If you have questions about this Privacy Policy, please:
- Open an issue on our GitLab repository
- Contact us at: [videosp.info@gmail.com]

## Your Rights

As SRT Probe does not collect any personal information, there is no personal data to:
- Request access to
- Request deletion of
- Request correction of
- Request transfer of

All application data is stored locally on your device and can be deleted by:
1. Uninstalling the application
2. Manually deleting the application data folder at: `%APPDATA%\srt-probe-gui`

## Compliance

This application complies with:
- General Data Protection Regulation (GDPR)
- California Consumer Privacy Act (CCPA)
- Other privacy regulations

Since we do not collect any personal information, most privacy regulation requirements do not apply.

## Summary

**In short: SRT Probe respects your privacy by not collecting any data. Everything stays on your computer.**

---

**SRT Probe Team**  
November 26, 2025
