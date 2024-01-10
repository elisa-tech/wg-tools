
![logo](logo_elisa_small.png)

# ELISA Tool Investigation & Code Improvement Working Group

## Date: 23-12-12

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
* Lukas Bulwahn
* Shefali Sharma
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

* 27 Feb 2024 [AvioSE'24](https://aviose*workshop.github.io/) in Linz, Austria

## Discussion Items

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
  * Translating runtime test to kunit tests
* Tool Qualification
  * What are the similarities/differences of Tool Qualification across industries?
  * How we do approach qualification of OSS tools?
* clang compatibility
  * Can we use clang in Yocto as an alternative to GCC

## Discussion Notes

* Current Proposal for new WG mission Statement:
  * Existing: "The Tool Investigation and Code Improvement WG focuses on application of tools, handling the tool results, and improving the kernel based on the tools’ feedback.
  * New: "The Tool Investigation and Code Improvement WG focuses on creation, analysis, and application of tools and techniques to contribute to the improvement of the kernel for use in safety cases."
  * Rationale
    * Making the wording more generic (less focused on tools) opens the mission statement up to ways of improving the code beyond static analysis (direct code improvements, increased configurability, testing (unit and others), etc.)
    * Added reference to safety as a reference to ELISA's overall mission statement. Our improvements sound be focused on helping improve the case for using Linux in safety and not just general improvement of the kernel (although we are not opposed to that either)
  * LB: Specifically avoided the word safety, to avoid the discussion to whether the activity actually contributes to safety
    * Could just use a more generic word like "quality" or avoid it completely
    * E.g. the real-time discussion, you could have a safety system that isn't real-time at all
  * Maybe to "to enable safety"?

* Tools WG will now be supporting BASIL
  * More to come on what this looks like

* Kernel Testing
  * Wrap regression test around a minimal kernel
  * MK: Focus originally was on the kunit tests
  * Any focus on the summary of testing strategies?
    * LB: No focus on this in ELISA yet. Worthwhile items:
      * Kernel CI system (collects test, but difficult to interpret them)
      * kunit tests / kselftests
      * Fuzzing (syzkaller, etc.)
    * Matrix of configuration vs. test is either not very well explored and most not relevant
    * Lots of runtime test in the kernel that haven't been translating (possible work statement)
    * Very little code that can be tested in isolation (usually has to be integrated to some degree)
* Tool Qualification
  * Would there be benefit to adding documentation / test cases to GCC / LLVM, etc.
* SS: Need access to ELISA servers for Yocto to setup CI
  * Medical devices group want to setup CI for OpenAPS
  * Need meta layer and at least 1 target
  * SS: Starting from scratch on this project
  * Yocto (latest) on RaspberryPi

* Issue working w/ Clang on local setup
  * Initially used apt to install
  * Running clang-tidy on a simple hello world file
  * Error trying to load compilation database

## Round Table

## Action Items

* [] Matt: Bring up engagement (present to vertical groups? blog post? presenting November summary meeting) at the TSC
* [] Matt: Model wg-tools README.md after wg-automative to educate newcomers quickly
* [] Matt: Contact Sudip/Lukas to pull together documentation on patch submission
* [] Qasim: Explore the open source static analysis tools
* [] Qasim: Understand clang static analysis tools (clang-tidy/clang-analyzer)
* [] Sudip: Setting up repo for medical devices CI

## Closing
