# Event-Driven Trading Backtester

## Overview
This project implements an event-driven backtesting engine that simulates how real-world trading systems operate.

Instead of processing historical data in batches, the system models market activity as a continuous stream of events, closely mirroring production trading and fintech infrastructure.

The focus of this project is **software architecture and system design**, not trading performance.

---

## Why Event-Driven Architecture?
Modern trading systems react to incoming market data in real time. An event-driven architecture enables:

- Realistic simulation of market behavior
- Loose coupling between system components
- Clear separation of responsibilities
- Easy extensibility for new strategies and assets
- Production-aligned engineering design

This architectural pattern is widely used in quantitative trading platforms, exchanges, and low-latency financial systems.

---

## System Architecture
The backtester is organized around a central **event queue**.

Each component listens for specific event types, processes them, and emits new events downstream. Components do not directly depend on one another, ensuring clean system boundaries and modularity.

### Event Flow
- MarketEvent is generated from incoming market data
- Strategy processes MarketEvent and produces SignalEvent
- Portfolio processes SignalEvent and generates OrderEvent
- ExecutionHandler simulates order execution and produces FillEvent
- Portfolio updates positions, cash balance, and PnL

All communication between components happens strictly through events.

---

## Project Structure
The project is organized into clearly defined modules, each with a single responsibility:

- **backtest** — Backtest engine and main event loop
- **data** — Market data ingestion and handling
- **events** — Definitions of all event types used in the system
- **execution** — Order execution and fill simulation
- **portfolio** — Position tracking, holdings, and PnL calculation
- **strategy** — Strategy interfaces and implementations
- **utils** — Logging and shared helper utilities
- **requirements.txt** — Python dependencies
- **README.md** — Project documentation

---

## Design Principles
- Event-driven communication
- Separation of concerns
- Single responsibility per module
- Deterministic and reproducible backtests
- Strategy-agnostic system design
- Extensible and scalable architecture

---

## Engineering Focus
This project emphasizes:

- System design over ad-hoc scripts
- Modular, production-style code organization
- Clean interfaces between components
- Realistic modeling of professional trading workflows

The architecture is intentionally designed to resemble real trading systems rather than research notebooks.

---

## End Goal
The goal is to build a production-quality backtesting framework that demonstrates strong software engineering fundamentals while remaining aligned with quantitative trading workflows.

Planned future extensions include:
- Multiple asset support
- Advanced execution models
- Risk management modules
- Performance and analytics reporting

---

