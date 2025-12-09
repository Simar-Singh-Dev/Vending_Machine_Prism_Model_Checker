# Vending_Machine_Prism_Model_Checker
Vending Machine Controller Model 

Authors:Simarpreet Singh

This repository contains a PRISM model of a vending machine controller designed for the ENSE803 assignment. The model captures drink selection, payment processing, inventory management, and error handling using formal methods.

Project Overview

The vending machine controller is divided into three modular components:

DrinkSelection – Manages drink selection, inventory, and maintenance mode.

EFPOSPayment – Handles electronic payment processing, including correct and incorrect PIN entry.

DrinkDispenser – Controls physical dispensing of drinks following successful payment.

The model ensures safety and liveness, providing robust operation even in the presence of errors or user mistakes.

Key Design Decisions

State Representation:

Drink selection codes: 0 = none, 1 = Kiwi-Cola, 2 = Bolt, 3 = Water, 4 = maintenance.

Payment states: 0 = ready, 1 = in progress, 2 = success, 3 = cancelled, 4 = error.

Drink quantities tracked with discrete ranges for clear inventory management.

Maintenance Mode:

Automatically triggered when all drinks are depleted.

Permanent state with no transitions out.

Inventory Management:

Prevents selection of out-of-stock drinks.

Decrements inventory only after successful payment.

Payment Flow:

Payment only starts when due.

Synchronizes with drink dispensing after success.

Error Handling:

Payment module can enter an error state, triggering maintenance mode.

Ensures system safety and prevents unauthorized dispensing.

Verification

Key Computation Tree Logic (CTL) properties verified using PRISM:

Maintenance Mode is Irreversible – Once activated, cannot exit.

Errors Lead to Maintenance Mode – Payment errors eventually trigger maintenance.

Selection Only Allowed When Drinks Available – Prevents selection of out-of-stock items.

Payment Leads to Dispensing – Ensures successful transactions result in product dispensing.

No Dispensing Without Payment Attempt – Prevents free dispensing or unauthorized release.

These properties validate both safety and liveness, ensuring correctness, reliability, and fail-safe operations.

Example Scenarios

Successful purchase: Customer selects a drink, enters correct PIN, and receives the product.

Incorrect PIN: Customer’s payment fails, selection is reset, no drink dispensed.

Error occurrence: Machine enters maintenance mode, blocking further interactions.

Out-of-stock selection: Prevents selection of unavailable drinks, maintaining inventory integrity.

Files

VendingMachineModel.txt – PRISM model code in a plain text file, including all modules, transitions, and synchronization.

README.md – Project description, verification details, and usage instructions.

Usage

Copy the text from VendingMachineModel.txt into a .prism file in PRISM.

Load the file into PRISM to explore modules: DrinkSelection, EFPOSPayment, DrinkDispenser.

Verify properties using CTL formulas included in the code.

Simulate scenarios to observe system behavior.

Conclusion

This PRISM model demonstrates formal verification of an embedded system controller, showing how model checking ensures reliable, safe, and predictable behavior for automated systems like vending machines.
