# Event-Driven Trading Backtester

## Overview
This project implements an event-driven backtesting engine that simulates how real-world trading systems operate.
Instead of processing data in batches, the system models market activity as a stream of events, closely mirroring production trading and fintech infrastructure.

The focus of this project is **software architecture and system design**, not trading performance.

---

## Why Event-Driven Architecture?
Modern trading systems react to incoming market data in real time.
An event-driven architecture enables:

- Realistic simulation of market behavior
- Loose coupling between system components
- Clear separation of responsibilities
- Easy extensibility for new strategies and assets
- Production-aligned engineering design

This architecture is commonly used in quantitative trading platforms, exchanges, and low-latency systems.

---

## System Architecture

The backtester is organized around an **event queue**.
Each component listens for specific event types, processes them, and emits new events downstream.

### Event Flow

MarketEvent  
→ Strategy consumes MarketEvent  
→ SignalEvent  
→ Portfolio consumes SignalEvent  
→ OrderEvent  
→ ExecutionHandler simulates execution  
→ FillEvent  
→ Portfolio updates positions, cash, and PnL  

Each module is independent and communicates **only through events**.

---

## Project Structure

```text
event-driven-backtester/
├── backtest/        # Backtest engine and event loop
├── data/            # Market data handling
├── events/          # Event definitions
├── execution/       # Order execution simulation
├── portfolio/       # Positions, holdings, and PnL logic
├── strategy/        # Strategy interface and implementations
├── utils/           # Logging and helper utilities
├── requirements.txt
└── README.md


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
- System design over scripts
- Modular, production-style code organization
- Clean interfaces between components
- Realistic modeling of trading workflows

The architecture is intentionally designed to resemble professional trading systems rather than research notebooks.

---

## End Goal

To build a production-quality backtesting framework that demonstrates strong software engineering fundamentals while remaining aligned with quantitative trading workflows.

Future extensions include:
- Multiple asset support
- Advanced execution models
- Risk management modules
- Performance analytics
