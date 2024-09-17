# EPAiV5-Session13 - Context Manager Generator for CSV Read

## Introduction
This Python notebook provides two approaches to reading and processing CSV files using context managers and generators. It is designed for efficient and flexible handling of CSV data, converting rows into named tuples for easy access. The code features two parts:

- **Part 1:** A custom implementation of a context manager using a class-based approach, which includes a generator to process CSV data lazily.
- **Part 2:** A context manager and generator using Python's built-in `contextmanager` decorator from the `contextlib` module, simplifying the code while maintaining similar functionality.
Both approaches allow for handling CSV files with different delimiters and modes, ensuring that files are properly managed with minimal memory usage.

## Key Features

- **Part 1: Custom Context Manager & Generator Class:**

    - The code includes a custom class (CSVReader) that implements the context manager protocol (`__enter__` and `__exit__`).
    - It also contains a generator for lazy iteration through CSV rows, where each row is parsed and returned as a named tuple.

- **Part 2: Built-in Context Manager & Generator:**
    - The code demonstrates a more Python built-in approach using the `contextlib.contextmanager` decorator.
    - This function-based context manager opens the file and yields a generator for lazy row processing, achieving similar functionality but with simpler code.

- **Named Tuples for Data:** Rows are converted into named tuples with field names derived from the CSV headers, making it easy to access individual columns using dot notation.

- **Lazy Iteration:** Both implementations process CSV files row-by-row, conserving memory and allowing the handling of large datasets.

- **Customizable Separator:** The code accepts a customizable separator (e.g., comma , or semicolon ;) for handling various CSV formats.

- **Error Handling:** Robust error handling ensures that files are closed properly and errors such as file not found or input/output errors are managed gracefully.

## Requirements
The notebook requires Python 3.x and uses the following Python Standard Library modules:

- `csv:` For reading and parsing CSV files.
- `namedtuple:` For creating immutable row objects based on field names.
- `contextlib:` For creating a function-based context manager using contextmanager.
- `re:` For sanitizing field names to valid Python identifiers.

## Usage
### Part 1: Custom Context Manager & Generator Class
In Part 1, the code uses the `CSVReader` class, which acts as both a custom context manager and a generator. The context manager ensures that the file is opened and closed properly, while the generator lazily processes the rows one at a time.


```
with CSVReader('your_file.csv', mode='r', separator=',') as csv_reader:
    print(csv_reader._header)  # Display header
    for row in csv_reader:
        print(row)  # Print each row as a named tuple

```

#### Key Parameters:
- `filename:` The name of the CSV file to read.
- `mode:` The file mode (`'r'` for read).
- `separator:` The delimiter separating fields (default is `,`).

### Part 2: Built-in Context Manager & Generator
In Part 2, the code utilizes Python's built-in `contextmanager` decorator from the `contextlib` module. This function-based context manager opens the CSV file, sanitizes the headers, and yields a generator for lazy row processing.

```
with csv_reader_generator('your_file.csv', mode='r', separator=',') as rows:
    for row in rows:
        print(row)  # Print each row as a list of values
```

#### Key Parameters:
- `filename:` The name of the CSV file to process.
- `mode:` The file mode (default is `'r'`).
- `separator:` The delimiter separating fields (default is `,`).

## Error Handling
- `FileNotFoundError:` In the function-based context manager, if the file does not exist, an error message is printed, and the file is not opened.
- `IOError:` The class-based context manager raises an error if there is an issue with opening or reading the file.

## Performance Considerations
Both implementations use lazy iteration, which is ideal for processing large CSV files without loading the entire file into memory. This makes the code efficient and capable of handling datasets that would otherwise cause memory constraints.

## Conclusion
This Python notebook offers two powerful methods for handling CSV files:

**1. Part 1: Custom Context Manager & Generator Class** – Provides flexibility and control over the CSV reading process, using a class-based approach.

**2. Part 2: Built-in Context Manager & Generator** – A simpler, more Python built-in method using `contextmanager` and generators.
Both methods allow for lazy row-by-row processing, making the code suitable for large datasets, and offer customization through file mode and delimiters. The code is an excellent solution for efficiently handling CSV data in Python.

---------------------------------------------------------------------------------------------------------------------------------------------------

**Submission by** - Hema Aparna M

**mail id** - mhema.aprai@gmail.com

---------------------------------------------------------------------------------------------------------------------------------------------------