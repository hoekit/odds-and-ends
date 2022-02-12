# Odds and ends
A hodge-podge of unrelated stuff:

----
- [`LibreCalc-Timesheet-Macro`](LibreCalc-Timesheet-Macro.md)
    - Using a macro to enter current date-time into a simple timesheet.

- [`Fix-Toshiba-USB-Over-Current-Status-Detected`](Fix-Toshiba-USB-Over-Current-Status-Detected.md)
    - Fixing the `USB over current status detected` error on a Toshiba TV

- [`English-Reading-Materials`](English-Reading-Materials.md)
    - Interesting online reading materials for the young (and
      young-at-heart :) )

- `Ricoh-SP229Nw`
    - Contains a hard-to-find .deb driver for the Ricoh SP220Nw printer

- [`Pieter Hintjens Books`](Pieter-Hintjens-Books)
    - Working links to Pieter Hintjens books online

- [`LINE and cvlc tips`](LINE-and-cvlc-tips.md)
    - Running LINE on Linux
    - Using cvlc for audio/video bookmarking

- [`Assembly Code`](Assembly-Code.md)
    - A collection of articles, videos and information related to coding in assembly.

- [`Dhamma`](Dhamma.md)
    - A collection of quotes, articles, videos and information related to Dhamma.

- [`Maths Concepts`](Maths-Concepts.md)
    - Explanations of maths concepts in a way that's relatively easy to understand.

- [`Wordle Program`](Wordle-Program.md)
    - A quick program to solve [Wordle](https://www.nytimes.com/games/wordle/index.html).


----
### Loose Ends

- Learn to create RSS Feeds for this
- Pieter Hintjens and Richard C. Hipp
- Improve `screeshot_book.pl`:
    - Before turning the page, check if some given region is filled with
      white pixels
    - Write a small program that, when given the pixel coordinates (x,y)
      returns 0  if all pixels in the region is white
- Profession
    - Teach
- Write up on auth vs unauth requests. user-auth vs shared-key-auth.
- Computer Sciency stuff
    - Foundations of Computer Science - C Edition by Aho & Ullman
        - http://infolab.stanford.edu/~ullman/focs.html
    - Programming Abstractions in C++ (2012)
        - https://archive.org/details/pdfy-wOLAM2q0x2jLTG2I/mode/2up
        - Downloadable PDF
        - Reader for CS106B course
    - Programming abstractions in C (1997)
        - https://archive.org/details/programmingabstr00robe/mode/2up
    - Lambda Calculus
        - David Beazley: Lambda Calculus from the Ground Up - PyCon 2019
            - https://www.youtube.com/watch?v=pkCLMl0e_0k
        - David Beazley: Lambda Calculus: PyCon 2019 Tutorial (Screencast)
            - https://www.youtube.com/watch?v=5C6sv7-eTKg
        - A Tutorial Introduction to the Lmabda Calculus - Raul Rojas
            - https://www.cs.tufts.edu/comp/105-2020f/readings/rojas.pdf
- Other Stuff
    - Feynman Lectures on Physics
        - https://www.feynmanlectures.caltech.edu/
        - https://archive.org/details/academictorrents_c5af268ec55cf2d3b439e7311ad43101ba8322eb
    - Nice Review Lecture
        - https://www.feynmanlectures.caltech.edu/TIPS_01.html

- Tools
    - cgit: A hyperfast web frontend for git repositories written in C
        - https://git.zx2c4.com/cgit/about/

- Precision Programming
    - If Toyota applied precision engineering to create a robust,
      reliable car, what is the analagous, i.e precision programmang to
      create robust, reliable programs

- COVID-19
    - SARS-CoV-2 in water and wastewater: A critical review (Feb 2021)
        - https://www.ncbi.nlm.nih.gov/pmc/articles/PMC7528884/

- Design Notes

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

