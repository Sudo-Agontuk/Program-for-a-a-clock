# Digital Clock

A simple console-based digital clock written in C that continuously displays the current local time in `HH : MM : SS` format, updating once per second.

## Features

- Displays real-time local system time
- Updates every second using a continuous loop
- Uses carriage return (`\r`) to overwrite the previous time on the same line for a clean display

## Requirements

- C compiler (GCC, Clang, or MSVC)
- Standard C libraries: `stdio.h`, `time.h`, `stdbool.h`
- Platform-specific headers:
  - Unix/Linux/macOS: `unistd.h` (for `sleep`)
  - Windows: `windows.h` (for `Sleep`)

**Note:** The current source mixes Unix (`sleep`) and Windows (`windows.h`) headers. For cross-platform use, conditional compilation is recommended.

## Compilation

### On Linux / macOS

```bash
gcc digital_clock.c -o digital_clock
```

### On Windows (MinGW)

```bash
gcc digital_clock.c -o digital_clock.exe
```

### On Windows (MSVC)

```bash
cl digital_clock.c
```

## Usage

Run the compiled executable:

```bash
./digital_clock          # Linux/macOS
digital_clock.exe        # Windows
```

The program will print:

```
Digital clock
HH : MM : SS
```

and continuously update the time in place. Press `Ctrl+C` to terminate.

## Source Code Overview

| Component              | Purpose                                      |
|------------------------|----------------------------------------------|
| `time(&rawtime)`       | Retrieves current system time since epoch    |
| `localtime(&rawtime)`  | Converts to local broken-down time structure |
| `printf("\r...")`      | Overwrites the previous line with new time   |
| `sleep(1)` / `Sleep(1000)` | Pauses execution for one second           |

## Limitations

- Infinite loop with no graceful exit (relies on external interrupt)
- Platform-dependent sleep function
- No error handling for time-related system calls
- Uses the non-reentrant `localtime` function


## License

This code is provided as-is for educational purposes.
