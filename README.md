# Hospital Patient Triage & Bed Allocator

## Course
CL2006 – Operating Systems Lab
FAST-NUCES, CFD Campus
Spring 2026

## Project Description
This project simulates a real hospital emergency room 
using core Operating System concepts. Patients arrive, 
get a triage priority, and are assigned to hospital beds. 
The system handles concurrent arrivals, enforces 
priority-based scheduling, prevents race conditions, 
and manages memory using Best-Fit allocation.

## Group Members
- Aqsa Ishaq (23F-0839)
- Ayesha Rauf (23F-0807)

## OS Concepts Demonstrated
- fork() + exec() for process management
- Anonymous Pipes and Named FIFOs for IPC
- Shared Memory for bed bitmap
- POSIX Threads (Receptionist, Scheduler, Nurse)
- Mutex and Condition Variables for synchronization
- Semaphores for ICU and Isolation capacity control
- Best-Fit, First-Fit, Worst-Fit memory allocation
- Coalescing of free memory partitions
- Fragmentation reporting

## Project Structure

hospital_project/
├── src/
│   ├── admissions.c        ← Main process
│   ├── patient_simulator.c ← Child process
│   └── hospital.h          ← Shared structs

├── scripts/
│   ├── triage.sh           ← Patient admission
│   ├── start_hospital.sh   ← System startup
│   └── stop_hospital.sh    ← Clean shutdown

├── logs/
│   ├── schedule_log.txt    ← Scheduling output
│   └── memory_log.txt      ← Fragmentation log
└── Makefile
## How to Build
```bash
make clean
make all
```

## How to Run
```bash
# Start hospital
./admissions --strategy best

# Admit patient (new terminal)
./scripts/triage.sh Alice 25 2

# Stop hospital
./scripts/stop_hospital.sh
```

## Memory Allocation Strategies
```bash
./admissions --strategy best   # Best-Fit
./admissions --strategy first  # First-Fit
./admissions --strategy worst  # Worst-Fit
```

## Build Requirements
- Linux / Ubuntu
- GCC compiler
- POSIX threads library

## My Contribution
I implemented:
- admissions.c main process
- fork() + exec() process management
- POSIX threads design
- Best-Fit memory allocator
- Fragmentation reporting
- triage.sh shell script
