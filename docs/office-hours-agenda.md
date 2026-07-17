# Office Hours Agenda Items

Feel free to drop in any agenda items for the monthly office hours.

## August 2026 (TBC)

1. Software Optimisation Guide - Philip/Peter

## July 2026

1. glibc status - Peter
2. [Toolchains Proposal around Optimisation Tuning Options](https://riscv.atlassian.net/wiki/spaces/SSNJ/pages/2033909774/Toolchains+and+Optimisation+Guidance+Options) - Sam
3. Software Optimisation Guide Status - Philip
4. What's going on with the group mergers - Philip/Peter

## June 2026

1. Update on RP021 from Luke Lau.
2. Porting Small SIMD to RVV. - Craig
3. Pre-commit and Fuzzer status - Jeff

## April 2026

1. Did anyone nominate for chair of this group?

    1. JL – my understanding is Peter Bergner has self-nominated to lead this group for the next year.

2. Update on LLVM buildbots: we have enough funding from RISE to run them until December

## March 2026

1. 2026-1H Priorities still need cleanup.
2. FYI, returning a small struct or vector less than XLen bits on clang generates unnecessary zero extend to zero the upper bits of a0.
3. Philip Reames update on RFP21, vectorizer contract with Igalia for LLVM. Was not discussed at board meeting on Feb 12. There will be an email board vote, no firm ETA.
4. gcc and LLVM CI on build farm. Mainly ran by Rivos. Looking for volunteers to step up to maintain this infrastructure. If not volunteers, will probably plan to shut down. If you know anyone who is interested send to Developer Infrastructure Group. LLVM fuzzer also needs volunteers to triage.

    1. Philip will get dates of when contracts will expire.
    2. LLVM fuzzer reporting may have stopped in November. Is this machine still running? Philip will get summary.

5. Craig asked if anyone is interested in P extension.

    1. 32-bit vectors on RV32 and RV64 can codegen without crashing LLVM.
    2. Intrinsic wrapper over inline assembly created.
    3. Paul mentioned RISE may be starting a baremetal group that might be more interested in P.

6. Chip asked about OpenBLAS patch blocking GEMM. Maintainer pushing back as being too intrusive due to repacking data for cache. Seems to help for super large sizes, but not smaller sizes. Patch listed as being from RISE. Is it from AI/ML? Min says there is an ongoing effort, but he didn't know the details.

    1. gcc 1.7x slower than llvm on one GEMM kernel. LMUL=1. Measured on BananaPi.

## February 2026

1. Need a new chair for this group.
2. Is this a good meeting time? Would we get more participation from Asia at a different time?
3. Need to create 2026-1H Priorities
4. llvm.clmul intrinsic introduced, with generic lowering: [https://github.com/llvm/llvm-project/pull/168731](https://github.com/llvm/llvm-project/pull/168731) – Craig is working on RV-specific follow-ups
5. Proposal to make zvknha a subset of zvknhb: [https://github.com/llvm/llvm-project/pull/178680](https://github.com/llvm/llvm-project/pull/178680)

    1. isa-manual PR [https://github.com/riscv/riscv-isa-manual/pull/2635](https://github.com/riscv/riscv-isa-manual/pull/2635)
    2. There's a similar issue with Zbc/Zbkc. [https://github.com/riscv/riscv-isa-manual/issues/2523](https://github.com/riscv/riscv-isa-manual/issues/2523)

6. Proposal to lower blends earlier in VPlan: [https://github.com/llvm/llvm-project/pull/171851](https://github.com/llvm/llvm-project/pull/171851)
7. llvm.vector.splice.{left,right} work ongoing: [https://github.com/llvm/llvm-project/pull/179219](https://github.com/llvm/llvm-project/pull/179219)
8. GCC performs over 50% better than LLVM on hmmer SPEC2006INT. To prioritize speculative task of enabling LDist by default?

    1. Hmmer is known to require last iteration peeling and loop distribute. [https://groups.google.com/g/llvm-dev/c/jXrYmjjPhNE/m/xePYf7drBgAJ](https://groups.google.com/g/llvm-dev/c/jXrYmjjPhNE/m/xePYf7drBgAJ)

9. GCC performs 30% better than LLVM on xalancbmk SPEC2006INT. To investigate.
10. RP21 [https://lists.riseproject.dev/g/RISE-Compilers-and-Toolchains-WG/message/118](https://lists.riseproject.dev/g/RISE-Compilers-and-Toolchains-WG/message/118)

## January 2026

1. Need a new chair for this group.

## December 2025

1. Open: building whole system with vl=512 for TT Blackhole
2. LLD issue: [https://github.com/llvm/llvm-project/issues/168308](https://github.com/llvm/llvm-project/issues/168308)
3. LLVM is about to make Spacemit X60 as default scheduling model: [https://github.com/llvm/llvm-project/pull/167008](https://github.com/llvm/llvm-project/pull/167008)

    1. Rationale: this is better than no scheduling model, though will cause performance changes on (lots of) code that doesn't set mcpu/mtune
    2. X60 was selected as a common implementation, intent is to have a generic scheduling model at some point; X60 tuning currently produces decent results on a variety of implementations

4. LLVM is adding a new mtune syntax: [https://github.com/llvm/llvm-project/pull/168160](https://github.com/llvm/llvm-project/pull/168160)

    1. Works as "base scheduling model + modifiers", Arm has something similar in principle, though RISC-V syntax is simpler
    2. Discussing to standardize across both compilers: [https://github.com/riscv-non-isa/riscv-toolchain-conventions/pull/122](https://github.com/riscv-non-isa/riscv-toolchain-conventions/pull/122)

5. RVI proposal for software optimization features: [https://riscv.atlassian.net/wiki/spaces/TOXX/pages/585400366/Optimization+Directives+Fast+Track+Approval+Request](https://riscv.atlassian.net/wiki/spaces/TOXX/pages/585400366/Optimization+Directives+Fast+Track+Approval+Request)

    1. There's overlap with tune features, which we should raise as a feedback (Min)
    2. Maybe revisit next month

6. AVL vs LMUL in the optimization guide: should it have different cases for statically known vs dynamic AVL?

    1. [https://gitlab.com/riseproject/riscv-optimization-guide](https://gitlab.com/riseproject/riscv-optimization-guide)
    2. Return to at later point

## November 2025:

1. NASA HPSC and compilers

## October 2025:

1. [https://lf-rise.atlassian.net/wiki/spaces/HOME/pages/8591091](https://lf-rise.atlassian.net/wiki/spaces/HOME/pages/8591091)

    1. Jeff suggests to close it, upstreaming never started
    2. Min Hsu is looking at if-conversion and is interested to understand the example better, particularly how it aligns with scheduling model.

2. Potential follow up to CT_01_007 CRC Optimization (LLVM) - add CLMUL intrinsic and produce CLMUL instruction for CRC/GHASH

    1. Craig: Zbc is not part of any profile, vector version is in Zvbc (64-bit), Zvbc32e is not yet ratified - question about available implementations

3. LLVM loop distribute
4. Philip: potential item is follow up to non-trivial rematerialization in LLVM (Luke Lau just finished a change)
5. LLVM shrink wrapping

    1. MIR changes landed for Mikhail patch
    2. Philip: long term register allocation driven solution might be better approach, but likely would require a change to reg allocator core logic
    3. Petr: there is a fix to benchmark miscompiles in Mikhail's repo
    4. Philip: Using register scavenger for shrink-wrapping is not a good idea, we likely need to address that eventually

6. Philip: LLVM register scavenger doesn't yet support remobilization, but it would be very easy to add if there is a motivating example
7. LLVM: addressing spilling for stack frames that don't fit into 12 bits of address

    1. cactuBSSN in SPEC is affected
    2. Philip: that creates catastrophically bad spill code
    3. Jeff: GCC has a hook for reloading a memory address
    4. Philip is interested in looking further into it

8. glibc patch for string and memory functions to use generic RVV VLA is in review
9. A few people are interested in converting Neon code to RVV, maybe a work item for 2026

## September 2025:

1. Originally planned HPSC (see October), but logistics didn't work out.
2. Philip Reames: LLVM EVL vectorization enabled by default. Ramping down on open items. Call for opportunities for improvement preferably with impacted workload.
3. Peter Bergner added static trampoline support for RV32 and RV64 to libffi. Gets rid of executable stack. Merged upstream, not in a release yet.
4. Philip Reames asked about vectorized versions of mem* functions in glibc. These were proposed several years ago and are still not merged.
5. Ruinland asked if anyone had tried Qualcomm's eld linker.

## August 2025:

1. LLVM vectorizer plan

    1. EVL vectorization would be enabled by default, patch landing soon
    2. Todo: segmented loads and stores in vectorizer (backend can produce it)
    3. WIP: strided load support, non ^2 length support - cost model, non-1 element stride
    4. WIP: SLP vectorizer: non ^2 support, loop-aware cost model, copyable elements
    5. Support of uncountable loops, fault-first-only loads
    6. Support division using vp intrinsics
    7. Multiply reduce with scalable vectors (currently uses fixed)
    8. Worth noting fault first loads RFC: [https://github.com/llvm/llvm-project/pull/151300](https://github.com/llvm/llvm-project/pull/151300)

2. LLVM backend

    1. Fault first only loads: [https://github.com/llvm/llvm-project/pull/128593](https://github.com/llvm/llvm-project/pull/128593)

3. GCC

    1. VLS vectorization generates unnecessary spills - WIP
    2. Improvements to zero-stride support
    3. Vineet went over [CT_00_057 2025-2H - Improve Scalar code generation for cactuBSSN](https://lf-rise.atlassian.net/wiki/spaces/HOME/pages/597196813)

4. Items moving to 2H - for LLVM Craig and Petr to take that offline, Jeff is out this time
5. Other updates

    1. GDB has proposed vector register support
    2. Peter Bergner is adding static trampoline support to libffi, needs to test it in 32-bit environment

## May 2025:

1. Peter Berger joined the WG via Tenstorrent
2. GCC notes (Vineet, Jeff Law is out)

    1. Spacemit X60 cost model
    2. FRM save-restore, first set of patches posted

3. LLVM notes

    1. CT_01_012 - Improve shrink-wrapping (LLVM), Petr Penzin to join the review effort
    2. Igalia landed Spacemit X60 model, with significant performance improvements
    3. Vectorizer indvar changes, EVL vectorization WIP (somewhat slow), tail folding, zvqdot
    4. Craig Topper is working on load-store pairs for RV32 - WIP for fp64, can be done for structs, needs more cost model

4. Exposure to more software

    1. BPI dev Gentoo images - official landing page would be a good idea
    2. Exploring a distro build with LLVM
    3. Rust ecosystem still has some hiccups with cross builds
    4. Android and Fuchsia are WIP, there is a LLD linker bug exposed by Android builds which we don't yet have a line of sight on fixing

## Apr 2025:

1. Petr Penzin taking over as WG lead! Thanks a ton for stepping in

    1. Petr's decision on meeting time and such going forward
    2. Obviously I'll provide whatever support I can to Petr

2. RP006/RP006A Extension

    1. Not surprisingly Igalia is doing fine work, so we'd like to keep them engaged
    2. Also provides ongoing resources to LLVM builders/CI system they've set up
    3. Seems like we should take direction from Philip, Craig, etc. If they want it to renew, then I'm supportive
    4. Do we want to expand any areas? For example, transition from icount testing to BPI performance testing?

3. Need to update project pages for both LLVM and GCC. We're halfway through 1H2025!
4. Starting to ponder if we're going to have a RISC-V GCC coordination branch again this year

    1. It's certainly proven useful, though we don't have as many big ticket items landing now
    2. But we have lots of smaller stuff
    3. It's a fair amount of work
    4. Will discuss in patchwork meeting tomorrow AM

5. GCC notes

    1. Synopsys fusion work looks good from a static standpoint, but hasn't been performing well on design

        1. Could well be a design problem our fusion support or misunderstanding of docs
        2. It'd probably be useful to run this on silicon, but we don't have fusion info on the SpacemiT chip. I've reached out to SpacemiT, but haven't heard back
        3. Lower priority task going forward

    2. mvconst_internal removal

        1. Basic idea is to hook the logical expanders and generate more sensible code there
        2. Will likely need some bridge patterns to deal with combine limitations
        3. Will also likely need to improve support for REG_EQUAL notes in combine
        4. POC to prove viability. So far nothing screaming "this won't work"

## Mar 2025:

1. Elections coming up. Would love to see someone else step into the leadership role. Obviously I'd still be around to help, but with transition and with info on what's going on in the GCC space in general and what Ventana's doing across both toolchains.
2. RFP Status. I haven't had the time to follow-up on any of this stuff.
3. llvm-20 release in flight (RC stage). We probably should get together RISC-V highlights for the wider audiences. Any RISC-V specific concerns that need to be addressed?
4. gcc-15 release in flight (regression bugfixing, ETA May). No major concerns, though we do have some smaller fixes that need to get wrapped up. Mass Fedora builds just starting up, so wouldn't be surprised to see issues start showing up shortly
5. Stuff on the radar for GCC post gcc-15

    1. Synopsys fusion work looks interesting

        1. Discussed in GCC RISC-V Coordination meeting last week.

    2. Looking at notable changes in extension removal that might really help our ability to utilize Zbs better. Under investigation

        1. Key issue is we have sign extensions in the RTL for various ops. Largely due to how we deal with sub-word access in GCC.
        2. That sign extension makes more bits appear live than we really care about from a source standpoint
        3. Thinking we might be able to use ext-dce to convert those extensions to subregs, much like we do simple sign extensions.

            1. May require a lot more patterns
            2. Perhaps push the subreg into the operands

    3. Conditional move improvements

        1. Use standard API to extend comparison operands allowing more cases as a result.
        2. Use standard approaches for partial word destinations (store into full word temporary and narrowing subreg to final dest)

## Feb 2025:

1. Updated GCC pages for 1H2025

    1. Obviously feel free to add more stuff
    2. Need similar effort for LLVM pages

2. Fortran in LLVM needs a page
3. Update on glibc mem*, str* work
4. Update on x264 findings
5. Project plans going forward (new election in the spring, who wants to step up?)

## Dec 2024:

1. vmvXr situation

    1. GCC is just treating this as a bug and has already been fixed
    2. Codegen impacts are expected to be trivial, requires vector regs to be live across calls to trigger which doesn't happen with the default ABI.
    3. LLVM is still deciding what to do
    4. May also be clarified at the ABI level

2. gcc-15 development window closed

    1. Most of Robin & my work has been submitted and is working its way through reviews
    2. Mariam (RAU)'s CRC work had been submitted well in advance, bulk of work is in

3. LLVM

    1. Separate shrink wrapping integrated upstream
    2. Stack clash protection being updated in response to Craig's feedback

4. glibc:

    1. I still need to start pushing the mem* and str* patches

5. BPI quirks

    1. Process hangs have been seen by others (golang project in particular), it's been reported and is in both the golang bug tracker and a spacemit tracker
    2. Rebuilt kernel (6.6.XX) with a modern GCC (Ventana's internal release, so gcc-14 + improvements) and I haven't seen a hang since!

## Nov 2024:

1. What to do about the vmvXr situation

    1. Does it depend on vtype or not?
    2. If it does, then that implies we'll need a vsetvl at the start of each function with vector code
    3. Unclear at this point

2. GCC 15 development window closing rapidly, will transition into bugfixing mode in ~2wks

    1. Key is that any new development must be posted for review by the deadline (Nov 17 IIRC)
    2. Robin and I have various internal patches to submit, mostly around vector performance for x264
    3. Patches already submitted have already met the deadline and are thus eligible for inclusion even if they're going through revisions
    4. Nov & December will be "general bugfixing", so any bug in bugzilla is eligible for fixing, though we reserve the right to reject things that are too risky or gaming the system
    5. Sometime in Jan we transition to regression fixes only

3. LLVM

    1. Misha's separate shrinking wrapping posted upstream for review. Should notably help 500.perlbench and 502.gcc
    2. Stack clash work is done, but engineer is engaged on other stuff right now

4. Notable work that should be landing shortly

    1. ifunc'd mem* and str*. Andreas S. ACK'd memset with a minor fix, so I'll be submitting the rest shortly

        1. Based on work from SiFive and Rivos engineers
        2. My involvement is just the ifunc wiring

    2. CRC optimization needs minor fixes

        1. One chunk of generic code is goofy and apparently causes regressions for risc-v when fixed
        2. Looks like we need a way to check for zbkb dynamically in dejagnu harness. Probably zbc as well

    3. Function multi-versioning for GCC
    4. Various minor changes to improve vector codegen, scheduling, etc.

5. PSAs. BPI F3 in my tester, bootstrap & regression test every 2-3 days

    1. Right now it's always the same config, but considering alternating -march switch testing to broaden coverage (zvl)
    2. Experiencing process hangs, which look like kernel issues

## Aug 2024:

1. Reminder of GCC patch coordination meeting every Tuesday (2:30pm UTC)
2. GNU Cauldron Prague (Sept 14-16)
3. RV Summit NA in Oct
4. RFP009 is out for bidding (LLVM performance investigation)
5. Stack Clash (GCC & LLVM)
6. CRC Work (GCC)
7. VRULL's work on narrow store feeding wider load

## July 2024:

1. RFP008
2. 2H2024 projects – especially LLVM
3. GCC Coordination Branch Discussion

    1. Keeping RISC-V backend in sync with trunk
    2. Limited cherry-picking of generic code (when it's known to help RISC-V in meaningful ways)
    3. Question we'll be discussing in patchwork meeting – late-combine changes, to include or not

## June 2024:

1. Unaligned vector loads/stores status
2. Constant Synthesis revamp. Largely done for GCC. Need to see if there's any significant cases for LLVM after Craig's recent fixes
3. Shrink Wrapping for LLVM

    1. Misha is diving into the EH issues and xz performance regression

4. Stack clash, later than expected, but still moving forward

    1. LLVM – Major development appears to be done. Porting testcases from other archs to rv64 did expose one problem that Raphael is diving into now
    2. GCC – Going through internal review now

5. RFP008 – Will go through review this week
6. Flang – need a project page for LLVM. Do we want to propose this as a contractor project?

## May 2024:

1. Jeff Law: Introduction
2. Jeff Law: Constant Synthesis (both compilers)

    1. Jeff to get Craig examples of commonly missed cases (bseti, only consistently weak idiom for LLVM)
    2. GCC needs much more work (bseti, shNadd, "uw" forms, duplicated high/low)
    3. Both compilers probably need better support for pack)
    4. Concerns about overall structure of code, but may be inherent in the problem

3. Jeff Law: Shrink Wrapping (LLVM)

    1. Just looking for high level sanity check right now
    2. Doesn't work with EH, but that's got to be an implementation detail, get the CFI notes right and it should work
    3. Interactions with push/pop?
    4. How many new code paths are showing up? Is the code getting harder to reason about?

4. Jeff Law: Stack clash status (both compilers)

    1. External review probably 1-2 weeks out
    2. Testing with scanner to find vulnerable binaries, then test after rebuilding with new compiler

5. RFP008

    1. New language. Jeff to review & comment
    2. Launch LLVM equivalent RFP (ADLR?)

6. ADLR & Jeff to circle back with Baylibre folks WRT LTO (they think it doesn't work)
7. IFUNCS. How to handle case where kernel claims V, but it's actually V0.7?

    1. We can't control where the kernel for these SBCs come from
    2. We should expect those kernels to occasionally mis-represent the hardware
    3. Make glibc, gcc & llvm ifunc resolvers be reasonably defensive for these cases
    4. Avoid crashing user code in these scenarios, bad user experience
    5. Fallback to sensible default when the syscall isn't available

8. Frame pointers vs Zcmp – ABI implications and desire to unwind without CFI tables

    1. Known issue at the RVI level
    2. Distros (Fedora, Canonical, etc) likely aren't going to care. ABI for them is set, and they're likely rv64 only
    3. Would like to see ABI or extension fixed, but if that's not possible, they may do a vector extension.

9. Flang

    1. new vs old flang
    2. General need to fix flang to be cross-buildable – contractor proposal

10. LLVM Testing proposal

    1. Desire to add another configuration, who is the coordination point for this contract?
    2. Expectation is cost delta should be small (initial bring-up and ongoing resources)
