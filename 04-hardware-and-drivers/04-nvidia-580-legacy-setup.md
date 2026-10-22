# Nvidia 580 Legacy Driver Setup

To maintain full hardware acceleration and system stability on older graphics cards, PikaOS provides a specialized Nvidia 580 legacy package.

_Installing this driver automatically pulls in the legacy kernel to ensure future kernel compatibility._

## Supported Hardware

This driver package is officially required for the following legacy Nvidia GPU series and architectures (including desktop and mobile variants) supported by the 580 driver branch:

### Pascal Architecture

- **GeForce GTX 10 Series**: GTX 1080 Ti, GTX 1080, GTX 1070 Ti, GTX 1070, GTX 1060, GTX 1050 Ti, GTX 1050, GT 1030
- **GeForce GTX 10 Series (Mobile / Max-Q)**: GTX 1080 Mobile, GTX 1080 Max-Q, GTX 1070 Mobile, GTX 1070 Max-Q, GTX 1060 Mobile, GTX 1060 Max-Q, GTX 1050 Ti Mobile, GTX 1050 Mobile
- **GeForce MX Series (Pascal)**: MX350, MX330, MX250, MX230, MX150
- **TITAN Series (Pascal)**: TITAN X / Xp
- **NVIDIA RTX / Quadro (Pascal)**: Quadro P6000, P5000, P4000, P3200, P3000, P2200, P2000, P1000, P620, P600, P520, P500

#### Maxwell Architecture

- **GeForce 900 Series**: GTX 980 Ti, GTX 980, GTX 970, GTX 960, GTX 950
- **GeForce 900M & Mobile Series**: GTX 980 (Mobile), GTX 980M, GTX 970M, GTX 965M, GTX 960M, GTX 950M, 945M, 940MX, 940M, 930MX, 930M, 920MX, 920M, 910M
- **GeForce 800M Series**: GTX 860M, GTX 850M, GTX 845M, GTX 840M, GTX 830M
- **GeForce 700 Series (Maxwell variants only)**: GTX 750 Ti, GTX 750
- **GeForce MX Series (Maxwell)**: 940MX, 930MX, MX130, MX110
- **TITAN Series (Maxwell)**: GeForce GTX TITAN X
- **NVIDIA RTX / Quadro (Maxwell)**: Quadro M6000, M5000, M4000, M2000, M1200, M620, M520, Quadro K620 (Maxwell variant)

#### Volta Architecture

- **TITAN Series (Volta)**: TITAN V

### Required Packages

The setup is bundled into a single installation step:

Both packages will be installed in the next step

- **`pika-nvidia-driver`**: The Nvidia 580 legacy graphics driver.
- **`kernel-pika-legacy`**: The customized kernel patch (automatically installed as a dependency).

## Install the Nvidia legacy drivers when installing PikaOS.

### First Stage: Install the Distro

Proceed through the PikaOS installer as normal to install the distribution.

After a successful install the system will now reboot.

### Second Stage: User Setup, updates and configuring packages

Now you have landed in the setup stage.

**Connect to the internet and open a terminal, run the following command to install the driver and kernel:**

```bash
pikman upgrade
pikman i pika-nvidia-driver kernel-pika-legacy
```

> Password is **pikaos**

**Proceed setting up the system followed by a reboot**

## Verification

After rebooting, verify that the correct driver is active.

- **Check Nvidia driver status:**

```bash
nvidia-smi
```

_The output should display driver version `580.xx`._
