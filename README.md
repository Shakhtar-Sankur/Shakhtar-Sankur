# Sankur Kundu

### NASA's collision-risk team, the European Space Agency, NIST, a Harvard professor, and twenty-three fixes merged by the people who lead the projects.

> **NASA Conjunction Assessment Risk Analysis (CARA)**, its Analysis Team on my two findings: *"your sampling space results indeed appear to be fully consistent with what we see in CARA operations"* · *"your time window results indeed appear to be fully consistent with what we see in CARA operations"* · [signed email from nasa.gov](https://drive.google.com/file/d/1dLeScUyhyjEL-Ipwn6sjNaJUHn1SIhZP/view), evidence pages 150–155
>
> **Prof. Vijay Janapa Reddi, Harvard University**, merging my lab into his Machine Learning Systems textbook: *"Merged, thanks @Shakhtar-Sankur. I reran the experiments module and every result in your table reproduces."* He then [listed me among the textbook's contributors](https://harvard-edge.github.io/cs249r_book_dev/about/contributors.html) and later merged my fix to its simulator ([#2192](https://github.com/harvard-edge/cs249r_book/pull/2192)). · [merge comment on #2175](https://github.com/harvard-edge/cs249r_book/pull/2175) · [signed emails](https://drive.google.com/file/d/1dLeScUyhyjEL-Ipwn6sjNaJUHn1SIhZP/view), evidence pages 156–163
>
> **European Space Agency**: Dario Izzo, co-author of its pagmo2 optimisation library, merged my fix to a crash open since May 2024 [the day I opened it](https://github.com/esa/pagmo2/pull/660) · [signed email](https://drive.google.com/file/d/1dLeScUyhyjEL-Ipwn6sjNaJUHn1SIhZP/view), evidence pages 175–178
>
> **US National Institute of Standards and Technology (NIST)**: Jonathan Guyer, one of the authors of FiPy, NIST's solver for partial differential equations, [merged my fix](https://github.com/usnistgov/fipy/pull/1243) after a review round · [email](https://drive.google.com/file/d/1dLeScUyhyjEL-Ipwn6sjNaJUHn1SIhZP/view), evidence pages 198–201

**Dario Izzo**, co-author of pagmo2 (European Space Agency) · **Jonathan Guyer**, one of FiPy's authors (US National Institute of Standards and Technology) · **Damien Lebrun-Grandié**, who leads Kokkos at Los Alamos National Laboratory (US Department of Energy) · **Raul Metsma**, libdigidocpp maintainer (Estonian Information System Authority) · **Tristan Müller**, first author of Relay-BP (IBM Quantum) · **Ardavan Oskooi**, original lead developer of MEEP (Massachusetts Institute of Technology) · **Bruno P. Kinoshita**, Autosubmit maintainer (Barcelona Supercomputing Center) · the **PSyclone** maintainers (UK Met Office and Science and Technology Facilities Council) · **nihui**, creator of Tencent ncnn · **John van de Wetering**, co-creator of PyZX (University of Oxford) · and the maintainers at NVIDIA, Apple and Meta.

GPU software for AI and science, with every result checked against a reference implementation. Bhubaneswar, India · Co-founder, Gigzen.

- **23 fixes merged** into the European Space Agency, the US National Institute of Standards and Technology, the US Department of Energy national laboratories, the Estonian Information System Authority (two), the Massachusetts Institute of Technology (two), the Barcelona Supercomputing Center (two), the UK Met Office and Science and Technology Facilities Council, Harvard University, NVIDIA, Apple, Meta, IBM Quantum, Tencent, Hugging Face, Carnegie Mellon University and the University of Oxford, several by the projects' own creators
- **Public-sector science software:** merged at the European Space Agency (pagmo2, by its co-author Dario Izzo, the day I opened it), the US National Institute of Standards and Technology (FiPy, by Jonathan Guyer, one of its authors), the US Department of Energy national laboratories (Kokkos, **merged** by its lead at Los Alamos National Laboratory after approval from Oak Ridge National Laboratory, in the Kokkos 5.4 release notes), the Estonian Information System Authority (libdigidocpp, two), the Massachusetts Institute of Technology (two), the Barcelona Supercomputing Center (two, for its 4.2.0 release, credited in its changelog) and the UK Met Office and Science and Technology Facilities Council (PSyclone, after its integration tests, entry 82 of its changelog); in review at the ITER Organization (reviewed by Maarten Sebregts, Simon Pinches and Olivier Hoenen; 1,808 tests pass), NASA's Jet Propulsion Laboratory (F´, issue assigned to me), the US National Institute of Standards and Technology (a second FiPy fix, 1.2–1.6× faster), the US Department of Energy's OpenMC, the UK Met Office's Iris, the Space Telescope Science Institute's JWST pipeline, CERN, the European Centre for Medium-Range Weather Forecasts, the Swiss National Supercomputing Centre, CSIRO and the Nordic Institute for Interoperability Solutions (ten merged at seven institutions, eleven in review)
- **NASA Conjunction Assessment Risk Analysis (CARA):** my reproduction of its collision probabilities, 53 of 53 test cases, 15–19× faster per core; its Analysis Team Lead, Eliot Toumey, answered both of my findings: "fully consistent with what we see in CARA operations"
- **Harvard University:** a full lab merged into the Machine Learning Systems textbook by its author, Prof. Vijay Janapa Reddi, after he reran it; [listed as a contributor](https://harvard-edge.github.io/cs249r_book_dev/about/contributors.html) for code, doc and test; he also merged my fix to its mlsysim simulator, which modelled FP32 work on the T4 about 8× too fast

[Portfolio](https://shakhtar-sankur.github.io) · [**Original emails (signed, 215 pages)**](https://drive.google.com/file/d/1dLeScUyhyjEL-Ipwn6sjNaJUHn1SIhZP/view) · [Résumé](https://shakhtar-sankur.github.io/Sankur-Kundu-Resume.pdf) · [CV](https://shakhtar-sankur.github.io/Sankur-Kundu-CV.pdf) · [sankur.kundu.tw@gmail.com](mailto:sankur.kundu.tw@gmail.com)

### Merged

| Project | Fix | Pull request |
|---|---|---|
| **European Space Agency, pagmo2** | Monotonic basin hopping crashed when its inner optimiser left the bounds (open since May 2024); merged by Dario Izzo, co-author of pagmo2, the day I opened it | [#660](https://github.com/esa/pagmo2/pull/660) |
| **US National Institute of Standards and Technology, FiPy** | NIST's PDE solver truncated boundary half-cell distances on integer grids (dy = 3 gave 1, not 1.5); merged by Jonathan Guyer, one of FiPy's authors, after a review round | [#1243](https://github.com/usnistgov/fipy/pull/1243) |
| **US Department of Energy national laboratories, Kokkos** | GPU sort for types without a default constructor (CUDA and HIP); merged by Kokkos lead Damien Lebrun-Grandié (Los Alamos National Laboratory) after approval by Daniel Arndt (Oak Ridge National Laboratory); in the [Kokkos 5.4 changelog](https://github.com/kokkos/kokkos/issues/9714) | [#9738](https://github.com/kokkos/kokkos/pull/9738) |
| **Estonian Information System Authority, libdigidocpp** | Estonia's digital-signature library: tests crashed without a network connection, and the OCSP time-check notes did not match the code; approved by maintainer Raul Metsma ("Thanks, both rules now match the code.") | [#777](https://github.com/open-eid/libdigidocpp/pull/777), [#775](https://github.com/open-eid/libdigidocpp/pull/775) |
| **Barcelona Supercomputing Center, Autosubmit** | PostgreSQL crash for its 4.2.0 release (job timestamps overflowed 32-bit columns), invited and merged by maintainer Bruno P. Kinoshita, with a thank-you in the [4.2.0 changelog](https://github.com/BSC-ES/autosubmit/commit/689cadf): "Looks great! ... Thank you!!"; a second fix at his request: "Thanks (again) @Shakhtar-Sankur !!!"; "it was a pleasure working with you as well!" | [#3405](https://github.com/BSC-ES/autosubmit/pull/3405), [#3406](https://github.com/BSC-ES/autosubmit/pull/3406) |
| **UK Met Office and Science and Technology Facilities Council, PSyclone** | Code generator of the Met Office's LFRic weather and climate model dropped Fortran BIND(C) and crashed on BIND(C) functions; its maintainer ran the integration tests, approved and merged it ("otherwise it looks good"); entry 82 of the [PSyclone changelog](https://github.com/stfc/PSyclone/blob/master/changelog) | [#3668](https://github.com/stfc/PSyclone/pull/3668) |
| **Harvard University, Machine Learning Systems textbook** | A full lab, The Same-Bits Contract, on why temperature-0 language models are not deterministic; merged by its author, Prof. Vijay Janapa Reddi, after rerunning it: "every result in your table reproduces"; [contributor](https://harvard-edge.github.io/cs249r_book_dev/about/contributors.html); then a fix to its mlsysim simulator, which modelled FP32 work on the T4 about 8× too fast | [#2175](https://github.com/harvard-edge/cs249r_book/pull/2175), [#2192](https://github.com/harvard-edge/cs249r_book/pull/2192) |
| **Tencent ncnn** | Vulkan GPU NaNs in Mish; approved, extended and merged by its creator nihui | [#7239](https://github.com/Tencent/ncnn/pull/7239) |
| **Relay-BP, IBM Quantum** | Decodings changed with batch order (1,970 of 2,000 shots → 0); merged by its first author, Tristan Müller | [#49](https://github.com/trmue/relay/pull/49) |
| **Massachusetts Institute of Technology (MIT) MEEP** | Remaining-time estimates up to 4× too short, now 0.97–1.02× the real time, and a clear error instead of a silent override ("the correct approach"); both merged by its original lead developer, Ardavan Oskooi | [#3364](https://github.com/NanoComp/meep/pull/3364), [#3363](https://github.com/NanoComp/meep/pull/3363) |
| **NVIDIA Ising-Decoding** | NVIDIA's Hugging Face models now load in its tests | [#98](https://github.com/NVIDIA/Ising-Decoding/pull/98), [#99](https://github.com/NVIDIA/Ising-Decoding/pull/99) |
| **Apple MLX** | Data race in the distributed backend (2–4 races per run → 0) | [#4737](https://github.com/ml-explore/mlx/pull/4737) |
| **Meta ExecuTorch** | Out-of-bounds read and zero-point checks in on-device LLM kernels | [#23677](https://github.com/pytorch/executorch/pull/23677), [#23912](https://github.com/pytorch/executorch/pull/23912) |
| **Hugging Face OpenEnv** | Reward rubrics ran hooks out of order and scored async judges as coroutines | [#1441](https://github.com/huggingface/OpenEnv/pull/1441), [#1442](https://github.com/huggingface/OpenEnv/pull/1442) |
| **Carnegie Mellon University XGrammar** | Jump-forward decoding crashed when a grammar forced part of a UTF-8 character | [#1012](https://github.com/mlc-ai/xgrammar/pull/1012) |
| **University of Oxford PyZX** | A rewrite broke 25 of 100 random Clifford circuits; merged by its co-creator | [#563](https://github.com/zxcalc/pyzx/pull/563) |
| **JaxMARL** (Oxford, University College London, Imperial) | Rollouts behind 8 Q-learning baselines zeroed each episode's first observation | [#206](https://github.com/bold-lab-ai/JaxMARL/pull/206) |

### Public-sector science software

| Sector | Organisation | Project | Status |
|---|---|---|---|
| Space | European Space Agency, Advanced Concepts Team | pagmo2 | **Merged:** [#660](https://github.com/esa/pagmo2/pull/660) by Dario Izzo, co-author of pagmo2, the day I opened it |
| Standards | US National Institute of Standards and Technology | FiPy | **Merged:** [#1243](https://github.com/usnistgov/fipy/pull/1243) by Jonathan Guyer, one of FiPy's authors; in review: [#1244](https://github.com/usnistgov/fipy/pull/1244), 1.2–1.6× faster |
| Fusion energy | ITER Organization | IMAS-Python | In review: [#152](https://github.com/iterorganization/IMAS-Python/pull/152), reviewed by Maarten Sebregts, Simon Pinches and Olivier Hoenen, who assigned me the issue; 1,808 tests pass |
| Space | NASA Jet Propulsion Laboratory | F´ flight software, FPP | In review: [#1190](https://github.com/nasa/fpp/pull/1190); issue assigned to me |
| Digital government | Estonian Information System Authority | libdigidocpp, Estonia's digital-signature library | **Merged:** [#775](https://github.com/open-eid/libdigidocpp/pull/775) and [#777](https://github.com/open-eid/libdigidocpp/pull/777), approved by maintainer Raul Metsma |
| Energy and national security | US Department of Energy national laboratories | Kokkos | **Merged:** [#9738](https://github.com/kokkos/kokkos/pull/9738) by Kokkos lead Damien Lebrun-Grandié (Los Alamos National Laboratory), approved by Daniel Arndt (Oak Ridge National Laboratory), reviewed by Andrey Prokopenko (Oak Ridge); in the [Kokkos 5.4 changelog](https://github.com/kokkos/kokkos/issues/9714) |
| Weather and climate | European Centre for Medium-Range Weather Forecasts (intergovernmental, 35 states) | ecCodes | In review: [#684](https://github.com/ecmwf/eccodes/pull/684) |
| Weather and climate | UK Met Office and Science and Technology Facilities Council Hartree Centre | PSyclone | **Merged:** [#3668](https://github.com/stfc/PSyclone/pull/3668) after the integration tests; entry 82 of its changelog |
| National supercomputing | Barcelona Supercomputing Center, Spain | Autosubmit | **Merged:** [#3405](https://github.com/BSC-ES/autosubmit/pull/3405) and [#3406](https://github.com/BSC-ES/autosubmit/pull/3406) by maintainer Bruno P. Kinoshita, for the 4.2.0 release; thank-you in the 4.2.0 changelog |
| National supercomputing | Swiss National Supercomputing Centre, ETH Zurich | ReFrame | In review: [#3750](https://github.com/reframe-hpc/reframe/pull/3750) |
| Particle physics | European Organization for Nuclear Research (CERN) | Rucio, Large Hadron Collider data management | In review: [#8862](https://github.com/rucio/rucio/pull/8862) |
| Academic research | Massachusetts Institute of Technology | MEEP | **Merged:** [#3364](https://github.com/NanoComp/meep/pull/3364) and [#3363](https://github.com/NanoComp/meep/pull/3363) ("the correct approach") |
| Oceans | Commonwealth Scientific and Industrial Research Organisation (CSIRO), Australia's national science agency | emsarray | In review: [#233](https://github.com/csiro-coasts/emsarray/pull/233) |
| Nuclear | US Department of Energy, OpenMC | OpenMC | In review: [#4227](https://github.com/openmc-dev/openmc/pull/4227) |
| Weather and climate | UK Met Office | Iris | In review: [#7375](https://github.com/SciTools/iris/pull/7375) |
| Astronomy | Space Telescope Science Institute | stpipe, James Webb Space Telescope pipeline | In review: [#393](https://github.com/spacetelescope/stpipe/pull/393) |
| Digital government | Nordic Institute for Interoperability Solutions | X-Road Metrics | In review: [#226](https://github.com/nordic-institute/X-Road-Metrics/pull/226) |

Also in review: Google JAX, Google DeepMind MuJoCo, Microsoft ONNX Script, vLLM, SGLang, PyTorch, Allen Institute for AI OLMo, MIT Han Lab, ETH Zurich DaCe. Scouted by Entrepreneur First (UK) from public work alone.

### Projects

| | |
|---|---|
| [**kessler**](https://github.com/Shakhtar-Sankur/kessler) | Screens all 140 million pairs of active satellites every day, in public; collision probabilities agree with NASA CARA's on 53 of 53 test cases; CARA's Analysis Team: "fully consistent with what we see in CARA operations" |
| [**Larzavan**](https://github.com/Shakhtar-Sankur/larzavan) | Open global earthquake early-warning system: with each earthquake held out of its own fit, its GNSS magnitude puts Tohoku's 9.0 at 8.8, within 0.3 units 126 seconds after the rupture began |
| [**samebit**](https://github.com/Shakhtar-Sankur/samebit) | A 494M-parameter LLM run entirely in integers, bit-identical on an NVIDIA T4 GPU and an x86 CPU, within 0.75% of float32 perplexity; its lab is [merged into Harvard's Machine Learning Systems textbook](https://github.com/harvard-edge/cs249r_book/pull/2175) |
| [**torino**](https://github.com/Shakhtar-Sankur/torino) | Daily independent check of NASA JPL's and ESA's asteroid impact-risk lists; my orbit propagator agrees with JPL Horizons to within 1 km after a year |
| [**syndrome**](https://github.com/Shakhtar-Sankur/syndrome) | GPU decoder for IBM's quantum LDPC codes, bit-identical to IBM's reference, 28.7× faster per shot |
| [**tessel**](https://github.com/Shakhtar-Sankur/tessel) | Tile-language compiler for CUDA, Metal and TPU; GEMM at cuBLAS parity, an engine at 1.05× vLLM's throughput |
| [**lipi**](https://github.com/Shakhtar-Sankur/lipi) | Tokenizer that needs fewer tokens than GPT-4o's and Gemini's in 23 of 24 Indian languages |
| [**ratchet**](https://github.com/Shakhtar-Sankur/ratchet) | GRPO post-training from scratch; found and removed a silent training–inference mismatch (5.2 → 0.04 nats) |
| [**relay**](https://github.com/Shakhtar-Sankur/relay) | Disaggregated LLM inference in C++/CUDA; 384 of 384 requests identical through 60 worker kills |
| [**switchyard**](https://github.com/Shakhtar-Sankur/switchyard) | Mixture-of-experts serving with expert parallelism on my own CUDA kernels, bit-identical to one GPU |
| [**babelguard**](https://github.com/Shakhtar-Sankur/babelguard) | Scam detection across languages; links a translated scam 85% of the time, text matching 1.5% |

Method, results, stated limits and raw data for each project are on its [study page](https://shakhtar-sankur.github.io).
