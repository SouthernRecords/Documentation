# Southern Records Documentation

## Sound Designer Audio Files

### Sound Designer II (SD2) Audio Files

#### Corrupt .sd2/.sd2f files

We had a problem where digital masters stored in SD2 audio file format could
not be opened by applications that supposedly supported the format. 

- The SD2 format is [no longer supported][sd2-deprecation] by Avid/DigiDesign
  (as of version 10.3.6 of Pro Tools).
- The format is similar to AIFF, but holds extra metadata which AIFF does not
  know about.
- We were using SD2 as an alternative to DDP.

What we found out:

- Storing SD2 files on non-HFS (or other non-Apple) filesystems damages the
  [resource fork][resource-fork].
- The data offset on SD2 files is 0x0080 or 128 bytes.
    - Even tools like Soundhack will not fix the problem because it is not
      aware of the offset.
    - [Audacity][audacity] (open source) and Wave Editor can open the corrupt
      SD2 files if you tell them where to start reading the data. We have
      tested this.
- Read the file as raw audio. Settings: 16-bit signed PCM, big endian, 2
  channels, 44100 Hz sample rate, 128-byte offset

The settings above will give us a clean wave form on (most of) our CD
production masters. 

#### Sources

- [Audacity `sd2.c` file](https://code.google.com/p/audacity/source/browse/sf-cvs/trunk/lib-src/libsndfile/src/sd2.c?spec=svn1940&r=1940)
- [Crucial Systems' SD2 format docs](http://crucial-systems.com/SDII_format_specification)
- [Avid Pro Audio Community](http://duc.avid.com)
- [Roxio Toast Users having problems with SD2 exports](http://forums.support.roxio.com/topic/70991-cant-open-previous-toast-files/)



[audacity]: https://code.google.com/p/audacity/
[sd2-deprecation]: http://avid.force.com/pkb/articles/en_US/Troubleshooting/SD2-support-with-PT-10-3-6-and-higher
[resource-fork]: https://en.wikipedia.org/wiki/Resource_fork
