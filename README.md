# Sankur Kundu

### NASA's collision-risk team, a Harvard professor, and eighteen fixes merged by the people who lead the projects.

> **NASA Conjunction Assessment Risk Analysis (CARA)**, its Analysis Team on my two findings: *"your sampling space results indeed appear to be fully consistent with what we see in CARA operations"* · *"your time window results indeed appear to be fully consistent with what we see in CARA operations"* · [signed email from nasa.gov](https://drive.google.com/file/d/1dLeScUyhyjEL-Ipwn6sjNaJUHn1SIhZP/view), evidence pages 150–155
>
> **Prof. Vijay Janapa Reddi, Harvard University**, merging my lab into his Machine Learning Systems textbook: *"Merged, thanks @Shakhtar-Sankur. I reran the experiments module and every result in your table reproduces."* He then [listed me among the textbook's contributors](https://harvard-edge.github.io/cs249r_book_dev/about/contributors.html). · [merge comment on #2175](https://github.com/harvard-edge/cs249r_book/pull/2175) · [signed emails](https://drive.google.com/file/d/1dLeScUyhyjEL-Ipwn6sjNaJUHn1SIhZP/view), evidence pages 156–163

**Damien Lebrun-Grandié**, who leads Kokkos at Los Alamos National Laboratory (US Department of Energy) · **Tristan Müller**, first author of Relay-BP (IBM Quantum) · **Ardavan Oskooi**, original lead developer of MEEP (Massachusetts Institute of Technology) · **Bruno P. Kinoshita**, Autosubmit maintainer (Barcelona Supercomputing Center) · the **PSyclone** maintainers (UK Met Office and Science and Technology Facilities Council) · **nihui**, creator of Tencent ncnn · **John van de Wetering**, co-creator of PyZX (University of Oxford) · and the maintainers at NVIDIA, Apple and Meta. All in 25 days.

GPU software for AI and science, with every result checked against a reference implementation. Bhubaneswar, India · Co-founder, Gigzen.

- **18 fixes merged in 25 days** into the US Department of Energy national laboratories, the Massachusetts Institute of Technology (two), the Barcelona Supercomputing Center (two), the UK Met Office and Science and Technology Facilities Council, NVIDIA, Apple, Meta, IBM Quantum, Tencent, Hugging Face, Carnegie Mellon University and the University of Oxford, several by the projects' own creators
- **Public-sector science software:** fixes at the US Department of Energy national laboratories (Kokkos, **merged** by its lead at Los Alamos National Laboratory after approval from Oak Ridge National Laboratory, in the Kokkos 5.4 release notes), the Massachusetts Institute of Technology (two, merged), the Barcelona Supercomputing Center (two, **merged** for its 4.2.0 release, credited in its changelog), the UK Met Office and Science and Technology Facilities Council (PSyclone, **merged** after its integration tests, entry 82 of its changelog), the European Organization for Nuclear Research (CERN), the European Centre for Medium-Range Weather Forecasts, the Swiss National Supercomputing Centre and CSIRO, Australia's national science agency (six merged, four in review)
- **NASA Conjunction Assessment Risk Analysis (CARA):** my reproduction of its collision probabilities, 53 of 53 test cases, 15–19× faster per core; its Analysis Team Lead, Eliot Toumey, answered both of my findings: "fully consistent with what we see in CARA operations"
- **Harvard University:** a full lab merged into the Machine Learning Systems textbook by its author, Prof. Vijay Janapa Reddi, after he reran it; [listed as a contributor](https://harvard-edge.github.io/cs249r_book_dev/about/contributors.html) for code, doc and test

[Portfolio](https://shakhtar-sankur.github.io) · [**Original emails (signed, 173 pages)**](https://drive.google.com/file/d/1dLeScUyhyjEL-Ipwn6sjNaJUHn1SIhZP/view) · [Résumé](https://shakhtar-sankur.github.io/Sankur-Kundu-Resume.pdf) · [CV](https://shakhtar-sankur.github.io/Sankur-Kundu-CV.pdf) · [sankur.kundu.tw@gmail.com](mailto:sankur.kundu.tw@gmail.com)

### Merged

| Project | Fix | Pull request |
|---|---|---|
| **US Department of Energy national laboratories, Kokkos** | GPU sort for types without a default constructor (CUDA and HIP); merged by Kokkos lead Damien Lebrun-Grandié (Los Alamos National Laboratory) after approval by Daniel Arndt (Oak Ridge National Laboratory); in the [Kokkos 5.4 changelog](https://github.com/kokkos/kokkos/issues/9714) | [#9738](https://github.com/kokkos/kokkos/pull/9738) |
| **Barcelona Supercomputing Center, Autosubmit** | PostgreSQL crash for its 4.2.0 release (job timestamps overflowed 32-bit columns), invited and merged by maintainer Bruno P. Kinoshita, with a thank-you in the [4.2.0 changelog](https://github.com/BSC-ES/autosubmit/commit/689cadf): "Looks great! ... Thank you!!"; a second fix at his request: "Thanks (again) @Shakhtar-Sankur !!!"; "it was a pleasure working with you as well!" | [#3405](https://github.com/BSC-ES/autosubmit/pull/3405), [#3406](https://github.com/BSC-ES/autosubmit/pull/3406) |
| **UK Met Office and Science and Technology Facilities Council, PSyclone** | Code generator of the Met Office's LFRic weather and climate model dropped Fortran BIND(C) and crashed on BIND(C) functions; its maintainer ran the integration tests, approved and merged it ("otherwise it looks good"); entry 82 of the [PSyclone changelog](https://github.com/stfc/PSyclone/blob/master/changelog) | [#3668](https://github.com/stfc/PSyclone/pull/3668) |
| **Harvard University, Machine Learning Systems textbook** | A full lab, The Same-Bits Contract, on why temperature-0 language models are not deterministic; merged by its author, Prof. Vijay Janapa Reddi, after rerunning it: "every result in your table reproduces"; [contributor](https://harvard-edge.github.io/cs249r_book_dev/about/contributors.html) | [#2175](https://github.com/harvard-edge/cs249r_book/pull/2175) |
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
| Energy and national security | US Department of Energy national laboratories | Kokkos | **Merged:** [#9738](https://github.com/kokkos/kokkos/pull/9738) by Kokkos lead Damien Lebrun-Grandié (Los Alamos National Laboratory), approved by Daniel Arndt (Oak Ridge National Laboratory), reviewed by Andrey Prokopenko (Oak Ridge); in the [Kokkos 5.4 changelog](https://github.com/kokkos/kokkos/issues/9714) |
| Weather and climate | European Centre for Medium-Range Weather Forecasts (intergovernmental, 35 states) | ecCodes | In review: [#684](https://github.com/ecmwf/eccodes/pull/684) |
| Weather and climate | UK Met Office and Science and Technology Facilities Council Hartree Centre | PSyclone | **Merged:** [#3668](https://github.com/stfc/PSyclone/pull/3668) after the integration tests; entry 82 of its changelog |
| National supercomputing | Barcelona Supercomputing Center, Spain | Autosubmit | **Merged:** [#3405](https://github.com/BSC-ES/autosubmit/pull/3405) and [#3406](https://github.com/BSC-ES/autosubmit/pull/3406) by maintainer Bruno P. Kinoshita, for the 4.2.0 release; thank-you in the 4.2.0 changelog |
| National supercomputing | Swiss National Supercomputing Centre, ETH Zurich | ReFrame | In review: [#3750](https://github.com/reframe-hpc/reframe/pull/3750) |
| Particle physics | European Organization for Nuclear Research (CERN) | Rucio, Large Hadron Collider data management | In review: [#8862](https://github.com/rucio/rucio/pull/8862) |
| Academic research | Massachusetts Institute of Technology | MEEP | **Merged:** [#3364](https://github.com/NanoComp/meep/pull/3364) and [#3363](https://github.com/NanoComp/meep/pull/3363) ("the correct approach") |
| Oceans | Commonwealth Scientific and Industrial Research Organisation (CSIRO), Australia's national science agency | emsarray | In review: [#233](https://github.com/csiro-coasts/emsarray/pull/233) |

Also in review: Google JAX, Google DeepMind MuJoCo, Microsoft ONNX Script, vLLM, SGLang, PyTorch, Allen Institute for AI OLMo, MIT Han Lab, ETH Zurich DaCe. Scouted by Entrepreneur First (UK) from public work alone.

### Projects

| | |
|---|---|
| [**kessler**](https://github.com/Shakhtar-Sankur/kessler) | Screens all 140 million pairs of active satellites every day, in public; collision probabilities agree with NASA CARA's on 53 of 53 test cases; CARA's Analysis Team: "fully consistent with what we see in CARA operations" |
| [**samebit**](https://github.com/Shakhtar-Sankur/samebit) | A 494M-parameter LLM run entirely in integers, bit-identical on an NVIDIA T4 GPU and an x86 CPU, within 0.75% of float32 perplexity; its lab is [merged into Harvard's Machine Learning Systems textbook](https://github.com/harvard-edge/cs249r_book/pull/2175) |
| [**syndrome**](https://github.com/Shakhtar-Sankur/syndrome) | GPU decoder for IBM's quantum LDPC codes, bit-identical to IBM's reference, 28.7× faster per shot |
| [**tessel**](https://github.com/Shakhtar-Sankur/tessel) | Tile-language compiler for CUDA, Metal and TPU; GEMM at cuBLAS parity, an engine at 1.05× vLLM's throughput |
| [**lipi**](https://github.com/Shakhtar-Sankur/lipi) | Tokenizer that needs fewer tokens than GPT-4o's and Gemini's in 23 of 24 Indian languages |
| [**ratchet**](https://github.com/Shakhtar-Sankur/ratchet) | GRPO post-training from scratch; found and removed a silent training–inference mismatch (5.2 → 0.04 nats) |
| [**relay**](https://github.com/Shakhtar-Sankur/relay) | Disaggregated LLM inference in C++/CUDA; 384 of 384 requests identical through 60 worker kills |
| [**switchyard**](https://github.com/Shakhtar-Sankur/switchyard) | Mixture-of-experts serving with expert parallelism on my own CUDA kernels, bit-identical to one GPU |
| [**babelguard**](https://github.com/Shakhtar-Sankur/babelguard) | Scam detection across languages; links a translated scam 85% of the time, text matching 1.5% |

Method, results, stated limits and raw data for each project are on its [study page](https://shakhtar-sankur.github.io).
