# Falcon

Falcon is a lightweight command-line utility designed to optimize game performance on Linux systems.

It works by managing CPU core affinity and system power profiles when launching applications.

## Features

- Automatically detects and assigns optimal CPU cores
- Manages power profiles for better performance
- Supports AMD CPU preferred core detection
- Configurable core selection strategies
- Custom core assignment options

## Usage

When used in steam game cmd line options:

```bash
falcon %command%
```

When used from the terminal:

```bash
falcon apptolaunch
```

If you have environment variables to set put them in front:

```bash
PROTON_LOG=1 falcon %command%
```

If you want to chainload other apps (e.g mangohud) they go after:

```bash
falcon mangohud %command%
```

If you want to use it in heroic launcher here is the setup:

![heroic.png](/heroic.png)

## Configuration

The configuration file is stored at `~/.config/falcon/config.json`

### Configuration options

```jsonc
{
  "force_lscpu": false,          // Force using lscpu instead of AMD detection
  "thread_count": 16,            // Number of threads to use
  "override_thread_count": false, // Override automatic thread count detection
  "enable_performance_mode": true, // Enable performance power profile
  "disable_taskset": false,       // Disable CPU core pinning
  "custom_taskset": "",          // Custom core list (e.g., "0,1,2,3")
  "lscpu_core_strategy": "HighestFreq" // Core selection strategy: "HighestFreq" or "Sequential"
}
```

### Core Selection Strategies

HighestFreq: Selects cores with the highest frequency capability (default)

Sequential: Selects cores in sequential order

### AMD-Specific Features

On AMD systems, Falcon automatically detects what cores the system prefers, this could be ones with higher frequency or ones with extra cache.

For non-AMD systems or when force_lscpu is true, it falls back to lscpu for core frequency detection and uses that to rank the cores instead.

### Thread Count Defaults

When override_thread_count is false, Falcon uses these defaults for AMD CPUs:

- 32 thread CPU: 16 threads
- 24 thread CPU: 12 threads
- 16 thread CPU: 8 threads
- Other: Uses all available threads

For Intel CPUs if the CPU has P and E cores then Falcon will put the process on the P cores.

## Requirements

- A Linux system
- powerprofilesctl for power profile management
- taskset for CPU affinity management

## How It Works

1. Loads configuration from ~/.config/falcon/config.json
2. Detects available CPU cores and their frequencies/preference
3. Selects optimal cores based on configuration
4. Sets power profile to performance mode (if enabled)
5. Launches the specified command with CPU affinity set to selected cores

## Source

Falcon is written in the [Zig programming language](https://ziglang.org/) and the source can be found on our [git here](https://git.pika-os.com/general-packages/falcon/src/branch/main/falcon).
