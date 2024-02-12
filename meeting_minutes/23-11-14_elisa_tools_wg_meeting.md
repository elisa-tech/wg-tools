
![logo](logo_elisa_small.png)

# ELISA Tool Investigation & Code Improvement Working Group

## Date: 23-11-14

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

* Sudip (CodeThink)
* Matt Kelly (Boeing)
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

## Discussion Items

* Revising/broadening the Working Group mission statement
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

## Discussion Notes

* Current Proposal for new WG mission Statement:
  * Existing: "The Tool Investigation and Code Improvement WG focuses on application of tools, handling the tool results, and improving the kernel based on the tools’ feedback.
  * New: "The Tool Investigation and Code Improvement WG focuses on creation, analysis, and application of tools and techniques to contribute to the improvement of the kernel for use in safety cases."
  * Rationale
    * Making the wording more generic (less focused on tools) opens the mission statement up to ways of improving the code beyond static analysis (direct code improvements, increased configurability, testing (unit and others), etc.)
    * Added reference to safety as a reference to ELISA's overall mission statement. Our improvements sound be focused on helping improve the case for using Linux in safety and not just general improvement of the kernel (although we are not opposed to that either)
* Reached out to Lukas about blog post

* Original idea was that other groups would propose tools that are needed or could be used, not many suggestions

* Sudip demo of CI
  * In GitLab
  * Started with Automotive Group
* Docker is being built from docker file in wg-automotive?
* Sudip has always used docker for building Yocto
  * Never has seen any issues
* OpenQA set of tests
  * Helps tests of the graphical interface
  * Previously could only develop with QEMU and VNC
  * Currently being enhanced to run on real HW
* system wg also has a CI which has the XEN demo
* Syzkaller CI
  * Full setup instructions are in the mailing list
* No current requests for additional improvements to CI

* How do we apply static analysis to any old package that gets pulled into the Yocto build?
* How do we show generation of code coverage?
  * We could do this for the general
  * And then same as above, more generic there is a problem for any old package that gets pulled in

* Qasim: How can we validate fixes from Code Checker?
  * Sudip: Before sending to upstream, we were encouraging to send to WG ML
  * In general, expected that you send it to staging
* Matt: Is there a way to setup a branch and test it to validate the warning is gone?
  * Sudip: Not right now, but we could set that up
* General path for new kernel contributors is to submit to staging first
  * https://git.kernel.org/pub/scm/linux/kernel/git/next/linux-next.git/tree/drivers/staging?h=next-20231114

* Sudip: Automotive
  * Built, tested, and validate automotive test case
  * Didn't use any other open source test cases
* Normal build tests, allnoconfig
  * Normal
  * Lots of of bots will pick it up and test against lots of environments
  * Intel Zero-day bot
  * Lava, kernelCI
  * CodeThink has build infrastructure for many different architectures

* We will meet on the 12th but not the 28th?

## Round Table

## Action Items

* [] Matt: Bring up engagement (present to vertical groups? blog post? presenting November summary meeting) at the TSC
* [x] Matt: Create proposal for broader WG mission statement
* [] Matt: Model wg-tools README.md after wg-automative to educate newcomers quickly
* [] Matt: Contact Sudip/Lukas to pull together documentation on patch submission
* [] Qasim: Explore the open source static analysis tools
* [] Qasim: Understand clang static analysis tools (clang-tidy/clang-analyzer)

## Closing
