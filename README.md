# Enhanced RC4 - Brute Force Attack Using CUDA

This project demonstrates the implementation of the RC4 and Enhanced RC4 encryption algorithms in CUDA for efficient brute-force attacks on a GPU. The project also includes a traditional RC4 implementation and an advanced Non-linear Conditional Key Scheduling Algorithm (NCKSA) for Enhanced RC4. The CUDA implementation accelerates the brute-force process by leveraging parallel processing on the GPU.

## Table of Contents

- [Introduction](#introduction)
- [Features](#features)
- [Requirements](#requirements)
- [Installation](#installation)
- [Usage](#usage)
- [Traditional RC4](#traditional-rc4)
- [Enhanced RC4](#enhanced-rc4)
- [Performance](#performance)
- [Acknowledgments](#acknowledgments)
- [License](#license)
- [Contact](#contact)

## Introduction

RC4 is a stream cipher used in various encryption protocols and standards. This project implements a brute-force attack on RC4 encryption using CUDA to leverage the parallel processing capabilities of modern GPUs. Additionally, an Enhanced RC4 algorithm with a Non-linear Conditional Key Scheduling Algorithm (NCKSA) is implemented to demonstrate more complex encryption.

## Features

- **Traditional RC4 Implementation:** A standard RC4 encryption algorithm with brute-force attack simulation using CUDA.
- **Enhanced RC4 Implementation:** An advanced RC4 variant with non-linear conditional key scheduling for increased security.
- **CUDA Acceleration:** Leveraging GPU parallelism to accelerate the brute-force key search process.
- **Brute-force Key Recovery:** Efficient key recovery using GPU brute-force on small key lengths.

## Requirements

- Python 3.x
- CUDA Toolkit and NVIDIA GPU with CUDA support
- PyCUDA
- NumPy

## Installation

Install the required Python packages using pip:

```bash
pip install pycuda
pip install numpy
```

Ensure that the CUDA Toolkit is installed and properly configured on your machine.

## Usage

### Traditional RC4

The traditional RC4 implementation allows you to simulate encryption with a given key and brute-force the key using GPU acceleration.

#### Example:

```python
key = "see"
plaintext = "hello"
key_used, encrypted_text, encrypted_str = simulate_encryption(key, plaintext)
print("Actual Key Used:", key_used)
print("Encrypted Text (array):", encrypted_text)
print("Encrypted Text (string):", encrypted_str)

# Brute force using GPU
found_key, decrypted_text = brute_force_gpu(encrypted_text, len(plaintext), len(key), plaintext)
if found_key is not None:
    print("Decrypted Text:", decrypted_text)
else:
    print("Failed to decrypt the text")
```

### Enhanced RC4

The Enhanced RC4 implementation uses a Non-linear Conditional Key Scheduling Algorithm (NCKSA) for encryption. The CUDA implementation accelerates the brute-force key search.

#### Example:

```python
key_length = 3
key_used, known_output = simulate_encryption(key_length)
print("Actual Key Used:", key_used)
print("Known Output (for testing):", known_output)

# Brute force using GPU
brute_force_gpu(known_output, key_length)
```

## Limitations

Key Size Limitation: The current implementation is limited to a key size of 3 bytes. Attempting to use larger key sizes can result in excessive memory usage, which may cause the system to run out of RAM or crash due to insufficient memory. This limitation is inherent to the brute-force approach used in this project, where the key space grows exponentially with key size.

Memory Constraints: The brute-force algorithm generates and stores all possible keys for the given key length in memory. For key sizes greater than 3 bytes, the memory required to store the key space becomes impractically large for most consumer-grade GPUs.

Performance Scalability: While CUDA provides significant performance improvements for smaller key sizes, the brute-force approach does not scale well with increasing key sizes. The number of possible keys grows exponentially, making brute-force attacks computationally infeasible for larger key sizes.

Limited to RC4 Stream Cipher: This project focuses solely on the RC4 stream cipher and its enhanced variant. It does not address other stream ciphers or block ciphers, and the techniques used here may not be directly applicable to other encryption algorithms.

Simplified Encryption for Demonstration: The plaintext used in the examples is simple and small. In real-world scenarios, plaintext might be larger and more complex, requiring additional adjustments to the algorithm and memory management.

## Performance

The CUDA implementation provides significant performance improvements over CPU-based brute-force attacks by leveraging parallel processing on the GPU. The performance gain is particularly noticeable for small key lengths, where a brute-force attack can quickly search through the key space.

## Acknowledgments

This project is inspired by the need to understand the security and vulnerabilities of stream ciphers like RC4. The CUDA implementation was made possible by leveraging the powerful parallel processing capabilities of modern GPUs.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Contact

Feel free to ask any questions on my email : samama4200@gmail.com

Connect with me on linkedin : www.linkedin.com/in/samama-


