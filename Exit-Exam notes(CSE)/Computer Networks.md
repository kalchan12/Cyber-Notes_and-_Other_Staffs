
# Computer Networking Fundamentals

                                 Compiled by psycho

## 1. Data vs Information

### Data

- Raw, unprocessed facts.
    
- Has no meaning on its own.
    

**Example:**

```
85, 90, 78
```

### Information

- Processed data that has meaning and can support decision-making.
    

**Example:**

```
Average score = 84.3 → Student passed
```

**Insight:**  
Data is useless until it becomes information. Think of data as ingredients and information as a cooked meal.

---

## 2. Data Communication

### Definition

The process of exchanging data or information between devices.

**Real-world examples:**

- Sending a message on WhatsApp
    
- Loading a webpage
    
- Streaming a video
    

---

### Characteristics of Effective Data Communication

1. **Delivery**
    
    - Data must reach the correct destination and intended user.
        
2. **Accuracy**
    
    - Data must be delivered without errors.
        
    - Corrupted data = useless data.
        
3. **Timeliness**
    
    - Data must arrive when needed.
        
    - Critical for real-time applications like video calls.
        
4. **Jitter**
    
    - Variation in packet arrival time.
        
    - High jitter leads to lag and unstable communication.
        

**Scenario:**  
You are on a video call:

- Delay = annoying
    
- Jitter = chaotic
    
- Packet loss = you start saying “hello? hello??”
    

---

## 3. Components of Data Communication

A complete communication system includes:

1. **Message**
    
    - The data to be transmitted (text, video, audio, etc.)
        
2. **Sender**
    
    - Device that sends the message.
        
3. **Receiver**
    
    - Device that receives the message.
        
4. **Transmission Medium**
    
    - Path through which data travels (Wi-Fi, fiber optic, cable).
        
5. **Protocol**
    
    - Set of rules governing communication.
        

**Scenario:**  
Sending an email:

- Message → Email content
    
- Sender → Your laptop
    
- Receiver → Recipient’s device
    
- Medium → Internet
    
- Protocol → SMTP, TCP/IP
    

---

## 4. Data Representation

Data can exist in different forms:

- Text
    
- Numbers
    
- Images
    
- Audio
    
- Video
    

Each type requires different encoding and handling methods.

---

## 5. Data Flow Modes

### 1. Simplex (Unidirectional)

- Data flows in one direction only.
    

**Examples:**

- Keyboard → Computer
    
- Television broadcast
    

---

### 2. Half Duplex

- Data flows in both directions, but not at the same time.
    

**Example:**

- Walkie-talkie communication
    

**Scenario:**  
One person speaks while the other waits. Interruptions cause chaos.

---

### 3. Full Duplex

- Data flows in both directions simultaneously.
    

**Example:**

- Phone calls
    

**Scenario:**  
Both parties talk at the same time (whether they should is a different story).

---

## 6. Computer Network

### Definition

A collection of autonomous computing devices connected together to share resources and communicate.

---

## 7. Network Categories

### Based on Size

- **LAN (Local Area Network)**  
    Small area (home, office, campus)
    
- **MAN (Metropolitan Area Network)**  
    Covers a city
    
- **WAN (Wide Area Network)**  
    Large scale (Internet)
    

---

### Based on Architecture

#### Client-Server

- Central server provides services.
    
- Clients request resources.
    

**Example:**  
Web applications

---

#### Peer-to-Peer

- No central authority.
    
- Devices communicate directly.
    

**Example:**  
File sharing systems

---

### Based on Transmission Technology

- Packet-switched
    
- Circuit-switched
    

---

### Based on Medium

- Wired
    
- Wireless
    

---

### Based on Administration

- Private
    
- Public
    

---

## 8. Protocol

### Definition

A set of rules that define how communication occurs.

### Protocol Defines:

- What to communicate
    
- How to communicate
    
- When to communicate
    

---

### Elements of Protocol

1. **Syntax**
    
    - Structure or format of the data.
        
2. **Semantics**
    
    - Meaning of each section of data.
        
3. **Timing**
    
    - When data should be sent and at what speed.
        

**Scenario:**  
If two devices follow different syntax rules:

- Communication fails
    
- Data becomes meaningless
    

---

## 9. Standards

### Purpose

To ensure interoperability between different devices and systems.

---

### Types of Standards

- **De facto**
    
    - Widely used but not officially approved.
        
- **De jure**
    
    - Officially recognized by regulatory bodies.
        

---

### Standard Organizations

- ISO
    
- ITU-T
    
- ANSI
    
- IEEE
    
- EIA
    

---

### Forums and Agencies

- ATM Forum
    
- MPLS Forum
    
- Frame Relay Forum
    
- FCC
    

---

## 10. Signals

During transmission, data is converted into electromagnetic signals.

---

## 11. Analog vs Digital Data

### Analog Data

- Continuous values.
    
- Infinite range.
    

**Example:**  
Human voice

---

### Digital Data

- Discrete values (0 and 1).
    

**Example:**  
Computer data

---

## 12. Analog Signals

### Characteristics of a Simple Analog Signal (Sine Wave)

1. **Amplitude**
    
    - Strength of the signal.
        
    - Proportional to energy.
        
2. **Frequency**
    
    - Number of cycles per second (Hz).
        
3. **Period**
    
    - Time for one cycle.
        
    
    ```
    Period = 1 / Frequency
    ```
    
4. **Wavelength**
    
    - Distance traveled in one period.
        
    
    ```
    Wavelength = Propagation Speed × Period
    Wavelength = Propagation Speed / Frequency
    ```
    
5. **Phase**
    
    - Position of the wave relative to time.
        
    - Indicates shift (forward/backward).
        

---

### Composite Signal

- Combination of multiple sine waves.
    

**Insight:**  
Real-world signals are rarely simple. They are layered and complex.

---

## 13. Digital Signals

### Key Concepts

- **Bit Interval (Tb)**
    
    - Time required to transmit one bit.
        
- **Bit Rate**
    
    - Number of bits transmitted per second (bps).
        
    
    ```
    Bit Rate = 1 / Bit Interval
    ```
    
- **Baud Rate**
    
    - Number of signal changes per second.
        

**Important Note:**

- Bit rate ≠ Baud rate (in most cases)
    

---

## 14. Signal Types

### Periodic Signals

- Repeat after a fixed time interval.
    

**Example:**  
Sine wave

---

### Non-Periodic Signals

- Do not repeat.
    
- Irregular patterns.
    

**Example:**  
Human speech

---

## Final Insight

All of this can be summarized as:

- Data becomes signals
    
- Signals travel through a medium
    
- Protocols control communication
    
- Networks connect devices
    
- Standards ensure compatibility
    

---

To be continued 