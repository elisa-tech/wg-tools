
![logo](logo_elisa_small.png)

# ELISA Tool Investigation & Code Improvement Working Group

## Date: 24-01-14

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
* Matt Weber (Boeing)
* Carole Garrison (NASA Langley)
* Sudip Mukherjee (CodeThink)
* Luigi Pellecchia (Red Hat)
* Alessandro Carminati (Red Hat)
  
### Attended in the past

* Chuck Wolber (Boeing)
* Jeannette N. (Boeing)
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

## Agenda Items

### Current Topics

* Announcements
  * Matt will be on leave at some point this year
* December Workshop Discussion
* 2025 Objectives
  * What should they be?
* ks-nav topics
  * MR for documentation: https://github.com/dnjean/ks-nav/tree/demo-upload
* BASIL topics
* DeltaKernel topics
* stress-ng Investigation
* Boeing/UIUC llvm-cov

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
  * Matt will be on leave at some point this year
    * 
    * Luigi volunteered to run the meetings
* December Workshop Discussion
  * LP: Was there in person and everything was awesome
    * Presented new features in BASIL tieing test cases to req spec, etc.
    * Tracing and triggering to test in external test infrastructures
    * Supports GitLab CI, GitHub Actions, KernelCI
    * Can't trigger on KernelCI but can in other cases
    * Talk: https://www.youtube.com/watch?v=laCsZ3DusEc&pp=ygUOYmFzaWwga2VybmVsY2k%3D
  * MW: Chuck is envisioning to see the commit change trigger only specific test which they are tied
    * MW: Chuck isn't quite there yet, they are currently focused on the format
    * LP: As long as there is a test case tied to the req, there is an API we can use to show what is tied to that requirement and trigger tests
  * MK: How does does the kernel requirements conversation tie in with BASIL?
    * LP: We'll likely need to collect additional requirements fields outside of the source code
    * LP: If we want to create traceability to other artifacts we'll use BASIL
    * LP: BASIL already supports creating requirements from something in a file
  * LP: When requirements change, we need to reflect that in BASIL in 
  * LP: First req, going into the ftrace area (which Steve R. maintains)
    * https://github.com/torvalds/linux/blob/master/kernel/trace/ftrace.c
  * MK: Does ftrace already have testing in place that we could leverage?
    * https://github.com/torvalds/linux/tree/master/tools/testing/selftests/ftrace
  * MW: Nathan (llvm-kernel maintainer) was interested in getting the kernel data published
  * LP: We can try to setup the CI action before the requirement goes in
  * MW: Space Grade Linux Group has split out to have their own call (first call this Thursday)
    * Ramon/Ivan are co-leading that SIG
    * Initially focused on established a `meta-sgl` and rallying around delivering frameworks
      * Frameworks like fPrime, CFS, etc.
    * Less concerned about artifacts right
    * Will probably be reaching out to Sudip for CI for sgl
  * MW: Do we have more computer beyond the "free OSS project" limit for GitHub?
  * MW: Is this the actions workflow that is being used?
    * https://github.com/elisa-tech/BASIL/blob/main/.github/workflows/build.yaml
  * Sudip: We run a build in GitLab, GitHub actions will pull from the cache and therefore not require much computer
    * https://github.com/elisa-tech/BASIL/actions/caches
* 2025 Objectives
  * What should they be?
    * Req -> Test Case -> KernelCI Result -> llvm-cov coverage
      * Show a requirement (from the kernel design doc discussion) tied to a test cases
      * Tied to a KernelCI result, showing test coverage from llvm-cov
    * Setup CI which scraps latest kernel for requirements?
* ks-nav topics
  * MR for documentation: https://github.com/dnjean/ks-nav/tree/demo-upload
  * LP: Presented a workflow where ks-nav is integrated with ftrace to investigate critical paths in the source code that you can't easily understand with just the code coverage.
    * This was presetned on the first day, but AC has a recording of a practice run
    * https://youtu.be/YP8Eu0KzYv4
* BASIL topics
  * LP presenting at FOSDEM as part of the SBOM track
  * Would like to talk about this SBOM part next week
* DeltaKernel topics
* stress-ng Investigation
* Boeing/UIUC llvm-cov

## Round Table

## Action Items

* [ ] Matt: Add link to the live instance of BASIL to the GitHub front page
* [ ] Matt: Add link to the kconfig visulization the GitHub front page
* [ ] Matt: Investigation leveraging stress-ng (send example for LP's talk)
* [ ] Matt K/Matt W/Jeannette: Talk about possible addition of complexity metrics

## Closing
