
![logo](logo_elisa_small.png)

# ELISA Tool Investigation & Code Improvement Working Group

## Date: 24-05-14

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
* Alessandro Carminati (Red Hat)
* Shefali Sharma

### Attended in the past

* Matt Weber (Boeing)
* Youssef Hajjiouri (Hurn3t S3c)
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

* BASIL
  * Public instance
    * Continuing to work on getting the ports opened correctly
    * Luigi setup VM that Sudip provisioned by cannot hit the ports
  * EOSS
    * About ~20 people in the room for the presentation
    * Kate was also presenting the keynote to ~200 people!
    * Available on YouTube [here](https://www.youtube.com/watch?v=1xmcpco14nE)
    * Looking to continue the discussion in Vienna in Sept.
    * LinkedIn video demo [here](https://www.linkedin.com/posts/luigi-pellecchia_how-basil-can-help-linux-test-project-to-activity-7186248090129956864-d-vC)
      * Shows how we can track to upstream test and improve the man pages
      * Also started a conversation on the ltp mailing list
        * Thread: Re: [LTP] Identify current test coverage and clarify contribution opportunities
        * The response was interesting
        * In part, they didn't want additional work to do the mapping between man page page
        * Mapping helps identify gaps
  * SDPX as a data exchange format
    * Data can be exported to SPDX but doesn't cover test results
    * Import feature is not ready
    * The catch with SDPX is that even though you can export to SPDX it can be exported in a non-standard way
    * Custom fields are kind of key/value but maybe
  * Xen selected another tool (OpenTrace??)
    * Stefano provided some rationale in his [EOSS talk](https://www.youtube.com/watch?v=uuBhqwbaObE)
    * Most data is stored in the git repo
* ks-nav
  * Alessandro: still working on the global symbols
    * Extraction work is done, but need to find a way to present the data in an effective way
    * Currently only static drawings which are quite commplicated
    * Looking to create something interactive
  * Matt W and Jeannette N. (@Boeing) are getting ks-nav setup.
    * May upstream a setup fix or two.
* syzkaller
  * Alessandro explored skykaller in a personal blog [post](https://carminatialessandro.blogspot.com/2024/05/navigating-syzkaller-experience-bug.html)
  * Do we want to talk about it this group?
  * Matt K: We have previously talked about it in this group, but lately interest has been elsewhere
  * Matt K: Related discussion coding standard discussion
    * How do we approach coding standards in an open source collaboration?

## Round Table

## Action Items

* [ ] Matt/WG: Understand how we can engage Vertical Groups (Automotive, etc.) so we have real examples of how to use tools
* [ ] Matt: Bring up engagement (present to vertical groups? blog post? presenting November summary meeting) at the TSC
* [ ] Matt: Contact Sudip/Lukas to pull together documentation on patch submission
* [ ] Qasim: Explore the open source static analysis tools used by kernel
* [ ] Qasim: Understand clang static analysis tools (clang-tidy/clang-analyzer)

## Closing
