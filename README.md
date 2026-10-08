# Sankur Kundu

**Co-founder & Founding Engineer at Gigzen.** I build systems that measure themselves.

Two products, both written solo, from Postgres policies to the signed release build. One is
**Waggle**, local delivery as three Android apps (for riders, shops and customers) on one Postgres
backend. The other is **Populace**, the testing tool I had to build to prove Waggle worked. Its first
run found five defects in three and a half minutes, after a full manual test had passed.

Alongside them, systems written from scratch: reinforcement-learning post-training of an LLM on two
GPUs, sandboxed RL environments for coding agents, mixture-of-experts serving across GPUs, an LLM
inference cluster in C++, CUDA and Swift, distributed training on my own collectives, and five Rust
systems with no dependencies. Each has the scripts and raw results behind its numbers in the repo.

🌐 [gigzen](https://shakhtar-sankur.github.io/gigzen/) · 🧑‍💻 [portfolio](https://shakhtar-sankur.github.io) · 📧 sankur.kundu.tw@gmail.com

---

## 🚀 LLM training, serving and distributed training

| | What it is | What it measures |
|---|---|---|
| **[switchyard](https://github.com/Shakhtar-Sankur/switchyard)** | Mixture-of-experts serving with **expert parallelism** from scratch: OLMoE-1B-7B across 2 GPUs on my own **CUDA** kernels (routing, sorting, tensor-core grouped GEMM/GEMV) and **peer-to-peer** dispatch in place of NCCL | **Bit-identical** to one GPU; decodes **2.2× faster** than Hugging Face (112 vs 52 tok/s at batch 8); dispatch **1.25× faster** than NCCL all-to-all at 256 tokens/GPU; measured that dropping overflow tokens raises perplexity **12.9 → 20.2**, so it never drops one |
| **[ratchet](https://github.com/Shakhtar-Sankur/ratchet)** | Reinforcement-learning post-training (**GRPO**) from scratch: rollouts with per-token log-probabilities on relay, a **PyTorch** trainer data-parallel on tandem, weights synced back **in place on the GPU**, partial rollouts and one-step-ahead training | On 2× T4, 100 steps raised Qwen2.5-0.5B on **GSM8K** from **48.1% to 52.5%** (all 1,319 test problems); weight sync **369× faster** than a reload (0.017 s); found that fp16 rounding silently discarded the training updates and fixed it (engine–trainer log-prob gap **5.2 → 0.04**) |
| **[crucible](https://github.com/Shakhtar-Sankur/crucible)** | Sandboxed environments for training **coding agents with RL**: sandboxes built from **Linux namespaces, seccomp-BPF** and resource limits, forked from a warm process (no VMs), forkable mid-episode; an **OpenEnv**-compatible server whose grader runs the tests outside the model's code | **GRPO** on ratchet with every reward from a sandbox lifted MBPP pass@1 **34.9% → 38.6%** (mean of **3 seeds**, paired test **p = 0.013**); **0 of 9** reward hacks pass its grader (the usual grader: 4); a live sandbox forks in **4.5 ms** vs 138 ms to rebuild |
| **[relay](https://github.com/Shakhtar-Sankur/relay)** | A disaggregated LLM inference cluster: prefill and decode workers in **C++20/CUDA** with my own **flash-attention** and **flash-decoding** kernels, a KV-cache transfer engine, and a **Swift** control plane (C++ interop, OpenAI-compatible streaming API, prefix-aware routing). Fault-tolerant | On a T4, 2,048-token prefill **8.7× faster** and 32-sequence decode **5.4× faster** than its first kernels; streaming hides **99–100%** of the KV transfer (21.6 ms → 0.08 ms); **384 of 384** requests identical to a fault-free run through **60 random worker kills** |
| **[tandem](https://github.com/Shakhtar-Sankur/tandem)** | Distributed training with no torch.distributed or NCCL: DDP, **ZeRO-1/2/3** (FSDP-style sharding), **GPipe** and **1F1B** on its own ring all-reduce, and a **C++/CUDA** engine (CUDA IPC, a fused reduce kernel) | On 2× T4, DDP and every ZeRO stage train **bit-identically to PyTorch DDP and FSDP**; all-reduce within **2% of NCCL's bandwidth** at 64–256 MB; the README says where it still loses: **86%** of PyTorch DDP's throughput |

**Open source:** three pull requests to PyTorch, all under review.
[#199875](https://github.com/pytorch/pytorch/pull/199875) makes torch.compile fill `torch.empty` in
deterministic mode as eager does, without filling Inductor's own buffers, which is what got an earlier
fix reverted; [#199441](https://github.com/pytorch/pytorch/pull/199441) checked all 37 Inductor-skipped tests in
`test_torch.py` on CPU and two T4 GPUs and removes 13 stale torch.compile skips;
[#199646](https://github.com/pytorch/pytorch/pull/199646) traces 19 skipped determinism tests to a
forward/backward mode mismatch, so 8 now run under torch.compile and 11 stay skipped with verified causes.

`C++20` `CUDA` `Swift` `Python` `PyTorch`

---

## ⚙️ Systems, from scratch in Rust

| | What it is | What it measures |
|---|---|---|
| **[tessel](https://github.com/Shakhtar-Sankur/tessel)** | A Triton-style tile language and its compiler: one kernel, compiled to **CUDA** (tensor cores), **Metal** (Apple GPUs) and **Pallas** (TPUs) | On an NVIDIA T4, GEMM at **parity with cuBLAS** (1.00–1.04×) and attention **1.3–1.9× faster than PyTorch SDPA**. An LLM engine built only on its kernels runs TinyLlama-1.1B with output **identical to vLLM's**, token for token, at **1.05× vLLM's throughput** with 32 requests at once |
| **[kiln](https://github.com/Shakhtar-Sankur/kiln)** | An ML compiler: ONNX through operator fusion and a loop IR to SIMD and CUDA code, auto-tuned | BERT on 4 CPU cores in **117 ms**, against 149 for torch.compile, 153 for ONNX Runtime and 189 for JAX/XLA; on a T4, SmolLM2 **1.65× faster than torch.compile** |
| **[ferrolm](https://github.com/Shakhtar-Sankur/ferrolm)** | An LLM inference server and RAG stack: paged KV cache, continuous batching, prefix caching, speculative decoding | Output matches Hugging Face transformers; **3.4× the throughput** of one-at-a-time serving, first token **46× sooner** with prefix caching; retrieval lifts a 1.7B model's SQuAD F1 from **15 to 48** |
| **[quorumdb](https://github.com/Shakhtar-Sankur/quorumdb)** | A distributed SQL database that psql connects to: LSM storage, Raft, serializable transactions (Percolator) | **10,000 simulated clusters** and **610K crashes**, every history machine-checked; a **TLA+** model of the transaction protocol; **6 real bugs** found before it passed |
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
