# MACE Timestamps
MACE timestamps refer to the four timestamps stored in the NTFS file system metadata:
1. **M**odified (M).
2. **A**ccessed (A).
3. **C**reated (C).
4. **E**ntry Modified (E).

In Windows NTFS file systems, MACE (Modified, Accessed, Created, and Entry Modified) timestamps are stored in two attributes: `$STANDARD_INFORMATION` ($SI) and `$FILE_NAME` ($FN). These attributes contain metadata about a file, including timestamps, and are essential in digital forensic analysis.

## \$STANDARD_INFORMATION (\$SI)
The `$STANDARD_INFORMATION` attribute stores four timestamps:
1. **Modified** (mtime): The last time the file's contents were modified.
2. **Accessed** (atime): The last time the file was accessed (read or executed).
3. **Created** (ctime): The file's creation time.
4. **Entry Modified** (mctime): The last time the file's metadata was modified.

These timestamps are updated by Windows Explorer, file system utilities, and other processes that interact with the file system. `$STANDARD_INFORMATION` is a critical attribute for forensic analysis, as it provides a record of the file's history.

## \$FILE_NAME (\$FN)
The `$FILE_NAME` attribute also stores four timestamps, similar to `$STANDARD_INFORMATION`:
1. **Modified** (mtime): The last time the file's name or attributes were modified.
2. **Accessed** (atime): The last time the file's name or attributes were accessed.
3. **Created** (ctime): The file's name creation time (not necessarily the same as the file's content creation time).
4. **Entry Modified** (mctime): The last time the file's name or attributes were modified.

The `$FILE_NAME` attribute is updated when the file's name, attributes, or permissions are changed. This attribute is less frequently modified than `$STANDARD_INFORMATION`, as most file system operations do not involve changing the file's name.

## Key differences
1. **Modification**: `$STANDARD_INFORMATION` is updated more frequently than `$FILE_NAME`, as it reflects changes to the file's contents, permissions, and metadata. `$FILE_NAME` is primarily updated when the file's name or attributes are modified.
2. **Creation time**: The creation times stored in `$STANDARD_INFORMATION` and `$FILE_NAME` may differ. `$STANDARD_INFORMATION` stores the creation time of the file's contents, while `$FILE_NAME` stores the creation time of the file's name.
3. **Modification detection**: Analysts can use the differences between `$STANDARD_INFORMATION` and `$FILE_NAME` timestamps to detect potential tampering or anti-forensic activities, such as timestomping.

## Tools and analysis
Several tools, including `analyzemft.py` and `MFTRipper`, can be used to extract and analyze the timestamps stored in `$STANDARD_INFORMATION` and `$FILE_NAME` attributes. Forensic analysts can use these tools to reconstruct the file's history, detect anomalies, and identify potential evidence of tampering or manipulation.

In summary, `$STANDARD_INFORMATION` and `$FILE_NAME` are two essential attributes in NTFS file systems that store MACE timestamps. Understanding their differences and how they are updated is crucial for digital forensic analysis and the detection of potential anti-forensic activities.
* Timestomp: A tool that can modify MACE timestamps, specifically the **Standard Information (SI)** timestamps.
* setMACE: A tool that allows modifying the `$FILE_NAME` timestamp values within NTFS file systems, unlike Timestomp which only modifies `$STANDARD_INFORMATION` timestamps.
* Procmon: A tool used to capture the chain of events occurring when a file's timestamps are altered using setMACE.

## Considerations
* MACE timestamps are stored in the NTFS file system metadata, specifically in the Master File Table (MFT) and the $LogFile.
* The **Entry Modified (E)** timestamp is unique to NTFS and represents the last time the file's metadata was changed.
* Some tools, such as Timestomp, can modify MACE timestamps, but only the **Standard Information (SI)** timestamps, not the **Filename (FN)** timestamps.
* The **Filename (FN)** timestamps are only modified by the kernel and cannot be altered by user-mode malware.
* The **$LogFile** contains a record of all changes made to MACE timestamps, allowing for forensic analysis and detection of tampering.

## Forensic Analysis
* When analyzing MACE timestamps, it's essential to consider the time resolution and potential anomalies.
* In cases where anomalies are detected, it may indicate tampering with timestamps using tools like Timestomp or setMACE.
* Forensic analysts should examine the $LogFile and MFT to identify changes made to MACE timestamps and determine the likelihood of tampering.

## Conclusion
MACE timestamps provide valuable information about a file's history, including creation, modification, access, and metadata changes. Understanding the nuances of MACE timestamps, including the differences between **Standard Information (SI)** and **Filename (FN)** timestamps, is crucial for effective forensic analysis and digital investigation.

## Questions
* <a href="https://superuser.com/questions/973547/how-can-i-display-all-8-ntfs-timestamps" target="_blank">How can I display all 8 NTFS timestamps?</a>