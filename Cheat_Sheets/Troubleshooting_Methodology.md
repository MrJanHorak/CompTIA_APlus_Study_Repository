# Cheat Sheet: CompTIA 6-Step Troubleshooting Methodology

> This framework applies universally — hardware faults, network outages, OS failures, security incidents, printer jams. Mastering it is essential for both Performance-Based Questions (PBQs) and real-world career readiness.

---

## The 6-Step Process

| Step | Name                                            | Core Question                |
| ---- | ----------------------------------------------- | ---------------------------- |
| 1    | Identify the Problem                            | What exactly is wrong?       |
| 2    | Establish a Theory of Probable Cause            | Why might this be happening? |
| 3    | Test the Theory                                 | Is my theory correct?        |
| 4    | Establish a Plan of Action                      | How will I fix it safely?    |
| 5    | Implement the Solution and Verify Functionality | Did my fix work?             |
| 6    | Document Findings, Actions, and Outcomes        | What did I learn and record? |

---

## Step-by-Step Detail

### Step 1 — Identify the Problem

**Goal:** Gather complete, accurate information before forming any theory.

Key actions:

- **Talk to the user** — ask open-ended questions: "What were you doing when this happened?" "Has this happened before?"
- **Identify symptoms** — not just the reported issue; look for related symptoms that may point to the root cause
- **Determine what has changed recently** — updates installed, new hardware connected, new software, physical moves, network changes
- **Check system event logs** — Windows Event Viewer, application logs, system logs
- **Duplicate the problem if possible** — reproduce the issue to confirm it is consistent and understand the conditions

> **Avoid jumping to solutions.** Many wrong repairs stem from diagnosing too quickly. A complete identification step saves time overall.

---

### Step 2 — Establish a Theory of Probable Cause

**Goal:** Form a plausible hypothesis based on the gathered information.

Key actions:

- **Question the obvious** — The simplest explanation is often correct (Occam's Razor)
- **Start with the most common causes** — Loose cable before failed motherboard; driver issue before hardware failure
- **Consider multiple theories** — List 2–3 possibilities, ranked by likelihood
- **Research if needed** — Consult internal knowledge bases, vendor documentation, and online resources
- **Check the physical layer first** — Network issues often start with a disconnected cable

> Example: A printer won't print → Theory 1: Paper jam. Theory 2: Print spooler error. Theory 3: Driver corrupt. Start with Theory 1.

---

### Step 3 — Test the Theory to Determine the Cause

**Goal:** Confirm or eliminate the theory through controlled testing.

Key actions:

- **Isolate variables** — Change **only one thing at a time**
- **Confirm the theory** — If the change resolves the issue, the theory was correct; proceed to Step 4
- **If the theory is wrong** — Return to Step 2 with new information
- **Escalate if necessary** — If testing is beyond your tools or expertise, escalate to the appropriate team

> **Critical principle:** Never change multiple components simultaneously when troubleshooting. If you swap three parts and the problem goes away, you do not know which change fixed it — and you may have replaced good parts needlessly.

---

### Step 4 — Establish a Plan of Action and Identify Potential Effects

**Goal:** Build a roadmap to fix the confirmed problem safely and predictably.

Key actions:

- **Define the fix** — Document exactly what changes will be made
- **Risk assessment** — Will the fix cause downtime? Could it affect other systems?
- **Create a rollback plan** — How will you restore the previous state if the fix fails? (Snapshot, backup, driver rollback)
- **Communicate with stakeholders** — Inform the user and management about expected impact, downtime, and timeline
- **Schedule appropriately** — Use a maintenance window for changes affecting business-critical systems

---

### Step 5 — Implement the Solution and Verify Full System Functionality

**Goal:** Apply the fix, then **confirm the issue is fully resolved** and no new issues were introduced.

Key actions:

- **Implement the plan** exactly as documented
- **Test the specific fix** — Confirm the original symptom is gone
- **Check for side effects** — Did the fix affect anything else?
- **Test the entire affected system** — Not just the reported issue (e.g., after fixing a DNS issue, test all DNS-dependent applications)
- **Implement preventive measures** — Update firmware, install security patches, enforce policy changes to prevent recurrence

> If the fix does not work, **execute the rollback plan** and return to Step 2 with the new information gained.

---

### Step 6 — Document Findings, Actions, and Outcomes

**Goal:** Create a formal record of the entire incident for organizational knowledge.

Key actions:

- **Record what the problem was** — including exact symptoms and affected systems
- **Record what caused it** — the root cause identified in Step 3
- **Record what was done** — each action taken, in order, with timestamps
- **Record the outcome** — was the issue fully resolved?
- **Update the knowledge base** — if this is a recurring issue, document the fix so future technicians can resolve it faster
- **File an incident report** if required by policy (security incidents, significant outages)

> **Why document?** The most experienced technician cannot remember every fix for every system indefinitely. Documentation protects the organization, protects you, enables continuity, and builds institutional knowledge.

---

## Common Exam Scenarios

### Scenario: Network Connectivity Issue

| Step          | Action                                                                                                                          |
| ------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| 1 — Identify  | User says "I can't get to the internet." Check other devices on the same network.                                               |
| 2 — Theory    | Theory: DHCP failure (APIPA address). Check with `ipconfig`.                                                                    |
| 3 — Test      | Run `ipconfig` → sees `169.254.x.x`. Theory confirmed.                                                                          |
| 4 — Plan      | Plan: Run `ipconfig /release` then `ipconfig /renew`. If DHCP fails again, restart DHCP server.                                 |
| 5 — Implement | Run commands. New valid IP assigned. Internet restored.                                                                         |
| 6 — Document  | "User had APIPA address; DHCP lease was not renewing. Forced renew resolved issue. DHCP server log reviewed — no errors found." |

---

### Scenario: Application Not Starting

| Step          | Action                                                                                         |
| ------------- | ---------------------------------------------------------------------------------------------- |
| 1 — Identify  | "App crashes immediately on launch." Check Event Viewer for application error codes.           |
| 2 — Theory    | Theory: Missing Visual C++ redistributable after recent Windows update.                        |
| 3 — Test      | Check installed programs — redistributable is listed. Check app version compatibility instead. |
| 4 — Plan      | Reinstall the application. Create a restore point first.                                       |
| 5 — Implement | Uninstall and reinstall. App launches successfully.                                            |
| 6 — Document  | "App crash after Windows update. Reinstall resolved. Possibly related to update KB number."    |

---

## Key Principles to Remember for the Exam

1. **Do not skip steps** — especially under time pressure. The methodology exists because shortcuts create new problems.
2. **Change one variable at a time** — this is the most frequently tested concept in troubleshooting scenarios.
3. **Always have a rollback plan** before making changes to a production system.
4. **Documentation is not optional** — expect one or more questions testing whether students value documentation.
5. **Escalation is acceptable** — knowing when a problem is beyond your current scope is a professional skill.

---

_See also: [Core_1/1.5_Hardware_and_Network_Troubleshooting.md](../Core_1/1.5_Hardware_and_Network_Troubleshooting.md) and [Core_2/2.3_Software_Troubleshooting.md](../Core_2/2.3_Software_Troubleshooting.md)_
