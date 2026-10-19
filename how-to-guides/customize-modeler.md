---
title: Customization Guide
parent: How-to Guides
nav_order: 3
---

# Cybergrid Modeler – Customization Guide

##  Overview

This document explains how to customize **Cybergrid Modeler** for project-specific requirements.

Cybergrid Modeler is structured as a monorepo composed mainly of two application layers:

- **CybergridML** – the backend, responsible for the core modeling logic and backend services.
- **frontend** – the frontend application, responsible for the user interface and user interactions.

Depending on the type of customization, changes may be required in one or both layers.

---

##  Project Architecture

The project is organized as follows:

```text
cybergrid-modeler/
│
├── CybergridML/       # Backend
├── frontend/          # Frontend
├── .github/           # GitHub configuration and workflows
├── .idea/             # IDE configuration
├── node_modules/      # Node.js dependencies
│
├── cybergridml.sh     # Development/startup script
├── package.json       # Root project configuration
├── package-lock.json  # Dependency lock file
├── turbo.json         # Monorepo configuration
├── .npmrc             # npm configuration
└── README.md          # Project documentation
```

### Main Components

| Component | Role |
|---|---|
| `CybergridML/` | Backend and core modeling logic |
| `frontend/` | Frontend application and user interface |
| `cybergridml.sh` | Script used to run or configure the application |
| `package.json` | Root scripts and project configuration |
| `turbo.json` | Monorepo task and build configuration |
| `.npmrc` | npm configuration |
| `.github/` | CI/CD and GitHub configuration |

---

##  Customization Overview

Customization can be performed at different levels depending on the required change.

### Backend Customization

The `CybergridML/` directory contains the backend.

Backend customization is required when changing:

- Core modeling behavior
- Domain logic
- Data processing
- Validation rules
- Backend services
- APIs
- Model transformations

### Frontend Customization

The `frontend/` directory contains the user interface.

Frontend customization is required when changing:

- User interface components
- Layout
- User interactions
- Model visualization
- Forms
- Navigation
- Styling and themes




---


##  Backend and Frontend Integration

When a customization requires both backend and frontend changes, the communication between the two layers must be considered.

A typical flow is:

```text
┌──────────────┐
│   Frontend   │
│              │
│ User Action  │
└──────┬───────┘
       │
       │ API
       ▼
┌──────────────┐
│ CybergridML  │
│   Backend    │
│              │
│ Model Logic  │
└──────┬───────┘
       │
       │ Result
       ▼
┌──────────────┐
│   Frontend   │
│              │
│ Update UI    │
└──────────────┘
```

When implementing a full-stack customization, make sure that the backend API contract and the frontend implementation remain consistent.

---

##  Project Configuration

### `package.json`

The root `package.json` contains the project scripts, dependencies, and configuration.

Before adding or modifying scripts, review the existing project conventions.

### `turbo.json`

The `turbo.json` file configures the monorepo task and build pipeline.

Changes may be required when adding new packages or custom build tasks.

### `.npmrc`

The `.npmrc` file contains npm-specific configuration.

Do not commit credentials, tokens, or other sensitive information.

### `cybergridml.sh`

The `cybergridml.sh` script can be used to automate development or startup tasks.

Any required environment variables or assumptions should be documented when modifying this script.



## Customization 


## Best Practices

When customizing Cybergrid Modeler:

- Keep backend and frontend responsibilities separated.
- Reuse existing components and utilities whenever possible.
- Avoid unnecessary changes to the core architecture.
- Keep custom code easy to maintain.
- Document new configuration options.
- Add tests for new behavior.
- Avoid modifying generated files.
- Do not commit credentials, tokens, or secrets.
- Keep customizations compatible with the existing build system.


For each customization, first determine whether the requirement belongs to the **backend**, the **frontend**, or both.

Keeping these responsibilities separated makes the customization easier to maintain and reduces the risk of breaking existing functionality.
