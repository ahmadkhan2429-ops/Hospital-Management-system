# Hospital-Management-system
# MediCore — Hospital Management System
### OOP Project | Spring 2026 | BCS-2A

A fully-featured Hospital Management System built in C++17 with an SFML graphical user interface.

---

## Features
- **Three user roles**: Patient, Doctor, Admin — each with their own menu
- **SFML GUI**: Dark teal medical theme, interactive buttons and input fields, scrollable lists
- **File persistence**: All data saved to `.txt` files, reloaded on every startup
- **Security**: Login attempt tracking, lockout after 3 failures, security log
- **Operator Overloading**: `==` (conflict/ID compare), `<<` (display), `+=`/`-=` (balance)
- **Custom Exceptions**: `InsufficientFundsException`, `SlotUnavailableException`, `InvalidInputException`, `FileNotFoundException`
- **Generic Storage\<T\>**: Template class with dynamic array (no `std::vector` in interface)
- **No global variables**, no goto, no static arrays, modular design

---

## Project Structure
```
MediCore/
├── include/         # All .h header files
│   ├── Person.h         (abstract base)
│   ├── Patient.h
│   ├── Doctor.h
│   ├── Admin.h
│   ├── Appointment.h
│   ├── Bill.h
│   ├── Prescription.h
│   ├── Storage.h        (generic template)
│   ├── FileHandler.h    (all file I/O)
│   ├── Validator.h      (all validation)
│   ├── HospitalException.h
│   └── GUI.h            (SFML GUI)
├── src/             # All .cpp source files
│   ├── main.cpp
│   ├── Person.cpp
│   ├── Patient.cpp
│   ├── Doctor.cpp
│   ├── Admin.cpp
│   ├── Appointment.cpp
│   ├── Bill.cpp
│   ├── Prescription.cpp
│   ├── FileHandler.cpp
│   ├── Validator.cpp
│   └── GUI.cpp
├── data/            # Auto-created on first run
│   ├── patients.txt
│   ├── doctors.txt
│   ├── admin.txt
│   ├── appointments.txt
│   ├── bills.txt
│   ├── prescriptions.txt
│   ├── security_log.txt
│   └── discharged.txt
├── Makefile
└── README.md
```

---

## How to Compile & Run

### Prerequisites
- g++ with C++17 support
- SFML 2.6 development libraries

Install SFML on Ubuntu/Debian:
```bash
sudo apt-get install libsfml-dev
```

### Build
```bash
make
```

### Run
```bash
./MediCore
# or
make run
```

### Clean
```bash
make clean
```

---

## Default Login Credentials

| Role    | ID | Password  |
|---------|----|-----------|
| Patient | 1  | pass123   |
| Doctor  | 1  | doc123    |
| Doctor  | 2  | doc456    |
| Doctor  | 3  | doc789    |
| Admin   | 1  | admin123  |

---

## File Formats (CSV)

```
patients.txt:      id,name,age,gender,contact,password,balance
doctors.txt:       id,name,specialization,contact,password,fee
admin.txt:         id,name,password
appointments.txt:  id,patient_id,doctor_id,date,time_slot,status
bills.txt:         id,patient_id,appointment_id,amount,status,date
prescriptions.txt: id,appointment_id,patient_id,doctor_id,date,medicines,notes
security_log.txt:  timestamp,role,entered_id,result
```

---

## Class Relationships
- `Person` ← `Patient`, `Doctor`, `Admin` (inheritance)
- `Storage<T>` — generic container for all entity types
- `FileHandler` — sole file I/O class
- `Validator` — sole validation class
- `HospitalException` ← `FileNotFoundException`, `InsufficientFundsException`, `InvalidInputException`, `SlotUnavailableException`
- `GUI` — SFML front-end, references all stores

---

## GitHub Repository
https://github.com/ahmadkhan2429-ops/Hospital-Management-system/blob/main/README.md
