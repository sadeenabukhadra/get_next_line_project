
## Get_next_line
## Description

The Get Next Line (GNL) project is a C programming exercise that aims to implement a function capable of reading a file line by line from a given file descriptor. 
The function reads from the file descriptor and returns one line at a time, including the newline character (\n) when it exists. 
It manages internal memory efficiently to handle partial reads and ensures that data not returned in the current call is saved for the next call. This project focuses on:

    Working with file descriptors.
    Using the read() system call.
    Managing static variables.
    Handling dynamic memory allocation.
    Understanding buffer-based input reading. The function continues reading until the end of file (EOF) is reached or an error occurs. It is designed to work with different buffer sizes and supports reading from files as well as standard input.

## Instructions

1- Write a function called: char *get_next_line(int fd); 
2- The functi on reads one line at a time from a file descriptor. 
3- The returned line must include the newline character (\n) if it exists. 
4- When the end of file (EOF) is reached, the function must return NULL. 
5- The function must use the read() system call to read from the file. 
6- The reading size is defined by BUFFER_SIZE. 
7- A static variable must be used to store remaining data between function calls. 
8- Dynamic memory allocation is required, and all allocated memory must be freed. 
9- The function must work with: 
- Regular files. 
- Standard input (stdin). 
10- Each call to get_next_line() returns the next line from the file.
## Algorithm

The algorithm used in the Get Next Line project is based on buffered incremental reading. Instead of reading the entire file at once, the function reads small chunks of data using the read() system call with a fixed size defined by BUFFER_SIZE. A static buffer is used to store leftover data that was read but not returned in the current function call. Each time get_next_line() is called, the algorithm: 
- Reads data from the file descriptor into a temporary buffer. 
- Appends the read data to a static storage variable. 
- Searches for a newline character (\n) in the stored data. 
- If a newline is found, extracts and returns the line up to and including \n. 
- Keeps the remaining data for the next function call. 
- If no newline is found, continues reading until a complete line or EOF is reached. 
This process repeats for each function call until the entire file has been read.

## Justification of the Algorithm Choice This algorithm was selected for the following reasons:

- Memory Efficiency: Reading the file in small chunks avoids loading the entire file into memory, which is important for large files.
- Line-by-Line Processing: The algorithm ensures that only one line is returned per function call, exactly matching the project requirements.
- Performance: Using a buffer reduces the number of system calls to read(), improving performance compared to reading one character at a time.
- State Preservation: The use of a static variable allows the function to remember unread data between calls without using global variables.
- Flexibility: The algorithm works with different buffer sizes and supports reading from files and standard input.
- Robustness: It correctly handles edge cases such as empty files, files without a trailing newline, and end-of-file conditions.


## Resources

- Man pages for function behaviors.
- 42 project guides.
- AI for testing and explanations.
- Peer collaboration.
- Youtube.


