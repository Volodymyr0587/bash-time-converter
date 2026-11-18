# ⏱️ timeconvert

A lightweight Bash utility for converting between seconds and human-readable time formats.

`timeconvert` automatically detects the input format and converts it to the appropriate output. It also supports custom output formats, including clock notation and human-readable durations.

## ✨ Features

- Convert seconds to `HH:MM:SS`
- Convert `H:M:S` to seconds
- Convert `M:S` to seconds
- Parse human-readable durations (`1d 2h 30m`)
- Support for days, hours, minutes, and seconds
- Automatic input format detection
- Three output formats: `clock`, `human`, and `short`
- Input validation and error handling
- Protection against arithmetic overflow
- Short and long CLI options
- Can be installed system-wide

## 📦 Installation

### 1. Clone the repository

```bash
git clone https://github.com/Volodymyr0587/bash-time-converter.git
cd bash-time-converter
```

### 2. Make the script executable

```bash
chmod +x timeconvert
```

### 3. (Optional) Install system-wide

To run `timeconvert` from anywhere on your system:

```bash
sudo install -m 755 timeconvert /usr/local/bin/timeconvert
```

Now you can run:

```bash
timeconvert --help
```

## 🕹️ Usage

```bash
timeconvert [OPTIONS] <TIME>
```

### Input formats

`timeconvert` supports four input formats.

**1. Seconds**

```bash
timeconvert 3661
```

Output:

```text
01:01:01
```

**2. Hours:Minutes:Seconds (`H:M:S`)**

```bash
timeconvert 01:01:01
```

Output:

```text
3661
```

**3. Minutes:Seconds (`M:S`)**

```bash
timeconvert 12:30
```

Output:

```text
750
```

**4. Human-readable duration**

```bash
timeconvert "1d 2h 3m 4s"
```

Output:

```text
93784
```

Human-readable input can also be provided without spaces:

```bash
timeconvert 1d2h30m
```

## 🎨 Output formats

Use `-f` or `--format` to choose the output format.

### Clock format

Displays the duration as `HH:MM:SS`.

```bash
timeconvert --format clock 93784
```

Output:

```text
26:03:04
```

Hours are not limited to 24.

### Human format

Displays all non-zero time units.

```bash
timeconvert -f human 93784
```

Output:

```text
1d 2h 3m 4s
```

### Short format

Displays up to three largest non-zero time units.

```bash
timeconvert -f short 93784
```

Output:

```text
1d 2h 3m
```

For zero seconds, both `human` and `short` formats return `0s`.

## ⚙️ Command-line options

| Option      | Long option       | Description                 |
| ----------- | ----------------- | --------------------------- |
| `-h`        | `--help`          | Display help information    |
| `-v`        | `--version`       | Display version information |
| `-f FORMAT` | `--format FORMAT` | Specify output format       |

Available output formats:

- `clock` — `HH:MM:SS`
- `human` — `1d 2h 3m 4s`
- `short` — up to three largest units

### Examples

```bash
# Display help
timeconvert --help

# Display version
timeconvert --version

# Convert seconds to human-readable format
timeconvert -f human 3661

# Convert seconds to short format
timeconvert --format=short 93784

# Convert H:M:S to clock format
timeconvert -f clock 01:30:45
```

## 🔍 Input validation

### Seconds

```text
3661
```

- Digits only
- No negative values
- No fractional seconds

### H:M:S

```text
01:23:45
```

- Hours: any non-negative integer
- Minutes: `00–59`
- Seconds: `00–59`

### M:S

```text
12:30
```

- Minutes: any non-negative integer
- Seconds: `00–59`

### Human-readable format

```text
1d 2h 3m 4s
```

Supported units:

| Unit | Description | Example |
| ---- | ----------- | ------- |
| `d`  | Days        | `1d`    |
| `h`  | Hours       | `2h`    |
| `m`  | Minutes     | `30m`   |
| `s`  | Seconds     | `15s`   |

Rules:

- Units can appear in any order.
- Spaces between values are optional.
- Each unit can appear only once.
- Values must be non-negative integers.
- Unknown characters and units are not allowed.
- Maximum supported duration: `999999999999` seconds.

### Invalid examples

```text
01:99:10
1h 2h
1x 30m
-100
hello
```

Invalid input produces an error message and exits with a non-zero status.

## 🛠️ How it works

1. Parses command-line options.
2. Detects the input format.
3. Validates the input.
4. Converts the input into seconds.
5. Applies the requested output format.
6. Prints the result.

If no output format is specified:

- Seconds input produces `HH:MM:SS`.
- `H:M:S`, `M:S`, and human-readable input produce total seconds.

## 🧪 Testing

Automated tests are written using [Bats](https://github.com/bats-core/bats-core).

Run the test suite from the project directory:

```bash
bats tests/
```

Or run a specific test file:

```bash
bats tests/timeconvert.bats
```

## 📋 Requirements

- Bash 4.0 or newer
- Linux or another Unix-like system

Bats is required only for running automated tests.

## 🤝 Contributing

Contributions, bug reports, and suggestions are welcome!

Feel free to open an issue or submit a pull request.

## 📄 License

See the [LICENSE](LICENSE) file for license information.
