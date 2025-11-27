# 📘 timeconvert — Convert Seconds ↔ H:M:S in Bash

`timeconvert` is a simple and powerful Bash utility that converts:

    - Seconds → Hours:Minutes:Seconds (H:M:S)

    - Hours:Minutes:Seconds (H:M:S) → Seconds

It includes **input validation**, **interactive mode**, and supports installation as a **system-wide command**.

## ✨ Features

- Convert seconds → H:M:S

- Convert H:M:S → seconds

- Automatic format detection

- Interactive input (no arguments needed)

- Error checking for invalid formats

- Works on any Linux system with Bash

- Can be installed globally using /usr/local/bin/

## 📦 Installation
1. Clone the repository
```git clone https://github.com/<your-username>/timeconvert.git```
```cd timeconvert```

2. Make the script executable
```chmod +x timeconvert```

3. (Optional) Install system-wide

To use timeconvert from anywhere on your system:

```sudo mv timeconvert /usr/local/bin/```


Now you can run it globally:

```timeconvert```

## 🕹 Usage

Just run:

```./timeconvert```


or (if installed globally):

```timeconvert```


You will be prompted:

```Enter seconds OR H:M:S:```

✔ Example 1: Convert seconds → H:M:S
```Enter seconds OR H:M:S: 3661```
```01:01:01```

✔ Example 2: Convert H:M:S → seconds
```Enter seconds OR H:M:S: 01:30:45```
```5445```

## 🔍 Input rules
**Valid seconds format:**
`12345`

- Must be digits only

- No negative numbers

- No letters or symbols

**Valid H:M:S format:**
`01:23:45`

**Rules:**

- Hours: any number

- Minutes: 00–59

- Seconds: 00–59

**Invalid examples:**

- `❌` 1:2:3
- `❌` 01:99:10
- `❌` hello

The script will show an error:

Error: format must be H:M:S (e.g., 01:23:45)

## 🛠 How the script works

Detects whether input is seconds or H:M:S

Converts accordingly

Prints result in standard time format (HH:MM:SS)

Validates all inputs before processing

## 🤝 Contributing

Feel free to open issues or submit pull requests with improvements!