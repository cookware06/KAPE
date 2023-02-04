# KAPE

Kroll Artifact Parser and Extractor (KAPE) is primarily a triage program that will target a device or storage location, find the most forensically relevant artifacts (based on your needs), and parse them within a few minutes. Because of its speed, KAPE allows investigators to find and prioritize the more critical systems to their case.

Purpose for keeping file as multiple time cames across issues in downloading file from the kape official website (https://www.kroll.com/en). This package doesn't contain any modules. Just kape.exe utility and powershell script to download the modules and updates.

KAPE serves two primary functions: 

1. Collect Files
2. Process collected files with one or more programs.

KAPE can be used on a live system or against a dead box system in the form of a write-blocked hard drive or a mounted E01. In every case, usage is the same. KAPE handles in-use files and volume shadow copies as well, making it very thorough in its approach to finding and collecting data.

KAPE wants a drive letter, directory, or UNC path as its source of data. If you can point KAPE at a path, it will do its thing.

# Targets

Targets are responsible for defining the files and directories for KAPE to copy. The full specification for a target and its properties is in the manual, but it is pretty straightforward.


# Modules

Put simply, modules run programs. More specifically, they run a SINGLE program. This is important to understand as modules are written for a single purpose.

E.g PECmd

# Variable names

The values surrounded by % are variables that KAPE will replace at runtime. All the available variables are specified in the manual as well as in all the included modules for reference and examples, but it is pretty straightforward. 

1. %sourceDirectory% will be replaced with the value of --msource.
2. %destinationDirectory% will be replaced with --mdest plus the category from the module (ProgramExecution in the case of PECmd)

This allows KAPE to work regardless of source or destination directories, drive letters, UNC paths, etc.

# Running KAPE

KAPE requires administrator rights, so the first thing to do is open up an administrative level command prompt or PowerShell window.

Sample examples:

1. kape.exe --tsource c --tdest c:\temp\tout --target evidenceofexecution --vhdx MyBaseNameExample
2. kape.exe --tsource c --tdest c:\temp\tout --target evidenceofexecution --vhdx MyBaseNameExample --vss
3. kape.exe --tsource c --tdest c:\temp\tout --target evidenceofexecution --tflush --mdest C:\Temp\mout --module PECmd --mflush
4. kape.exe --tsource c: --tdest L:\collect --target QuickTimeline --mdest L:\output --module QuickTimelinekape.exe --tsource c: --tdest L:\collect%d --target EvidenceOfExecution--mdest L:\output%d --module PECmd

Once you're familiar with the tool, try performing the below task from INE-Public Lab

https://raw.githubusercontent.com/ine-content/INE-Public/main/Labs/Evidence%20Acquisition%20Using%20KAPE

# Documentation Credits: 
https://binaryforay.blogspot.com/2019/02/introducing-kape.html 

# Big Thanks for Eric Zimmerman for this wonderful tool.
All Credits goes to : https://github.com/EricZimmerman/KapeFiles
