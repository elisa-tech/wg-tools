
![logo](logo_elisa_small.png)

# ELISA Tool Investigation & Code Improvement Working Group

## Date: 24-07-25

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
* Steve VanderLeest (Boeing)
* Shefali Sharma (Nextleap Aeronautics)
* Muhammad Qasim (Seimens)

### Attended in the past

* Yizhen Zhang (Boeing)
* Matt Weber (Boeing)
* Luigi Pellecchia (Red Hat)
* Jeannette N. (Boeing)
* Sudip Mukherjee (CodeThink)
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
  * cregit discussion
* ks-nav topics
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

* Discussion on cregit 
  * MK: Meeting with Kate Stewart & cregit author to discuss moving the tool under this group
  * SV: Even just having a list of the tools is a useful exercise
  * SV: This could help us identify the gaps we have in delivering the right development assurance
* DeltaKernel
  * MK: Initial MR is out (link above)
  * MK: Would be good to get feedback on usage to draw out assumptions  didn't realize she made
* ks-nav
  * JN has an MR out to add a tutorial for new users of ks-nav
    * Changes in fork here for review: https://github.com/dnjean/ks-nav/tree/demo-upload
* QM: Is the group still working on submitting kernel pathces
  * MK: Yes, still consider it part of the work scope but attendees haven't been as focused on it recently
  * MK: A few of the more active kernel patching folks haven't been attending recently but are still engaged
  * MK: Post to the mailing and you should get responses from them!

## Round Table

## Action Items

* [ ] Matt K/Matt W/Jeannette: Talk about possible addition of complexity metrics
* [ ] Jeanette: Add notes to documentation setup
* [ ] Matt/WG: Understand how we can engage Vertical Groups (Automotive, etc.) so we have real examples of how to use tools
* [ ] Matt: Bring up engagement (present to vertical groups? blog post? presenting November summary meeting) at the TSC
* [ ] Matt: Contact Sudip/Lukas to pull together documentation on patch submission

## Closing
