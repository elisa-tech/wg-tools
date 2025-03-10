
![logo](logo_elisa_small.png)

# ELISA Tool Investigation & Code Improvement Working Group

## Date: 24-04-25

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
* Shefali Sharma
* Matt Weber (Boeing)
* Youssef Hajjiouri (Hurn3t S3c)

### Attended in the past

* Alessandro Carminati (Red Hat)
* Luigi Pellecchia (Red Hat)
* Sudip Mukherjee (CodeThink)
* Lukas Bulwahn (Elektrobit Automotive)
* Roberto Bagnara (Bugseng)
* Phillip Ahmann (Bosch)
* Thomas Mittlestadt (Bosch)
* Gabriele Paoloni (Red Hat)
* Muhammad Qasim (Seimens)

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

* 11-12 June, Embedded Real Time Systems (Toulouse, France)
* 15-19 July, IEEE Space Mission Challenges for Information Technology (Mountain View, USA)
* 29-2 July-Aug, AIAA Aviation Aviation Forum (Las Vegas, USA)
* 13-15 June, DevConf Czech Republic (Brno, Czech Republic)
* 16-18 Sept, Open Source Summit Europe (Vienna, Austria)
* 18-20 Sept, Linux Plumbers Conference (Vienna, Austria)
* 28-29 Oct, Open Source Summit Japan (Tokyo, Japan)

## Agenda Items

### Current Topics

* Announcements
  * June workshop [schedule](https://elisa.tech/event/elisa-workshop-lund/)
* ks-nav topics
  * Boeing has ks-nav setup for kernel 6.6!
  * MR for new features!
* BASIL topics
  * Public instance status
  * EOSS Report?
  * Further Xen Interaction?
* Boeing/UIUC llvm-cov
  * Making Linux Fly: Towards Certified Linux Kernel (5/22/24 @ 7:00 Pacific / 14:00 UTC)
* Static Analysis in Open Source SW
  * Continuation on of mixed static/dynamic analysis discussion
  * How should we approach it?
    * Do we (and if so how?) reconcile OSS coding standards with Certification coding standards
  * How can we contribute?
    * Contribute to clang-tidy / clang-format?

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

* Boeing/UIUC llvm-cov
* ks-nav
  * Matt W. working with another engineer to setup scanning a custom kernel version
    * Found a few bugs that have been worked out
    * Going to do some MRs to add additional documentation for new users
* BASIL

## Round Table

## Action Items

* [ ] Matt/WG: Understand how we can engage Vertical Groups (Automotive, etc.) so we have real examples of how to use tools
* [ ] Matt: Bring up engagement (present to vertical groups? blog post? presenting November summary meeting) at the TSC
* [ ] Matt: Contact Sudip/Lukas to pull together documentation on patch submission
* [ ] Qasim: Explore the open source static analysis tools used by kernel
* [ ] Qasim: Understand clang static analysis tools (clang-tidy/clang-analyzer)

## Closing
