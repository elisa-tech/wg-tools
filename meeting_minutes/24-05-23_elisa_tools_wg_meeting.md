
![logo](logo_elisa_small.png)

# ELISA Tool Investigation & Code Improvement Working Group

## Date: 24-05-23

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
* Jeannette Nounagnon (Boeing)
* Alessandro Carminati (Red Hat)
* Shefali Sharma
* Luigi Pellecchia (Red Hat)

### Attended this meeting

### Attended in the past

* Matt Kelly (Boeing)
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
* 29-2 July-Aug, AIAA Aviation Forum (Las Vegas, USA)
* 13-15 June, DevConf Czech Republic (Brno, Czech Republic)
* 16-18 Sept, Open Source Summit Europe (Vienna, Austria)
* 18-20 Sept, Linux Plumbers Conference (Vienna, Austria)
* 28-29 Oct, Open Source Summit Japan (Tokyo, Japan)

## Agenda Items

### Current Topics

* Announcements
  * June workshop [schedule](https://elisa.tech/event/elisa-workshop-lund/)
* ks-nav topics
* BASIL topics
  * Public instance available!
    * http://elisa-builder-00.iol.unh.edu:9056
  * Tour by Luigi
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

* Conference Notes
  * Alessandro has submitted a talk for OSS Europe and two (one ELISA, one non-ELISA) for Linux Plumbers
* ks-nav
  * JN: Have it running w/ a debug build. Is there an ideal debug configuration?
    * Not well documented, but it is straightforward
    * Main issue is the database connection
    * All other parameters can be overriden
  * JN: Was more wondering about the kernel configuration
    * AC: Doesn't require a specific kernel configuration, just has to have the debug information
  * JN: Set it to the latest DWARF mode. Could provide docs on the minimum set for debugging
    * AC: Had always used V4, but good to hear that V5 works
    * AC: Was confident it should work because V5 is primarily an extension of V4
  * JN: Updated so it pulls the latest radare2 tag and it does work
    * AC: Good to hear but radare2 is pretty unstable which is why it was fixed
    * AC: Thinking of replace it with [rizin](https://github.com/rizinorg/rizin) which is a fork of radare that should be stable
  * JN: One idea would be to extract the complexity metrics that radare2 is generating
    * AC: We could add that, we haven't had a use for it
    * AC: Happy to add it if it useful, but we need to think of how to visualize it
    * AC: Since things are image-based, it's kind of tough to add additional data
    * AC: In the roadmap to change it to a tool that allows a degree of interaction (via a web interface)
  * MK: Can we perhaps dump it to a simple text file in the meantime?
    * AC: Should be easy to implement, potential as comments
  * AC: Feedback on new feature, given a function report all the global symbols that are used
    * The image generates but there are some quirks
    * When scanning the global data, we often end up in compiler generated symbols (e.g. variables from macro expansion)
      * Example is the warn once macro, which has an internal variable, it gets renamed by the compiler each time
      * These are usually not very interesting to a safety analysis
    * Should we just ignore these variables?
      * They demonstrate big coupling between the function and some common global variables
    * JN: Could we strip it from the image?
      * AC: Don't want to alter the binary, but want to filter it out
    * MK: Filtering it out makes sense to me
      * Likely still have to provide a rationale for why it can be ignored but could make better visualizations
  * AC: __key.11 is a bit of a bug where you can have duplicate symbol names
    * Several scenarios where symbols are duplicated
      * Same address corresponding to different symbol names (__key.11)
        * This is the structure that helps manage lockdep (lock subsystem debugging)
        * When lockdep is not enabled, the symbols stay but they are of size 0, so you get same address
        * Just pushed a [commit](https://github.com/elisa-tech/ks-nav/commit/2b8cbf54c5f48d406a02116d4edca30eb1fdbeab) with hacky way to resolve this problem
        * [Blog post](https://carminatialessandro.blogspot.com/2024/05/investigate-obscure-kernel-symbols.html) which explains in detail
    * You can compare the binary to see if they are the same
    * If you enable lockdep, there is no problem because those symbols no longer have size 0
    * MK: Can we just throw out size 0 symbols?
      * AC: Considered this, currently using addr2line, would need to switch DWARF parsing and there is a performance issue with this
      * Would probably push a single run into the 15-20+ minute range
    * MK: We should write down the method of enabling lockdep as a workaround
      * Don't love this because it's now not the same binary, but if you are only using it for analysis
      * AC: Right debug symbols can be stripped but config change adds code and data to the binary so it's now different than production

## Round Table

## Action Items

* [ ] Matt/Jeannette: Talk about possible addition of complexity metrics
* [ ] Jeanette: Add notes to documentation setup
* [ ] Matt/WG: Understand how we can engage Vertical Groups (Automotive, etc.) so we have real examples of how to use tools
* [ ] Matt: Bring up engagement (present to vertical groups? blog post? presenting November summary meeting) at the TSC
* [ ] Matt: Contact Sudip/Lukas to pull together documentation on patch submission

## Closing
