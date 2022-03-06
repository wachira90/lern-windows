# diskpart

You can list the available objects and determine an object's number or drive letter by using:

`list disk` - Displays all the disks on the computer.

`list volume` - Displays all the volumes on the computer.

`list partition` - Displays the partitions on the disk that has focus on the computer.

`list vdisk` - Displays all the virtual disks on the computer.

After you run the list commands, an asterisk (*) appears next to the object with focus.



## PARAMETERS

You can run the following commands from the Diskpart command interpreter:


Command	Description

`active`	Marks the disk's partition with focus, as active.

`add`	Mirrors the simple volume with focus to the specified disk.

`assign`	Assigns a drive letter or mount point to the volume with focus.

`attach` vdisk	Attaches (sometimes called mounts or surfaces) a virtual hard disk (VHD) so that it appears on the host computer as a local hard disk drive.

`attributes`	Displays, sets, or clears the attributes of a disk or volume.

`automount`	Enables or disables the automount feature.

`break`	Breaks the mirrored volume with focus into two simple volumes.

`clean`	Removes any and all partition or volume formatting from the disk with focus.

`compact` vdisk	Reduces the physical size of a dynamically expanding virtual hard disk (VHD) file.

`convert`	Converts file allocation table (FAT) and FAT32 volumes to the NTFS file system, leaving existing files and directories intact.

`create`	Creates a partition on a disk, a volume on one or more disks, or a virtual hard disk (VHD).

`delete`	Deletes a partition or a volume.

`detach` vdisk	Stops the selected virtual hard disk (VHD) from appearing as a local hard disk drive on the host computer.

`detail`	Displays information about the selected disk, partition, volume, or virtual hard disk (VHD).

`exit`	Exits the diskpart command interpreter.

`expand` vdisk	Expands a virtual hard disk (VHD) to the size that you specify.

`extend`	Extends the volume or partition with focus, along with its file system, into free (unallocated) space on a disk.

`filesystems`	Displays information about the current file system of the volume with focus and lists the file systems that are supported for formatting the volume.

`format`	Formats a disk to accept Windows files.

`gpt`	Assigns the gpt attribute(s) to the partition with focus on basic GUID partition table (gpt) disks.

`help`	Displays a list of the available commands or detailed help information on a specified command.

`import`	Imports a foreign disk group into the disk group of the local computer.

`inactive`	Marks the system partition or boot partition with focus as inactive on basic master boot record (MBR) disks.

`list`	Displays a list of disks, of partitions in a disk, of volumes in a disk, or of virtual hard disks (VHDs).

`merge` vdisk	Merges a differencing virtual hard disk (VHD) with its corresponding parent VHD.

`offline`	Takes an online disk or volume to the offline state.

`online`	Takes an offline disk or volume to the online state.

`recover`	Refreshes the state of all disks in a disk group, attempt to recover disks in an invalid disk group, and resynchronizes mirrored volumes and RAID-5 volumes that have stale data.

`rem`	Provides a way to add comments to a script.

`remove`	Removes a drive letter or mount point from a volume.

`repair`	Repairs the RAID-5 volume with focus by replacing the failed disk region with the specified dynamic disk.

`rescan`	Locates new disks that may have been added to the computer.

`retain`	Prepares an existing dynamic simple volume to be used as a boot or system volume.

`san`	Displays or sets the storage area network (san) policy for the operating system.

`select`	Shifts the focus to a disk, partition, volume, or virtual hard disk (VHD).

`set id`	Changes the partition type field for the partition with focus.

`shrink`	Reduces the size of the selected volume by the amount you specify.

`uniqueid`	Displays or sets the GUID partition table (GPT) identifier or master boot record (MBR) signature for the disk with focus.
