# Distributed Conway’s Game of Life (Elixir)

A distributed and concurrent implementation of Conway’s Game of Life using Elixir and the BEAM ecosystem.

## Overview

This project simulates a cellular automaton where each cell evolves based on simple rules, leading to complex emergent behavior.

The system is:

* **Concurrent** → each cell is an independent process
* **Distributed** → computation runs across multiple nodes
* **Fault-tolerant** → built with Elixir/OTP principles

## Architecture

The system is composed of four main modules:

* **Cell**: Each cell is a `GenServer` process managing its own state and neighbors
* **Coordinator**: Synchronizes all cells and ensures consistent generations
* **Controller**: Handles simulation timing (step/run/stop)
* **Display**: Transforms grid state into a human-readable format

## Key Features

* One process per cell (e.g., 30×30 → 900 processes)
* Parallel computation of generations
* Distributed execution across multiple BEAM nodes
* Interactive visualization with Kino (Livebook)
* Synchronous evolution (global coordination)

## Distributed Execution

The system runs on:

* **Master node** (Livebook UI)
* **Worker node** (remote processes)

Cells are split across nodes and communicate via message passing, ensuring true distributed computation.

## How to Run

1. Start Livebook (master node)
2. Launch a worker node with the same Erlang cookie
3. Load modules (`Cell`, `Coordinator`, `Controller`, `Display`)
4. Initialize the system
5. Use the UI to:

   * Step through generations
   * Run continuously
   * Stop simulation

## Validation

* Nodes communicate successfully (`:pong`)
* 900 independent processes created
* Cells distributed across nodes
* Visualization confirms correct evolution

## Tech Stack

* Elixir / Erlang (BEAM VM)
* GenServer & Supervisor (OTP)
* Kino + Livebook (UI & visualization)
