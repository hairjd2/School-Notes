# File Concept
- Contiguous logical address space
- Types:
	- Data
		- numeric
		- character
		- binary
	- Program
- Contents defined by file's creator
	- Many types 
		- Consider **text file, source file, executable file**
## File Attributes
- Name
- Identifier - unique tag (number) identifies file within file system
- Type - needed for systems that support different types
- Location - pointer to file location on device
- Size
- Protection - controls who can do reading, writing, executing
- Time, date, and user identification - data for protection, security, and usage monitoring
## File Operations
- File is an **abstract data type**
- **Create**
- **Write** - at write pointer location
- **Read** - at read pointer location
- **Reposition within file** - seek
- **Delete**
- **Truncate**
- **Open(F_i)** - search the directory structure on disk for entry F_i, and move the content of entry to memory
- **Close(F_i)** - move the content of entry F_i in memory to directory structure on disk
### Open Files
- Several pieces of data are needed to manage open files:
	- **Open-file table**: tracks open files
	- File pointer: pointer to last read/write location, per process that has the file open
	- **File-open count**: counter of number of times a file si open - to allow removal of data from open-file table when last processes closes it
	- Disk location of the file: cache of data access information
	- Access rights: per-process access mode information
## Open File Locking
- Provided by some OS and file systems
	- Similar to reader-writer locks
- Mediates access to a file
- Mandatory or advisory
	- **Mandatory**: enforced
	- **Advisory**: processes can find status of locks and decide what to do
# Access Methods
- Sequential access
	- ![[Pasted image 20221207103303.png]]
- Direct Access - file is fixed length *logical records*
	- ![[Pasted image 20221207103333.png]]
	- n = relative block number
- Relative block numbers allow OS to decide where file should be placed
## Other Access Methods
- Can be built on top of base methods
- General involve creation of an index for the file
- Keep index in memory for fast determination of location of data to be operated on (consider UPC code plus record of data about that item)
- If too large, index (in memory) of the index (on disk)
- IBM indexed sequential-access method (ISAM)
# Disk and Directory Structure
- ![[Pasted image 20221207103718.png]]
## Disk Structure
- Disk can be subdivided into **partitions**
- Disks or partitions can be **RAID** procected against failure
- Disk or partition can be used **raw** - without a file system, or **formatted** with a file system
- Partitions also known as minidisks, slices
- Entity contains file system known as a **volume**
- Each volume containing file system also tracks that file system's info in **device directory** or **volume table of contents**
- As well as **general-purpose file systems** there are many **special-purpose file systems**, frequently all within the same operating system or computer
- ![[Pasted image 20221207104306.png]]
## Types of file systems
- We mostly talk about GP fs'
## Operations Performed on Directory
- Search for a file
- Create a file
- Delete a file
- List a directory
- Rename a file
- Traverse the file system
## Directory Organization
- The directory is organized logically to obtain
	- Efficiency - locating a file quickly
	- Naming
	- Grouping - logical grouping of files by properties
### Single-Level Directory
- A single directory of all users
- Naming and grouping problem
### Two-Level Directory
- Separate directory for each user
- Path name
- Can have the same file name for different user
- Efficient searching
- No grouping capability
### Tree-Structured Directory
- ![[Pasted image 20221207105224.png]]
- Efficient searching
- Grouping Capability
- Current directory (working directory)
	- cd /spell/mail/prog
	- Type list
- **Absolute** or **relative** path name
- Creating a new file is done in current directory
### Acyclic-Graph Directories
- Have shared subdirectories and files
- ![[Pasted image 20221207105504.png]]
- Acyclic graph does not have cycles (will be on exam)
- Two different names (aliasing)
- If **dict** deletes **list** => dangling pointer
- Solutions
	- Backpointers, so we can delete all pointers Variable size records a problem
	- Backpointers using a daisy chain organization
	- Entry-hold-count solution
- New directory entry type
	- **Link** - another name (pointer) to an existing file
	- **Resolve the link** - follow pointer to locate the file
### General Graph Directory
- ![[Pasted image 20221207105802.png]]
- Can have cycles
- How do we guarantee no cycles?
	- Allow only links to file not subdirectories
	- **Garbage collection**
	- Every time a new link is added use a cycle detected algorithm to determine it is OK
# File-System Mounting
- A FS must be **mounted** before it can be accessed
- A unmounted fs is mounted at a **mount point**
## Mount Point
- ![[Pasted image 20221207110109.png]]
# File Sharing
- Sharing of files on multi-user systems is desirable
- Sharing may be done through a **protection** scheme
- On distributed systems, files may be shared across a network
- Network File System (NFS) is a common distributed file-sharing method
- If multi-user system
	- **User IDs** identify users, allowing permissions and protections to be per-user
	- **Group IDs** allow users to be in groups, permitting group access rights
	- Owner of a file / directory
	- Group of a file / directory
## Failure Modes
- All file systems have failure modes
- **Stateless** protocols such as NFS v3 include all info in each request, allowing easy recovery but less security
## Consistency Semantics
- Specify how multiple users are to access a shared file simultaneously
	- Andrew File System (AFS) implemented complex remote file sharing semantics
# Protection
- FIle ower/creator should be able to control
	- What can be done
	- By whom
- Types of access
	- **Read**
	- **Write**
	- **Execute**
	- **Append**
	- **Delete**
	- **List**
## Access Lists and Groups
- Mode of access: read, write, and execute
- Three classes of users on Unix/Linux
- Ask manager to create a group (unique name), say G, and add some users to the group
- For a particular file (say game) or subdirectory, define an appropriate access