
![logo](logo_elisa_small.png)

# ELISA Tool Investigation & Code Improvement Working Group

## Date: 23-10-10

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
* Sudip (CodeThink)
* Qasim (Seimens)

### Attended in the past

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

* 14-15 Nov 2023 [Aerospace TechWeek](https://www.aerospacetechweek.com/americas/) in Atlanta, US
* 13-15 Nov 2024 [Linux Plumbers Conference](https://lpc.events/) in Richmond, US
* 27 Feb 2024 [AvioSE'24](https://aviose*workshop.github.io/) in Linz, Austria

## Discussion Topics

* Logistics
  * Current meeting times work for Sudip and Qasim
* Prioritizing Discussion Topics
  * Non-negotiable: Revising/broadening the Working Group mission statement
  * Other Topics
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
    * Tool Qualification
      * What are the similarities/differences of Tool Qualification across industries?
      * How we do approach qualification of OSS tools?
    * clang compatibility
      * Can we use clang in Yocto as an alternative to GCC
    * Rust?
      * No particular interesting, maybe future topic?

* Sudip's time is limited but he willing to help
  * Setting up tools
  * Assisting with Debian
  * Assisting with Yocto
* Brendan Higgins maintains the kunit and is very welcome to patches
  * Unclear if other maintainers are open to adding
* Sudip can help with the integration static analysis into the CI
* Current demo is for the automotive WG
  * Running QEMU tests
  * OpenQA server for testing
  * Generated SDPX documentation as part CI
* Sudip: Rust is currently entirely dependent on a particular compiler version
* Sudip sends out kernel testing run reports for every stable
  * Only failures go to Linux
* Sudip willing to setup a CI to build a Yocto image using clang which builds and loads on qemu
* Existing Static Analysis:
  * https://elisa-builder-00.iol.unh.edu:8001/
  * https://elisa-builder-00.iol.unh.edu/syzkaller/
  * https://elisa-builder-00.iol.unh.edu/syzkaller-next/
* Qasim is interested in submitting patches to Linux based on the static analysis

## Round Table

## Action Items

## Closing
