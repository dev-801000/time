

# PRACTICAL NO 1  
## AIM:- Creating a forensic image using FTK Imager  

• Creating forensic image.  
• Check integrity of data.  
• Analyse forensic image.  

### Steps:

1. Install and open FTK Imager.  
2. Go to File menu and click on Create Disk Image.  
3. In Select Source tab, select Content of the Folder, then click Next, click Yes for permission.  
4. In Select File tab, click Browse, select source file, click Finish.  
5. In Create Image tab, click Add, add Image Destination.  
6. Fill Evidence Item Information, click Next.  
7. Select Image Destination, provide filename, click Finish.  
8. Click checkboxes in Create Image tab, click Start.  
9. Image creation completed.  
10. Go to File → Add Evidence Item.  
11. Select Image File, click Next.  
12. Select the .ad1 file created earlier, click Open → Finish.  
13. Access files from Evidence Tree in left pane.  

---

# PRACTICAL NO 2  
## AIM :- Analyse the memory dump of a running computer system  

• Extract volatile data, such as open processes, network connections, and registry information.  

### Steps:

**Process Analysis:**  
1. Download and extract Sysinternals Suite.  
2. Open Procmon64 as Administrator.  
3. Analyse running processes.  

**Network Connections:**  
1. Open TcpView64 as Administrator.  
2. Analyse network connections.  

**Registry Editor:**  
1. Open Registry Editor as Administrator.  
2. Analyse permissions and configurations.  

---

# PRACTICAL NO 3  
## AIM :- Analyse the live network and capture packets using Wireshark  

• Identification of live network.  
• Capture packet.  
• Analyse captured packets.  

### Steps:

**Identification of Live Network:**  
1. Download and install Wireshark.  
2. Open Wireshark as Administrator.  
3. Analyse live network.  

**Capture Packets:**  
- Analyse colour packets (View → Colour Rules).  
- Apply filters:  
  - `ip.addr == 192.168.177.11`  
  - `ip.src == 138.199.14.92`  
  - `ip.dst == 224.0.0.251`  
  - `http`  
  - `http.request`  
  - `tcp`  
  - `http.response.code == 200`  
  - `tcp.port == 80 || udp.port == 80`  
  - `tcp contains "google"`  

**Analyse Captured Packets:**  
- Open file ‘Ask Snoopes’.  
- Filter and analyse HTTP/TCP packets.  
- Check webserver issued by `microsoft.com`.  
- Check client concerns via `frame matches "Microsoft"`.  
- Reassemble TCP streams, check HTTP responses, servers.  

---

# PRACTICAL NO 5  
## AIM :- Recovering and Inspecting deleted files  

• Check for deleted files.  
• Recover deleted files.  
• Analyse and inspect recovered files using Autopsy or command line.  

### Steps:

1. Download and install Autopsy.  
2. Open as Administrator, click New Case.  
3. Fill case information (name, base directory), click Next.  
4. Fill optional info (case number, examiner, phone, email, notes), click Finish.  
5. Add Data Source → Logical Files → Add file → Next.  
6. Configure ingest module → select all → Next.  
7. Data source added → Finish.  
8. In dashboard, select data source, go to Deleted Files tab.  
9. Generate Report → select type → Next → All Results → Finish.  
10. View results in folder.  

---

# PRACTICAL NO 6  
## AIM :- Steganography Detection  

• Detect hidden information in images using SteganPEG.  
• Extract and examine hidden content.  

### Steps:

1. Download and install SteganPEG.  
2. Open as Administrator.  
3. Embed files into JPEG → Enter password → Select image.  
4. Add text file to merge.  
5. Save stegged image → provide filename/destination.  
6. Read files from stegged image → Enter password → Select image.  
7. Select text file → Save Selected → Choose location → OK.  
8. Open downloaded file to read content.  

---

# PRACTICAL NO 7  
## AIM :- Email Forensics  

• Analyse email headers and content to trace origin.  
• Identify email forgeries or tampering.  

### Steps:

1. Open Forensic Toolkit as Administrator.  
2. Email tab → Deleted Items → view deleted emails.  
3. Launch Detached Viewer to read emails.  
4. Inbox → select email → Export File → Verify → Open exported file.  

---

# PRACTICAL NO 8  
## AIM :- Web Browser Forensics  

• Analyse browser artifacts: history, bookmarks, downloads.  
• Analyse cache and cookies to reconstruct browsing history.  
• Extract logs/timestamps, determine last internet activity.  

### Steps:

1. Download and install Forensic Toolkit.  
2. Open as Administrator → Start New Case.  
3. Fill investigator name, case number, base directory → Next.  
4. FTK Report Wizard → fill fields → Next.  
5. Case Log Options → select all → Next.  
6. Process to Perform → select all → Next.  
7. Refine Case Default → check fields → Next.  
8. Refine Index Default → check fields → Next.  
9. Add Evidence → select file → Continue → Provide evidence number → OK.  
10. Case Summary → verify → Finish.  
11. Forensic Toolkit Dashboard → Email tab → Deleted Items → check emails.  
12. View deleted emails → Inbox → Export any email → Open exported file.  

---


Course: B.Sc. IT  
Subject: Digital Forensics  
