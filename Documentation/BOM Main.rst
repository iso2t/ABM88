ABM88 "Abomination" 16-bit Dual CPU Computer
============================================

BILL OF MATERIALS (BOM): MULTI-PROCESSOR INTEL 8088 CUSTOM COMPUTER
-------------------------------------------------------------------

Architecture: 8088 + 8087 + 8089 + Secondary 8088 (Maximum Mode, 5 MHz Baseline)

Notes
~~~~~

- All processors and support chips should match the same clock speed rating.
- Standard NMOS parts run at 5 MHz (driven by a 15 MHz crystal on the 8284A).
- For an 8 MHz build, source "-2" speed-graded Intel parts and a 24 MHz crystal.
- All CPUs and the 8089 must be wired in Maximum Modes (MN/MX tied to Ground) to support
  shared-bus multiprocessing via the 8288/8289 chipset.

1. PROCESSORS & COPROCESSORS
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. list-table::
   :header-rows: 1
   :widths: 6 27 14 53

   * - Qty
     - Part Number / Name
     - Package
     - Description & Role
   * - 1
     - Intel 8088
     - 40-pin DIP
     - Primary CPU. Wired in Maximum Mode. Handles OS, general code, and coordinated
       system tasks.
   * - 1
     - Intel 8087
     - 40-pin DIP
     - Math coprocessor. Works alongside the primary 8088 to accelerate floating-point
       calculations.
   * - 1
     - Intel 8089
     - 40-pin DIP
     - I/O coprocessor. Manages DMA and peripheral communication independently of the
       primary CPU.
   * - 1
     - Intel 8088
     - 40-pin DIP
     - Secondary CPU. Wired in Maximum Mode. Assists with parallel processing and
       shared-bus operations.

2. CLOCK, BUS CONTROL, & ARBITRATION
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. list-table::
   :header-rows: 1
   :widths: 6 27 14 53

   * - Qty
     - Part Number / Name
     - Package
     - Description & Role
   * - 1
     - Intel 8284A
     - 18-pin DIP
     - Clock generator and driver. Provides the system clock and reset signals for the
       CPUs and support chips.
   * - 1
     - 15 Mhz Crystal
     - HC-49/U
     - Provides the reference clock for the 8284A clock generator (divides by 3 to
       produce the 5 MHz system clock)
   * - 3
     - Intel 8288
     - 20-pin DIP
     - Bus controller for the primary CPU. Manages control signals for memory and I/O
       operations in Maximum Mode.
   * - 3
     - Intel 8289
     - 20-pin DIP
     - Bus arbiter. Coordinates access to the shared system bus among multiple
       processors.

3. ADDRESS LATCHES & DATA TRANSCEIVERS
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. list-table::
   :header-rows: 1
   :widths: 6 27 14 53

   * - Qty
     - Part Number / Name
     - Package
     - Description & Role
   * - 9
     - 74LS373 (or 8282)
     - 20-pin DIP
     - Octal Transparent Latch. Demuxes and holds the 20-bit address bus (A0-A19) strady
       during cycles (3 per processor cluster).
   * - 3
     - 74LS245 (or 8286)
     - 20-pin DIP
     - Octal Bidirectional Bus Transceiver. Buffers and isolates the data bus (D0-D7)
       during read and write cycles (1 per processor cluster).

4. INTERRUPTS, TIMERS, & PERIPHERAL I/O
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. list-table::
   :header-rows: 1
   :widths: 6 27 14 53

   * - Qty
     - Part Number / Name
     - Package
     - Description & Role
   * - 1
     - Intel 8259A (2 if cascaded)
     - 28-pin DIP
     - Programmable Interrupt Controller. Manages hardware interrupts for the system,
       with a second unit used if cascading is required.
   * - 1
     - Intel 8253 (or 8254)
     - 24-pin DIP
     - Programmable Interval Timer. Provides timing and counting functions for the
       system, including generating periodic interrupts.
   * - 1
     - Intel 8251A (or 16550)
     - 28/40-pin DIP
     - Programmable Communication Interface. Manages serial communication for the
       system, supporting asynchronous and synchronous modes.
   * - 1
     - Intel 8255A
     - 40-pin DIP
     - Programmable Peripheral Interface. Provides parallel I/O capabilities for the
       system, supporting multiple modes of operation.

5. MEMORY & ADDRESS DECODING GLUE LOGIC
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. list-table::
   :header-rows: 1
   :widths: 6 27 14 53

   * - Qty
     - Part Number / Name
     - Package
     - Description & Role
   * - 1
     - 27C256 (or 27C5112)
     - 28-pin DIP
     - 32 KB / 64 KB UV-EPROP or EPROM. Stores the system firmware and boot code at top
       of memory (F0000h-FFFFFh).
   * - 1
     - AS6C4008 (or 628512) (2 for 1 MP map)
     - 32-pin DIP
     - 512 KB Static RAM (SRAM). Provides main system memory for the processor(s), with
       two chips used for a single MP memory map.
   * - 2
     - 74LS138 (or 8288)
     - 16-pin DIP
     - 3-to-8 Line Decoder. Used for address decoding in the memory and I/O map,
       enabling selection of specific memory or peripheral regions.
   * - 4
     - 74LS00 / 74LS04 / 74LS32
     - 14/16-pin DIP
     - Basic Logic Gates. Provides essential logic functions (NAND, NOT, OR) for glue
       logic and address decoding in the system.
