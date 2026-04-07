# CompTIA A+ Study Repository

> A structured, evidence-based study framework for the CompTIA A+ Core 1 and Core 2 certification exams.

![Exam Codes](https://img.shields.io/badge/Exam%20Codes-220--1201%20%7C%20220--1202-blue)
![Version](<https://img.shields.io/badge/Version-15%20(2025)-green>)
![License](https://img.shields.io/badge/License-MIT-yellow)
![Contributions Welcome](https://img.shields.io/badge/Contributions-Welcome-brightgreen)

---

## Purpose

This repository provides a complete, community-maintained study resource for students preparing for the **CompTIA A+** certification. It integrates technical reference material with proven cognitive science learning strategies — spaced repetition, active recall, and the Feynman Technique — to move students beyond rote memorization toward genuine, exam-ready mastery.

Whether you are a first-time IT student or an experienced technician refreshing your credentials for the 2025 Version 15 exams, this resource is designed to serve as your primary study hub.

---

## Who This Is For

- Students pursuing their first IT certification
- Help desk and desktop support professionals validating their skills
- Self-taught technicians who need a structured study path
- Instructors looking for a classroom-ready framework

---

## Exam Version Overview

| Exam   | Code (v14) | Code (v15) | Launch     |
| ------ | ---------- | ---------- | ---------- |
| Core 1 | 220-1101   | 220-1201   | Early 2025 |
| Core 2 | 220-1102   | 220-1202   | Early 2025 |

> **Note:** Both v14 and v15 exams are currently active. Check the [CompTIA website](https://www.comptia.org/certifications/a) for exam retirement dates. The notes in this repository are aligned with **Version 15 (220-1201 / 220-1202)** objectives but call out major changes from v14 where relevant.

---

## Table of Contents

- [How to Use This Repository](#how-to-use-this-repository)
- [Repository Structure](#repository-structure)
- [Core 1: Hardware & Infrastructure](#core-1-hardware--infrastructure)
- [Core 2: Software & Operational Security](#core-2-software--operational-security)
- [Cheat Sheets](#cheat-sheets)
- [Resources](#resources)
- [Labs](#labs)
- [Recommended Study Schedule](#recommended-study-schedule)
- [Contributing](#contributing)

---

## How to Use This Repository

### Recommended Path for New Students

1. **Start with the Study Strategies guide** → [Resources/Study_Strategies.md](Resources/Study_Strategies.md)
   Understand _how_ to learn before diving into _what_ to learn.

2. **Work through Core 1 domains in order**
   Each domain folder contains objective-aligned notes. Read one objective section per study session.

3. **After each section, drill the Cheat Sheets**
   The `Cheat_Sheets/` folder contains condensed tables for fast review.

4. **Set up your flashcard system**
   Use the guidance in [Resources/Flashcards/README.md](Resources/Flashcards/README.md) to build or import Anki/Quizlet decks.

5. **Complete Core 2 domains** using the same approach.

6. **Run practice exams** (see [Resources/Recommended_Resources.md](Resources/Recommended_Resources.md)) until you score **85%+** consistently.

7. **Do at least two labs** from the `Labs/` directory to convert knowledge into hands-on skill.

---

## Repository Structure

```
A+ Resources/
├── README.md                         ← You are here
├── CONTRIBUTING.md                   ← How to contribute
├── LICENSE
│
├── Core_1/                           ← Exam 220-1201 (Hardware & Infrastructure)
│   ├── README.md
│   ├── 1.1_Mobile_Devices.md
│   ├── 1.2_Networking.md
│   ├── 1.3_Hardware.md
│   ├── 1.4_Virtualization_and_Cloud.md
│   └── 1.5_Hardware_and_Network_Troubleshooting.md
│
├── Core_2/                           ← Exam 220-1202 (Software & Operational Security)
│   ├── README.md
│   ├── 2.1_Operating_Systems.md
│   ├── 2.2_Security.md
│   ├── 2.3_Software_Troubleshooting.md
│   └── 2.4_Operational_Procedures.md
│
├── Cheat_Sheets/                     ← Quick-reference tables and mnemonics
│   ├── Ports_and_Protocols.md
│   ├── Hardware_Reference.md
│   ├── RAID_Reference.md
│   ├── Command_Line_Reference.md
│   └── Troubleshooting_Methodology.md
│
├── Resources/                        ← Learning tools and external links
│   ├── Study_Strategies.md
│   ├── Recommended_Resources.md
│   └── Flashcards/
│       └── README.md
│
└── Labs/                             ← Hands-on exercises
    ├── README.md
    ├── Lab_01_Home_Lab_Setup.md
    └── Lab_02_Network_Simulation.md
```

---

## Core 1: Hardware & Infrastructure

| Domain | Topic                                                                                      | Exam Weight |
| ------ | ------------------------------------------------------------------------------------------ | ----------- |
| 1.0    | [Mobile Devices](Core_1/1.1_Mobile_Devices.md)                                             | ~15%        |
| 2.0    | [Networking](Core_1/1.2_Networking.md)                                                     | ~23%        |
| 3.0    | [Hardware](Core_1/1.3_Hardware.md)                                                         | ~25%        |
| 4.0    | [Virtualization and Cloud Computing](Core_1/1.4_Virtualization_and_Cloud.md)               | ~12%        |
| 5.0    | [Hardware and Network Troubleshooting](Core_1/1.5_Hardware_and_Network_Troubleshooting.md) | ~25%        |

---

## Core 2: Software & Operational Security

| Domain | Topic                                                              | Exam Weight |
| ------ | ------------------------------------------------------------------ | ----------- |
| 1.0    | [Operating Systems](Core_2/2.1_Operating_Systems.md)               | ~31%        |
| 2.0    | [Security](Core_2/2.2_Security.md)                                 | ~25%        |
| 3.0    | [Software Troubleshooting](Core_2/2.3_Software_Troubleshooting.md) | ~22%        |
| 4.0    | [Operational Procedures](Core_2/2.4_Operational_Procedures.md)     | ~22%        |

---

## Cheat Sheets

Quick-reference documents designed for rapid review sessions and last-minute cramming.

| Sheet                                                                      | Contents                                      |
| -------------------------------------------------------------------------- | --------------------------------------------- |
| [Ports & Protocols](Cheat_Sheets/Ports_and_Protocols.md)                   | All required port numbers with mnemonics      |
| [Hardware Reference](Cheat_Sheets/Hardware_Reference.md)                   | RAM pin counts, connector types, form factors |
| [RAID Reference](Cheat_Sheets/RAID_Reference.md)                           | RAID levels, functions, fault tolerance       |
| [Command-Line Reference](Cheat_Sheets/Command_Line_Reference.md)           | Windows, Linux, and macOS CLI commands        |
| [Troubleshooting Methodology](Cheat_Sheets/Troubleshooting_Methodology.md) | CompTIA 6-step process with key actions       |

---

## Resources

| Resource                                                    | Description                                         |
| ----------------------------------------------------------- | --------------------------------------------------- |
| [Study Strategies](Resources/Study_Strategies.md)           | Spaced repetition, active recall, Feynman Technique |
| [Recommended Resources](Resources/Recommended_Resources.md) | Vetted courses, practice exams, and free tools      |
| [Flashcard Guide](Resources/Flashcards/README.md)           | How to build and use Anki/Quizlet decks             |

---

## Labs

| Lab                                                             | Description                                     |
| --------------------------------------------------------------- | ----------------------------------------------- |
| [Lab 01: Home Lab Setup](Labs/Lab_01_Home_Lab_Setup.md)         | Build a free virtualized practice environment   |
| [Lab 02: Network Simulation](Labs/Lab_02_Network_Simulation.md) | Configure routers and switches in Packet Tracer |

---

## Recommended Study Schedule

This schedule uses the **spaced repetition** intervals proven by cognitive science research to maximize long-term retention.

| Review Session | Timing                      | Technique                                       |
| -------------- | --------------------------- | ----------------------------------------------- |
| First Review   | Within 24 hours of learning | Summarize key points; create initial flashcards |
| Second Review  | 3 days later                | Active recall — test without notes              |
| Third Review   | 7 days later                | Practice questions or "blurting" exercise       |
| Fourth Review  | 14 days later               | Integrate into a full domain review session     |
| Fifth Review   | 30 days later               | Timed mock exam validation                      |

A realistic full study timeline for a student studying **1–2 hours per day**:

- **Weeks 1–3:** Core 1 domains + daily flashcard drills
- **Weeks 4–5:** Core 1 practice exams + weak area review
- **Weeks 6–8:** Core 2 domains + daily flashcard drills
- **Weeks 9–10:** Core 2 practice exams + comprehensive review
- **Week 11:** Full mock exams for both cores; target 85%+ before scheduling

---

## Contributing

Contributions are welcome and encouraged. See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines on submitting corrections, adding new content, or sharing flashcard decks.

---

_This repository is not affiliated with or endorsed by CompTIA. All exam objectives referenced are the property of CompTIA._
