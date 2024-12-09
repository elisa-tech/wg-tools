
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
* Alessandro Carminati (Red Hat)
* Jeannette N. (Boeing)
* Matt Weber (Boeing)

### Attended in the past

* Luigi Pellecchia (Red Hat)
* Shefali Sharma (Nextleap Aeronautics)
* Sudip Mukherjee (CodeThink)
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

* 16-18 Sept, Open Source Summit Europe (Vienna, Austria)
* 18-20 Sept, Linux Plumbers Conference (Vienna, Austria)
  * Safety Critical Microconference
* 28-29 Oct, Open Source Summit Japan (Tokyo, Japan)

## Agenda Items

### Current Topics

* Announcements
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
* ks-nav Topics
  * AC: Not a lot to report, been on PTO
  * JN: Have received some feedback on the MR
* BASIL Topics
* DeltaKernel Topics
  * Merged PR#3 so the code is now on main
  * A few standing tickets 
    * Decoupling it from a user's checkout of linux
    * kconfig analysis gap
* Base configuration Discussion
  * Background: Matt W release a initial draft of Boeing's "extremely minimal" configuration
  * AC: Items that are not defined end up taking the arch default
  * MW: Haven't caught on emails yet, but seems to have prompted a lot of response
  * MW: Still working through the analysis
  * MK: Who maintains the configuration checker?
    * MW: Not sure
    * MW: Lots of improvements we could make to it
      * Profiles? Debug/Release? Different use cases?
  * AC: Goal of other discussions was to start a "do nothing" application
    * Found lots of dependencies that weren't expected. Crypto?
    * A lot of times this was because of the arch default
  * MK: Basically we need to explicitly set everything so arch default is taken
    * AC: Yes, but more importantly you need to thoroughly review the result
  * MW: We did have lots of explicit "not sets" but there items in the arch default that we cannot manage via configuration
    * The "not sets" are respected however if it's a hard dependency than they are still pulled in, so we need to make code changes
  * AC: That data is in the kconfig files
  * MW: Example in chat of hard dependencies
    ```
    config ARM64
        def_bool y
        select ACPI_CCA_REQUIRED if ACPI
        select ACPI_GENERIC_GSI if ACPI
        select ACPI_GTDT if ACPI
        select ACPI_IORT if ACPI
        select ACPI_REDUCED_HARDWARE_ONLY if ACPI
        select ACPI_MCFG if (ACPI && PCI)
        select ACPI_SPCR_TABLE if ACPI
        select ACPI_PPTT if ACPI
        select ARCH_HAS_DEBUG_WX
        select ARCH_BINFMT_ELF_STATE
        select ARCH_ENABLE_HUGEPAGE_MIGRATION if HUGETLB_PAGE && MIGRATION
        select ARCH_ENABLE_MEMORY_HOTPLUG
        select ARCH_ENABLE_MEMORY_HOTREMOVE 
    ```

  * AC: Another note, when you use a particular item, if any of the downstream dependencies are later disabled. That item will be removed. 
  * MW: Arch default is select flags that change common code behavior downstream
    * Some options simply include or exclude code
    * Some options change the behavior of certain code
  * MW: We may want to make the checker smarter such that it pulls in the kconfig data as well, not just checks the results
  * AC: Kernel is always a moving target, may need to fix a kernel version
    * MK: Perhaps we can include this in the checker
    * AC: Maybe the tool can also produce the minimal kernel 
  * MW: Tickets under the delta kernel repo to add features to compare differences in kconfig based on version differences
    * Where does it change because of config vs. changes in code?
  * MK: We also should set it up so we can see the code diff based on changing the config
    * MK: This could be useful just in analyze what we want to turn 
    * MW: We can do this today with a subset of the features, just need to setup the workflow
  * AC: Not for today, but we should put this information directly into the ks-nav database
  * MW: Biggest limitation w/ DeltaKernel is that git tools cannot be parallelized
    * There are some research projects out there on parallelizing blame but didn't dig too deep
* Other Topics
  * MW: There may be some work coming from the Space Grade Linux SIGs
    * There is going to be a survey to help define the groups themselves
    * Going out to ESA, NASA, LibreSpace, linux4space


## Round Table

## Action Items

* [ ] Matt: Investigation leveraging stress-ng (send example for LP's talk) 
* [ ] Matt K/Matt W/Jeannette: Talk about possible addition of complexity metrics
* [ ] Matt/WG: Understand how we can engage Vertical Groups (Automotive, etc.) so we have real examples of how to use tools
* [ ] Matt: Bring up engagement (present to vertical groups? blog post? presenting November summary meeting) at the TSC
* [ ] Matt: Contact Sudip/Lukas to pull together documentation on patch submission

## Closing
