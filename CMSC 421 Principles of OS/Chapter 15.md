# FS
- GP computers can have multiple storage devices
# FS mounting
![[Pasted image 20221212105344.png]]
# Partitions and Mounting
- Partition can be a volume containing a file system ("cooked") or **raw** - just a sequence of blocks with no fs
- Boot block can point to boot volume or boot loader set of blocks that contain enough code to know how to load the kernel from the fs
- **Root partition** contains the OS, other partitions can hold other OSes, other fs', or be raw
- At mount time, fs consistency checked
# File Sharing
- Allows multiple users/systems access to the same files
- Permissions, ownership, yadda yadda yadda
# Virtual FS
- **Virtual File Systems (VFS)** on Unix provide an object-oriented way of implementing file systems
- VFS allows the same system call interface (the API) to be used for different types of file systems
- The API is to the VFS interface, instead of a specific type of FS
## Implementation
- For example, Linux has four object types:
	- **inode, file, superblock, dentry**
- VFS defines set of ops on the objects that must be implemented
# Remote File Systems
- Sharing of files across a network
- First method uses programs like FTP (manual)
- Second method uses a **distributed file system (DFS)**
- Third method - WWW
## Client-Server Model
- Sharing between a server (providing access to a file system via a network protocol) and a client (using the protocol access the remote file system)
- NFS an example
# Consistency Semantics
- When a session is created you must determine the semantics of that session
# NFS
- The Sun Network File System (NFS)
- Implementation and specification of a software system for accessing remote files across LANs (or WANs)
- Can use UDP or TCP
- NFS is designed to operate in a heterogeneous environment of different machines, OSes, and network architectures
- NFS is stateless, NFS V4 is stateful, less used