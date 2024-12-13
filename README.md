# RCKangaroo Auto-Range Script

This repository contains a Python script to simplify the process of launching [RCKangaroo](https://github.com/RetiredC/RCKangaroo) by RetiredCoder. The script automatically calculates the `-range` parameter based on a specified `-start` and `-end` hexadecimal range for private keys, making it easier to specify exact key ranges without manual bit calculations. This is particularly useful for those who prefer convenience or need precise control over the search space.

## Features

- **Automatic Range Calculation**: The script calculates the `-range` parameter automatically based on the provided `-start` and `-end` values.

## Usage

### Script Parameters

- `-dp` (Mandatory): Must be between 14 and 60. Defines DP bits.
- `-gpu` (Optional): Specifies which GPUs to use. For example, `"035"` means GPUs #0, #3, and #5 are used. If not specified, all available GPUs are used.
- `-pubkey` (Optional): The public key to solve. Both compressed and uncompressed keys are supported. If not provided, the script starts in benchmark mode.
- `-start` and `-end` (Mandatory if `-pubkey` is specified): Define the private key search space in hexadecimal.

### Examples

#### Puzzle 135 Example:

Start with the following parameters:

- **Start**: `4000000000000000000000000000000000`
- **End**: `7fffffffffffffffffffffffffffffffff`

The bit range (`-range`) will be calculated automatically as `134`.

Run the script for **Linux** as follows:
```bash
python3 script.py -dp 16 -pubkey 02145d2611c823a396ef6712ce0f712f09b9b4f3135e3e0aa3230fb9b6d08d1e16 -start 4000000000000000000000000000000000 -end 7fffffffffffffffffffffffffffffffff
```
Run the script for **Windows** as follows:
```bash
python script.py -dp 16 -pubkey 02145d2611c823a396ef6712ce0f712f09b9b4f3135e3e0aa3230fb9b6d08d1e16 -start 4000000000000000000000000000000000 -end 7fffffffffffffffffffffffffffffffff
```


#### Specifying a Custom Range for Puzzle 135:

If you choose a smaller range, for example:

- **Start**: `5500000000000000000000000000000000`
- **End**: `5600000000000000000000000000000000`

The calculated bit range will be `129`.

Run the script for **Linux** as:
```bash
python3 script.py -dp 16 -pubkey 02145d2611c823a396ef6712ce0f712f09b9b4f3135e3e0aa3230fb9b6d08d1e16 -start 5500000000000000000000000000000000 -end 5600000000000000000000000000000000
```
Run the script for **Windows** as:
```bash
python script.py -dp 16 -pubkey 02145d2611c823a396ef6712ce0f712f09b9b4f3135e3e0aa3230fb9b6d08d1e16 -start 5500000000000000000000000000000000 -end 5600000000000000000000000000000000
```

#### Benchmark Mode

To run in benchmark mode without specifying a `-pubkey`, simply omit the `-pubkey`, `-start`, and `-end` parameters:

**Linux:**
```bash
python3 script.py -dp 16 -gpu 035
```
**Windows:**
```bash
python script.py -dp 16 -gpu 035
```

## Notes

- The script ensures the calculated `-range` is always between 32 and 170 bits.
- It validates all mandatory parameters to prevent misconfigurations.

## Installation

1. Clone this repository.
2. Ensure (Python 3 for Linux / Python for Windows) is installed on your system.
3. Place the script in the same directory as the `RCKangaroo` executable.
