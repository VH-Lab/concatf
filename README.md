# concatf - Concatenate Files with Headers

`concatf` is a simple and powerful shell script that recursively finds files in a directory and concatenates them into a single output file. It adds the relative path of each file as a header before its content, making it easy to navigate the bundled code.

It is written in `bash` and is compatible with both macOS and Linux.

## Features

-   **Recursive Search**: Traverses nested directories to find all matching files.
-   **Multiple Extensions**: Specify one or more file extensions to include.
-   **Relative Path Headers**: Automatically prepends `--- path/to/file.ext ---` before each file's content.
-   **Safe and Robust**: Correctly handles filenames with spaces or special characters.
-   **Cross-Platform**: Works on macOS and modern Linux distributions.

## Installation

1.  **Download the Script**

    You can either clone this repository or download the `concatf` script directly.
    ```sh
    git clone [https://github.com/VH-Lab/concatf.git](https://github.com/VH-Lab/concatf.git)
    cd concatf/
    ```

2.  **Make it Executable**

    In your terminal, give the script execution permissions.
    ```sh
    chmod +x concatf
    ```

3.  **Move to your PATH**

    Move the script to `/usr/local/bin` to make it available as a command from any location in your terminal. This is the standard directory for user-installed executables.
    ```sh
    sudo mv concatf /usr/local/bin/
    ```
    You will be prompted for your administrator password.

## Usage

The script requires at least three arguments: the directory to search, the name of the output file, and at least one file extension.

### Syntax
```sh
concatf [OPTIONS] <input-directory> <output-file> <extension_1> [extension_2] ...
````

### Arguments

  - `<input-directory>`: The directory to search for files.
  - `<output-file>`: The file to write the concatenated content to.
  - `<extension_1>...`: One or more file extensions to include (without the dot, e.g., `c`, `h`, `txt`).

### Options

  - `-h`, `--help`: Display the help message.

### Example

Imagine a project with the following structure:

```
my_app/
├── main.c
├── utils/
│   ├── helper.c
│   └── helper.h
└── README.md
```

To concatenate all `.c` and `.h` files into a single `bundle.txt`, run the following command:

```sh
concatf ./my_app bundle.txt c h
```

### Example Output

The resulting `bundle.txt` would look like this:

```
--- my_app/main.c ---
#include <stdio.h>
#include "utils/helper.h"

int main() {
    // ... main function ...
    print_hello();
    return 0;
}

--- my_app/utils/helper.h ---
#ifndef HELPER_H
#define HELPER_H

void print_hello();

#endif //HELPER_H

--- my_app/utils/helper.c ---
#include <stdio.h>
#include "helper.h"

void print_hello() {
    printf("Hello from helper!\n");
}

```
