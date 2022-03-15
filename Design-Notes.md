# Design Notes

A collection of notes on application design and implementation.

----
Table of Contents
- [`Understanding Web Applications`](#1)
- [`Requesting Changed Data`](#2)
- [`Dirty Pipe Vulnerability`](#3)
- [`Unsorted`](#4)


----
<a name="1"></a>
#### Understanding Web Applications

__

A web application is essentially this:
    - Put data into the system
    - Process data along the way, possibly making changes to other data
    - Store that data
    - Access and use that data
    - Present that data
    - Handle errors that may occur at every step of the way above

So one of the most important tasks in building web applications is the
design of data structures suitable for the application.

It could be structured or semi-structured or unstructured. The processes
associated with each type is slightly different. (Not so sure about
this)


**The Right Building Blocks**

The Scratch programming language by MIT is a huge success and part of
the reason is that it provides the right building blocks for kids.

I have seen really fantastic games being built using Scratch and they
probably cannot be built if the building blocks are not in place.


**Why am I always starting from scratch?**

When I build, I get the feeling that I'm always starting from scratch.
And I don't seem to have a grasp on how to solve this problem. I've
tried creating snippets, creating templates, creating wholesale programs

Cos I'm not using building blocks. Cos I'm not building building blocks.
Cos I'm not learning from the masters.


**The Right Way To Build Systems (perhaps)**

1. Build the system.
2. Extract out building blocks.
3. Build another similar system.
4. Go back to step 2 and repeat.

Building blocks in systems are analogous to maths concepts. Math
concepts, once internalized can be used in various situations.

For example, an intuitive understanding of the concept of fraction is
the notion of something that is not whole, not full. Hence, given the
following:

    600 x ___ = 2000

Understanding the notion of fraction and multiplication tells us that
the answer is somewhere between three (3) and four (4).

Similarly, creating building blocks, polishing them and allows us to
grasp and solve system design problems.

FIXME: What do the masters say on this topic?
..

----
<a name="2"></a>
#### Requesting Changed Data

__

A request for data typically returns the `current` data e.g. getting a
list of user promotions will return the current promotions. This kind of
data is like a current `snapshot`.

However, in some cases, the snapshot data could be very large and
returning the entire dataset is inefficient. In such cases, we are only
interested in the changes to the dataset since some previous point in
time.

Changes could include inserts, updates and deletions to the previous
snapshot. The client is then responsible for applying the changes to its
local copy of the dataset to make it in sync with the data on the
server.

In some cases, especially if a long time has passed since the previous
point in time, the accumulated changes may be very large, possibly
larger than the snapshot data itself. In such cases, it may make more
sense to return the snapshot instead.

Another technique is to always return the snapshot but divide up the
snapshot into blocks of data, returning the more recent data first. Or
returning the data in the order where the most urgently needed data e.g.
for display, is returned first.
..

----
<a id="3"></a>
## Dirty Pipe Vulnerability and Gems

__

Max Kellerman found this vulnerability in the Linux Kernel and did a
[fantastic write-up](https://dirtypipe.cm4all.com/).

There are many gems (at least for me) in this write-up:

- cm2all uses a custom open source HTTP server
    - https://github.com/CM4all/beng-proxy/

- cm2all uses a custom open source in-memory database
    - https://github.com/CM4all/pond

- The notion of `zero-copy`:
    - `Via HTTP, all access logs of a month can be downloaded as a single
      .gz file. Using a trick (which involves Z_SYNC_FLUSH), we can just
      concatenate all gzipped daily log files without having to
      decompress and recompress them, which means this HTTP request
      consumes nearly no CPU. Memory bandwidth is saved by employing the
      splice() system call to feed data directly from the hard disk into
      the HTTP connection, without passing the kernel/userspace boundary
      (“zero-copy”).`
    - Use [zlib](https://www.bolet.org/~pornin/deflate-flush-fr.html)
      with the `Z_SYNC_FLUSH` flag
    - This SO [article](https://stackoverflow.com/questions/8005114)
      mentions that you can just `cat` multiple gzip files into one big
      file without decompressing.

- The differences and similarities of .gz and ZIP files:
    - `Windows users can’t handle .gz files, but everybody can extract
      ZIP files. A ZIP file is just a container for .gz files, so we
      could use the same method to generate ZIP files on-the-fly; all we
      needed to do was send a ZIP header first, then concatenate all .gz
      file contents as usual, followed by the central directory (another
      kind of header).`

- The notion of a CRC32 trailing block

- The clever use of `splice()` with pipes for performance

- The [Web Application Socket](https://github.com/CM4all/libwas/)
  protocol
    - The documentation is [here](https://libwas.readthedocs.io/en/latest/)
    - Very nice write-up

- Discussion on [Hacker News](https://news.ycombinator.com/item?id=30586740)

- The [`libcommon`](https://github.com/CM4all/libcommon) C++ libraries:
    - The notion and workflow is more valuable than the actual content

- The notion of [`git submodules`](https://git-scm.com/book/en/v2/Git-Tools-Submodules)
..


----
<a id="999"></a>
## Unsorted

__

- SAS session runtime configuration

    - SAS session runtime configuration is divided into `options` and `procs`. Options are like runtime options, while `procs` are procedures. This combination makes it easy to setup default options and also load standard libraries but at the cost of some complexity.
    - The configuration of a SAS session runtime can be modified at
      various places.
        - In sasv9.cfg files
        - In sasv9_usermods.cfg files
        - At the AppServer level or
        - At the Workspace Server level
    - On top of that, there is an autoexec-like file that can be run
        - At the AppServer level or
        - At the Workspace Server level

- This has some similarity to Ansible/Puppet/Azure DevOps
    - The notion of configuration as code
    - Also known as GitOps

- Cache SQLite tables in memory for performance
    - Only a single process has read/write access to the table
    - Each sqlite db file contains only one table
    - On update, update the table, then update the cache

- Error Handling
    - Principle #1: All system exceptions should be captured and reported
        - Create just one Exception Log File for the entire system
        - All exceptions in all services go into a the same exception log file
        - Send exceptions to sysadmin nightly
    - Principle #2: Capture enough context to replicate the problem

- Protobuf for serialization
    - Schema to enforce types and validation
        - https://codeclimate.com/blog/choose-protocol-buffers/
    - Backward compatibility
..

