# File-System Structure
- File structure
	- Logical storage unit
	- Collection of related info
- **File system** resides on secondary storage (disks)
	- Provided user interface to storage, mapping logical to physical
	- Provides efficient and convenient access to disk by allowing data to be stored, located retreived easily
- **File control block** (FCB) - storage structure consisting information about a file
- **Device driver** controls the physical device
## File System Layers
- **Device drivers** manage I/O devices at the I/O control layer
	- Given commands like "read drive1, cylinder 72, track 2, sector 10, into memory location 1060" outputs low-level hardware specific commands to hardware controller
- **Basic file system** given commnd like "retreive block 123" translates to device driver
- **File organization module** understands files, logical address, and physical blocks
- **Logical file system** manages metadata information
	- Translates file name into file number, file handle, location by maintaining file control blocks (**inodes** in UNIX)
	- Directory management
	- Protection
- Layering useful for reducing complexity and redundancy, but adds overhead and can decrease
- Many fs', sometimes many within an OS
	- Each with its own format (CD-ROM is ISO 9660; UNIX has UFS, FFS; Windows FAT, FAT32, NFS, as well as floppy)
	- New ones still arriving - ZFS, GoogleFS, Oracle ASM, FUSE
# File-System Operations