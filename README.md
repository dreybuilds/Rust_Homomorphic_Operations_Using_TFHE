## Overview 
- This Rust project shows how to use the TFHE library to conduct homomorphic operations on encrypted data in both parallel and single-threaded execution modes. The application maintains privacy by enabling safe computation on encrypted 64-bit unsigned integers (FheUint64) without decrypting them.

## Features
- **Homomorphic Operations:** Supports addition, subtraction, multiplication, and division on encrypted integers.
- **Execution Modes:** Choose between parallel and single-threaded execution for optimized performance.
- **Configurable Cryptographic Parameters:** Customize the security settings and error probability using the TFHE library's configuration options.
- **Automatic Encryption/Decryption:** Input data is automatically encrypted before computation, and results are decrypted for verification.
## Performance Considerations
   - Parallel execution  is often faster on multi-core platforms, especially when working with huge datasets. However, it may cause overhead in situations where the data size is small or the system has limited parallel processing capabilities.
   - Single-Threaded Mode: Use single-threaded mode when parallelism is unnecessary or when running in environments with limited resources.
## Benefits
- **Improved Performance:** Parallel execution of huge datasets or complex computations can result in significant performance increases. This is accomplished by dividing the task across numerous CPU cores, which reduces processing time.
- **Efficient Resource Utilization:** Parallel processing makes the best use of available CPU cores, resulting in better resource utilization and faster execution times.
- **Scalability:** The technique scales well with the size of the dataset and the number of operations, making it appropriate for scenarios involving enormous amounts of data.
## Customization
- Modify Cryptographic Parameters: Adjust the security and error probability by editing the custom_params in the parallel_homomorphic_operations function.
- Change Execution Mode: Switch between ExecutionMode::Parallel and ExecutionMode::SingleThreaded by changing the argument in the main function.
## Code  Structure
- **ExecutionMode Enum:** Defines the available execution modes (Parallel and SingleThreaded).
- **HomomorphicOps Trait:** Encapsulates the homomorphic operations (add, subtract, multiply, divide) that can be performed on encrypted integers.
- **Implementation for FheUint64:** The HomomorphicOps trait is implemented for the FheUint64 type, supporting both parallel and single-threaded operations.
- **Main Function:** The entry point of the program, which calls the parallel_homomorphic_operations function to perform operations using the chosen execution mode.
- **Execution Modes:** ExecutionMode enum allows switching between parallel and single-threaded execution.
- **Parallel Homomorphic Operations Function:**
   - Configures the TFHE encryption parameters.
   - Generates client and server keys.
   - Encrypts two 64-bit integers.
   - Performs homomorphic operations in parallel or single-threaded mode.
   - Decrypts and verifies the results against clear-text calculations.

## Requirements
- **Rust:** Ensure you have the latest stable version of Rust installed.
- **TFHE-rs:** This project uses the TFHE-rs library for fully homomorphic encryption. It is included as a dependency in the Cargo.toml file.
- **Rayon:** The Rayon library is used for parallel processing, also included as a dependency.
- First, add TFHE-rs as a dependency in your Cargo.toml.
  - For x86_64 machine running a Unix-like OS:
>```
>tfhe = { version = "0.7.2", features = [ "boolean", "shortint", "integer", "x86_64-unix" ] }
  - For ARM machine running a Unix-like OS:
>```
> tfhe = { version = "0.7.2", features = [ "boolean", "shortint", "integer", "aarch64-unix" ] }
  - For x86_64 machines with the rdseed instruction running Windows:
>```
> tfhe = { version = "*", features = ["boolean", "shortint", "integer", "x86_64"] }

## Usage 
- To run the program and perform homomorphic operations in parallel mode, use
 >```
>  cargo run --release --parallel
> #if the command above raises an error,try :  
> cargo run --release -- --parallel

- To run the program and perform homomorphic operations in single-threaded mode, use:
 >```
>  cargo run --release --single-threaded
- By default, the code runs in parallel mode. You can switch to single-threaded mode by modifying the parallel_homomorphic_operations function call in the main function:

 ## Contributing
  - If you intend to contribute to this project, fork the repository and make a pull request.

 ## Installation

- To use this project, you need to have Rust installed on your machine.
- If Rust is not installed, follow the instructions on the [official Rust website](https://www.rust-lang.org/tools/install) to install it.
- After installing Rust, clone this repository or copy the code into a Rust project, Compile and run the code using cargo run.
## Acknowledgments
- TFHE Library
- Rayon
- Rust
### Clone the repository or copy the source code into a Rust project. 
```bash
git clone https://github.com/cypriansakwa/Rust_Homomorphic_Operations_Using_TFHE.git
cd Rust_Homomorphic_Operations_Using_TFHE
