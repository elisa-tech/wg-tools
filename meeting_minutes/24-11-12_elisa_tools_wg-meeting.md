
![logo](logo_elisa_small.png)

# ELISA Tool Investigation & Code Improvement Working Group

## Date: 24-11-12

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
* Luigi Pellecchia (Red Hat)
* Matt Weber (Boeing)
* Chuck Wolber (Boeing)
  
### Attended in the past

* Sudip Mukherjee (CodeThink)
* Alessandro Carminati (Red Hat)
* Jeannette N. (Boeing)
* Shefali Sharma (Nextleap Aeronautics)
* Jeannette N. (Boeing)
* Steve VanderLeest (Boeing)
* Muhammad Qasim (Seimens)
* Youssef Hajjiouri (Hurn3t S3c)
* Lukas Bulwahn (Elektrobit Automotive)
* Roberto Bagnara (Bugseng)
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
  * Nov. 28th instance of this meeting cancelled (US Thanksgiving)
* Workshop Topics
  * Discuss any topics being presented from our group
* ks-nav topics
  * MR for documentation: https://github.com/dnjean/ks-nav/tree/demo-upload
* BASIL topics
* DeltaKernel topics
* stress-ng Investigation
* Boeing/UIUC llvm-cov
* Static Analysis in Open-Source SW
  * Continuation on of mixed static/dynamic analysis discussion
  * How should we approach it?
  * Do we (and if so how?) reconcile OSS coding standards with Certification coding standards
  * How can we contribute?
  * Contribute to clang-tidy / clang-format??

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
  * Nov. 28th instance of this meeting cancelled (US Thanksgiving)
* December Workshop Discussion (https://elisa.tech/event/elisa-workshop-at-nasa-goddard-space-grade-linux/)
  * Matt W and Matt K can't go due to business environment
  * CW: The requirements topic is on the agenda
  * Luigi is giving a talk about BASIL improvements
    * Link work items tests that are external to BASIL itself
    * Focus initially will be on Kernel CI (but also possibly GitHub CI, etc.)
    * Proposing another talk about ks-nav, using ks-nav in combination another tool to identify if a path has been executed
  * There are a some talks from NASA folks that might be only one time
    * Hope is that some will be redone via Webinars (they won't be recorded and posted)
* Requirements Topic
  * LG: Is the requirements discussion the same on the Gabrielle is involved in?
  * CW: Yes, it's quite the mashup of a conversation
    * Coming with an proposal to the workshop
* ks-nav Topics
* BASIL Topics
  * Nothing particularly new this week
  * Just the effort going on to link external test results
* DeltaKernel Topics
  * This effort is on hold for the moment.
  * Likely won't be picked up until next year.
  * CW: Is it open for contribution?
    * MW: Sure
  * MK: Is there enough documentation for people to contribute?
    * MW: It's good enough
  * MW: How do we get toward binary analysis with this tool?
  * MW: Kconfig tool could be useful in understand why code is remove with config options
* KConfig Tools
  * Showed off AC's tool
  * https://github.com/alessandrocarminati/kconfig-
* Other
  * MW: Interesting note from Aerospace WG--really close to putting together a black box test
    * Assembling NASA's copilot tool with emulated use case running test applications
    * Creating pipelines in Aero WG CI
    * Copilot might have some application to Tools WG
    * Copilot formal verification tool
      * https://copilot-language.github.io/
    * Copilot watches traffic / tracepoints and verifies they are in-bounds
  * MW: Think Copilot will be a big topic for space groups going forward given the tool stacks they want to use
  * Test setup running in an Ubuntu container

## Round Table

## Action Items

* [ ] Matt: Add link to the live instance of BASIL to the GitHub front page
* [ ] Matt: Add link to the kconfig visulization the GitHub front page
* [ ] Matt: Investigation leveraging stress-ng (send example for LP's talk)
* [ ] Matt K/Matt W/Jeannette: Talk about possible addition of complexity metrics
* [ ] Matt/WG: Understand how we can engage Vertical Groups (Automotive, etc.) so we have real examples of how to use tools
* [ ] Matt: Bring up engagement (present to vertical groups? blog post? presenting November summary meeting) at the TSC
* [ ] Matt: Contact Sudip/Lukas to pull together documentation on patch submission

## Closing
