
![logo](logo_elisa_small.png)

# ELISA Tool Investigation & Code Improvement Working Group

## Date: 24-06-10

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

* Matt Kelly (Boeing)
* Muhammad Qasim (Seimens)
* Matt Weber (Boeing)
* Shefali Sharma (Nextleap Aeronautics)
* Alessandro Carminati (Red Hat)

### Attended this meeting

### Attended in the past

* Jeannette Nounagnon (Boeing)
* Luigi Pellecchia (Red Hat)
* Youssef Hajjiouri (Hurn3t S3c)
* Sudip Mukherjee (CodeThink)
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

* 11-12 June, Embedded Real Time Systems (Toulouse, France)
* 15-19 July, IEEE Space Mission Challenges for Information Technology (Mountain View, USA)
* 29-2 July-Aug, AIAA Aviation Forum (Las Vegas, USA)
* 13-15 June, DevConf Czech Republic (Brno, Czech Republic)
* 16-18 Sept, Open Source Summit Europe (Vienna, Austria)
* 18-20 Sept, Linux Plumbers Conference (Vienna, Austria)
* 28-29 Oct, Open Source Summit Japan (Tokyo, Japan)

## Agenda Items

### Current Topics

* Announcements
* ks-nav topics
* BASIL topics
  * Public instance available!
    * http://elisa-builder-00.iol.unh.edu:9056
  * Tour by Luigi
* Boeing/UIUC llvm-cov
* Kernel Change Impact Tooling
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

* MQ: Investigation around kernel static analysis tools
  * Ran clang-tidy analysis on kernel
  * Already setup git send-email
  * Need to rework patch because the kernel has been updated since it was created
  * Wondering about validation
    * Sudip recommended to just submit and let the machinery work
    * Matt W has had a similar experience
    * Be careful about what you submit!
* MW: Intern working on change impact analysis
  * Hoping to get a patchset submitted to the kernel
  * Compare a current configuration vs. future tag of the kernel
  * Compare what kernel code is included/changed in the kernel
  * Hoping to use it as a tool for planning change impact for safety critical
* MQ: Looking at ks-nav slides, why do we need a compiled version of the kernel
  * MK: Pretty difficult to tell what is compiled in source + config
  * MK: Configuration options mean something may or may not be called. Using the binary gives an exact answer on the call trees, etc.
* MQ: ks-nav documentation is spread out in a few places
  * MK: We also experienced that it's a bit difficult to setup
  * MK: JN from Boeing was going to contribute some updates
  * MK: Open an MR if you have suggestions
* MQ: We using radare2 as the RE tool
  * Interfaces change rapidly with this tool
  * AC: Agreed, that said the features we are using are pretty stable
  * AC: We've put it in the roadmap to use other backends
  * AC: Rizin is a fork, that is more stable and a quick drop-in replacement
  * AC: Ghidra is more complicated, does the same thing but interfaces are completely different
    * Provides only Java APIs
  * AC: Another option is implementing radare features from scratch
    * Possible, but a decent amount of work
* MQ: We discussed the kernel can be around 100K via configuration options
  * MK: My experience has been around 250K for the "allno"
  * MW: Aerospace WG looking at creating a minimal configuration because the Auto config is still pretty large
  * AC: In Lund, kernel tinyconfig might be a good starting point
    * https://github.com/torvalds/linux/blob/master/kernel/configs/tiny.config
  * AC: Not sure I agree with this
  * AC: Tinyconfig is basically just the architecture default, meaning it is not a single configuration
  * AC: A lot of items are also not specified in tinyconfig (e.g. kernel support for mutex, can't really live w/o it)
  * AC: Mutex is required by most C system libraries
  * AC: It doesn't specify any output devices. Need at least a serial driver
  * AC: We should decide a reference board (or QEMU device) and specify a config over it that is usable
  * MK: We've similarly thought of picking a reference board
    * Key pieces is that you can run and test that things are working
  * AC: Going to upload some slides on the topic
    * https://github.com/elisa-tech/wg-lfscs/blob/main/lfscs-meetings/resources/20240611-LFSCS-Meeting.pdf
* MK: Still need to talk to talk to JN about complexity metrics
  * AC: Want to present ks-nav at Plumbers
  * AC: Looking at adding complexity to help a usecase I want to present at LPC
  * AC: https://github.com/elisa-tech/ks-nav/issues/25
  * Lund Workshop material: https://github.com/elisa-tech/wg-lfscs/blob/main/lfscs-meetings/resources/20240611-LFSCS-Meeting.pdf
  * MK: What is the "automate builds" feature
    * Want to present a use case which allows maintainers to undrestand how patches impact other subsystems
    * In order to do this want to automate builds otherwise it is painful to compare between built images
  * MK: Need to coordinate this w/ MW's change impact tooling

## Round Table

## Action Items

* [ ] Matt/Matt/Jeannette: Talk about possible addition of complexity metrics
* [ ] Jeanette: Add notes to documentation setup
* [ ] Matt/WG: Understand how we can engage Vertical Groups (Automotive, etc.) so we have real examples of how to use tools
* [ ] Matt: Bring up engagement (present to vertical groups? blog post? presenting November summary meeting) at the TSC
* [ ] Matt: Contact Sudip/Lukas to pull together documentation on patch submission

## Closing
