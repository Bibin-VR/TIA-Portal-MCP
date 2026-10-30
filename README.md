# TIA-Bridge: Siemens TIA Portal for AI agents

TIA-Bridge connects Claude, or any other AI agent that speaks the Model Context Protocol
(MCP), to Siemens TIA Portal and the PLCs it programs. You describe the machine in plain
language. The agent creates the project, configures the hardware, writes the PLC program,
sets up motion axes and HMI screens, compiles everything, tests it in the simulator and
downloads it to the PLC. During commissioning it reads and writes live PLC values while
you work on the machine.

## What you can ask for

> *"Create a project with an S7-1200 G2 CPU and write a conveyor program in ladder: start,
> stop, an E-stop that needs a reset, and a 2-second hold after the metal detector clears."*

> *"Build a pick-and-place cell with six servo axes on a CPU 1511T and SINAMICS S210
> drives: homing, jogging, teach positions and an automatic cycle, with a WinCC Unified
> panel to run it."*

> *"Compile the hardware and the program, and fix every error."*

> *"Load the program into PLCSIM, switch it to RUN and compare it with the project."*

> *"Watch I0.4 to I0.7 and Q0.1 while I press the buttons on the panel."*

> *"Download to the PLC."* A download to a real PLC always waits for your confirmation.

## What it covers

| Area | Covers |
|---|---|
| Projects | Create, open, save and archive projects; global and project libraries |
| Hardware | S7-1200, S7-1200 G2 and S7-1500 CPUs (1500T included), distributed I/O, SINAMICS drives, HMI panels, PROFINET networks, IP addresses, topology and IRT |
| Hardware catalog | The whole TIA Portal V21 catalog, about 11,700 entries, searchable by article number or name |
| PLC program | Blocks in LAD and SCL, and FBD, STL and GRAPH blocks by import; tag tables and PLC data types |
| Motion | Positioning axes and other technology objects, drive telegrams, isochronous servo mode |
| HMI | WinCC Unified and WinCC Comfort/Advanced: PLC connections, tags, screens, buttons, I/O fields and their events |
| Protection | PLC access protection and the project password |
| Compile | Hardware and software, with every message traced to the object it came from |
| Simulation | S7-PLCSIM: start, load, RUN, STOP and PAUSE, online compare |
| Commissioning | Download, going online, online/offline compare, live reading and writing of PLC values |
| Exchange | AutomationML hardware import and export; block and tag table export and import |

## Simulation

TIA-Bridge works with S7-PLCSIM, Siemens' PLC simulator, so a program can run in
simulation before it goes near a real PLC. The agent starts PLCSIM, loads the hardware
and the program, switches between RUN, STOP and PAUSE, compares the simulated PLC with the
project, reloads it after a change, and closes it again. PLCSIM has to match the TIA
Portal version: PLCSIM V17 for TIA Portal V17, PLCSIM V21 for V21.

The agent can also switch on the project option that prepares blocks for simulation when
they compile.

PLCSIM Advanced and WinCC runtime simulation are not supported yet.

## Test runs

| Run | What was done | Result |
|---|---|---|
| Conveyor on a real PLC | S7-1200 G2 (CPU 1214C DC/DC/DC): a ladder program with start, stop, an E-stop latch with reset, a metal-detector hold and the run relay of a VFD | Downloaded and running; inputs and outputs read and written live during commissioning |
| Live values on a real PLC | Reads and writes of inputs, outputs, memory bits and data block values on the same S7-1200 G2 | Every write was read back and checked; out-of-range writes were refused before anything was sent |
| New machine program | A project built from scratch: CPU, SCL function block, compile, export for version control, AutomationML export, archive | Compiled with 0 errors on TIA Portal V17 and V21 |
| Commissioning in PLCSIM | Load, RUN and STOP, online compare, reload after a change, close | Every step passed on TIA Portal V17 with PLCSIM V17 |
| 6-axis pick and place | A CPU 1511T, six SINAMICS S210 servo drives on PROFINET IRT, six positioning axes, an SCL program and a WinCC Unified panel, built from one request in about 5 minutes | The HMI panel compiles with 0 errors, and an earlier build of the cell compiled completely; the latest build is still being finished |

## Works with

- Claude Code, Claude Desktop, Cursor, Cline, Windsurf and other MCP clients.
- TIA Portal V21 and V17.
- The agent runs on a Mac or a Linux machine. TIA Portal stays on its Windows PC on the
  same network.

## Safety

- Downloads, going online, writes to PLC values and simulator control need an explicit
  confirmation.
- If you have a project open in TIA Portal, the agent leaves it alone and works in a
  TIA Portal session of its own.
- The project password is typed once on your own machine and stored encrypted on the
  engineering PC. The agent never sees it.

## Why

TIA Portal is a large tool, and much of a PLC engineer's day goes into clicking through
it: adding hardware, setting parameters, wiring up HMI tags, compiling and fixing. With
TIA-Bridge an agent does that work from a description, and the engineer reviews the result
and decides what goes to the machine.

---

<sub>TIA-Bridge is proprietary. This repository is an overview; the source is private.</sub>
