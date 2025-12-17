<h1 align="center">ZipTree</h1>
<h3 align="center">A lossless file compressor and decompressor built using Huffman Coding in C++</h3>

<p align="center">
  <img src="https://upload.wikimedia.org/wikipedia/commons/d/d8/HuffmanCodeAlg.png" width="600"/>
</p>

---

## Overview

**ZipTree** is a command-line based file compression and decompression utility implemented in **C++** using the **Huffman Coding algorithm**.  
The project focuses on reducing file size by encoding frequently occurring characters with shorter binary codes while preserving data integrity (lossless compression).

This project was built to deeply understand **greedy algorithms, priority queues, tree-based encoding, and bit-level file I/O**, similar to how ZIP-like tools work internally.

---

## Key Features

- Lossless file compression and decompression
- Supports text and binary files
- Efficient space utilization using variable-length encoding
- Handles padding bits and end-of-file scenarios safely
- Clean modular design with reusable components

---

## Huffman Coding – Concept

Huffman Coding is a **greedy algorithm** used for optimal prefix code generation.

- Each character is assigned a weight equal to its frequency
- Characters with higher frequency get shorter binary codes
- Characters with lower frequency get longer binary codes
- A binary tree (Huffman Tree) is constructed using a min-heap

The final tree guarantees **minimum weighted path length**, making it optimal for compression.

---

## Algorithm Steps

1. Calculate the frequency of each character in the input file
2. Insert all characters into a **min-priority queue** based on frequency
3. Repeatedly extract two minimum-frequency nodes and merge them
4. Build the Huffman Tree from merged nodes
5. Generate binary codes using tree traversal
6. Encode the file using generated codes
7. Store metadata required for decompression

---

## Compression & Decompression Flow

### Compression (Huffing)

- Read input file
- Build frequency table
- Construct Huffman Tree
- Generate encoding map
- Write compressed bitstream + header

### Decompression (Un-Huffing)

- Read header metadata
- Rebuild Huffman Tree
- Decode bitstream
- Restore original file exactly

---

## Data Structures Used

- **Priority Queue (Min Heap)** – Huffman Tree construction
- **Binary Tree** – Encoding and decoding
- **Unordered Maps** – Frequency table and code mapping
- **Bit-level I/O** – Efficient storage of compressed data

---

## File Header Design

To enable decompression, the compressed file stores metadata:

- Character frequency information
- Padding bits count
- Special EOF marker to identify end of valid data

This ensures correctness even when file size is not byte-aligned.

---

## Handling Padding & EOF

Since files are written in byte-sized chunks:

- Extra bits may be added for alignment
- Padding size is calculated using modulo-8 logic
- A **pseudo EOF character** is used to safely terminate decoding

This prevents corruption and guarantees exact reconstruction.

---

## Project Structure

└── ZipTree
    ├── CharFrequency.cpp
    ├── CharFrequency.h
    ├── CMakeLists.txt
    ├── Encoder.cpp
    ├── Encoder.h
    ├── EncodingUtils.cpp
    ├── EncodingUtils.h
    ├── input.txt
    ├── LICENSE
    ├── main.cpp
    ├── README.md
    ├── TreeNode.cpp
    └── TreeNode.h



---

## Technologies Used

- **Language:** C++
- **Concepts:** Greedy Algorithms, Trees, Heaps, Bit Manipulation
- **STL:** priority_queue, unordered_map, vector

---

## Learning Outcomes

- Practical implementation of Huffman Coding
- Understanding real-world compression challenges
- Efficient memory and file handling
- Writing modular, maintainable C++ code

---

## References

- Huffman Coding – Wikipedia
- _Introduction to Algorithms_ – Cormen et al.
- _Data Structures and Algorithm Analysis_ – Mark Allen Weiss

---

<h3 align="center">Built with ❤️ by Vikash Gautam</h3>
