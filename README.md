# ELISA Tools Working Group

The Tools WG evaluates, designs, and implements tools that assist in enabling Linux in safety applications.

## Interact

* [Mailing List](https://lists.elisa.tech/g/tools)
* [Discord](http://chat.elisa.tech/)

### Meeting Times

* [Calendar](https://zoom-lfx.platform.linuxfoundation.org/meetings/elisa?view=month)
  * Look for the "Tools WG Meeting"
  * Click on the entry and select "Register" to get an invite.

## Our Work

### Tools

* [BASIL](https://github.com/elisa-tech/BASIL)
  * BASIL is a tool for developing and managing work items such as requirements, test specifications, test cases, justifications, while building a traceability matrix that connects these artifacts and their relationships. It also provides test execution support, allowing test results to be linked back to the relevant work items and traceability relationships for end-to-end verification and coverage.
  * BASIL Instance: http://elisa-builder-00.iol.unh.edu:9056/ 
* [ks-nav](https://github.com/elisa-tech/ks-nav)
  * A static analysis / reverse engineering tool targeting elf executables with DWARF information and source code, specialized on the Linux kernel. It provides information on functions, data and call trees. It is used for static code analysis, safety analysis and more. 
* [DeltaKernel](https://github.com/elisa-tech/delta-kernel/)
  * Kernel change impact analysis tool which creates visualization of kernel differences between versions
* [stress-ng](https://github.com/ColinIanKing/stress-ng)
  * stress-ng is the leading HW and SW stressing system for Linux. It is developed by Colin King and is partially supported by ELISA.
* [cregit](https://github.com/cregit/cregit)
  * Cregit is a tool for analyzing Git repositories and generating HTML views that show who contributed which parts of the source code, using token-level analysis to produce more meaningful blame information. It processes repository history, maps commits and authors, and produces browsable visualizations of code contributions, making it useful for studying code ownership and developer contributions over time.

### Kernel Static Analysis

* CodeChecker Instance: [https://elisa-builder-00.iol.unh.edu:8001/](https://elisa-builder-00.iol.unh.edu:8001/)
* Syzkaller Instance: [https://elisa-builder-00.iol.unh.edu/syzkaller/](https://elisa-builder-00.iol.unh.edu/syzkaller/)
* Syzkaller-next Instance: [https://elisa-builder-00.iol.unh.edu/syzkaller/](https://elisa-builder-00.iol.unh.edu/syzkaller/)


### ELISA CIs

* [ELISA Automotive WG meta-elisa CI](https://gitlab.com/elisa-tech/meta-elisa-ci)
  * Yocto build of AGL profile for Automotive WG
* [ELISA Automotive OpenQA CI](https://openqa.qa.codethink.co.uk/tests/6312)
  * Verification test of Automotive CI products via OpenQA
* [ELISA System WG CI](https://gitlab.com/elisa-tech/systems-wg-ci)

## Governance

  The Tools WG operates under the guidance of the ELISA Technical Steering Committee ([TSC](https://elisa.tech/about/tsc/)). It is headed by Luigi Pellecchia from Red Hat and co-hosted by Alessandro Carminati from NVIDIA.

## External Links

* [ELISA Home](https://elisa.tech/)
