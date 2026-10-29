# Sankur Kundu

**ML systems engineer and researcher · Matched NASA on 53/53 cases, 15× faster, now under review by NASA CARA · GPU quantum decoder bit-identical to IBM's, 28.7× faster per shot · cuBLAS-parity compiler · Tokenizer that beats GPT-4o and Gemini in 23 of 24 Indian languages · 7 fixes merged in 13 days at Apple, Meta, Hugging Face, Oxford's PyZX and JaxMARL · Official Vesuvius ink model finds 79% of real ink moved into an unread scroll (AUC 0.94) · In review at research labs of MIT, Carnegie Mellon and ETH Zurich**

Sole author of four manuscripts: on the **token tax** that Indian languages pay in LLMs, on a silent
**training–inference mismatch** in RL post-training, on how **scam defence stops at English**, and on
**satellite collision risk**, reproducing NASA CARA's Monte Carlo on all 53 of its test conjunctions.
Seven fixes merged in 13 days into [**Apple MLX**](https://github.com/ml-explore/mlx/pull/4737), **Meta ExecuTorch** (two), **Hugging Face OpenEnv**, Oxford's [PyZX](https://github.com/zxcalc/pyzx/pull/563) (merged by its co-creator) and [**JaxMARL**](https://github.com/bold-lab-ai/JaxMARL/pull/206) (merged by its lead author; BOLD Lab: **Oxford, UCL and Imperial**), and pull requests under review at **Google JAX**, **NVIDIA**, **vLLM**, **PyTorch**, and the research labs [MIT Han Lab](https://github.com/nunchux-ai/nunchaku/pull/957) (**MIT**), [XGrammar](https://github.com/mlc-ai/xgrammar/pull/1012) (**Carnegie Mellon**) and [DaCe](https://github.com/spcl/dace/pull/2729) (**ETH Zurich**). Co-founder and founding engineer at **Gigzen**.

Everything below is built from scratch and measured against the best in the field: GPU kernels at
**cuBLAS parity**, an LLM engine at **1.05× vLLM's** throughput with identical output, a tokenizer that
beats **GPT-4o's and Gemini's** in 23 of 24 Indian languages, and **kessler**, which screens **140 million**
pairs of active satellites in public every day and whose collision probabilities agree with NASA CARA's Monte Carlo on all
53 of NASA's test conjunctions, **15–19× faster** per core than NASA's own library, and **samebit**, which runs a 494M-parameter LLM entirely in integers with **identical bits on an NVIDIA GPU and a CPU**. Each project has the scripts and raw results behind its numbers, and a
study page with its method, results, stated limits and a citation.

🧑‍💻 [portfolio](https://shakhtar-sankur.github.io) · 🔎 [evidence for every claim](https://shakhtar-sankur.github.io/evidence/) · 📄 [résumé](https://shakhtar-sankur.github.io/Sankur-Kundu-Resume.pdf) · 📚 [full CV](https://shakhtar-sankur.github.io/Sankur-Kundu-CV.pdf) · 🌐 [gigzen](https://shakhtar-sankur.github.io/gigzen/) · 📧 sankur.kundu.tw@gmail.com

---

## 🏅 Recognition

- **NASA CARA**: I sent CARA my independent reproduction of its Monte Carlo collision probabilities on all 53 of its
test conjunctions; its operations team lead referred it to CARA's analysis team, and it is now under review by NASA CARA (20 Oct 2026).
- **Entrepreneur First** (UK): scouted me from my public work alone (Oct 2026), citing tessel's cuBLAS-parity GEMM,
switchyard's MoE serving and a negative result I chose to publish.
- **Meta ExecuTorch** ([#23677](https://github.com/pytorch/executorch/pull/23677), merged 16 Oct 2026, approved by two Meta maintainers):
“LGTM! Thanks for the fix!” A second fix to the same kernels, [#23912](https://github.com/pytorch/executorch/pull/23912), was merged by Meta's Jacob Stevens on 28 Oct 2026.
- **Apple MLX** ([#4737](https://github.com/ml-explore/mlx/pull/4737), merged 22 Oct 2026 by MLX maintainer @zcbenz after review and approval):
my fix for a data race in the distributed backend that links Macs for multi-machine training.
- **Oxford PyZX** ([#563](https://github.com/zxcalc/pyzx/pull/563), merged 22 Oct 2026 by its co-creator John van de Wetering):
“Thanks for the fix! This was a regression from an earlier PR that changed how XPhase gates were handled in optimization.”
- **JaxMARL** ([#206](https://github.com/bold-lab-ai/JaxMARL/pull/206), NeurIPS 2024; BOLD Lab: Oxford, UCL & Imperial; merged 26 Oct 2026 by lead author Alex Rutherford after his approval):
“Good find!!”
- **Hugging Face OpenEnv** ([#1441](https://github.com/huggingface/OpenEnv/pull/1441), [#1442](https://github.com/huggingface/OpenEnv/pull/1442),
merged 19 Oct 2026), approved by its reviewer: “Reviewed hook ordering and async composition; 177 rubric tests pass.”

## 📈 Scale

- **Every day, in public:** kessler screens all **140 million** pairs of the **16,768** active satellites (about **60,000**
close approaches a day); the full **32,593**-object catalogue, all **531 million** pairs, takes **28 s** on one T4.
- **Verified under failure:** quorumdb ran **10,000** simulated clusters through **610,064** crashes and **144,354**
network partitions with zero safety violations; faultline ran **1.26 million** operations under **288** injected faults
against four etcd releases.
- **Breadth:** 16 open-source systems in C++, CUDA, Rust, Python and Swift, with kernels for NVIDIA GPUs, Apple Metal and
Google TPUs; studies of **24** languages on **15** production tokenizers and **33,869** scams in **49** languages;
Populace has **1,600+** npm downloads.

---

## 🔬 Research

| | Manuscript | Finding |
|---|---|---|
| **[The token tax](https://shakhtar-sankur.github.io/token-tax/)** · [lipi](https://github.com/Shakhtar-Sankur/lipi) · [on Hugging Face](https://huggingface.co/Shakhtar-Sankur/lipi-indic-96k) · [paper](https://github.com/Shakhtar-Sankur/lipi/blob/main/paper/main.pdf) | *Removing the Token Tax from an Existing Model: A Vocabulary Extension for 24 Indian Languages That Keeps Every Other Token.* Manuscript, 2026; arXiv submission in progress | Odia costs **4.99×** English on GPT-4o. lipi-Indic extends Qwen 2.5's tokenizer without changing a single English or code token id, and needs **fewer tokens than GPT-4o's and Gemini's in 23 of 24** languages; in equal GPU time the model predicts held-out Odia **20% better**. Try every tokenizer in the browser on the study page |
| **[The sampler was not the policy](https://shakhtar-sankur.github.io/ratchet/)** · [ratchet](https://github.com/Shakhtar-Sankur/ratchet) · [report](https://github.com/Shakhtar-Sankur/ratchet/blob/main/paper/main.pdf) | *The Sampler Was Not the Policy: Finding and Removing a Silent Training–Inference Mismatch in a From-Scratch GRPO Stack.* Technical report, 2026; arXiv submission in progress | The inference engine's fp16 weights rounded away most training updates, so it sampled a policy the trainer never had (gap up to **5.2 nats**); mixed-precision rounding cut it to **0.04**. Taking the gap apart shows rounding at weight sync outweighs fp16 arithmetic **9–22×**, and low-probability tokens carry it |
| **[Scam defence stops at English](https://shakhtar-sankur.github.io/babelguard/)** · [babelguard](https://github.com/Shakhtar-Sankur/babelguard) | *Scam Defence Stops at English: Measuring the Multilingual Protection Gap and Linking Scam Campaigns Across Languages.* Manuscript in preparation, 2026 | An English keyword filter catches **86%** of English scams but **10–36%** of Korean, Japanese, Urdu, Arabic, Thai and Hindi ones. Linking by meaning recognises a translated scam **85%** of the time, against **1.5%** for text matching |
| **[Satellite collision risk](https://shakhtar-sankur.github.io/kessler/)** · [kessler](https://github.com/Shakhtar-Sankur/kessler) · [paper](https://github.com/Shakhtar-Sankur/kessler/blob/main/paper/main.pdf) | *Reproducing NASA CARA's Monte Carlo Probability of Collision: An Open Two-Body Implementation, Checked on All 53 of CARA's Test Conjunctions.* Manuscript, 2026; arXiv submission in progress | An open two-body Monte Carlo agrees with NASA CARA's on **all 53** of its test conjunctions (χ² p = 0.67), including the 28 where the standard 2D method is wrong, and runs **15–19×** faster per core than CARA's own library |

---

## 🛡️ Scam defence across languages

| | What it is | What it measures |
|---|---|---|
| **[babelguard](https://github.com/Shakhtar-Sankur/babelguard)** · [study](https://shakhtar-sankur.github.io/babelguard/) · in progress | An open **early-warning system for scams that cross languages**: script-aware cleaning that removes the hidden characters and look-alike letters used to evade filters while keeping their legitimate uses in Indic, Arabic-script and Thai text; indicator extraction (links, phone numbers for 22 countries, UPI IDs, checksum-verified wallets); cross-language campaign linking with MinHash LSH; leak-free benchmark splits; multilingual-embedding linking by meaning; a **crash-safe streaming campaign engine** (write-ahead log, atomic snapshots); an offline labelling tool for native speakers | In the largest open set of reported scam SMS (IMC 2025: **33,869** messages, **49** languages), South Asian languages are **0.8%** and African **0.1%**; **96** scam templates recur across languages; only **4 of 49** languages have any genuine messages to measure false alarms against; in one public benchmark's random split, **22.5%** of test scams had a near-copy in training; linking by meaning recognises a translated scam **85%** of the time (character matching: **1.5%**); an English keyword filter catches **86%** of English scams but **10–36%** in six Asian languages; the engine links **4,057 messages/s** on 4 cores, **0.21 KB** per message at **1M**, B-cubed F1 **0.995** against known campaigns, with nothing lost across 50 random crashes |

`Python` `NumPy` `Unicode (UTS #39)` `MinHash LSH` — defensive only: measurements and fixes are published, never evasion kits.

---

## 🤝 Open source

- **Apple MLX** [#4737](https://github.com/ml-explore/mlx/pull/4737) (**merged** 22 Oct 2026 by an MLX maintainer, after review and approval): the socket threads of MLX's distributed ring
backend, the TCP transport that links machines for multi-machine runs, read their task queues outside the lock while other
threads appended to them. They now take the front tasks while holding it. A ThreadSanitizer harness built from the class
found 2–4 races on every run before the fix and none after, and MLX's ring tests pass on 8 ranks.
- **Meta ExecuTorch** [#23677](https://github.com/pytorch/executorch/pull/23677) (merged 16 Oct 2026, approved by two maintainers): the 2-bit and 4-bit quantized
embedding kernels that on-device LLMs use did not check their token ids, so an id past the end of the table
read memory outside it and returned it as an embedding, while the 8-bit kernel rejects it. I added the same
bounds check, with tests that fail without it; the quantized kernel suite passes 82 of 82.
- **Hugging Face OpenEnv** (both merged 19 Oct 2026, reviewed by Hugging Face), the framework for RL environments:
[#1441](https://github.com/huggingface/OpenEnv/pull/1441) makes composite reward rubrics (`Sequential`, `Gate`,
`WeightedSum`) run their pre-hooks before scoring their children, as single rubrics do; on `main`, a timing
hook around two 0.2 s children read 0.01 ms. [#1442](https://github.com/huggingface/OpenEnv/pull/1442) awaits
an async child returned by a sync `forward()`, the pattern in the rubrics tutorial, which had recorded an
unawaited coroutine as the score. 9 of the 13 new tests fail without the fixes.
- **Google JAX** [#41859](https://github.com/jax-ml/jax/pull/41859) (under review; assigned to Matthew Johnson, one of JAX's original authors): `jax.grad` through `lax.reduce_window`
with a custom reduction has failed since 2021 ([#7815](https://github.com/jax-ml/jax/issues/7815)), because its derivative was a
single primitive over (value, tangent) pairs that JAX cannot transpose. The derivative is now a fold over the window
offsets, built only from transposable primitives and in the same order XLA evaluates the reduction; it also fixes
[#32548](https://github.com/jax-ml/jax/issues/32548). 2,097 cases pass in 32-bit and 2,578 in 64-bit; the 242 new ones fail on `main`.
- **NVIDIA Ising-Decoding** [#98](https://github.com/NVIDIA/Ising-Decoding/pull/98) (under review): the public-model tests, offline
smoke test and docs looked only for `.pt` checkpoints, so anyone using the SafeTensors models NVIDIA publishes on
Hugging Face failed them. They now accept the published files, with tests that fail on `main`.
- **Meta ExecuTorch** [#23912](https://github.com/pytorch/executorch/pull/23912) (**merged** by Meta's Jacob Stevens, 28 Oct 2026): the same kernels checked their zero points
against the output type instead of the scales' type, so valid models with fp16 scales and fp32 output aborted, and
the `.out` variants read past the end of their scales (AddressSanitizer: heap-buffer-overflow). With the fix the
quantized kernel suite passes 86 of 86; without it, all 6 new tests fail. Revised after maintainer review so the 2- and 4-bit export kernels also report the scales' dtype.
- **vLLM** [#60955](https://github.com/vllm-project/vllm/pull/60955) (under review): running vLLM's FlashInfer tests on a T4 and
checking every output against a float64 reference showed that the prefill tests compared non-causal
attention with a causal reference, and passed only because their tolerance was larger than the outputs.
With `causal=True` and a tolerance that matters, all 32 cases pass, and all 32 fail if the bug returns.
- **ETH Zurich DaCe** [#2729](https://github.com/spcl/dace/pull/2729) (under review): DaCe, the data-centric compiler from ETH
Zurich's Scalable Parallel Computing Lab, compiled `numpy.rint` to C's `round`, which rounds halfway values away from zero, so
compiled programs returned 3 for 2.5 where NumPy returns 2. Fixed for float and complex types; the new test fails without the fix.
Also reported that `np.max`/`np.min` drop NaN ([#2730](https://github.com/spcl/dace/issues/2730)). Its maintainer (28 Oct 2026):
“Seems all good, once we have the CI calmer, I will let these workflows run, once green can be merged.”
- **Oxford PyZX** [#563](https://github.com/zxcalc/pyzx/pull/563) (**merged** by co-creator John van de Wetering, 22 Oct 2026): PyZX, the ZX-calculus library for quantum
circuit optimisation, put an X rotation on the wrong qubit after rewriting two CNOTs as a SWAP, so `basic_optimization`,
`full_optimize` and `phase_block_optimize` returned a different unitary for 25 of 100 random Clifford circuits (0 after the fix).
- **BOLD Lab (Oxford, UCL, Imperial) JaxMARL** [#206](https://github.com/bold-lab-ai/JaxMARL/pull/206) (**merged** 26 Oct 2026 by lead author Alex Rutherford: “Good find!!”): the rollout
wrapper behind 8 of JaxMARL's Q-learning baselines (QMIX, VDN, IQL, PQN-VDN, SHAQ, TransfQMIX) replaced the first observation of
every new episode with zeros after an auto-reset, so agents chose their first action blind and trained on it. Agents that die
mid-episode still get zeros; two of the three new tests fail without the fix.
- **Carnegie Mellon (CMU) XGrammar** [#1012](https://github.com/mlc-ai/xgrammar/pull/1012) (under review): XGrammar, the structured-output engine used by vLLM and SGLang,
crashed in jump-forward decoding whenever a grammar forced only part of a UTF-8 character (e.g. `"é" | "è"`), the bug behind its issue #132; it now returns
only whole characters, with four new tests that fail without the fix.
- **MIT Han Lab nunchaku** [#957](https://github.com/nunchux-ai/nunchaku/pull/957) (under review): `compose_lora` returned a
single Nunchaku-format LoRA at full strength whenever its strength was below 1, so 0.5 had no effect and 0 did not switch
it off, with no error. Only strength 1 now takes that shortcut; three of the four new tests fail without the fix.
- **PyTorch** (under review): [#199875](https://github.com/pytorch/pytorch/pull/199875) makes torch.compile fill `torch.empty` in
deterministic mode as eager does, without filling Inductor's own buffers, which is what got an earlier
fix reverted; [#199441](https://github.com/pytorch/pytorch/pull/199441) checked all 37 Inductor-skipped tests in
`test_torch.py` on CPU and two T4 GPUs and removes 13 stale torch.compile skips;
[#199646](https://github.com/pytorch/pytorch/pull/199646) traces 19 skipped determinism tests to a
forward/backward mode mismatch, so 8 now run under torch.compile and 11 stay skipped with verified causes.

---

## 🚀 LLM training, serving and distributed training

| | What it is | What it measures |
|---|---|---|
| **[switchyard](https://github.com/Shakhtar-Sankur/switchyard)** · [study](https://shakhtar-sankur.github.io/switchyard/) | Mixture-of-experts serving with **expert parallelism** from scratch: OLMoE-1B-7B across 2 GPUs on my own **CUDA** kernels (routing, sorting, tensor-core grouped GEMM/GEMV) and **peer-to-peer** dispatch in place of NCCL | **Bit-identical** to one GPU; decodes **2.2× faster** than Hugging Face (112 vs 52 tok/s at batch 8); dispatch **1.25× faster** than NCCL all-to-all at 256 tokens/GPU; measured that dropping overflow tokens raises perplexity **12.9 → 20.2**, so it never drops one |
| **[ratchet](https://github.com/Shakhtar-Sankur/ratchet)** · [study](https://shakhtar-sankur.github.io/ratchet/) | Reinforcement-learning post-training (**GRPO**) from scratch: rollouts with per-token log-probabilities on relay, a **PyTorch** trainer data-parallel on tandem, weights synced back **in place on the GPU**, partial rollouts and one-step-ahead training | On 2× T4, 100 steps raised Qwen2.5-0.5B on **GSM8K** from **48.1% to 52.5%** (all 1,319 test problems); weight sync **369× faster** than a reload (0.017 s); found that fp16 rounding silently discarded the training updates and fixed it (engine–trainer log-prob gap **5.2 → 0.04**) |
| **[crucible](https://github.com/Shakhtar-Sankur/crucible)** · [study](https://shakhtar-sankur.github.io/crucible/) | Sandboxed environments for training **coding agents with RL**: sandboxes built from **Linux namespaces, seccomp-BPF** and resource limits, forked from a warm process (no VMs), forkable mid-episode; an **OpenEnv**-compatible server whose grader runs the tests outside the model's code | **GRPO** on ratchet with every reward from a sandbox lifted MBPP pass@1 **34.9% → 38.6%** (mean of **3 seeds**, paired test **p = 0.013**); **0 of 9** reward hacks pass its grader (the usual grader: 4); a live sandbox forks in **4.5 ms** vs 138 ms to rebuild, and rollout trees grown from forks need up to **10.9×** less environment time than replaying |
| **[lipi](https://github.com/Shakhtar-Sankur/lipi)** · [study](https://shakhtar-sankur.github.io/token-tax/) · [on Hugging Face](https://huggingface.co/Shakhtar-Sankur/lipi-indic-96k) | The **token tax** on Indian languages, measured and then cut: 24 languages × 15 production tokenizers, then **lipi-Indic**, Qwen 2.5's byte-level **BPE** tokenizer extended for every Indian language (a pre-tokenizer fix plus 96K new merges that no other script can trigger), and **continued pre-training** of Qwen2.5-0.5B with new embeddings on 2× T4 | Odia costs **4.99×** English on GPT-4o, Santali **13.7×**; lipi-Indic uses **fewer tokens than GPT-4o's and Gemini's tokenizers in 23 of 24 languages** (speaker-weighted **1.30×** vs 1.92× and 1.58×) with a smaller vocabulary than Gemini's; Odia text **8.6× fewer tokens**, the same training text in **19 min instead of 104**, and in equal GPU time held-out Odia predicted **20% better** |
| **[relay](https://github.com/Shakhtar-Sankur/relay)** · [study](https://shakhtar-sankur.github.io/relay/) | A disaggregated LLM inference cluster: prefill and decode workers in **C++20/CUDA** with my own **flash-attention** and **flash-decoding** kernels, a KV-cache transfer engine, and a **Swift** control plane (C++ interop, OpenAI-compatible streaming API, prefix-aware routing). Fault-tolerant | On a T4, 2,048-token prefill **8.7× faster** and 32-sequence decode **5.4× faster** than its first kernels; streaming hides **99–100%** of the KV transfer (21.6 ms → 0.08 ms); **384 of 384** requests identical to a fault-free run through **60 random worker kills** |
| **[tandem](https://github.com/Shakhtar-Sankur/tandem)** · [study](https://shakhtar-sankur.github.io/tandem/) | Distributed training with no torch.distributed or NCCL: DDP, **ZeRO-1/2/3** (FSDP-style sharding), **GPipe** and **1F1B** on its own ring all-reduce, and a **C++/CUDA** engine (CUDA IPC, a fused reduce kernel) | On 2× T4, DDP and every ZeRO stage train **bit-identically to PyTorch DDP and FSDP**; all-reduce within **2% of NCCL's bandwidth** at 64–256 MB; the README says where it still loses: **86%** of PyTorch DDP's throughput |
| **[samebit](https://github.com/Shakhtar-Sankur/samebit)** | LLM inference in integers with **the same bits on every chip**: a written spec with proved overflow bounds, run on a real model, **Qwen2.5-0.5B (494M parameters)**, with int8 weights, int16 activations and int64 sums; six independent backends (C99/OpenMP, NumPy, PyTorch, **Apple MLX**, **CUDA**, a plain-Python reference) | Within **0.75%** of float32 perplexity on WikiText-2; logits **bit-identical on an NVIDIA Tesla T4 and an x86 CPU** under every split-K order ([public Kaggle run](https://www.kaggle.com/code/sankurkundu/samebit-qwen2-5-0-5b-in-integers-bit-identical-o)), where PyTorch float16 on the same GPU shifts them by up to 0.25 |

`C++20` `CUDA` `Swift` `Python` `PyTorch`

---

## 📜 The Herculaneum scrolls

| | What it is | What it measures |
|---|---|---|
| **[ink-sensitivity](https://github.com/Shakhtar-Sankur/ink-sensitivity)** · [Kaggle run](https://www.kaggle.com/code/sankurkundu/notebookf235893e91) | **Injection-recovery tests for the Vesuvius Challenge's ink detection**: can today's official model see letters on a scroll no one has read? Real ink from PHerc. 139, located by its published 2.4 µm ink map, is moved into the CT volume of **PHerc. 800**, a scroll eligible for the First Letters prizes, with bare papyrus moved through the same stroke shapes as the control. | The official 9 µm model finds **79%** of the real-ink windows at a 5% false-positive rate (**AUC 0.94**, 168 ink vs 168 controls; no untouched window flagged), and transplanted ink scores like the same text left in place. Read in reversed depth order it finds **0 of 48** real-text windows, so averaging both directions dilutes it; a pure brightness profile of ink, even at 4×, is barely seen. |

`Python` `PyTorch` `zarr` `CT volumes`

---

## ⚛️ Quantum error correction

| | What it is | What it measures |
|---|---|---|
| **[syndrome](https://github.com/Shakhtar-Sankur/syndrome)** · [study](https://shakhtar-sankur.github.io/syndrome/) | An open **GPU decoder for IBM's quantum LDPC codes**: IBM's Relay-BP for the [[144,12,12]] gross code (1,728 detectors, 67,752 error mechanisms, 391,320 edges), written once in C++ for the CPU and a CUDA thread block | On a T4, **bit-identical to IBM's reference on 256 of 256 shots**, in float64 and float32: every decoding, posterior and iteration count, up to all 301 relay legs. **One shot decodes 28.7× faster than IBM's decoder** (median 37.5 ms vs 1.08 s, whole GPU, identical on every shot), and a batch 4.0× faster than IBM's decoder on all CPU threads of the same machine. IBM's published rate reproduced first (**41 vs 44** errors in 10,000) |
| **[parity](https://github.com/Shakhtar-Sankur/parity)** | An open, independent benchmark for **quantum error-correction decoders**: every decoder on the same Stim circuits, noise, seeds and machine, and each one reproduced against its own published claim before it is compared | Reproduced PyMatching 2 / Sparse Blossom's scaling (d = 29 vs 17: **6.2×**, paper 5.6×) and threshold crossings (**0.67–0.80%**); ran NVIDIA's Ising pre-decoders through NVIDIA's own pipeline on **524,288** shots per distance, with inputs checked against NVIDIA's own logs to every printed digit |

`Python` `Stim` `PyMatching` `CUDA`

---

## 🛰️ Space traffic

| | What it is | What it measures |
|---|---|---|
| **[kessler](https://github.com/Shakhtar-Sankur/kessler)** · [live globe](https://shakhtar-sankur.github.io/kessler/) | An independent, open-source **auditor of space traffic**: one **C++** SGP4 propagator compiled for CPU and **CUDA**, all-vs-all conjunction screening with a GPU spatial hash (proven against brute force), collision probability (Foster, Alfano), and a maneuver detector for auditing operators' collision-avoidance reports; it screens all **140 million** pairs of active satellites every day on GitHub Actions, from CelesTrak's open catalogue, and publishes a 3D globe | All **531 million** pairs of the **32,593** tracked objects screened for a day in **28 s** on a T4; reproduces CelesTrak SOCRATES's 100 closest conjunctions (median **0.24 m**) and NASA CARA's 2D probabilities to **1.6e-8**; its Monte Carlo agrees with CARA's on **all 53** of NASA's test conjunctions (χ² p = 0.67), including the 28 where the 2D method is wrong, **15–19×** faster per core than CARA's library |
| **[kessler-commons](https://github.com/Shakhtar-Sankur/kessler-commons)** · in progress | **Orbital Watch**: an open, multi-operator record of what satellites do in orbit, built only on open data. Finds every detectable orbit change of every satellite, by operator, and tags each with geomagnetic storm conditions (NOAA Kp), so storm drag is not mistaken for a manoeuvre | Detector and storm tagging tested on synthetic histories with known manoeuvres; results stay private until the data providers confirm that publishing derived results is allowed |


`C++20` `CUDA` `Python` `NumPy` `GitHub Actions` `three.js`

---

## ⚙️ Systems, from scratch in Rust

| | What it is | What it measures |
|---|---|---|
| **[tessel](https://github.com/Shakhtar-Sankur/tessel)** · [study](https://shakhtar-sankur.github.io/tessel/) | A Triton-style tile language and its compiler: one kernel, compiled to **CUDA** (tensor cores), **Metal** (Apple GPUs) and **Pallas** (TPUs) | On an NVIDIA T4, GEMM at **parity with cuBLAS** (1.00–1.04×) and attention **1.3–1.9× faster than PyTorch SDPA**. An LLM engine built only on its kernels runs TinyLlama-1.1B with output **identical to vLLM's**, token for token, at **1.05× vLLM's throughput** with 32 requests at once |
| **[kiln](https://github.com/Shakhtar-Sankur/kiln)** · [study](https://shakhtar-sankur.github.io/kiln/) | An ML compiler: ONNX through operator fusion and a loop IR to SIMD and CUDA code, auto-tuned | BERT on 4 CPU cores in **117 ms**, against 149 for torch.compile, 153 for ONNX Runtime and 189 for JAX/XLA; on a T4, SmolLM2 **1.65× faster than torch.compile** |
| **[ferrolm](https://github.com/Shakhtar-Sankur/ferrolm)** | An LLM inference server and RAG stack: paged KV cache, continuous batching, prefix caching, speculative decoding | Output matches Hugging Face transformers; **3.4× the throughput** of one-at-a-time serving, first token **46× sooner** with prefix caching; retrieval lifts a 1.7B model's SQuAD F1 from **15 to 48** |
| **[quorumdb](https://github.com/Shakhtar-Sankur/quorumdb)** · [study](https://shakhtar-sankur.github.io/quorumdb/) | A distributed SQL database that psql connects to: LSM storage, Raft, serializable transactions (Percolator) | **10,000 simulated clusters** and **610K crashes**, every history machine-checked; a **TLA+** model of the transaction protocol; **6 real bugs** found before it passed |
| **[faultline](https://github.com/Shakhtar-Sankur/faultline)** | Jepsen-style fault injection for **etcd**: network partitions, crashes and pauses, with linearizability and watch checkers | **1.26M operations** under **288 faults** across 4 etcd release lines; traced lost updates under etcd locks to a paused leader applying a timed-out write **6 s late** |

`Rust` `CUDA` `Metal` `Pallas` `TLA+` — no speed is reported for output that has not first been checked against a reference: fp64, PyTorch, Hugging Face or vLLM.

---

## 🧪 [Populace](https://github.com/Shakhtar-Sankur/populace) — test what needs more than one person

Presence. Live sync. Read receipts. Notification fan-out. "Does deleting this remove it for
everyone." Every permission rule you wrote. **None of it can be tested by one developer with one
account**, however carefully they tap through every screen.

Populace gives you a few dozen believable people who sign up, move through a real city, post, like,
comment, message each other and join groups — as **real authenticated users**, through **your own
API**, with **your own permission rules applying**. Then it reports what broke.

🌐 [Site](https://shakhtar-sankur.github.io/populace/) · 📦 [npm](https://www.npmjs.com/package/@gigzen/populace) · 🪟 [Studio for Windows](https://github.com/Shakhtar-Sankur/populace/releases/latest)

### What it found in a real app

<img src="https://raw.githubusercontent.com/Shakhtar-Sankur/populace/main/docs/buzz-run-2026-08-21.svg" alt="Populace report for Buzz (now Waggle), 21 August 2026 — no failures across 932,455 API calls, 200 simulated drivers across 20 cities in 11 countries" width="100%">

That is the largest run that was clean end to end. The app was called Buzz then and is Waggle now.

The **first** run was in August, before the app launched. Six simulated drivers found **five defects
in three and a half minutes**, after the app had been signed and had passed a full manual test of
every screen. Three were in the app. A fourth app defect turned up in a later run.

The worst one: a privacy fix had restricted writes on `profiles` to a column list, and
`INSERT … ON CONFLICT DO UPDATE` needs `SELECT` on every column it touches — one of which was
deliberately unreadable. **Every new signup silently created no profile row**, and every post and
group-join after it died on a foreign key pointing at the row that was never written.

You never see that alone, because your own account already exists. Populace creates six brand-new
accounts every run and hit it in the first fifteen seconds.

> **You cannot upsert a column you cannot select.** Three of the five defects were that one mistake
> wearing different clothes.

The other two were in Populace's own reference adapter. The worse of those was an **unchecked
error**, the exact fault this tool exists to catch, sitting in our own code. It made the report blame
a later call for a failure that happened during signup. Fixing one line turned three confusing
symptoms into one sentence naming the cause.

Local runs have since made **3.17 million API calls in one day with zero API failures**. One run of
300 drivers still came back *inconclusive* rather than clean, because a single call never reached the
server: a socket was exhausted on the test machine. A verdict that is never withheld is worth nothing
when it is given. Against a hosted project, the largest run put **36 riders through 7,485 calls with
no failures**.

### And to software we did not write

Pointed at a local **Gitea** instance — a git forge, not a social app — it ran **1,106 API calls with
zero failures**, created ten accounts through Gitea's own signup, drove them under Gitea's own
permissions, and removed all ten. Five of the thirteen methods have no equivalent in a git forge, so
they are absent from the adapter rather than stubbed, and the report names each one and what it would
have covered.

**Going in, it found five defects — all of them in Populace.** Gitea's OpenAPI description carries 482
operations against the 18 in the fixture the adapter generator was built on, and at that scale it
mismatched four methods whose correct endpoint was right there in the spec. The best one: `"dm"`
matched inside `"admin"`, so *start a conversation* pointed at `POST /admin/cron/{task}`.

That is the tool doing its job in the least flattering direction available.

*Local runs are loopback latencies and contain no network; the same calls cost about 175 ms against
a hosted project. Three hundred drivers is where throughput stops scaling, not where the app breaks —
that is still unfound.*

`Node` `zero runtime dependencies` — 13-method adapter contract · 3 production guards · 122 self-tests · CI on Node 18 and 22

```bash
npx @gigzen/populace demo
```

Published on npm as **@gigzen/populace** 1.3.4. There is nothing to install first, which is the
zero-dependency claim proving itself. The demo runs against a bundled fake app with a real bug
planted in it. It finds the bug, names the policy, and **exits 1**. That exit code is the point: the
run fails your build instead of telling you everything went fine. CI fails if the bug ever stops
being found.

**Or skip the terminal.** [Populace Studio 1.0.16](https://github.com/Shakhtar-Sankur/populace/releases/latest)
is the same engine in a Windows app. It needs no Node and no npm. It shows every simulated person on a
world map as they move, and a box per contract method with its live latency. A method the run never
called is drawn dashed and named, never counted as covered. When something breaks, it shows the
failing method and the database's own error text while the run is still going. It never
reimplements the engine: every run is the same command a terminal would issue, and the window prints
the command it ran.

---

## 🐝 [Waggle](https://shakhtar-sankur.github.io/gigzen/waggle.html) — local delivery, three apps on one backend

One TypeScript codebase builds three Android apps on a shared Supabase Postgres backend, with
row-level security on every table.

| App | For | |
|---|---|---|
| **Waggle Gig** 1.6.2 | Riders | Offers nearby with the fare up front, spoken directions to the shop and the door, and earnings by the hour. The whole fare is the rider's |
| **Waggle Business** 1.2.0 | Shops | Each order becomes a delivery in one tap, with a 4-digit handover code, a live map of the rider, and GST invoices and payments in one place |
| **Waggle** 1.1.0 | Customers | Order from nearby shops, alone or as a group, now or later, and follow the rider to the door. **Waggle Send** carries parcels across town, up to 10 kg |

Checked as one product: **150 attacks on the database rules, all blocked**, and 42 steps clicked
through all three apps live, from a new rider's verification to the rating at the end of a delivery.

`React` `TypeScript` `Capacitor` `Supabase` — Android 7.0+

All three are signed and in closed testing. They are not on Google Play yet, so the APKs install
from the [site](https://shakhtar-sankur.github.io/gigzen/waggle.html).

**Where it started.** [Waggle 1.4](https://github.com/Shakhtar-Sankur/waggle) is the open-source
rider app that Waggle Gig replaced: a professional and social layer for gig workers in 43 languages
across 92 countries, with posts that queue offline and phone numbers unreadable to other users at
the database level. It is the app Populace was first pointed at.

---

## Also here

Machine learning and signal work from before the company, all of it public:

- [Edge model compression](https://github.com/Shakhtar-Sankur/AI-Model-Compression-for-TSMC-3nm-Chips-Disaster-Classification) — distillation, pruning and int8 quantization to ONNX
- [ML serving platform](https://github.com/Shakhtar-Sankur/ML-Model-Serving-Platform) — versioned rollout, A/B routing, circuit breaking, drift detection
- [Detek](https://github.com/Shakhtar-Sankur/Detek) — data-leak detection on AWS: a BERT content classifier paired with an LSTM behavioural model
- [Predictive maintenance on GCP](https://github.com/Shakhtar-Sankur/Predictive-Maintenance-for-IoT-GCP-Deployed-Real-Time-Optimized) — LSTM failure prediction on a 48-hour horizon
- [Synthetic data with diffusion](https://github.com/Shakhtar-Sankur/Generative-AI-for-Synthetic-Data-Generation) — a DDPM for conditions whose real datasets are tiny and unshareable
- [Multi-modal code intelligence](https://github.com/Shakhtar-Sankur/Multi-Modal-Code-Intelligence-System) — code as tokens and as a syntax tree at once, via tree-sitter
- [Software-defined radio](https://github.com/Shakhtar-Sankur/sdr-signal-processing) — demodulation, modulation classification and decoding, as a library with no hardware needed
- [Reinforcement learning on CartPole](https://github.com/Shakhtar-Sankur/Reinforcement-Learning-for-CartPole-AI) — a DQN written out in full, to be read rather than to win

Each README states its design target, what the code actually measures against it, and where it falls
short. Each also has a test suite that CI runs on every push to main. The compression pipeline aimed
for 8× smaller and measures **−6.3%** — the export got *bigger*. That number is in the repo, along
with why.

---

## The principle both products are built on

> **A system that reports success it has not earned is worse than no system at all.**

It is why a freshly scaffolded Populace adapter honestly reports **2/13 coverage and refuses to
run**, instead of reporting 13/13 and passing while testing nothing. It is why coverage counts only
the methods a run actually called. It is why the −6.3% is published. It is why the line under the
report above says *correctness run, not a load test.*

---

📍 Bhubaneswar, India · open to relocation · working globally · 📧 sankur.kundu.tw@gmail.com · 🔗 [LinkedIn](https://linkedin.com/in/sankur-kundu)
