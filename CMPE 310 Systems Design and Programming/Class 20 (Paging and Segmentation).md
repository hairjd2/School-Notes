# Paging and Segmentation
- ==Pay attention to slide 4==
## Virtual Memory Addressing in the 80386 and up:
- The virtual address is broken into three pieces:
	- Directory: Each page directory addresses a 4MB section of main mem.
	- Page Table: Each page table entry addresses a 4kB section of main mem.
	- Offset: Specifies the byte in the page.