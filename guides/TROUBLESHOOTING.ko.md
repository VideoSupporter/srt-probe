# 🔧 Troubleshooting

> 🌐 **Languages**: [English](TROUBLESHOOTING.md) | [日本語](TROUBLESHOOTING.ja.md) | [中文](TROUBLESHOOTING.zh.md) | [한국어](TROUBLESHOOTING.ko.md) | [Español](TROUBLESHOOTING.es.md)

This document provides solutions for problems that may occur while using SRT Probe.

## Cannot Connect

**Symptom**: Test stays "Disconnected" after starting

**Solutions**:
1. Verify that SRT Probe is allowed in the firewall
2. Confirm the port number is correct (use the same port number on sender and receiver)
3. Verify one side is waiting in Listener mode
4. Confirm the IP address is correct

## Statistics Not Displayed

**Symptom**: Connection succeeds but RTT or throughput is not displayed

**Solutions**:
1. Verify data is actually being sent and received
2. Confirm running in Sender mode (statistics may not display with Receiver only)
3. Check log output for errors

## Language Does Not Change

**Symptom**: UI does not change after selecting a language

**Solutions**:
1. Exit the app completely and restart
2. Check the settings file: `C:\Users\[username]\.srt-probe\settings.json`
3. If the settings file is corrupted, delete it and restart

## App Won't Start

**Symptom**: Nothing happens when double-clicking the icon

**Solutions**:
1. Check Windows version (Windows 10/11 required)
2. Verify Microsoft Visual C++ Redistributable Package is installed
3. Check Event Viewer for error logs

## Frequently Asked Questions (FAQ)

### Q1: Language change is not reflected
**A:** Please completely exit the app and restart. The settings file will be loaded.

### Q2: I don't know how to configure the firewall
**A:** In Windows Defender Firewall, add SRT Probe.exe to the allowed list.

**Steps:**
1. Open Windows Security
2. Select "Firewall & network protection"
3. Click "Allow an app through firewall"
4. Find "SRT Probe" and check both Private and Public

### Q3: RTT is always displayed as 0ms
**A:** Data may not be transmitted yet. Verify you are connected in Sender mode.

### Q4: Presets are not saved
**A:** Verify you have write permission to the settings file folder. It is usually `C:\Users\[username]\.srt-probe\`.

### Q5: Cannot connect (stays Disconnected)
**A:** Please check the following:
- Is the other side started first? (For Listener mode)
- Are the IP address and port number correct?
- Is the port open in the firewall?
- Is the network connected?

## Other Issues

If the above does not resolve your issue, please report the problem at [GitHub Issues](https://github.com/VideoSupporter/srt-probe-dev/issues).

