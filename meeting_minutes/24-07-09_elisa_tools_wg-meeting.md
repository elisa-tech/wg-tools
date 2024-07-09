
![logo](logo_elisa_small.png)

# ELISA Tool Investigation & Code Improvement Working Group

## Date: 24-07-09

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
* Yizhen Zhang (Boeing)
* Matt Weber (Boeing)
* Muhammad Qasim (Seimens)

### Attended in the past

* Luigi Pellecchia (Red Hat)
* Jeannette N. (Boeing)
* Shefali Sharma (Nextleap Aeronautics)
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

* 13-15 June, DevConf Czech Republic (Brno, Czech Republic)
* 16-18 Sept, Open Source Summit Europe (Vienna, Austria)
* 18-20 Sept, Linux Plumbers Conference (Vienna, Austria)
  * Safety Critical Microconference
* 28-29 Oct, Open Source Summit Japan (Tokyo, Japan)

## Agenda Items

### Current Topics

* Announcements
  * Plug stress-ng talk & short discussion
* Kernel Change Impact Tooling
  * Patch cover letter and demo tooling
* ks-nav topics
* BASIL topics
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

* ks-nav/Kernel Change Impact Analysis Overlap
  * MW: What would a good first step be?
  * MW: Comparison of what the change impact tool believes at source time vs. what actually ends up in the build?
  * MW: Filtering functions at a file level of what is activated
    * Use the binary to filter the functions
    * MK: Could also use the "post pre-processed" source (`-E` compiler flag)
  * MK: Could we use the "post pre-processed" source to allow hover over of the functions?
  * MK: Python used for the kernel change impact analysis?
    * YZ: Python + Bash
    * Python does the tokenization of metadata
  * ks-nav is mostly Go
  * MW: What visualizations are you think for the comparisons of two binary versions?
    * AC: Was thinking of something that was not a visualization
    * AC: Only attempting to provide the impact of a particular patch
  * AC: We could use the .dot files to look at the differences between tags
  * MW: If I build a superset function list, can I compare that to what is built via ks-nav?
    * AC: ks-nav is not aware of the config it just works on the binary
  * MW: Can I just get a global function list
    * AC: Yes
  * ks-nav is really designed to create the call tree, but all the data is there
  * MW: So if  wanted to contribute a version of the tool and integrate it with that database it would fit the model
    * Yes
* MK: stress-ng has a lot of API testing functionality (in addition to the things we normally think of)
  * Can we use this as the basis of adding kernel testing
  * Kate specifically asked Colin if we could formalized the testing
  * He sounded open to at least discussing it
* AC: Gave a presentation at the SOAFEE (automotive consortium) forum
  * Talk seemingly went well and we gained a bit of interest
  * Past presentations got basically no interaction
  * ks-nav presentation there was actually some relevant questions
* QM: Patch that was sent to the mailing list has already been accepted by kernel community

## Round Table

## Action Items

* [ ] Matt K/Matt W/Jeannette: Talk about possible addition of complexity metrics
* [ ] Jeanette: Add notes to documentation setup
* [ ] Matt/WG: Understand how we can engage Vertical Groups (Automotive, etc.) so we have real examples of how to use tools
* [ ] Matt: Bring up engagement (present to vertical groups? blog post? presenting November summary meeting) at the TSC
* [ ] Matt: Contact Sudip/Lukas to pull together documentation on patch submission

## Closing
