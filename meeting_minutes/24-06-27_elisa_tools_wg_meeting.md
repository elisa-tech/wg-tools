
![logo](logo_elisa_small.png)

# ELISA Tool Investigation & Code Improvement Working Group

## Date: 24-06-27

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
* Luigi Pellecchia (Red Hat)
* Jeannette N. (Boeing)
* Matt Weber (Boeing)
* Shefali Sharma (Nextleap Aeronautics)
* Yizhen Zhang (Boeing)
* Alessandro Carminati (Red Hat)
* Sudip Mukherjee (CodeThink)
* Muhammad Qasim (Seimens)

### Attended in the past

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

* 29-2 July-Aug, AIAA Aviation Forum (Las Vegas, USA)
* 13-15 June, DevConf Czech Republic (Brno, Czech Republic)
* 16-18 Sept, Open Source Summit Europe (Vienna, Austria)
* 18-20 Sept, Linux Plumbers Conference (Vienna, Austria)
  * Safety Critical Microconference
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

* BASIL Tour
  * Permissions
    * Public instance, everything can be viewed by guests
    * You can register for an account, and you will default to guess (only leave comments)
    * Admin can upgrade you to "User" who can create create/edit other items
    * Permissions on a per Software Component level
  * Creating a component / API
    * Under componments you have APIs
    * These APIs can be linked to manpages / source code etc.
    * Can specify and map software requirements as well
    * Justifications ensure completeness of analysis
  * Upcoming work: Adding document, mapping view that pulls together SW Spec, Requirement, and source code
  * Mapping a justification to a manpage
    * Can map sections of a document against sections of specify
  * Goal of the tool is to assess the impact of changes to certain work items
  * Tracks version and approval of basically everything
    * Version format (v1.1)
    * First number is the version of the relationship
    * Second number is the work item number
    * Stores full history of changes
    * Can leave comments on items
    * Items can be approved
  * Creating an example requirement and test
    * Example of creating requirements and marking coverage of less than 100%
    * Mapping test cases to requirements
    * Can run tests in a Fedora container from BASIL
    * To run tests you need to use a test management ool
      * Some examples in the BASIL repo
    * Can run via SSH or run a container
  * Can sign up for notifications to changes of items
  * Can store ssh keys in BASIL for use in running tests
  * Can check the impact of change in the specification
    * Changes will show "unmatched work items at the bottom of the page"
  * Coverage percentages are calculate for all items and roll up
  * Demo of getting a test result with results, logs, etc.!
  * SM: Is SDPX working now?
    * LP: It's partially implemented, export is somewhat working
    * Import is not yet working
* Kernel Change Impact Tooling
  * MW: Summer intern project
  * MW: Goal is to put forth an RFC of an open source change impact tool for the kernel
  * How do we get the subset of what we have actually configured and then compare between two tags that share history?
  * Run the script, inputs are two git tags
  * Renders a HTML report of the changes in great edetail
  * Changes are segmented into .c files and .h files
  * Example of comparint v5.15 to v5.15.100
  * Tags link to the public repos
  * Shows each file and the patch, links go to files directly
  * Hover over the line shows the details of the author, change, etc. 
  * Link to the specific commit that changes that line
  * Allows you to quickly get to the git history that change that item
  * Only compares files that are relevant to the paritcular compilation
  * AC: Looking to show the user differences between to commits the kernel
    * Show how changes impact other modules via global data etc.
    * MK referenced a similar effort
    * Is this the effort Matt K. was reference?
  * MK: Yes! Wondering if we can tie these together somehow. They are approaching the same problem from different angles
  * AC: These are different angles, one is the binary and one is the source
  * MW: We're using a few different angles
    * You can figure out what objects are going to be built
    * To figure out headers involves we had to mdofiy fix depends
    * Also doing some analysis of the kconfig settings to figure out what is impacted
    * Not sure we will get to the last step
    * Would be really interesting to compare the last stage to the binary
  * LP: Is it our charter to get the vertical groups to use these tools?
    * MK: I have a longstanding AI to figure out how to get the groups working together

## Round Table

## Action Items

* [ ] Matt/Matt/Jeannette: Talk about possible addition of complexity metrics
* [ ] Jeanette: Add notes to documentation setup
* [ ] Matt/WG: Understand how we can engage Vertical Groups (Automotive, etc.) so we have real examples of how to use tools
* [ ] Matt: Bring up engagement (present to vertical groups? blog post? presenting November summary meeting) at the TSC
* [ ] Matt: Contact Sudip/Lukas to pull together documentation on patch submission

## Closing
