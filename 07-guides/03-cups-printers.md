# CUPS Printer Stack Installation Guide

## Problem

Printers aren't working in PikaOS

![no-cups-service.png](/no-cups-service.png)

## Cause

The CUPS Printer Stack is not included by default in PikaOS

> This was due to an influx of security concerns.

## Solution

Simply install the CUPS printing stack and reboot

### GUI

![pika-welcome-install-cups.png](/pika-welcome-install-cups.png)

### CLI

```bash
pikman install cups cups-filters cups-pk-helper printer-driver-all
```
