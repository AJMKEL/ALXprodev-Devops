# Advanced Shell Scripting: API Automation & Process Management

[![Shell Script](https://img.shields.io/badge/Shell-Bash-4EAA25?style=flat&logo=gnu-bash&logoColor=white)](https://www.gnu.org/software/bash/)
[![API](https://img.shields.io/badge/API-PokéAPI-EF5350?style=flat&logo=pokemon&logoColor=white)](https://pokeapi.co/)
[![License](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

> A comprehensive shell scripting project demonstrating production-grade automation, parallel processing, and data pipeline engineering using the Pokémon API.

## 📋 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Architecture](#architecture)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Usage](#usage)
- [Project Structure](#project-structure)
- [Tasks & Components](#tasks--components)
- [Technical Implementation](#technical-implementation)
- [Best Practices](#best-practices)
- [Troubleshooting](#troubleshooting)
- [Contributing](#contributing)
- [License](#license)

## 🎯 Overview

This project showcases advanced shell scripting techniques by building a complete ETL (Extract, Transform, Load) pipeline that interacts with the Pokémon API. It demonstrates skills essential for DevOps engineers, site reliability engineers, and data engineers working with automated data pipelines, batch processing, and system automation.

### Real-World Applications

- **Data Engineering**: Automated data extraction from RESTful APIs
- **DevOps**: Robust error handling and retry mechanisms for CI/CD pipelines
- **System Administration**: Parallel process management and resource optimization
- **Reporting**: Automated report generation and data aggregation

## ✨ Features

### Core Capabilities

- ✅ **RESTful API Integration**: Automated HTTP requests with proper authentication and headers
- ✅ **Advanced JSON Processing**: Complex data extraction and transformation using `jq`
- ✅ **Intelligent Error Handling**: Exponential backoff retry logic with configurable attempts
- ✅ **Parallel Processing**: Background job management for high-performance data fetching
- ✅ **Data Validation**: Comprehensive input validation and response verification
- ✅ **Structured Logging**: Timestamped error logs with severity levels
- ✅ **CSV Report Generation**: Formatted data exports with statistical calculations
- ✅ **Modular Design**: Reusable functions and configuration management

### Technical Highlights

- HTTP status code validation (200, 404, 429, 500+)
- Rate limiting and throttling implementation
- Process synchronization using `wait` and signal handling
- Memory-efficient streaming for large datasets
- POSIX-compliant shell scripts for maximum portability

## 🏗️ Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                     API Request Layer                        │
│  (apiAutomation-0x00, batchProcessing-0x02/0x04)            │
│  • HTTP Request Management                                   │
│  • Error Handling & Retries                                  │
│  • Parallel Process Control                                  │
└─────────────────────┬───────────────────────────────────────┘
                      │
                      ▼
┌─────────────────────────────────────────────────────────────┐
│                  Data Processing Layer                       │
│         (data_extraction_automation-0x01)                    │
│  • JSON Parsing (jq)                                         │
│  • Data Transformation (awk, sed)                            │
│  • Format Conversion                                         │
└─────────────────────┬───────────────────────────────────────┘
                      │
                      ▼
┌─────────────────────────────────────────────────────────────┐
│                   Reporting Layer                            │
│              (summaryData-0x03)                              │
│  • CSV Generation                                            │
│  • Statistical Analysis                                      │
│  • Data Aggregation                                          │
└─────────────────────────────────────────────────────────────┘
```

## 🔧 Prerequisites

### Required Tools

| Tool | Minimum Version | Purpose |
|------|----------------|---------|
| `bash` | 4.0+ | Shell interpreter |
| `curl` | 7.29+ | HTTP client |
| `jq` | 1.5+ | JSON processor |
| `awk` | GNU Awk 4.0+ | Text processing |
| `sed` | GNU sed 4.2+ | Stream editor |

### Installation Commands

**Ubuntu/Debian:**
```bash
sudo apt-get update
sudo apt-get install -y curl jq gawk sed
```

**CentOS/RHEL:**
```bash
sudo yum install -y curl jq gawk sed
```

**macOS:**
```bash
brew install curl jq gawk gnu-sed
```

### System Requirements

- Unix-like operating system (Linux, macOS, BSD)
- Bash shell environment
- Internet connectivity for API access
- Minimum 100MB free disk space

## 📥 Installation

### Quick Start

```bash
# Clone the repository
git clone https://github.com/yourusername/ALXprodev-Devops.git
cd ALXprodev-Devops/Advanced_shell

# Make all scripts executable
chmod +x apiAutomation-0x00 \
         data_extraction_automation-0x01 \
         batchProcessing-0x02 \
         summaryData-0x03 \
         batchProcessing-0x04

# Verify installation
./apiAutomation-0x00 --help
```

### Directory Setup

```bash
# Create necessary directories
mkdir -p pokemon_data logs reports

# Set appropriate permissions
chmod 755 pokemon_data logs reports
```

## 🚀 Usage

### Task 0: Single Pokémon API Request

Fetch data for a single Pokémon and save to JSON.

```bash
./apiAutomation-0x00
```

**Output:**
- `data.json` - Pokémon data in JSON format
- `errors.txt` - Error log (if any failures occur)

### Task 1: Data Extraction & Formatting

Extract and format specific fields from the JSON response.

```bash
./data_extraction_automation-0x01
```

**Expected Output:**
```
Pikachu is of type Electric, weighs 6kg, and is 0.4m tall.
```

### Task 2: Batch Processing with Error Handling

Fetch multiple Pokémon sequentially with automatic retry logic.

```bash
./batchProcessing-0x02
```

**Features:**
- Sequential processing of Pokémon list
- Up to 3 retry attempts per failed request
- Detailed error logging with timestamps

### Task 3: CSV Report Generation

Generate structured reports with statistical analysis.

```bash
./summaryData-0x03
```

**Output:**
- `pokemon_report.csv` - Formatted data export
- Console: Average height and weight calculations

### Task 4: Enhanced Batch Processing

Advanced batch processing with improved error handling.

```bash
./batchProcessing-0x02  # Uses same script with enhanced features
```

### Task 5: Parallel Processing

High-performance parallel data fetching using background jobs.

```bash
./batchProcessing-0x04
```

**Performance:**
- Up to 10x faster than sequential processing
- Intelligent process management
- Resource-aware execution

## 📁 Project Structure

```
Advanced_shell/
│
├── 📜 Scripts
│   ├── apiAutomation-0x00                    # Core API request handler
│   ├── data_extraction_automation-0x01       # JSON parser & formatter
│   ├── batchProcessing-0x02                  # Sequential batch processor
│   ├── summaryData-0x03                      # Report generator
│   └── batchProcessing-0x04                  # Parallel batch processor
│
├── 📊 Data Directories
│   ├── pokemon_data/                         # JSON data storage
│   ├── logs/                                 # Application logs
│   └── reports/                              # Generated CSV reports
│
├── 📝 Output Files
│   ├── data.json                             # Single Pokémon data
│   ├── errors.txt                            # Error log
│   └── pokemon_report.csv                    # Formatted report
│
└── 📖 Documentation
    ├── README.md                             # This file
    └── LICENSE                               # Project license
```

## 🔨 Tasks & Components

### Task 0: API Request Automation
**File:** `apiAutomation-0x00`

**Objective:** Automate API requests with robust error handling.

**Key Features:**
- HTTP status code validation
- Connection timeout handling
- JSON response verification
- Structured error logging

**Code Snippet:**
```bash
curl -s -S -f \
  --connect-timeout 10 \
  --max-time 10 \
  -w "\n%{http_code}" \
  "https://pokeapi.co/api/v2/pokemon/pikachu"
```

### Task 1: Data Extraction
**File:** `data_extraction_automation-0x01`

**Objective:** Parse and format JSON data using text processing tools.

**Key Features:**
- `jq` for JSON extraction
- `awk` for unit conversion and formatting
- `sed` for text transformation
- Multi-type handling

**Transformation Pipeline:**
```
JSON → jq (extract) → awk (transform) → sed (format) → Output
```

### Task 2 & 4: Batch Processing
**File:** `batchProcessing-0x02`

**Objective:** Process multiple Pokémon with error handling and retries.

**Key Features:**
- Configurable retry logic (max 3 attempts)
- Exponential backoff
- Failed request tracking
- Progress indicators

**Retry Algorithm:**
```
attempt = 1
while attempt <= max_retries:
    if request_succeeds:
        break
    wait(2^attempt seconds)
    attempt++
```

### Task 3: Summary Reporting
**File:** `summaryData-0x03`

**Objective:** Generate CSV reports with statistical analysis.

**Key Features:**
- CSV header generation
- Data aggregation from multiple files
- Average calculations
- Formatted output

**Report Format:**
```csv
Name,Type,Height(m),Weight(kg)
Pikachu,Electric,0.4,6
Charizard,Fire and Flying,1.7,90.5
```

### Task 5: Parallel Processing
**File:** `batchProcessing-0x04`

**Objective:** Optimize performance through parallelization.

**Key Features:**
- Background job spawning (`&`)
- Process synchronization (`wait`)
- Resource management
- Concurrent execution control

**Process Management:**
```bash
for pokemon in $list; do
    fetch_pokemon "$pokemon" &
    pids+=($!)
done
wait ${pids[@]}
```

## 💡 Technical Implementation

### Error Handling Strategy

```bash
# Three-tier error handling
1. Network Level: curl exit codes (0-99)
2. HTTP Level: Status codes (200, 404, 500)
3. Application Level: JSON validation
```

### Retry Logic

```bash
# Exponential backoff implementation
retry_count=0
max_retries=3

while [ $retry_count -lt $max_retries ]; do
    if make_request; then
        break
    fi
    sleep $((2 ** retry_count))
    ((retry_count++))
done
```

### Parallel Processing Pattern

```bash
# Controlled parallelism
MAX_PARALLEL=5
current_jobs=0

for item in $items; do
    if [ $current_jobs -ge $MAX_PARALLEL ]; then
        wait -n  # Wait for any job to complete
        ((current_jobs--))
    fi
    
    process_item "$item" &
    ((current_jobs++))
done

wait  # Wait for all remaining jobs
```

## 🎓 Best Practices

### Code Quality
- ✅ POSIX-compliant shell syntax
- ✅ Comprehensive error checking (`set -euo pipefail`)
- ✅ Meaningful variable names
- ✅ Modular function design
- ✅ Extensive inline documentation

### Security
- ✅ Input validation and sanitization
- ✅ Secure temporary file handling
- ✅ No hardcoded credentials
- ✅ Proper file permissions

### Performance
- ✅ Efficient JSON parsing (streaming where possible)
- ✅ Minimal subprocess spawning
- ✅ Intelligent caching
- ✅ Resource-aware parallel execution

### Maintainability
- ✅ Configuration variables at script top
- ✅ Consistent error handling patterns
- ✅ Logging and debugging support
- ✅ Version control friendly

## 🐛 Troubleshooting

### Common Issues

**Problem:** `jq: command not found`
```bash
# Solution: Install jq
sudo apt-get install jq  # Ubuntu/Debian
brew install jq          # macOS
```

**Problem:** `Permission denied` when running scripts
```bash
# Solution: Make scripts executable
chmod +x script-name
```

**Problem:** API requests timing out
```bash
# Solution: Increase timeout in script configuration
HTTP_TIMEOUT=30  # Increase from 10 to 30 seconds
```

**Problem:** Too many parallel processes
```bash
# Solution: Reduce MAX_PARALLEL in batchProcessing-0x04
MAX_PARALLEL=3  # Reduce from 5 to 3
```

### Debug Mode

Enable verbose output:
```bash
# Add to beginning of any script
set -x  # Print commands before execution
```

### Logging

Check error logs:
```bash
# View recent errors
tail -n 50 errors.txt

# Search for specific error
grep "404" errors.txt
```

## 🤝 Contributing

Contributions are welcome! Please follow these guidelines:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

### Coding Standards
- Follow ShellCheck recommendations
- Include unit tests for new features
- Update documentation as needed
- Maintain POSIX compliance

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- [PokéAPI](https://pokeapi.co/) - Free RESTful Pokémon API
- [jq](https://stedolan.github.io/jq/) - Command-line JSON processor
- [ShellCheck](https://www.shellcheck.net/) - Shell script analysis tool
- ALX Africa - Software Engineering Program

## 📞 Contact

**Author:** ALX Professional Development - DevOps Track

**Repository:** [ALXprodev-Devops](https://github.com/yourusername/ALXprodev-Devops)

**Issues:** [Report a bug](https://github.com/yourusername/ALXprodev-Devops/issues)

---

<div align="center">

**⭐ Star this repository if you found it helpful!**

Made with ❤️ for the DevOps community

</div>
