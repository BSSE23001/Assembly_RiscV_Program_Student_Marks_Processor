# **RISC-V Grade Calculator Program**

## **Overview**
This program is a RISC-V assembly implementation of a **Grade Calculator** that processes student data from an input file, calculates weighted grades, and generates an output file with the results. The program also displays statistics like the total number of students and the class average.

### **Features**
1. **Input Processing**: Reads student records from `input.txt`.
2. **Weighted Grade Calculation**: Computes final grades based on predefined weights for different components (quizzes, assignments, midterm, final).
3. **Grade Assignment**: Assigns letter grades (A, B, C, D, F) based on weighted scores.
4. **Output Generation**: Writes processed records to `output.txt`.
5. **Statistics Display**: Shows the total number of students and class average on the console.
6. **Error Handling**: Exits gracefully if file operations fail.

---

## **Input File Format (`input.txt`)**
The input file should contain one student record per line in the following format:
```
<First_Name> <Last_Name> <Roll_No> <Quiz1> <Quiz2> <Assignment1> <Assignment2> <Midterm> <Final>
```
Example:
```
John Doe 101 8 9 85 90 45 92
Jane Smith 102 7 8 78 85 40 88
```

### **Weights and Total Marks**
| Component    | Weight (%) | Total Marks |
|--------------|-----------|-------------|
| Quiz 1       | 5%        | 10          |
| Quiz 2       | 5%        | 10          |
| Assignment 1 | 10%       | 100         |
| Assignment 2 | 10%       | 100         |
| Midterm      | 30%       | 50          |
| Final        | 40%       | 100         |

---

## **Output File (`output.txt`)**
The output file contains the processed student records with their weighted total and grade:
```
<First_Name> <Last_Name> <Roll_No> <Weighted_Total> <Grade>
```
Example:
```
John Doe 101 89 A
Jane Smith 102 82 B
```

### **Console Output**
The program also prints the following statistics:
```
Failed Students:
<First_Name> <Last_Name> <Roll_No>
...
Total No of Students: <N>
Average Marks of Class: <Avg>
```

---

## **Requirements**
- **RISC-V Toolchain**: `riscv64-linux-gnu-gcc` (for assembly compilation).
- **QEMU**: For RISC-V emulation (if not running on native RISC-V hardware).
- **Linux Environment**: Tested on Ubuntu.

---

## **Compilation and Execution**
### **1. Install Required Tools**
Ensure you have the RISC-V toolchain and QEMU installed:
```bash
sudo apt update
sudo apt install gcc-riscv64-linux-gnu qemu-user
```

### **2. Compile the Program**
Use `riscv64-linux-gnu-gcc` to assemble and link the program:
```bash
riscv64-linux-gnu-gcc -nostdlib -static -o grade_calculator grade_calculator.S
```
- `-nostdlib`: Avoid linking standard libraries (since we use raw syscalls).
- `-static`: Ensure static linking for standalone execution.

### **3. Run Using QEMU**
Execute the compiled binary using QEMU:
```bash
qemu-riscv64 ./grade_calculator
```

### **4. Verify Output**
- Check `output.txt` for processed grades.
- The console will display failed students, total students, and class average.

---

## **Error Handling**
- If `input.txt` is missing, the program exits with an error.
- If `output.txt` cannot be created, the program closes open files and exits.

---

## **Example Workflow**
1. **Prepare `input.txt`**:
   ```
   Alice Brown 103 9 10 92 95 48 96
   Bob Green 104 6 7 70 75 35 80
   ```
2. **Run the Program**:
   ```bash
   riscv64-linux-gnu-gcc -nostdlib -static -o grade_calculator grade_calculator.S
   qemu-riscv64 ./grade_calculator
   ```
3. **Check `output.txt`**:
   ```
   Alice Brown 103 94 A
   Bob Green 104 72 C
   ```
4. **Console Output**:
   ```
   Failed Students:
   Total No of Students: 2
   Average Marks of Class: 83
   ```
---

## **License**
This program is open-source and free to use.

---

## **Author**
[Muhammad Hamza]
