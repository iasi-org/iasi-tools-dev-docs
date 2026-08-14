[🇪🇸 Español](README.md) | [🇬🇧 **English**](README.en.md)

> **Language note**
>
> `iasi-quarto-docs` is developed primarily in Spanish as part of the **IASI (Engineering Assisted by Intelligent Systems)** ecosystem.
>
> English documentation is provided to make the project accessible to the international community.
> If you need any document that is only available in Spanish, just let us know: **we will translate it for you.**

# iasi-quarto-docs

> Official documentation for `iasi.quarto`.

`iasi-quarto-docs` contains the complete documentation for **iasi.quarto**, the document engineering framework built on top of Quarto and developed as part of the **IASI (Engineering Assisted by Intelligent Systems)** ecosystem.

This repository does not contain the framework source code.

It contains the knowledge required to use it, understand it and follow its evolution.

---

# Why does it exist?

The documentation for `iasi.quarto` has requirements that differ from those of the framework itself.

It must be able to:

- evolve independently;
- generate multiple books;
- share common resources;
- be published as HTML and PDF;
- document usage, architecture and the engineering decisions behind the framework.

For this reason, the documentation is maintained in a dedicated repository.

---

# The Books

`iasi-quarto-docs` is organized into three complementary books.

## User Guide

Designed for users who want to work with `iasi.quarto`.

It includes:

- installation;
- project structure;
- configuration;
- public API;
- rendering;
- examples;
- troubleshooting.

## Developer Guide

Designed for developers who want to understand, maintain or extend `iasi.quarto`.

It includes:

- architecture;
- package organization;
- internal engines;
- development conventions;
- testing strategy;
- contribution guidelines.

## The Journey

Documents the evolution of the project.

It records:

- engineering decisions;
- experiments;
- discarded alternatives;
- mistakes;
- changes of direction;
- the needs that led to new capabilities.

Understanding **how** a solution was built is considered part of the solution itself.

---

# Structure

```text
iasi-quarto-docs/
├── user-guide/
├── developer-guide/
├── journey/
└── shared/
```

Each book can be published independently while sharing common resources through the `shared/` directory.

---

# Relationship with `iasi.quarto`

This repository is a consumer of `iasi.quarto`.

The framework documentation itself is used as a real-world project to validate and evolve the framework.

Among the capabilities exercised by this repository are:

- rendering multiple books within a single project;
- automatic project discovery;
- shared resources;
- multi-format publishing.

---

# Project Status

The documentation is under active development.

Its organization and contents will evolve together with `iasi.quarto` and the IASI ecosystem.

---

# The IASI Ecosystem

This project is part of the **IASI** ecosystem.

- 📖 **iasi-book** – Conceptual framework for Engineering Assisted by Intelligent Systems.
- 📦 **iasi-quarto** – Document engineering framework built on Quarto.
- ⚙️ **iasi-lua** – Reusable Lua filters and extensions.
- 🎨 **iasi-render** – Rendering components.
- 📐 **iasi-standards** – Shared standards, templates and conventions.

Learn more at:

https://github.com/iasi-org

---

# License

This documentation is distributed under the **Creative Commons Attribution 4.0 International (CC BY 4.0)** license.

---

> **The product delivers the implementation. The documentation preserves how to use it, how it works and why it evolved the way it did.**