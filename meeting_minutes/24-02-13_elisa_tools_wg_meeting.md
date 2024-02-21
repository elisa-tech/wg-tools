
![logo](logo_elisa_small.png)

# ELISA Tool Investigation & Code Improvement Working Group

## Date: 23-02-13

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
* Lukas Bulwahn (Elektrobit Automotive)
* Shefali Sharma
* Roberto Bagnara (Bugseng)
* Sudip (CodeThink)
* Phillip Ahmann (Bosch)
* Matt Weber (Boeing)

### Attended in the past

* Luigi Pellecchia (Red Hat)
* Thomas Mittlelstadt (Bosch)
* Gabriele Paoloni (Red Hat)
* Qasim (Seimens)

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

* BASIL topics
  * ELISA instance setup discussion
* Static Analysis in Open Source SW
  * How should we approach it?
    * Do we (and if so how?) reconcile OSS coding standards with Certification coding standards
  * How can we contribute?
    * Contribute to clang-tidy / clang-format?
* ks-nav topics
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

* MK: Can only support 30 minutes for the meeting today
  * Feel free to carry on discussion afterwards
* Static Analysis Findings
  * Discussion on Lukas' dead stores analysis
    * Running clang static analyzer on linux-next everyday
    * The findings are very difficult to analyze (take you over many many paths)
    * Proposed looking at the simplest rule which is dead stores
      * This particular class of warnings are 100% correct
    * Meta analysis in some cases because of configurability of the kernel
      * In some cases it's active and in others it is not
      * This case is a "false positive"/non-actionable finding (the tool got it right for *this configuration*, but the code is still correct)
    * Lukas has already patched 2 / 17 found.
  * Interest in submitting patches?
    * Matt Kelly has interested in using this an exercise to submit a first patch
    * Shefali is also interested
  * AC: What is the purpose of this activity?
    * LB: Primarily, to help folks learn the patch submission process
    * LB: Secondarily, to learn how static analysis performs on the kernel
  * MK: Other types of violations to look at?
    * Dead stores are the most frequent and simplest to analyze
    * There is one kind of related bug that is quite severe
      * You create an if statement that doesn't actually get hit because of a missing condition
    * All other types of violations are much more complex
  * MK: If there is interest, can we open it up to the next simplest violation?
    * LB: That would be difficult, probably better to look at the dynamic analysis next
  * LP: Where does the static analysis live?
    * MK will update the README.md
  * AC: Symbolic execution or mixed static/dynamic analysis?
    * AC: Experimented with this by creating [sys_no](https://github.com/alessandrocarminati/sys_no)
    * LB: Yes, you can but its very complex to make it work in the kernel
    * AC: Have done some proofs of this in the past for glibc with qemu
    * LB: Built in features called static keys that helps do this
* BASIL Instance Setup
  * Building 1 of the 2 containers we need to run the application
  * Need to figure out how to unblock the correct ports once the second

## Round Table

## Action Items

* [ ] Matt: Bring up engagement (present to vertical groups? blog post? presenting November summary meeting) at the TSC
* [ ] Matt: Model wg-tools README.md after wg-automative to educate newcomers quickly
* [ ] Matt: Contact Sudip/Lukas to pull together documentation on patch submission
* [ ] Qasim: Explore the open source static analysis tools used by kernel
* [ ] Qasim: Understand clang static analysis tools (clang-tidy/clang-analyzer)

## Closing
