# Sankur Kundu

GPU software for AI and science, with every result checked against a reference implementation. Bhubaneswar, India · Co-founder, Gigzen.

- **13 fixes merged in 21 days** into NVIDIA, Apple, Meta, Tencent, IBM Quantum, the Massachusetts Institute of Technology, Hugging Face, Carnegie Mellon University and the University of Oxford, several by the projects' own creators
- **Public-sector science software:** fixes at the US Department of Energy national laboratories, the European Centre for Medium-Range Weather Forecasts, the UK Met Office, the Swiss National Supercomputing Centre and the Massachusetts Institute of Technology (one merged, five in review)
- **Under review by NASA Conjunction Assessment Risk Analysis (CARA):** my reproduction of its collision probabilities, 53 of 53 test cases, 15–19× faster per core

[Portfolio](https://shakhtar-sankur.github.io) · [Evidence for every claim](https://shakhtar-sankur.github.io/evidence/) · [Résumé](https://shakhtar-sankur.github.io/Sankur-Kundu-Resume.pdf) · [CV](https://shakhtar-sankur.github.io/Sankur-Kundu-CV.pdf) · sankur.kundu.tw@gmail.com

### Merged

| Project | Fix | Pull request |
|---|---|---|
| **Tencent ncnn** | Vulkan GPU NaNs in Mish; approved, extended and merged by its creator nihui | [#7239](https://github.com/Tencent/ncnn/pull/7239) |
| **Relay-BP, IBM Quantum** | Decodings changed with batch order (1,970 of 2,000 shots → 0); merged by its first author, Tristan Müller | [#49](https://github.com/trmue/relay/pull/49) |
| **Massachusetts Institute of Technology (MIT) MEEP** | Remaining-time estimates up to 4× too short, now 0.97–1.02× the real time; merged by its original lead developer, Ardavan Oskooi | [#3364](https://github.com/NanoComp/meep/pull/3364) |
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
| Energy and national security | US Department of Energy national laboratories (Sandia, Oak Ridge) | Kokkos | In review: [#9738](https://github.com/kokkos/kokkos/pull/9738) |
| Weather and climate | European Centre for Medium-Range Weather Forecasts (intergovernmental, 35 states) | ecCodes | In review: [#684](https://github.com/ecmwf/eccodes/pull/684) |
| Weather and climate | UK Met Office and Science and Technology Facilities Council Hartree Centre | PSyclone | In review: [#3668](https://github.com/stfc/PSyclone/pull/3668) |
| National supercomputing | Swiss National Supercomputing Centre, ETH Zurich | ReFrame | In review: [#3750](https://github.com/reframe-hpc/reframe/pull/3750) |
| Academic research | Massachusetts Institute of Technology | MEEP | **Merged:** [#3364](https://github.com/NanoComp/meep/pull/3364); approved: [#3363](https://github.com/NanoComp/meep/pull/3363) ("the correct approach") |

Also in review: Google JAX, Google DeepMind MuJoCo, Microsoft ONNX Script, vLLM, SGLang, PyTorch, Allen Institute for AI OLMo, MIT Han Lab, ETH Zurich DaCe. A lab submitted to Harvard's Machine Learning Systems textbook ([#2175](https://github.com/harvard-edge/cs249r_book/pull/2175)). Scouted by Entrepreneur First (UK) from public work alone.

### Projects

| | |
|---|---|
| [**kessler**](https://github.com/Shakhtar-Sankur/kessler) | Screens all 140 million pairs of active satellites every day, in public; collision probabilities agree with NASA CARA's on 53 of 53 test cases |
| [**syndrome**](https://github.com/Shakhtar-Sankur/syndrome) | GPU decoder for IBM's quantum LDPC codes, bit-identical to IBM's reference, 28.7× faster per shot |
| [**tessel**](https://github.com/Shakhtar-Sankur/tessel) | Tile-language compiler for CUDA, Metal and TPU; GEMM at cuBLAS parity, an engine at 1.05× vLLM's throughput |
| [**lipi**](https://github.com/Shakhtar-Sankur/lipi) | Tokenizer that needs fewer tokens than GPT-4o's and Gemini's in 23 of 24 Indian languages |
| [**ratchet**](https://github.com/Shakhtar-Sankur/ratchet) | GRPO post-training from scratch; found and removed a silent training–inference mismatch (5.2 → 0.04 nats) |
| [**relay**](https://github.com/Shakhtar-Sankur/relay) | Disaggregated LLM inference in C++/CUDA; 384 of 384 requests identical through 60 worker kills |
| [**switchyard**](https://github.com/Shakhtar-Sankur/switchyard) | Mixture-of-experts serving with expert parallelism on my own CUDA kernels, bit-identical to one GPU |
| [**babelguard**](https://github.com/Shakhtar-Sankur/babelguard) | Scam detection across languages; links a translated scam 85% of the time, text matching 1.5% |

Method, results, stated limits and raw data for each project are on its [study page](https://shakhtar-sankur.github.io).
