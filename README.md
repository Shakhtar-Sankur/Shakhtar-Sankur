# Sankur Kundu

**Co-founder & Director, Technology at Gigzen.** I build systems that measure themselves.

Two products, both written solo, from Postgres policies to the release build.

🌐 [gigzen](https://shakhtar-sankur.github.io/gigzen/) · 🧑‍💻 [portfolio](https://shakhtar-sankur.github.io)

---

### 🐝 [Buzz Buzz](https://github.com/Shakhtar-Sankur/buzz-buzz) — a home for gig workers

A Swiggy rider, an Uber driver and an Amazon Flex courier are often the same person, but no
platform connects those identities. Buzz Buzz is the professional and social layer across all of
them — GPS trip tracking with live earnings, a community feed, chat with read receipts, and 16
languages including right-to-left Arabic. It keeps working underground: anything written
without a signal is queued on the device and sent when the connection returns.
**Free for workers, permanently.**

`React` `TypeScript` `Capacitor` `Supabase` — 13,235 lines · 17 tables · 48 row-level-security policies

### 🧪 [Populace](https://github.com/Shakhtar-Sankur/populace) — a simulated population for your app

You cannot test presence, live sync, read receipts or notification fan-out while being only one
person. Populace gives you dozens of believable people who sign up, move, post, comment and message
each other — as real authenticated users, through your own API, with your own permission rules
applying. Then it reports what broke.

Built to test Buzz Buzz, and deliberately kept free of any reference to it — so Buzz Buzz became its
first customer rather than its purpose.

`Node` `zero runtime dependencies` — 13-method adapter contract · 3 production guards · 20/20 self-tests

`populace demo` runs the whole thing against a bundled fake app that has a real bug in it — no
backend, no signup. CI fails the build if that bug ever stops being found.

---

### Also here

Machine learning work from before the company: a compression pipeline for edge inference, a model
serving platform, serverless security analytics on AWS, and predictive maintenance on GCP.

Each README states its design target, what the code actually measures against it, and where it
falls short. The compression pipeline aimed for 8× smaller and measures **−6.3%** — the export got
bigger. That number is in the repo, along with why.

### The principle both products are built on

> A system that reports success it has not earned is worse than no system at all.

It is why a freshly scaffolded Populace adapter honestly reports **2/13 coverage and refuses to
run**, instead of reporting 13/13 and passing while testing nothing.

---

📍 Bhubaneswar, India · 📧 sankur.kundu.tw@gmail.com · 🔗 [LinkedIn](https://linkedin.com/in/sankur-kundu)
