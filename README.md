# Analysis-of-the-Disk-Structure-using-Sleuth-Kit
## AIM:
To analyze the disk structure of a given disk image using Sleuth Kit tools in Kali Linux.

## REQUIREMENTS
- **Operating System**: Windows 10/11 or Kali Linux
- **Tools**:  
  - [The Sleuth Kit for Windows](https://sleuthkit.org/)  
  - Optional GUI: [Autopsy Forensic Browser](https://www.autopsy.com/)
- **Test Data**: Disk image file (`disk.dd`, `disk.img`, `.E01`)

## ARCHITECTURE DIAGRAM
```mermaid
flowchart TD
    A[Disk Image / Physical Disk] --> B[mmls - Partition Analysis]
    B --> C[fsstat - File System Metadata]
    C --> D[fls - File Listing]
    D --> E[icat - File Recovery]
    E --> F[Recovered Data / Metadata Report]
```
## DESIGN STEPS:
### Step 1:
- Obtain or create a disk image file (e.g., disk.dd) to analyze.
- Open the terminal in Kali Linux.

### Step 2:
Use Sleuth Kit tools like:
 - mmls → Examine the partition layout.
 - fsstat → View file system details.
 - fls → Get file listing.
 - icat → Recover files using inode numbers.
### Step 3:
Interpret the output to understand:
 - Partition table layout
 - File system metadata (block size, creation time, etc.)
 - Deleted and allocated files
 - Inode-based file recovery

## PROGRAM:
Sleuth Kit Disk Analysis Commands
### Partition Analysis
```bash
mmls disk.dd
```
### File System Metadata
```bash
fsstat -f fat disk.dd
```
### File Listing
```bash
fls -f fat -o 0 disk.dd
```
### File Recovery
```bash
icat -f fat -o 0 disk.dd 4 > recovered_evidence.txt
```
- Recovers the file associated with inode 4.

## OUTPUT:

1.Disk Image creation:
<img width="683" height="542" alt="Screenshot 2026-08-19 154958" src="https://github.com/user-attachments/assets/7fe2b8d9-c81f-4ae2-986e-fa470afbbd48" />

2.File Sytem Creation:
<img width="699" height="565" alt="Screenshot 2026-08-19 155116" src="https://github.com/user-attachments/assets/5793fe9b-ffb2-45a3-9412-9611e4976bdb" />

3.Partion/Disk structure Analysis:
<img width="687" height="628" alt="Screenshot 2026-08-19 155313" src="https://github.com/user-attachments/assets/b91bb104-09c0-4b60-93c5-6e4c0c3d640b" />

4.File System Analysis:
<img width="683" height="567" alt="image" src="https://github.com/user-attachments/assets/9b7a1b68-899e-4ff8-b754-56eddae4737b" />

5.File Listing:
<img width="678" height="539" alt="image" src="https://github.com/user-attachments/assets/38f76257-b938-4c7b-88b1-1bf03278d657" />

6.File Recovery:
<img width="666" height="530" alt="image" src="https://github.com/user-attachments/assets/a76181e3-92b4-442b-828a-9fd724775187" />


## RESULT:
The analysis was performed successfully using Sleuth Kit, and the disk structure was understood in detail.
