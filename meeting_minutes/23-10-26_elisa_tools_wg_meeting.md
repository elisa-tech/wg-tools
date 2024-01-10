
![logo](logo_elisa_small.png)

# ELISA Tool Investigation & Code Improvement Working Group

## Date: 23-10-26

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
* Qasim (Seimens)

### Attended in the past

* Sudip (CodeThink)

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

## Discussion Topics

* Prioritizing Discussion Topics
  * Non-negotiable: Revising/broadening the Working Group mission statement
  * Other Topics
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
    * Rust
      * No particularly interesting, maybe future topic?

## Discussion Notes

* Current Mission Statement:
  * "The Tool Investigation and Code Improvement WG focuses on application of tools, handling the tool results, and improving the kernel based on the tools’ feedback.
  * Qasim: We can add tools which make things easier and adding configuration per earlier
  * Matt: Change "tools" to "techniques" such that it could including testing
  * Matt: Scratch "based on the tools feedback"
    * "Improving the kernel to enable it's use in safety cases"??
    * This could including increasing the configurability of the kernel to get only what is relevant to your use case

  * Current Proposal: "The Tool Investigation and Code Improvement WG focuses on creation, analysis, and application of techniques to contribute to the improvement of the kernel for use in safety cases."
  
* Qasim/Matt: There is a barrier to entry to ALL groups but especially the industry groups
  * How can we improve documentation for newcomers so that it is easy for the to participate in the next conversation!
* Qasim/Matt: There is a fear factor to submitting your first patch anywhere or jumping into a mailing list for the first time!
  * The prior group did great working getting people setup via active meetings but we need to create better documentation for newcomers
* Qasim: Linux Foundation Course 103 on guide on how to create patches
* Matt: Interested in being part of the broader OSS community
* Matt: Boeing making a big push to make Linux viable for aerospace safety use-cases
* Matt: Background in the tools required for aerospace compliance
* Matt: Want to broaden the mission statement beyond "contributing to Linux" to "contributing to Linux to improve the safety case"
* Matt: Very interesting in contributing additional kernel configuration options to make a smaller kernel possible (to help safety)
* Matt: Very interested in increasing kernel code testing coverage
* Qasim: Open source static analysis tools for Linux
  * https://docs.kernel.org/dev-tools/index.html
  * Kernel documentation lists coccinelle, sparse, and smatch
  * Can we qualify those tools for use in safety (aerospace, automotive)?s
* Qasim: How will we test and validate the addition of configuration options to the kernel?
  
## Round Table

## Action Items

* [] Matt: Bring up engagement (present to vertical groups? blog post? presenting November summary meeting) at the TSC
* [] Matt: Create proposal for broader WG mission statement
* [] Matt: Model wg-tools README.md after wg-automative to educate newcomers quickly
* [] Matt: Contact Sudip/Lukas to pull together documentation on patch submission
* [] Qasim: Explore the open source static analysis tools
* [] Qasim: Understand clang static analysis tools (clang-tidy/clang-analyzer)

## Closing
