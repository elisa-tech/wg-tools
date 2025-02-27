
![logo](logo_elisa_small.png)

# ELISA Tool Investigation & Code Improvement Working Group

## Date: 25-02-27

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
* Alessandro Carminati (Red Hat)
* Andrew Oppelt (Boeing)
* Luigi Pellecchia (Red Hat)
* Roberto Bagnara (Bugseng)

### Attended in the past

* Matt Weber (Boeing)
* Muhammad Qasim (Seimens)
* Chuck Wolber (Boeing)
* Jeannette N. (Boeing)
* Shefali Sharma (Nextleap Aeronautics)
* Jeannette N. (Boeing)
* Steve VanderLeest (Boeing)
* Youssef Hajjiouri (Hurn3t S3c)
* Lukas Bulwahn (Elektrobit Automotive)
* Phillip Ahmann (Bosch)
* Thomas Mittlestadt (Bosch)
* Gabriele Paoloni (Red Hat)

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

## Agenda Items

### Current Topics

* Announcements
  * Andrew Oppelt (Boeing) will lead in Matt’s absence
  * Luigi (Red Hat) will be Andrew’s backup
* 2025 Working Group Update
  * Thoughts?
* ks-nav topics
  * MR for documentation: https://github.com/dnjean/ks-nav/tree/demo-upload
* BASIL topics
* DeltaKernel topics
* Boeing/UIUC llvm-cov
* stress-ng Investigation

### Next Topics

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

* Announcements
  * Andrew Oppelt (Boeing) will lead in Matt’s absence (out for both March meetings)
  * Luigi (Red Hat) will be Andrew’s backup
* 2025 Working Group Update
  * Nothing in particular
* ks-nav topics
  * MR for documentation: https://github.com/dnjean/ks-nav/tree/demo-upload
  * AC: Working on the `graph-tool` which will be integrated into ks-nav
    * Similar to the kconfig-visualization tool but different visualization
    * Demonstrate the boolean logic that exists between different config options
  * MK: Is this published or just using it internally?
    * AC: Want to cleanup the graph-tool before publishing
  * AC: Includes other features like comparing the graphs and highlighting differences
    * These are helpful because a single change can completely change how things are rendered
* BASIL topics
  * LP: Should update the live version with the latest version of BASIL
  * LP: Updated BASIL with importer for (BASIL SPDX, StricDoc SDPX, Yaml, JSON, Spreadsheet)
  * LP: MR out for simplifying user management and permissions
    * Map all the users to permissions, easier to manage permissions across users
  * LP: MR out there for better password reset functionality (via email)
  * LP: Planning to include test import
    * Current uses Test Management Tool (TMT) which exports to json
    * Can import just the test that you want
  * LP: Upload to BASIL arbitrary kinds of file which can be reused as different types of items
  * LP: Invited by NASA to a conference in California in July
    * Unable to attend because of funding
  * LP: Possibility to deploy on Debian for RaspberryPi for test environments
* Boeing/UIUC llvm-cov
  * MK: Gus at Colloraba asking about using llvm-cov in Kernel-CI
    * Looking at doing gcov test, however is aware of the llvm-cov effort in ELISA
    * If it's the same amount of effort they'd like to align with us
    * MK: Are we still carrying any patches that would make it more difficult?
    * AO: Will double check w/ Chuck and UIUC to ensure there are not other patches
  * MK: UIUC team did demo of the object code coverage approach
  * Background: DO-178C has an object code coverage objective
    * At SWL-A, have to demonstrate assembly code not represented in source is also covered
    * Boeing working w/ UIUC to create an open source workflow to achieve this
    * It is a separate tool from llvm-cov because it was simplier that way
  * LP: KernelCI folks have a weekly meeting (today actually!) and a Discord channel
* DeltaKernel topics
* stress-ng Investigation

## Round Table

## Action Items

* [x] Matt: Add link to the live instance of BASIL to the GitHub front page
* [ ] Matt: Add link to the kconfig visualization the GitHub front page
* [ ] Matt: Investigation leveraging stress-ng (send example for LP's talk)
* [ ] Matt K/Matt W/Jeannette: Talk about possible addition of complexity metrics

## Closing
