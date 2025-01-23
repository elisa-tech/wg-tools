
![logo](logo_elisa_small.png)

# ELISA Tool Investigation & Code Improvement Working Group

## Date: 24-01-14

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
* Matt Weber (Boeing)
* Alessandro Carminati (Red Hat)
* Andrew Oppelt (Boeing)
* Roberto Bagnara (Bugseng)
* Muhammad Qasim (Seimens)
  
### Attended in the past

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

* FOSDEM

## Agenda Items

### Current Topics

* Announcements
  * Matt will be on leave for portions of this year
    * Tenatively ~1 month Feb/March, ~2 Months (July/August)
  * Andrew Oppelt (Boeing) will lead in Matt’s absence
  * Luigi (Red Hat) will be Andrew’s backup
* 2025 Objectives
  * Formalize what we discussed last week (if needed)
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
  * Matt will be on leave for portions of this year
    * Tenatively ~1 month Feb/March, ~2 Months (July/August)
  * Andrew Oppelt (Boeing) will lead in Matt’s absence
  * Luigi (Red Hat) will be Andrew’s backup
  * MK: Really appreciate both Andrew and Luigi for volunteering to help!!
* 2025 Objectives
  * Formalize what we discussed last week (if needed)
    * Overall Objective: Leveraging existing efforts to show the useful of traceability artifacts to standard kernel developer??
    * Workflow: KS-Nav (Call tree) -> Req -> Test Case -> KernelCI Result -> llvm-cov coverage -> ks-nav (ftrace coverage)
    * Benefits:
      * Demonstrates we can highlight test gaps based on the data available
      * Making the kernel coverage data available alone would be useful
      * AC: Kernel dev knows the critical paths
        * The dev can notionally claim they cover the important parts (~80)
        * Can't tell exactly where the coverage is w/o coverage tools
        * Give the dev tools to show which paths were actually taking via ftrace
    * Gaps:
      * No one currently working on putting llvm-cov into KernelCI
      * ELISA does have some outward connections to KernelCI that we could leverage
  * ks-nav: Resolve the problem of the indirect function calls
    * Leverage llvm C parsing
    * Not sure how achievable this really
    * Not getting as much time to work here because of leading the LFSC WG
* December Workshop
  * AC: Presented a way to track the coverage that a test creates w/ an ftrace
    * This helps solve the indirect call problem
    * This is more of a backup solution
    * MK: Why ftrace vs. gcov/llvm-cov?
      * Exports paths in terms of functions
        * Easier to match to the the ks-nav call tree
        * LP: Also shows which functions called which to know the path
        * ftrace is also lower overhead
        * ftrace is more used within kernel test community
      * Gcov/llvm export in terms of lines of code
        * This data requires mapping of line numbers to function calls
    * MW: Elaborating on ftrace will also be good for WCET activities w/o requiring lots of instrumentation
* WG Updates
  * MW: Wrote a tool to data mine the participation numbers of the group
  * MK: Will try to give a preview of the WG update slides...
    * At next meeting (day before WG Updates)
    * On the mailing list
* ks-nav topics
  * MR for documentation: https://github.com/dnjean/ks-nav/tree/demo-upload
* BASIL topics
  * Talking at FOSDEM next week about BASIL & SBOMs
  * BASIL now supports exports of WI/traceability in SPDX 3 format
  * Starting to see some contributions on the GitHub repo
    * Not really sure what group/project are coming from
* DeltaKernel topics
  * No updates today
* Boeing/UIUC llvm-cov
  * Started to do some work on objective code coverage
  * This will be done outside of llvm-cov as a seperate open source tooling
  * Submitting to DASC 2025 to present on LLVM coverage
* stress-ng Investigation
* Other interesting things
  * MW: Space Grade Linux kicked off licensing conversation that made it's way to the TSC
    * Preferring MIT for source, Creative Commons for Docs
    * TSC appears to have approve this split
  * Developer agreement
    * Use DCO sign off strategy for contributions
  * MW is still representing SGL in TSC because they are SIG rather than a WG
    * A SIG is forming by a WG and could be promoted to a WG
    * Mostly treating it WG already
    * SGL SIG is exploring CI/CD
  * RB: Just checking in on the topics. Interested in llvm-cov.
    * Started using llvm-cov because of the MC/DC coverage

## Round Table

## Action Items

* [ ] Matt: Add link to the live instance of BASIL to the GitHub front page
* [ ] Matt: Add link to the kconfig visulization the GitHub front page
* [ ] Matt: Investigation leveraging stress-ng (send example for LP's talk)
* [ ] Matt K/Matt W/Jeannette: Talk about possible addition of complexity metrics

## Closing
