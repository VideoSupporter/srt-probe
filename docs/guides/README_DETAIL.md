# SRT Probe - Detailed Guide

> 🌐 **Languages**: [English](README_DETAIL.md) | [日本語](README_DETAIL.ja.md) | [中文](README_DETAIL.zh.md) | [한국어](README_DETAIL.ko.md) | [Español](README_DETAIL.es.md)

This document provides detailed feature descriptions and usage instructions for SRT Probe.

## 📖 What is the SRT Protocol?

SRT (Secure Reliable Transport) is an open-source protocol developed for real-time delivery of high-quality video and audio over the Internet.

### Key Features of SRT
- **Low Latency**: Lower latency compared to traditional delivery protocols
- **Packet Loss Recovery**: Accurate data delivery even when the network is unstable
- **Encryption Support**: Secure communication with AES encryption
- **Firewall Traversal**: Works in NAT and firewall environments

### Use Cases
- SRT tool connection testing
- Live streaming (sports broadcasts, event streaming, etc.)
- Video transmission between broadcasting stations
- Remote production (REMI: Remote Integration Model)
- Cloud-based video production

## ✨ Complete Feature List

### 🌍 5 Language Support
- Supports English, 日本語, 中文, 한국어, Español

### 📊 Real-time Statistics

SRT Probe displays the following network quality metrics in real-time during connection:

#### RTT (Round Trip Time)
Round trip time. The time it takes for data to reach the destination and return.

#### Throughput
Data transfer rate displayed in Mbps (megabits per second).

#### Packet Loss
The percentage (%) of packets lost out of all transmitted packets.

### 📈 Performance Charts

Dynamic graphs using Chart.js display the following information over time:

- **RTT Chart**: Visualizes delay transitions
- **Throughput Chart**: Displays transfer speed variations
- **Packet Loss Chart**: Monitors network quality changes

### 🔄 3 Connection Modes

SRT Probe supports three SRT protocol connection modes:

#### 1. CALLER (Client) Mode
- **Role**: The side that initiates the connection (client)
- **Usage**: When connecting from source to destination
- **Settings**: Specify destination IP address and port number

**Example:**
```
Sender (caller) → Receiver (listener)
Source connects to server and sends data
```

#### 2. LISTENER (Server) Mode
- **Role**: The side that waits for connection (server)
- **Usage**: When waiting as a destination
- **Settings**: Specify listening port number (IP is usually 0.0.0.0)

**Example:**
```
Sender (listener) ← Receiver (caller)
Source waits as server and receives connection from receiver
```

#### 3. RENDEZVOUS Mode
- **Role**: Both sides attempt to connect simultaneously (P2P)
- **Usage**: When firewall or NAT traversal is needed
- **Settings**: Use the same port number on both sides

**Example:**
```
Sender (rendezvous) ⇄ Receiver (rendezvous)
Both sides initiate connection simultaneously (peer relationship)
```

### 💾 Preset Feature

Save frequently used settings and easily recall them next time.

#### Saving Presets
1. Enter connection settings (IP, port, mode, etc.)
2. Click the **Save** button
3. Enter preset name (e.g., "Head Office Server", "Tokyo Site")
4. Click Save

#### Loading Presets
1. Select a saved preset from the dropdown
2. Click the **Load** button
3. Settings are automatically filled in

#### Deleting Presets
1. Select the preset to delete from the dropdown
2. Click the **Delete** button

### 🎨 3-Panel UI Layout

The SRT Probe UI consists of three panels:

#### Left Panel: Settings Input
- **Test Mode**: Select sending/receiving mode
- **Connection Settings**: Configure IP and port number
- **Advanced Settings**: Detailed settings (described below)
- **Preset Management**: Save and load presets

#### Right Top Panel: Real-time Statistics
- **Connection Status**: Connected / Disconnected
- **RTT**: Real-time delay display
- **Throughput**: Throughput display
- **Packet Loss**: Packet loss rate display
- **Performance Chart**: Time-series graph

#### Right Bottom Panel: Log Output
- **Real-time Logs**: Connection status and error messages
- **Log Filters**: Filter by Debug / Info / Warn / Error
- **Clear Logs**: Clear log display

## ⚙️ Advanced Settings

When you expand **Advanced Settings**, you can adjust the following settings:

### Interval (Data Transmission Interval)
- **Description**: Interval for sending data packets (milliseconds)
- **Default**: 100ms
- **Recommended Values**:
  - High frequency test: 50-100ms
  - Normal test: 100-500ms
  - Low frequency test: 500-1000ms

### Data Size (Transmission Data Size)
- **Description**: Data size per transmission (bytes)
- **Default**: 1316 bytes (SRT recommended value)
- **Recommended Values**:
  - Standard: 1316 bytes (optimized for MTU 1500)
  - Small size: 512-1024 bytes
  - Large size: 2048-4096 bytes

### Log Level
- **Description**: Level of detail for displayed logs
- **Levels**:
  - **Debug**: Display all logs (for development/debugging)
  - **Info**: Display normal operation logs (recommended)
  - **Warn**: Display warnings and errors only
  - **Error**: Display errors only (minimum)

### Verbose Output
- **Description**: Output more detailed log information
- **Usage**: Enable during troubleshooting
- **Note**: Increases log volume, so usually disabled is OK

### Duration (Test Duration)
- **Description**: Automatic stop time for test (seconds)
- **Default**: 0 (unlimited)
- **Recommended Values**:
  - Short-term test: 10-60 seconds
  - Long-term test: 300-3600 seconds (5 minutes to 1 hour)

## 🎯 Usage Scenario Guide

### Scenario 1: LAN Network Testing

**Purpose**: Verify SRT connection on internal LAN

**Settings:**
1. **Receiver side**:
   - Mode: Receiver (listener)
   - IP: 0.0.0.0
   - Port: 9000

2. **Sender side**:
   - Mode: Sender (caller)
   - IP: 192.168.1.100 (Receiver IP address)
   - Port: 9000

**Expected Results:**
- RTT: 1-10ms
- Packet Loss: 0-0.1%
- Throughput: Depends on network speed (typically 100Mbps to 1Gbps)

### Scenario 2: Internet Distribution Test (Reverse Connection Pattern)

**Purpose**: Verify SRT distribution quality between locations (using source as server)

**Settings:**
1. **Source (Sender)**:
   - Mode: Sender (listener)
   - IP: 0.0.0.0
   - Port: 9000
   - Open port 9000 in firewall

2. **Destination (Receiver)**:
   - Mode: Receiver (caller)
   - IP: [Source global IP]
   - Port: 9000

**Use Case:**
Effective when the source side has firewall configuration authority or when operating the source as a fixed server.

**Expected Results:**
- RTT: 20-150ms (depends on distance)
- Packet Loss: 0.1-1%
- Throughput: Depends on line speed

### Scenario 3: P2P Test Through Firewall

**Purpose**: Testing when both sides are inside firewalls

**Settings:**
1. **Same settings on both sides**:
   - Mode: Rendezvous
   - IP: Other side's global IP
   - Port: 9000
   - Click "Start Test" simultaneously on both sides

**Notes:**
- Recommended in environments with UPnP enabled
- Or manual port forwarding configuration is required

## 🔍 Reading Statistics and Troubleshooting

### Example of Normal Connection

```
Status: Connected
RTT: 25ms
Throughput: 8.5 Mbps
Packet Loss: 0.05%
```
→ No problem. High-quality connection.

### Example of High Latency

```
Status: Connected
RTT: 450ms
Throughput: 2.1 Mbps
Packet Loss: 0.2%
```
→ High RTT. Possible long-distance connection or routing issues.

**Solutions:**
- Check network route
- Investigate relay routers with traceroute
- Contact ISP

### Example of High Packet Loss

```
Status: Connected
RTT: 35ms
Throughput: 4.2 Mbps
Packet Loss: 8.5%
```
→ High packet loss. Network is unstable.

**Solutions:**
- Switch to wired LAN if using Wi-Fi
- Possible bandwidth shortage (stop other communications)
- Restart network equipment (router, switch)

### Example of Low Throughput

```
Status: Connected
RTT: 18ms
Throughput: 0.3 Mbps
Packet Loss: 0.1%
```
→ Low throughput. Possible bandwidth limitation.

**Solutions:**
- Reduce Interval (send data more frequently)
- Increase Data Size
- Check network bandwidth

## 📞 Support and Feedback

### Support Channels

If you have questions or issues with SRT Probe, please contact us through the following methods:

#### GitHub Issues
For technical issues and bug reports, please report at [GitHub Issues](https://github.com/videosupporter/srt-probe/issues).

Including the following information enables faster response:
- Windows version
- SRT Probe version
- Error messages (if any)
- Reproduction steps
- Log files

#### Email Support
General inquiries: videosp.info@gmail.com

### Frequently Asked Questions (FAQ)

For frequently asked questions, please refer to the FAQ section in the [Troubleshooting Guide](TROUBLESHOOTING.md).

