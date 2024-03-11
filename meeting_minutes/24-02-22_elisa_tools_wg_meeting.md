
![logo](logo_elisa_small.png)

# ELISA Tool Investigation & Code Improvement Working Group

## Date: 23-02-21

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
* Shefali Sharma
* Sudip Mukherjee (CodeThink)
* Matt Weber (Boeing)

### Attended in the past

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

* 27 Feb 2024 [AvioSE'24](https://aviose-workshop.github.io/) in Linz, Austria
* 16-18 April 2024 Open Source North America in Seattle, Washington
* June DevConf Czech Republic

## Agenda Items

* Review README.md updates. Additions?
* BASIL topics
* ks-nav topics
* Static Analysis in Open Source SW
  * Continuation on of mixed static/dynamic analysis discussion
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
* ELISA CI
  * How can we contribute to / expand the ELISA CI?
* Engagement
  * How do we increase engagement with this group?
  * How do we directly tie our work to Vertical WGs?
  * How do we directly help maintainers?
  * How do we engage on peoples *actual* daily problems?

## Discussion Notes

* README.md
  * Added syzkaller instances
  * Added CI instances (Automotive, Systems, etc.)
* BASIL Instance Setup
  * Was able to connect to the server and build containers
    * Still need to open the port correctly
  * Deployment should be straightforward from this point on
  * User management implementation is in-progress
  * Working in the OSEP WG to find a real use-case to populate
  * LP: Did an overview of BASIL w/ Xen project
    * Have not received any feedback from them yet
* How do we get more folks involved in the BASIL/ks-nav development?
  * LP: We do have a list of open issue that folks
* ks-nav
  * AC: Allocating some more time to ks-nav soon
    * Concentrating on the web interface with near-term effort
  * AC: Have been some drafts of the web interface, but the graph navigation isn't great
    * Works well if there is a small graph, but isn't the case with kernel
    * LG: Can we just replace the just the visualization piece
      * AC: Unfortunately, not sure it is that simple
      * Want to use the SVG visualization that already exists
    * MK: Is there anyway to isolate graphs down to pieces you are interested in
      * AC: Never get the full graphic, we're always starting from a symbol (typically a syscall)
      * Even in this isolate uses, you still end up with hundreds/thousands of nodes
      * Even getpid(), a very simple syscall, has hundreds nodes because of locking mechanism
      * MK: can we filter out the locking mechanism
        * AC: Yes, ks-nav already has this, after/before filters for certain functions
        * Also supports regex for filtering
  * MK: We should think about how what applications Xen might use ks-nav
    * This collaboration potentially seems very positive
    * AC: ks-nav really only needs the binary
    * AC: We would just need to disable kernel specific features.
* Topics for the Workshop in June?
  * MK: Very good spot for hashing out collaboration w/ vertical WGs
  * LP: Conversation w/ the SPDX WG (for export features/change impact analysis type feature)
  * MK: Deep dive on mixed dynamic/static analysis (previously AC/LB discussion)
  * MK: Other static analysis violations to contribution
  * LP: Status of the WG
  * Others?

## Round Table

## Action Items

* [ ] Matt/WG: Understand how we can engage Vertical Groups (Automotive, etc.) so we have real examples of how to use tools
* [ ] Matt: Bring up engagement (present to vertical groups? blog post? presenting November summary meeting) at the TSC
* [x] Matt: Model wg-tools README.md after wg-automative to educate newcomers quickly
* [ ] Matt: Contact Sudip/Lukas to pull together documentation on patch submission
* [ ] Qasim: Explore the open source static analysis tools used by kernel
* [ ] Qasim: Understand clang static analysis tools (clang-tidy/clang-analyzer)

## Closing
