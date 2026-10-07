# Decentralized Synchronization Engine for Real-Time Applications

**An undergraduate thesis (TCC) by Guilherme Focassio dos Santos**
Information Systems · Federal University of Santa Catarina (UFSC)

[![Build Status](https://github.com/guiklose/graduation-thesis/actions/workflows/checks.yml/badge.svg)](https://github.com/guiklose/graduation-thesis/actions)
![Status](https://img.shields.io/badge/status-work--in--progress-yellow)
![Expected](https://img.shields.io/badge/defense-2027-blue)

---

## About Me

I'm Guilherme, an Information Systems undergraduate at UFSC (INE — Departamento
de Informática e Estatística, CTC — Centro Tecnológico). This repository is
where I'm writing, versioning, and building my thesis — in the open, the way
software gets built, not locked away in a single `.docx` file on someone's
laptop.

📫 [guilhermeklosesantos@gmail.com](mailto:guilhermeklosesantos@gmail.com) · [@guiklose](https://github.com/guiklose)

## About This Research

Every time you drag a pin on a shared map, drop a sticky note on a collaborative
board, or watch a cursor move in real time next to yours, something is quietly
resolving a hard problem: **what happens when two people change the same thing
at the same moment, and there's no central server around to say who's right?**

The client-server model answered that question for decades by simply
*having* a central authority — but centralization has a cost: a single point
of failure, a scalability ceiling, and a server bill that grows with every
user. Peer-to-peer architectures removed that single point of failure once
before — Napster, Gnutella, BitTorrent, Kademlia — but they were built for
static, immutable data: a file's hash doesn't change. Modern interactive
systems are the opposite: state changes *constantly*, from multiple places,
at the same time.

This thesis asks what happens if you take that same decentralized, no-single-point-of-failure
philosophy and apply it to **live, mutable, real-time state** instead —
without falling back on a central server to arbitrate conflicts.

**The approach:** a low-level, domain-agnostic synchronization engine built
around **Conflict-free Replicated Data Types (CRDTs)** and logical event
ordering, designed to guarantee *Strong Eventual Consistency* across peers
with no central coordinator. To validate it, the thesis builds a proof of
concept: real-time synchronization of an interactive map across multiple
simultaneous users — the kind of workload where latency, convergence time,
and correctness under concurrent edits actually matter.

### Research Goals

- Study the theoretical foundations of consistency in decentralized
  distributed systems — CRDTs, logical clocks, gossip protocols;
- Design a modular, low-level synchronization engine: async network I/O,
  data framing, multi-threaded concurrency control, volatile-state
  persistence;
- Implement the middleware with a focus on runtime performance —
  zero-copy serialization, concurrency-friendly data structures;
- Build a working proof-of-concept application that exercises the engine
  under real, concurrent, multi-user load;
- Measure it: replica convergence time, gossip payload/network throughput,
  induced latency, CPU and memory consumption;
- Document the design trade-offs, the engineering lessons, and the open
  questions for future work.

## Status

This is a living thesis, not a finished one — the repository evolves as the
research does.

| | |
|---|---|
| **Advisor** | Prof. Odorico Machado Mendizabal |
| **Institution** | Universidade Federal de Santa Catarina (UFSC) |
| **Program** | Bacharelado em Sistemas de Informação |
| **Expected defense** | 2027 |

Progress so far: front matter, abstract, and bibliography are in place; the
Introduction chapter is drafted and being refined on its own branch;
Development, Implementation, and Conclusion chapters are still ahead.

## Built With

This document is written in [LaTeX](https://www.latex-project.org/), using
the [`ufscthesisx`](https://github.com/UFSC/ufscthesisx) template — a
Canonical Model for UFSC theses, dissertations, and course conclusion
reports built on top of [abnTeX2](http://www.abntex.net.br/), which
implements Brazil's ABNT formatting standards (NBR 14724 and related norms)
directly in the document class, so the content stays separate from the
formatting rules.

## Getting Started

### Prerequisites

A full TeX Live (Linux) or MacTeX (macOS) / MiKTeX (Windows) installation,
including `latexmk` and `biber`:

```bash
# Ubuntu/Debian
sudo apt-get install texlive-full xzdec latexmk
```

### Building

```bash
git clone --recursive https://github.com/guiklose/graduation-thesis.git
cd graduation-thesis
make
```

The compiled PDF is generated at `main.pdf` in the project root. See
`make help` for every available build target.

## Repository Structure

```
main.tex              Root document — metadata, structure, includes
settings.tex          Package configuration
beforetext/            Front matter: cover, dedication, abstract, epigraph...
chapters/              Introduction, Development, Conclusion
aftertext/              References (references.bib)
pictures/               Figures and diagrams
setup/                  abnTeX2/ABNT class engine (submodule)
```

## Acknowledgments & License

This thesis is built on the [`ufscthesisx`](https://github.com/UFSC/ufscthesisx)
template, itself derived from
[`abntex2-ufsc`](https://github.com/AdrianoRuseler/abntex2-ufsc) and the
[abnTeX2](http://www.abntex.net.br/) project. The template (not this thesis'
own written content) is distributed under the following notice:

```
Copyright (c) 2012-2014 by abnTeX2 group at http://abntex2.googlecode.com/
Copyright (c) 2014-2015 Mateus Dubiela Oliveira
Copyright (c) 2015-2016 Adriano Ruseler
Copyright (c) 2017-2018 Evandro Coan, Luiz Rafael dos Santos
Copyright (c) 2019-2019 Alisson Lopes Furlani

Permission is hereby granted, free of charge, to any person obtaining a copy
of this template and associated software and documentation files (the
"Software"), to deal in the Software with the rights to use, copy, modify,
merge, publish, and distribute copies of the Software, and to permit persons
to whom the Software is furnished to do so, subject to the following
conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

The files `chapters/intro.tex` and `setup/ufscthesisx.sty` are licensed
under the LPPL (The LaTeX Project Public License). You must respect that
license for those files instead of the one above. However, the following
condition still applies to those LPPL-licensed files:

THE FILES IN THIS REPOSITORY ARE PROVIDED "AS IS", WITHOUT WARRANTY OF ANY
KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO
EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM,
DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR
OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE FILES IN THIS
REPOSITORY OR THE USE OR OTHER DEALINGS IN THE TEMPLATE AND SOFTWARE.
```

Any issue with the template itself (not this thesis' content) can be
reported upstream at [UFSC/ufscthesisx/issues](https://github.com/UFSC/ufscthesisx/issues).

---

<p align="center">
  <sub>Made with LaTeX, coffee, and a healthy respect for distributed systems.</sub>
</p>
