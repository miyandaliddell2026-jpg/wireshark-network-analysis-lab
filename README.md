## Exercise A — DNS Capture

### Step 1 — Launch Wireshark and Select the Wi-Fi Interface

Wireshark was launched and the Wi-Fi interface was selected to capture live network traffic.

![Step 1](screenshots/step1.png)

---

### Step 2 — Live Packet Capture Begins

Wireshark began capturing packets in real time on the Wi-Fi interface, showing live TCP, UDP, and ARP traffic.

![Step 2](screenshots/step2.png)

---

### Step 3 — Open Administrator Command Prompt

Command Prompt was opened with Administrator privileges to run nslookup and generate DNS traffic for Wireshark to capture.

![Step 3](screenshots/step3.png)

---

### Step 4 — Run nslookup to Generate DNS Traffic

The command `nslookup google.com` was run in Command Prompt, triggering a DNS query that Wireshark captured over the Wi-Fi interface.

![Step 4](screenshots/step5.png)

---

### Step 5 — Apply DNS Display Filter

The display filter `dns` was applied in Wireshark to isolate DNS traffic. Packet 1221 shows the Standard DNS query for google.com.

![Step 5](screenshots/step6.png)

---

### Step 6 — Identify the DNS Response Packet

Packet 1222 shows the DNS response from the server containing the resolved IP addresses for google.com, matching Transaction ID `0x0004`.

![Step 6](screenshots/step7.png)

---

### Step 7 — Expand the DNS Response Packet Details

The DNS response packet was expanded in the details pane to reveal the Transaction ID, flags, questions, and answer records.

![Step 7](screenshots/step8.png)

---

### Step 8 — Correlate DNS Answers with nslookup Output

The DNS Answers section in Wireshark was compared with the nslookup terminal output — both returned the same IP addresses for google.com, confirming the capture was successful.

![Step 8](screenshots/step9.png)

---

## Exercise B — TCP Three-Way Handshake

### Step 9 — Apply tcp.flags.syn == 1 Filter

The display filter `tcp.flags.syn == 1` was applied to isolate TCP connection initiation packets, revealing the SYN and SYN-ACK packets of the three-way handshake.

![Step 9](screenshots/step12.png)

---

## Exercise C — HTTP Credential Exposure

### Step 10 — Navigate to an Insecure HTTP Login Page

The browser was navigated to zero.webappsecurity.com — an intentionally insecure HTTP training site with no encryption.

![Step 10](screenshots/step13.png)

---

### Step 11 — View Plaintext Credentials in Packet Details

The display filter `http.request.method == POST` was applied. The captured POST packet revealed the login credentials transmitted in complete plaintext — no decryption required.

![Step 11](screenshots/step15.png)

---

## Exercise D — Follow TCP Stream

### Step 12 — Right-Click to Follow TCP Stream

The HTTP POST packet was right-clicked and Follow → TCP Stream was selected to reconstruct the full HTTP conversation.

![Step 12](screenshots/step16.png)

---

### Step 13 — TCP Stream Reconstruction Output

The Follow TCP Stream window displayed the complete HTTP exchange in ASCII format, including the login credentials and the server's 302 redirect response.

![Step 13](screenshots/step17.png)

---

## Saved Capture Files

Three capture files were saved from this lab session as portfolio evidence.

![Saved Files](screenshots/step23.png)

| File | Size | Contents |
|------|------|----------|
| `dns-capture.pcapng` | ~43 KiB | DNS lookup exercise |
| `http-post-capture.pcapng` | ~247 KiB | HTTP credential capture and TCP stream |
| `tcp-handshake.pcapng` | ~53 KiB | TCP three-way handshake |

---

## Key Takeaways

This lab demonstrated hands-on experience with:

- Capturing live network traffic using Wireshark
- Generating and identifying DNS query and response packets
- Identifying the TCP three-way handshake using display filters
- Exposing plaintext credentials transmitted over unencrypted HTTP
- Reconstructing full HTTP conversations using Follow TCP Stream
- Saving packet captures in .pcapng format as portfolio evidence

---

