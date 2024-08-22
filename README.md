## Overview 
- This Rust project shows how to use the TFHE library to conduct homomorphic operations on encrypted data in both parallel and single-threaded execution modes. The application maintains privacy by enabling safe computation on encrypted 64-bit unsigned integers (FheUint64) without decrypting them.

  ## Features
- **Parallel and Single-Threaded Execution Modes:** Select between parallelized operations for improved performance or single-threaded execution in contexts where parallelism may not be advantageous.
- **Optimized Homomorphic Operations:** Implementations of homomorphic addition, subtraction, multiplication, and division are provided as a foundation for future optimization.
- **Vectorized Operations:** The efficient handling of operations on vectors of FheUint64 values.
- **Extensible Design:** The code is designed to allow for future improvements, such as advanced cryptographic and algorithmic optimizations.

## Performance Considerations
   - Parallel execution  is often faster on multi-core platforms, especially when working with huge datasets. However, it may cause overhead in situations where the data size is small or the system has limited parallel processing capabilities.
   - Single-Threaded Mode: Use single-threaded mode when parallelism is unnecessary or when running in environments with limited resources.
## Benefits
- **Improved Performance:** Parallel execution of huge datasets or complex computations can result in significant performance increases. This is accomplished by dividing the task across numerous CPU cores, which reduces processing time.
- **Efficient Resource Utilization:** Parallel processing makes the best use of available CPU cores, resulting in better resource utilization and faster execution times.
- **Scalability:** The technique scales well with the size of the dataset and the number of operations, making it appropriate for scenarios involving enormous amounts of data.
## Customization
- Execution Modes: The ExecutionMode enum lets you choose between parallel and single-threaded execution. Simply change the mode argument in the parallel_homomorphic_operations function to switch modes.
 >```
> parallel_homomorphic_operations(ExecutionMode::Parallel)?;
- Advanced optimizations: The code includes placeholders for advanced multiplication and division logic. More advanced algorithms can be implemented in these areas to improve performance even further.
## Code Explanation
- **Configuration:** ConfigBuilder is used to configure TFHE parameters.
- **Key Generation:** generate_keys generates the client and server keys for encryption and decryption.
- **Encryption:** FheUint64::try_encrypt encrypts plaintext values.
- **Operations:** Implemented in the HomomorphicOps trait and its implementation for FheUint64.
- **Execution Modes:** ExecutionMode enum allows switching between parallel and single-threaded execution.
- **Results:** Decryption and verification of results ensure correctness.

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
  
```bash
git clone https://github.com/cypriansakwa/Rust_Homomorphic_Operations_Using_TFHE.git
cd Rust_Homomorphic_Operations_Using_TFHE
