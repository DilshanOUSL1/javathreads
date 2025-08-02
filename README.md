# 🚀 Parallel Matrix Multiplication in Java

This project demonstrates how to efficiently perform **matrix multiplication** using **Java's multithreading capabilities**. By distributing the workload across multiple threads, it significantly improves performance on multi-core processors.

---

## ✨ Features

* **🔁 Parallel Processing**: Leverages Java threads for concurrent matrix computation.
* **🎛️ Dynamic Input**: Accepts matrix dimensions and elements via console input.
* **🧠 Smart Thread Management**: Automatically detects available CPU cores to decide thread count.
* **📊 Detailed Output**: Displays thread metadata (ID, Name, Priority, State, Assigned Rows) and final results.

---

## 🧠 How It Works

The core idea is to **divide the matrix multiplication** into smaller chunks and execute them **simultaneously** using threads.

### 🧭 `ThreadCaller` (The Orchestrator)

* Accepts user input for **Matrix A** and **Matrix B** using `Scanner`.
* Validates matrix dimensions for compatibility.
* Determines the **optimal thread count** (based on CPU cores).
* Splits rows of the result matrix between threads.
* Spawns and starts `ChildThread` instances.
* Waits for all threads to finish using `.join()`.
* Prints the final result matrix.

### 🧵 `ChildThread` (The Worker Bee)

* Each thread is responsible for **a range of rows** in the result matrix.
* Receives:

  * References to Matrix A, Matrix B
  * Its assigned `startRow`, `endRow`
  * Shared `resultMatrix`
* Performs matrix multiplication logic in its `run()` method.
* Prints status (start and finish), along with:

  * `ID`, `Name`, `Priority`, `State`, and `Assigned Rows`

> This parallel model ensures **faster execution** by utilizing all available processor cores.

---

## ⚙️ Getting Started

### 📋 Prerequisites

* Java Development Kit (**JDK 8** or higher)

### 🛠️ Installation & Running

1. **Clone the repository** (if hosted on GitHub):

   ```bash
   git clone <your-repo-url>
   cd <your-repo-name>
   ```

2. **Compile the Java code**:

   ```bash
   javac ChildThread.java ThreadCaller.java
   ```

3. **Run the application**:

   ```bash
   java ThreadCaller
   ```

4. **Follow the prompts** to enter dimensions and elements for Matrix A and Matrix B.

---

## 🖥️ Sample Output

```plaintext
Enter rows for Matrix A:
2
Enter columns for Matrix A:
2
Enter elements for row 1:
1
1
Enter elements for row 2:
2
2

Matrix A entered:
1	1
2	2

Enter rows for Matrix B:
2
Enter columns for Matrix B:
2
Enter elements for row 1:
3
3
Enter elements for row 2:
4
4

Matrix B entered:
3	3
4	4

----------------------------------------
Thread started:
ID: 22
Name: Thread-0
Priority: 5
State: RUNNABLE
Assigned rows: 0 to 0
----------------------------------------
Thread started:
ID: 23
Name: Thread-1
Priority: 5
State: RUNNABLE
Assigned rows: 1 to 1
----------------------------------------

Thread finished:
ID: 22
Name: Thread-0
State: RUNNABLE
----------------------------------------
Thread finished:
ID: 23
Name: Thread-1
State: RUNNABLE
----------------------------------------

Multiplication of Matrix A * Matrix B:
7	7
14	14

Process finished with exit code 0
```

---

## 📄 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

