
![logo](logo_elisa_small.png)

# ELISA Tool Investigation & Code Improvement Working Group

## Date: 24-08-12

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
* Shefali Sharma (Nextleap Aeronautics)
* Matt Weber (Boeing)
* Sudip Mukherjee (CodeThink)
* Jeannette N. (Boeing)

### Attended in the past

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

* 16-18 Sept, Open Source Summit Europe (Vienna, Austria)
* 18-20 Sept, Linux Plumbers Conference (Vienna, Austria)
  * Safety Critical Microconference
* 28-29 Oct, Open Source Summit Japan (Tokyo, Japan)

## Agenda Items

### Current Topics

* Announcements
  * cregit Webinar
  * 9/10 instance of this meeting will cancelled
* ks-nav topics
  * MR for documentation: https://github.com/dnjean/ks-nav/tree/demo-upload
* BASIL topics
* DeltaKernel topics
  * MR for Initial Work: https://github.com/elisa-tech/delta-kernel/pull/1
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
  * September 10th instance of the meeting will be cancelled
* Conferences Discussion
  * Lots of relevant talks and discussions coming up!
  * 16-18 Sept [OSS Europe](https://events.linuxfoundation.org/open-source-summit-europe/) - Sessions to be published
    * [Linux in Space: Fault Detection, Recovery and Fault-Tolerant System Designs - Lenka Kosková Třísková & Lukas Mazl, Technical University of Liberec & Tomas Novotny, VZLU](https://sched.co/1ej1t)
  * 16-18 Sept [Linux Plumbers Conference]
    * Luigi's Talks
      * [BASIL The FuSa Spice to spot gaps in kernel testing and more](https://lpc.events/event/18/contributions/1736/)
      * [BASIL development roadmap](https://lpc.events/event/18/contributions/1898/)
    * Alessandro's Talks
      * [ks-nav](https://lpc.events/event/18/contributions/1900/)
      * [Integrating kas-alias into kernel build: Overcoming Challenges with Non-Invasive Modifications](https://lpc.events/event/18/contributions/1830/)
      * [Addressing Duplicated Symbol Names in kallsyms: Introducing kas_alias for Symbol Differentiation](https://lpc.events/event/18/contributions/1730/)
    * UIUC Team on llvm-cov
      * [Measuring and Understanding Linux Kernel Tests](https://lpc.events/event/18/contributions/1793/)
    * Other Relevant Talks
      * [Building for Safety in a Security and Feature Focused World](https://lpc.events/event/18/contributions/1745/)
      * [Safe Systems with Linux - Micro Conference](https://lpc.events/event/18/contributions/1663/) [Topics](https://lpc.events/event/18/sessions/187/#20240920)
* LP: Could use help with mapping existing testing to system calls in our public instance of BASIL
  * This will be used in a presentation to demonstrate gaps in the current Linux kernel testing
  * Trying to leverage this to get more folks from Linux Test Project (LTP) involved
  * MK: stress-ng could be another potential source of testing for Luigi's talk for existing kernel testing
* ks-nav Topics
  * ks-nav MR
    * JN: Added more details to the current GitHub documentation in the form of a demo
    * Also some typo fixes
    * Demo includes the scripting approach and GUI usage
    * Forming them into patches that can submitted to the main ks-nav repo
* BASIL Topics
  * MK: What version of SDPX is BASIL using?
    * LP: Currently using SDPX 3.0
    * MK: Curious because Yocto seems way behind (2.2) but patches for 3.0 are coming
    * Interested to see what kind of connections we can make between Yocto SBOM and BASIL data
* DeltaKernel Topics
  * MR for Initial Work: https://github.com/elisa-tech/delta-kernel/pull/1
  * Lots of comments but we need to push it through as Yizhen's internship has ended
  * Matt W. to take a look at thread closure
  * MW: Interested in people who want to add the object analysis into the tool

## Round Table

## Action Items

* [ ] Matt: Investigation leveraging stress-ng (send example for LP's talk) 
* [ ] Matt K/Matt W/Jeannette: Talk about possible addition of complexity metrics
* [x] Jeanette: Add notes to documentation setup
* [ ] Matt/WG: Understand how we can engage Vertical Groups (Automotive, etc.) so we have real examples of how to use tools
* [ ] Matt: Bring up engagement (present to vertical groups? blog post? presenting November summary meeting) at the TSC
* [ ] Matt: Contact Sudip/Lukas to pull together documentation on patch submission

## Closing
