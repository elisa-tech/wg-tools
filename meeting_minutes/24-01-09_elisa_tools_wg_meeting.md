
![logo](logo_elisa_small.png)

# ELISA Tool Investigation & Code Improvement Working Group

## Date: 23-01-09

## Agenda

* Roll Call
* Announcements
* Discussion Items
  * Logistics
  * Prioritize Discussion Topics
* Closing
  * Action Items
  * Round Table

## Roll Call

### Attended this meeting

* Matt Kelly (Boeing)
* Alessando Carminati (Red Hat)
* Phillip Ahmann (Bosch)
* Luigi  
* Matt Weber (Boeing)
* Thomas Mittlelstadt (Bosch)
* Gabriele Paoloni (Red Hat)
* Sudip (CodeThink)
* Qasim (Seimens)

### Attended in the past

* Lukas Bulwahn
* Shefali Sharma

## Announcements

### Brief Notices

* ELISA Project meetings involve participation by industry competitors, and it is the intention of the Linux Foundation to conduct all of its activities in accordance with applicable antitrust and competition laws. It is therefore extremely important that attendees adhere to meeting agendas, and be aware of, and not participate in, any activities that are prohibited under applicable US state, federal, or foreign antitrust and competition laws.
  * [Linux Foundation Antitrust Policy](http://www.linuxfoundation.org/antitrust*policy)
* Email communication will be treated as documentation and be received and made available by the Project under the [Creative Commons Attribution 4.0 International License](http://creativecommons.org/licenses/by/4.0). Please refer to the ELISA Technical Charter section 7 subsection iv. for details.
* The discussions in these meetings are exploratory. The opinions expressed by participants are not necessarily the policy of the companies.
* No recordings of working group meetings are permitted. Special provisions may be arranged for recording in advance with explicit consent of the participants.
* The kernel and LF Code of Conduct applies to all communication with this project
  * [Linux Foundation Code of Conduct](https://www.linuxfoundation.org/code*of*conduct/)
  * Linux [Contributor Covenant Code of Conduct](https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/tree/Documentation/process/code*of*conduct.rst)
  * Linux Kernel Contributor Covenant [Code of Conduct Interpretation](https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/tree/Documentation/process/code*of*conduct*interpretation.rst)

### Upcoming Conferences

* 3-4 Feb 2024 FOSSDEM (https://fosdem.org/2024/) in Brussels
* 27 Feb 2024 [AvioSE'24](https://aviose*workshop.github.io/) in Linz, Austria
* 16-18 April 2024 Open Source North America in Seattle, Washington

## Discussion Items

* ELISA CI
  * How can we contribute to / expand the ELISA CI?
* Engagement
  * How do we increase engagement with this group?
  * How do we directly tie our work to Vertical WGs?
  * How do we directly help maintainers?
  * How do we engage on peoples *actual* daily problems?
* Static Analysis in Open Source SW
  * How should we approach it?
    * Do we (and if so how?) reconcile OSS coding standards with Certification coding standards
  * How can we contribute?
    * Contribute to clang-tidy / clang-format?
* Kernel testing
  * Can we contribute to kernel testing in a systematic way?
  * Translating runtime test to kunit tests
* Tool Qualification
  * What are the similarities/differences of Tool Qualification across industries?
  * How we do approach qualification of OSS tools?
* clang compatibility
  * Can we use clang in Yocto as an alternative to GCC

## Discussion Notes

* Overview of BASIL and discussion
  * How can the WG help with BASIL? Design Discussion? Contribution? Other?
  * Previously discussed in the Automotive Working Group
  * Focused at Software Quality / Traceability
  * Web Application (written in React / butterfly?)
  * Links together Software Requirements, Test Specification, Test Cases
  * Based  on requirements in the man pages
  * Calculates coverage as a percentage of the feature
  * Tool also comes with SDPX support
    * Can export all the relations and data
  * Tool provides a REST API
  * Draft documentation
  * Issues tracking improvements here
  * Next Step: Live version of the tool for ELISA to use
  * Gab: Are we looking for additional owners for issues
    * No other contributors at this time, would be good to increase engagement
  * Applied to present at Open Source North America
  * Currently no authentication mechanism
  * Sudip: All of our resources are open to the internet, no ELISA only access
  * Luigi: We can look at implementing auth or creating a read only
* Overview of ks-nav and discussion
  * Diagram producing tool
  * Written in Go
  * Split into two parts
    * Scan and interpret the binary
    * User interface
  * Takes the kernel as an argument
  * Safety Analysis argument requires a detailed understanding of the kernel
    * Including dependencies between functions
  * Starts from binary rather than source code
    * This was a design choice
    * We get a post configuration output
  * Improvements
    * Documented here: https://github.com/elisa-tech/ks-nav/issues
    * Browse the source code based on the diagrams
    * Via a web interface
    * Have a prototype of this web interface
    * Looking for feedback on this interface
    * Component used for diagramming may not be the best choice
    * Need to add additional backend APIs to provide the data to the web interface
    * Can't track indirect calls perfectly
      * Can't solve this problem completely
      * All the candidates can be indentified because of the contained nature of the source
    * Back-end engine that is used to analyze the binary
      * redare2
      * Has a single maintainer
      * Typically has regressions
      * May want to look at other others
      * Want to abstract the current implementation so that you could pick the backend
      * Candidates
        * rizin - Fork of redare (binary replacement)
        * gidra - RE tool maybe by NSA
        * binutils (objdump, objcopy, etc.)
    * Gathering of static and global data
    * Support / export of list data into a graph DB
  * A similar tool from Samsung: https://github.com/Samsung/CAS?tab=readme-ov-file
    * Has a front-end that projects have been adopted by other projects
    * Have some data models that we may be able to learn from them
  * Gab: Let's look at other tools (func_parser, CAS tool)
    * Have those tools already addressed some of the issues? Can we leverage them to help us?
* System Working Group CI
  * Thomas setup a sample system (Xen, Linux, Zephyr) on ZCU102
  * It's already building artifacts
  * How can we bring QEMU into the CI
  * Xilinx has patched QEMU so using that with the artifacts from the System CI
  * Creating a skeleton with Xen, dom0
  * Need some  (applications) on top of the partitions
  * Constructions script to stitch things together
  * For the target this is a usb stick/sd card
  * With this set, can start QEMU
  * Can connect to QEMU console
  * Dependent on some special network configuration
  * Functionally equivalent but 4-5x slower
  * Sudip: May not be possible to get into OpenQA
    * Due to licensing rules
  * Don't need OpenQA since there is no graphical component

## Round Table

## Action Items

* [] Alesssandro: Compare ks-nav to CAS tool
* [] Matt: Compare ks-nav to func_parser
* [] Matt: Bring up engagement (present to vertical groups? blog post? presenting November summary meeting) at the TSC
* [] Matt: Model wg-tools README.md after wg-automative to educate newcomers quickly
* [] Matt: Contact Sudip/Lukas to pull together documentation on patch submission
* [] Qasim: Explore the open source static analysis tools used by kernel
* [] Qasim: Understand clang static analysis tools (clang-tidy/clang-analyzer)
* [x] Sudip: Setting up repo for medical devices CI

## Closing
