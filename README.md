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

1. **kape.exe -tsource C: --tdest D:\Task1\RegistryFiles --target RegistryHives**
2. **kape.exe -tsource C: --target !ALL --tdest D:\Tasks2 --vhdx Task2**
3. **kape.exe --tsource C: --tdest D:\Task3 --target FileSystem,EventLogs --vss --vhdx Task3**

Once you're familiar with the tool, try performing the below task from INE-Public Lab

https://raw.githubusercontent.com/ine-content/INE-Public/main/Labs/Evidence%20Acquisition%20Using%20KAPE

# Let's Practise KAPE with some tasks.,

# Task 1: Understanding KAPE Basics

You are required to understand KAPE's basics: modules, targets, etc.

Refer SANS Documentation:

Prefer Reading: 

1. https://ericzimmerman.github.io/KapeDocs/#!index.md
2. https://www.sans.org/blog/triage-collection-and-timeline-generation-with-kape/
3. https://www.giac.org/paper/gcih/34611/kape-fast-flexible-incident-response/152146

Prefer Watching:

1. https://www.youtube.com/watch?v=iYyWZSNBNcw
2. https://www.youtube.com/watch?v=L9H1uj2HSb8

# Task 2: Acquiring Evidence Using KAPE

1.  Show how to acquire all the registry files and store them in the path D:\Task1\RegistryFiles.

    **kape.exe -tsource C: --tdest D:\Task1\RegistryFiles --target RegistryHives**
 
2.  When a malware is executed, it will leave different execution evidence, use KAPE to acquire all the evidence of execution from the victim's system. Store the evidence in a VHDX file with the name Task2

    **kape.exe -tsource C: --target !ALL --tdest D:\Tasks2 --vhdx Task2 --vss**
    
    **Note**: "--tflush" can be used to delete all files in 'tdest' prior to collection.

3.  Show how to acquire the file system evidence with the event logs all in once acquisition. Then we want to store the evidence in a VHDX file with the name Task3.

    **kape.exe --tsource C: --tdest D:\Task3 --target FileSystem,EventLogs --vss --vhdx Task3**

4.  Show how to acquire all the evidence on the system and store them in a VHDX file with the name Task4.

    **kape.exe -tsource C: --target !ALL --tdest D:\Tasks2 --vhdx Task4**
    
# Task 3: KAPE GUI and Updates

You are required to acquire evidence using the KAPE GUI, then use a module(s) to process the evidence acquired. You are also required to check how to make sure KAPE is up to date.

Refer: 
1. https://assets.ine.com/cybersecurity-lab-images/1e108bbc-52ec-4b79-981a-2f6629dba35d/image29.PNG
2. https://assets.ine.com/cybersecurity-lab-images/1e108bbc-52ec-4b79-981a-2f6629dba35d/image30.PNG

# Task 4: KAPE DIY Tasks

1.  Collect all Cloud service applications from the C: drive and save the output to D:\DIY1.

2.  Collect Evidence of Execution on a system, save the output to a zip file in the path D:\DIY2, and make sure the computer name is used as the name for the zip.

3.  Collect all the Windows Browser evidence from C: and all the volume shadow copies and store them in D:\DIY3. This time store your collected evidence to a network destination.

**Note:** For this example, you will need to use UNC paths.

4.  Collect all Prefetch files from the C: drive and save the output to Z:\DIY5.

5.  Run the KAPE modules needed to process the results acquired in Task \#4.

# References: 

1. https://binaryforay.blogspot.com/2019/02/introducing-kape.html 
2. https://www.giac.org/paper/gcih/34611/kape-fast-flexible-incident-response/152146
3. https://www.kroll.com/en/insights/publications/cyber/kroll-artifact-parser-extractor-kape
4. https://thinkdfir.com/2019/02/23/kape-tricks/
5. https://ericzimmerman.github.io/KapeDocs/#!index.md

# Big Thanks for Eric Zimmerman for this wonderful tool.
