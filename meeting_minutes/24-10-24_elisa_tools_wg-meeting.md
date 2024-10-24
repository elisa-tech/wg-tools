
![logo](logo_elisa_small.png)

# ELISA Tool Investigation & Code Improvement Working Group

## Date: 24-10-24

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

### Attended in the past

* Sudip Mukherjee (CodeThink)
* Chuck Wolber (Boeing)
* Jeannette N. (Boeing)
* Matt Weber (Boeing)
* Shefali Sharma (Nextleap Aeronautics)
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

* 28-29 Oct, Open Source Summit Japan (Tokyo, Japan)

## Agenda Items

### Current Topics

* Announcements
* Workshop Topics
  * Workshop Agenda is full of topics from individuals
* ks-nav topics
  * MR for documentation: https://github.com/dnjean/ks-nav/tree/demo-upload
* BASIL topics
* DeltaKernel topics
  * Initial work is in and on main
* stress-ng Investigation
* Boeing/UIUC llvm-cov
  * Lots of positive feedback from LPC audience
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
* Linux Plumbers Conference Discussion
  * AC: Three different talks at plumbers, presentations went well
    * Wasn't successful in convincing kernel community to take his solution on an unrelated project
    * ks-nav talks were in the Safety micro-conference
    * Safety micro-conference doesn't have a huge audience, but got several questions from new contacts
    * More attendance on the OSS side of the conference
  * LP: Talk to OSS Summit where there was a great audience
    * Presentations went well, received some questions/feedback/interest
    * Plumbers presented an application to syscalls
    * The interest was close to zero
    * Might have been in the wrong track to get the right audience
  * MK: Sharing the requirements discussion (Luigi was present for it and Gab P is working) (see blow)
* ks-nav Topics
  * General Update
    * Not much new
    * Starting to explore the indirect call problem
      * Approach is static analysis-ish
      * Can't do it purely in binary
      * Looking at leveraging llvm toolchain to generate the right data
      * Currently stuck, posting question the LLVM mailing list
        * https://discourse.llvm.org/t/detecting-struct-field-assignments-in-c-using-clang-cursor-api/82691
      * MK: Might be able to chat with the UIUC students who are leveraging llvm for coverage
  * MR Discussion
    * MK: JN left our team (and also the company) so reach out to MW or MK if we need to keep making updates
    * AC: Sounds good--haven't much time to dedicate it to it yet. MW was providing good comments as well
* BASIL Topics
  * General Update
    * Topic for the workshop about tracing external test results
    * Targeting KernelCI
      * Trigger a test in KernelCI and have BASIL have trace to the result
      * MK: How do you show that the kernel that ran in KernelCI is similar enough that you can say they are equivalent?
      * LP: Not sure, but a topic we could discuss
    * An issue was generated by a real user!
      * Minor problem but a real life problem to fix
  * Requirements discussion
    * MK: We should make sure that BASIL should be able to parse the template they come up with
    * LP: We should definitely stay plugged in to that conversation
    * AC: There was a discussion of adding it to checkpatch, but that was strongly rejected
      * Idea was that Tools WG would be responsible for creating a tool around this
      * For starting this effort, we would concentrate on sysfs since it's already partially documented
    * MK: Whatever tool is created it should be around validation of the data
      * So should it be an additional tool that is run after checkpatch?
      * AC: Yep that's right
    * MK: There were at least two threads around creating the template, we were able to connect those at the TSC on Wednesday
    * MK: Chuck was proposing something based on SDPX
    * LP: Think it's too early say but we will track it
  * Syscall example
    * Showing new syscalls section
    * There are ~360 syscalls that are parsed automatically
    * Showing an example of chmod coverage that is mapped
    * The process of mapping the manpage to the test coverage is pretty manual
    * MK: Where my head immediately goes because of the recent discussion is how this changes when we start adding requirements? (Realizing we are quite far away)
    * MK: To me, this is useful to highlight test cases that newcomers could write a test for and it could be a relatively small improvement someone could work on that.
    * LG: Was talking to several people about exactly that but no one explicitly volunteered
    * MK: Maybe you can take that argument to the larger OSS conference (understanding that we didn't get much interest from the maintainers themselves)
* DeltaKernel Topics
* KConfig Tools
  * AC: We talked about kconfig tools in the past
    * https://github.com/alessandrocarminati/kconfig-
  * Visualizes the dependencies of kconfig
  * AC gave a live demo of the tool

## Round Table

## Action Items

* [ ] Matt: Add link to the live instance of BASIL to the GitHub front page
* [ ] Matt: Add link to the kconfig visulization the GitHub front page
* [ ] Matt: Investigation leveraging stress-ng (send example for LP's talk)
* [ ] Matt K/Matt W/Jeannette: Talk about possible addition of complexity metrics
* [ ] Matt/WG: Understand how we can engage Vertical Groups (Automotive, etc.) so we have real examples of how to use tools
* [ ] Matt: Bring up engagement (present to vertical groups? blog post? presenting November summary meeting) at the TSC
* [ ] Matt: Contact Sudip/Lukas to pull together documentation on patch submission

## Closing
