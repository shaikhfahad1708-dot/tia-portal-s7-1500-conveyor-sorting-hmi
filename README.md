# Siemens S7-1500 Conveyor Sorting & Batch Counter (TIA Portal V19 + WinCC)

Modular industrial sorting and batching prototype built in **Siemens TIA Portal V19 (SCL)** for **SIMATIC S7-1500** and **WinCC Basic (KTP700 PN)**, tested live with **S7-PLCSIM**.

## Architecture
* **`DB_coveyorData [DB1]`**: Global Data Block storing machine states (`start_belt`, `stop_belt`, `reset_belt`, `belt_run`), measured part size (`part_size_mm`), and counters (`good_count`, `reject_count`, `batch_done`).
* **`FB_sorterLogic [FB1]`**: Core SCL control logic evaluating part tolerances (`10.0 mm – 25.0 mm`), sorting good vs. reject parts, and flagging batch completion (`good_count >= 5`).
* **`FB_CONVEYORSIM [FB2]`**: Virtual hardware simulation block generating alternating in-spec (`18.0 mm`) and out-of-spec (`32.0 mm`) sensor inputs during active belt runs.
* **`HMI_1 [KTP700 Basic PN]`**: Operator interface with momentary `Start`, `Stop`, and `Reset` controls plus live batch and quality counters.
