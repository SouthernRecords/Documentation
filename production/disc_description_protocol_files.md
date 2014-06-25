# Southern Records Documentation

## Disc Description Protocol (DDP) Archives

DDP is another proprietary standard that is widely used in music production.
Many factories that manufacture CDs can use DDP archives to import directly
into their system. The advantage for labels in using DDP is that there are no
real intermediate steps where errors can occur during the production process.

DDP files have built-in checksums (CRC32), so if the data is corrupted, the
system at the other end will tell you. The error messages are usually sensible
as well, so you can use them to troubleshoot from either end of the transfer.

### DDP Tools

Andreas Ruge has created [command-line tools][ddptools] to create DDP archives,
view their metadata, and view the metadata (text) in CD binary files.

[ddptools]: http://ddp.andreasruge.de

The source code is sadly not available since [Doug Carson and Associates (DCA)][dca], 
the company that owns the DDP standard, does not allow the specifications to be
shared.

[dca]: http://www.dcainc.com/products/ddplicense/index.html

[ddp-licence]: http://dcainc.com/support/documentation/docs/DDP-License-20111005.pdf
