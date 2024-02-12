
![logo](logo_elisa_small.png)

# ELISA Tool Investigation & Code Improvement Working Group

## Date: 23-01-25

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
* Luigi Pellecchia (Red Hat)
* Shefali Sharma
* Roberto Bagnara (Bugseng)
* Phillip Ahmann (Bosch)

### Attended in the past

* Matt Weber (Boeing)
* Thomas Mittlelstadt (Bosch)
* Gabriele Paoloni (Red Hat)
* Sudip (CodeThink)
* Qasim (Seimens)
* Lukas Bulwahn

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
* 27 Feb 2024 [AvioSE'24](https://aviose-workshop.github.io/) in Linz, Austria
* 16-18 April 2024 Open Source North America in Seattle, Washington
* June DevConf Czech Republic

## Agenda Items

* ks-nav topics
  * Comparison to CAS tool
  * funcParser features that were nice
* BASIL topics
  * Meeting w/ Xen Project, need to select their quality management for cert
  * On-going conversation w/ them, asking for some new features
  * Sharing with Xen what it can do for them
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
* ELISA CI
  * How can we contribute to / expand the ELISA CI?
* Engagement
  * How do we increase engagement with this group?
  * How do we directly tie our work to Vertical WGs?
  * How do we directly help maintainers?
  * How do we engage on peoples *actual* daily problems?

## Discussion Notes

* ks-nav topics
  * Topic: Comparison to CAS tool
    * CAS
      * Software suite for large source code maintance, offers two twos for generating metainfo
      * build-related info and source code-related
      * Dependencies
        * Python, LLVM, RapidJson
      * Takes any source tree as input
      * Two main tools
        * BAS (spying on the build)
        * FTDB (parsing the source code)
          * Extracts function data, function names
          * Puts the data into a document database
        * Compilers and build tools, source files used, makefiles use, build times statistics
        * Function and types
        * Function signatures, return types, and variables
        * Call relations
        * Preprocessor relation information
    * ks-nav is specific for the kernel
      * kern_bin_db, nav, nav-web
    * MK: Are there an features we should implement that you saw in CAS?
      * Parsing the code with LLVM might be useful for trying to resolve indirect calls
      * The way they spy the build system is interesting but not sure the use for it here
    * Is ks-nav really linux kernel specific?
      * The architecture does not prevent you from using a different binary
      * Some features (MAINTAINERS usage) are specific
      * ks-nav is not design to use with libraries
      * Most other builds would use libraries to some degree
    * Does it handle kernel modules?
      * Modules are not included in the analysis
      * This is a similar but different problem to indirect function calls
      * Modules are binaries and have no external dependencies
  * Topic: funcParser features that were nice
    * Ability to define "modules"
      * MK: I think this is covered by subsystems (though that is not as flexible but I think that's OK)
    * Sizing of functions
      * This is useful even if it is relative
      * ks-nav doesn't provide any sizing functionality
    * AC: Linux kernel source code is full of macros
      * Without preprocessing the line counts may be way off for func_parser
      * ks-nav working the result of the binary so it's accurate
    * AC: Subsystem in ks-nav are taken from maintainers files but that is not flexible
      * It does not assure that any given files belongs to a single subsystem
      * Some cases where same source file is applied to multiple subsystems
    * MK: Is there lots of files that aren't assigned to any subsystems?
      * Subsystem called "the rest" which captures all those files that aren't captured elsewhere
      * MAINTAINERS isn't really designed to defined elements but rather to define who you must include on your patch submission
      * "The rest" gets addressed to Linus himself
    * RB: There are different notions of size
      * The ideal way thing to measure would be post-preprocessed but pre-macro expansion
    * AC: You can capture that particular state but but it requires clang or other tools
    * AC: In the end, the code that is actually run is the binary
      * Also matters how the source is translated to machine code
      * Code could be safe with one compiler but not another
      * MK: To me, it depends on what you are trying to use it for
        * SWL-A considers object code, SWL-E through SWL-B only deal with source code
      * RB: Lots of aspects of the C langauge that can be implemented differently by different compilers
        * The code that is generated depends on these implementation defined details
        * If you want to track source -> object, you have to take into account implementation details
        * Compilers cannot be trusted! Functional safety methods usually qualify the compiler
        * Aerospace does not require qualification of the compiler because it looks at object code (SWL-A)
        * Same source can create many different executables (compiler with different settings for pre-defined macros)
        * For each translation unit, must track all specific compiler flags
    * AC: There is a correspondence with the source code
      * It relates bytes of code via the DWARF debug information
      * Using binutils for this currently (addr2line, etc.)
* BASIL topics
  * Meeting w/ Xen Project, need to select their quality management tool for cert
  * On-going conversation w/ them, asking for some new features
  * Sharing with Xen what it can do for them
  * Submitted talk proposal for EOSS and DevConf
  * Traceability export capability
    * SDPX?
    * Cert authority could import into another instance of BASIL

## Round Table

## Action Items

* [x] Alesssandro: Compare ks-nav to CAS tool
* [x] Matt: Compare ks-nav to func_parser
* [] Matt: Bring up engagement (present to vertical groups? blog post? presenting November summary meeting) at the TSC
* [] Matt: Model wg-tools README.md after wg-automative to educate newcomers quickly
* [] Matt: Contact Sudip/Lukas to pull together documentation on patch submission
* [] Qasim: Explore the open source static analysis tools used by kernel
* [] Qasim: Understand clang static analysis tools (clang-tidy/clang-analyzer)

## Closing
