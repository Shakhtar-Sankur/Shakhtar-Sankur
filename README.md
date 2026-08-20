# Sankur Kundu

**Co-founder & Director, Technology at Gigzen.** I build systems that measure themselves.

Two products, both written solo, from Postgres policies to the signed release build. One is a
gig-worker platform shipping in 16 languages across 49 countries. The other is the testing tool I
had to build to prove the first one worked — and it found five bugs in it that a full manual test
had missed.

🌐 [gigzen](https://shakhtar-sankur.github.io/gigzen/) · 🧑‍💻 [portfolio](https://shakhtar-sankur.github.io) · 📧 sankur.kundu.tw@gmail.com

---

## 🧪 [Populace](https://github.com/Shakhtar-Sankur/populace) — test what needs more than one person

Presence. Live sync. Read receipts. Notification fan-out. "Does deleting this remove it for
everyone." Every permission rule you wrote. **None of it can be tested by one developer with one
account**, however carefully they tap through every screen.

Populace gives you a few dozen believable people who sign up, move through a real city, post, like,
comment, message each other and join groups — as **real authenticated users**, through **your own
API**, with **your own permission rules applying**. Then it reports what broke.

### It has done this to a real, finished app

<img src="https://raw.githubusercontent.com/Shakhtar-Sankur/populace/main/docs/buzz-run-2026-08-15.svg" alt="Populace report for Buzz, 15 August 2026 — no failures across 6,539 API calls, 30 simulated drivers across Manila and Mumbai" width="100%">

That is the largest run that was clean end to end. On the **first** run, six simulated drivers found
**five bugs in three and a half minutes** in an app that was finished, signed, and had just passed a
full manual test of every screen. It has found **eight** across both products since.

The worst one: a privacy fix had restricted writes on `profiles` to a column list, and
`INSERT … ON CONFLICT DO UPDATE` needs `SELECT` on every column it touches — one of which was
deliberately unreadable. **Every new signup silently created no profile row**, and every post and
group-join after it died on a foreign key pointing at the row that was never written.

You never see that alone, because your own account already exists. Populace creates six brand-new
accounts every run and hit it in the first fifteen seconds.

> **You cannot upsert a column you cannot select.** Three of the five bugs were that one mistake
> wearing different clothes.

Two of the five were in Populace's own reference adapter, and the worse of those was an **unchecked
error** — the exact fault this tool exists to catch, sitting in our own code. It made the report
blame a later call for a failure that happened during signup. Fixing one line turned three
confusing symptoms into one sentence naming the cause.

*Thirty concurrent users is the highest figure tested, not a measured maximum — the runs stopped at a
signup quota, never because the app slowed down. Populace now drives two unrelated backends, but both
of them are still ours; the next should be someone else's.*

`Node` `zero runtime dependencies` — 13-method adapter contract · 3 production guards · 78 self-tests · CI on Node 18 and 22

```bash
npx @gigzen/populace demo
```

Published on npm as **@gigzen/populace**. No install step and nothing to install, which is the
zero-dependency claim proving itself.
It runs against a bundled fake app with a real bug planted in it, finds the bug, names the policy,
and **exits 1**. That exit code is the whole point: the run fails your build rather than telling you
everything went fine. CI fails if the bug ever stops being found.

---

## 🐝 [Buzz](https://github.com/Shakhtar-Sankur/buzz-buzz) — a home for gig workers

A Swiggy rider, an Uber driver and an Amazon Flex courier are often the same person, but no platform
connects those identities. Buzz is the professional and social layer across all of them.

| | |
|---|---|
| **Earnings that follow the road** | Money accrues from distance genuinely travelled — a stationary phone earns nothing, so sitting in traffic cannot inflate the number |
| **A map with people on it** | Live driver positions, search any city or street on earth. Sharing your position is **off** until you turn it on |
| **The street, told by the street** | Flooding, surges, closures, queues — from the drivers who just came through them |
| **Works underground** | Posts and messages written with no signal queue on the device and send on reconnect |
| **16 languages at full parity** | 278 keys each, consent and legal text included, mirrored right-to-left for Arabic |
| **27 currencies, 49 countries** | Selected automatically from where the driver actually is |
| **Privacy enforced by the database** | 48 row-level-security policies. Phone numbers are unreadable to other users — not hidden in the UI, **unreadable**, and a migration assertion fails if that ever stops being true |

`React` `TypeScript` `Capacitor` `Supabase` — 13,235 lines · 17 tables · 48 RLS policies · 7.9 MB

Signed and live on Google Play's internal track. **Free for workers, permanently** — funded by
enterprise supply, fleet APIs and workforce analytics, the shape that funded LinkedIn and Waze.

---

## Also here

Machine learning work from before the company: a compression pipeline for edge inference, a model
serving platform, serverless security analytics on AWS, and predictive maintenance on GCP.

Each README states its design target, what the code actually measures against it, and where it falls
short. The compression pipeline aimed for 8× smaller and measures **−6.3%** — the export got
*bigger*. That number is in the repo, along with why.

---

## The principle both products are built on

> **A system that reports success it has not earned is worse than no system at all.**

It is why a freshly scaffolded Populace adapter honestly reports **2/13 coverage and refuses to
run**, instead of reporting 13/13 and passing while testing nothing. It is why the −6.3% is
published. It is why the line under the report above says *correctness run, not a load test.*

---

📍 Bhubaneswar, India · working globally · 📧 sankur.kundu.tw@gmail.com · 🔗 [LinkedIn](https://linkedin.com/in/sankur-kundu)
