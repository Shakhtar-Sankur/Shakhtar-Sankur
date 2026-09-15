# Sankur Kundu

**Co-founder & Head of Engineering at Gigzen.** I build systems that measure themselves.

Two products, both written solo, from Postgres policies to the signed release build. One is
**Waggle**, a gig-worker app in 43 languages across 92 countries. The other is **Populace**, the
testing tool I had to build to prove the first one worked. Its first run found five defects in three
and a half minutes, after a full manual test had passed.

🌐 [gigzen](https://shakhtar-sankur.github.io/gigzen/) · 🧑‍💻 [portfolio](https://shakhtar-sankur.github.io) · 📧 sankur.kundu.tw@gmail.com

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

`Node` `zero runtime dependencies` — 13-method adapter contract · 3 production guards · 121 self-tests · CI on Node 18 and 22

```bash
npx @gigzen/populace demo
```

Published on npm as **@gigzen/populace** 1.3.3. There is nothing to install first, which is the
zero-dependency claim proving itself. The demo runs against a bundled fake app with a real bug
planted in it. It finds the bug, names the policy, and **exits 1**. That exit code is the point: the
run fails your build instead of telling you everything went fine. CI fails if the bug ever stops
being found.

**Or skip the terminal.** [Populace Studio 1.0.15](https://github.com/Shakhtar-Sankur/populace/releases/latest)
is the same engine in a Windows app. It needs no Node and no npm. It shows every simulated person on a
world map as they move, and a box per contract method with its live latency. A method the run never
called is drawn dashed and named, never counted as covered. When something breaks, it shows the
failing method and the database's own error text while the run is still going. It never
reimplements the engine: every run is the same command a terminal would issue, and the window prints
the command it ran.

---

## 🐝 [Waggle](https://github.com/Shakhtar-Sankur/waggle) — a home for gig workers

A Swiggy rider, an Uber driver and an Amazon Flex courier are often the same person, but no platform
connects those identities. Waggle is the professional and social layer across all of them.

🌐 [Site](https://shakhtar-sankur.github.io/gigzen/waggle.html) · 📱 [Download the APK](https://shakhtar-sankur.github.io/gigzen/Waggle-1.4.3.apk)

| | |
|---|---|
| **Earnings that follow the road** | Money accrues from distance genuinely travelled — a stationary phone earns nothing, so sitting in traffic cannot inflate the number |
| **A map with two modes** | *Me* draws the roads you actually drove, any day you pick, matched onto the street network rather than joining GPS fixes with straight lines. *Friends* shows where your connections are now. Sharing your position is **off** until you turn it on |
| **The street, told by the street** | Flooding, surges, closures, queues — from the drivers who just came through them |
| **Works underground** | Posts and messages written with no signal queue on the device and send on reconnect |
| **43 languages** | Consent and legal text included, mirrored right-to-left for Arabic, Urdu and Hebrew |
| **70 currencies, 92 countries, 33 gig platforms** | Selected automatically from where the rider actually is |
| **Privacy enforced by the database** | Row-level security on every table. Phone numbers are unreadable to other users — not hidden in the UI, **unreadable** |

`React` `TypeScript` `Capacitor` `Supabase` — Android 7.0+ · 8.2 MB

Version 1.4.3, signed, in closed testing. It is not on Google Play yet, so the APK installs from the
site. **Free for workers, permanently** — funded by enterprise supply, fleet APIs and workforce
analytics, the shape that funded LinkedIn and Waze.

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
run**, instead of reporting 13/13 and passing while testing nothing. It is why coverage counts only
the methods a run actually called. It is why the −6.3% is published. It is why the line under the
report above says *correctness run, not a load test.*

---

📍 Bhubaneswar, India · working globally · 📧 sankur.kundu.tw@gmail.com · 🔗 [LinkedIn](https://linkedin.com/in/sankur-kundu)
