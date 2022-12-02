- I/O takes a significant amount of OS' code
- I/O devices: keyboard, display, disk, clock
- I/O devices can be divided into block devices (that store data in fixed-size blocks, each one with its one address) and character devices (delivers or accepts a stream of bytes, the device is not addressable and does not have seek function). Block devices: USB, HDD, SDD, character devices: mouse, printer, network interface
- this scheme is incomplete. clocks are nor block devices, neither character devices (they just cause interrupts at defined intervals)
- 3 ways to implement IO: programmed, interrupt-driven, using DMA:
1. Programmed: let CPU handle all work. Polling/busy waiting - CPU repeatedly asks IO device for output. Programmed IO is easy to implement but it takes CPU for whole time IO needs it.

### I/O software layers
User-level IO software  
Device-independent OS software  
Device drivers  
Interrupt handlers  
Hardware

### Buffering
1. No buffering at all: a process reading from network card, it performs **read** system call, blocks waiting for one character, each arriving character causes an ISP (it hands the character to the process and unblocks it). After putting the character somewhere, the process reads another character blocks again.
2. 