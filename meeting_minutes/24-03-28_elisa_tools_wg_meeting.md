
![logo](logo_elisa_small.png)

# ELISA Tool Investigation & Code Improvement Working Group

## Date: 23-03-28

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
* Luigi Pellecchia (Red Hat)
* Matt Weber (Boeing)

### Attended in the past

* Shefali Sharma
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

* 16-18 April 2024 Open Source North America in Seattle, Washington
* June DevConf Czech Republic
* Open Source Summit Europe (Vienna, Austria)
* Open Source Summit Japan
* Linux Plumbers Conference (Vienna, Austria)

## Agenda Items

### Current Topics

* BASIL topics
  * Very close on public instance?
* ks-nav topics
* Topics for the June Workshop
* Boeing/UIUC llvm-cov
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

* ks-nav
  * AC: One need was to highlight the global symbols
    * Just added via this commit: https://github.com/elisa-tech/ks-nav/compare/main...alessandrocarminati:ks-nav:main
    * The commit creates the data and populates the database
    * AC showed a demo of the data that is generated: https://pastebin.com/B6R855ik 
      * For a single function is shows all global variables uses with line and memory address
      * Then boils this down to a simple list
      * Still working on the visualization pieces for this data
* BASIL
  * Working on the authentication is still on-going
    * Still working on reverse proxy with nginx with Sudip
    * nginx routing is clashing with the React router
  * Added a layer of abstraction to test cases so they can describe any test
  * BASIL will provide a test environment as a Fedora container
* llvm-cov
  * Boeing working with University of Illinois (UIUC) on enhancing llvm-cov to support MC/DC on the kernel
    * MC/DC was implemented in llvm by Alan Phipps @ Texas Instruments
    * UIUC helped find and fix several bugs and improved reporting
    * Kernel requires PGO patch from Google/Meta
    * UIUC team updated this patch is going to resubmit to upstream (it's been previously rejected)
  * MC/DC
    * A method to show you've covered all important cases in a multi-art conditional
    * https://en.wikipedia.org/wiki/Modified_condition/decision_coverage
* Topics for the Workshop in June
  * MK will probably give a Tools WG update
  * MK considering adding a topic around llvm-cov/kernel testing
  * AC volunteered to present on ks-nav and LFSCS
  * LP is unfortunately on vacation

## Round Table

## Action Items

* [ ] Matt/WG: Understand how we can engage Vertical Groups (Automotive, etc.) so we have real examples of how to use tools
* [ ] Matt: Bring up engagement (present to vertical groups? blog post? presenting November summary meeting) at the TSC
* [ ] Matt: Contact Sudip/Lukas to pull together documentation on patch submission
* [ ] Qasim: Explore the open source static analysis tools used by kernel
* [ ] Qasim: Understand clang static analysis tools (clang-tidy/clang-analyzer)

## Closing
