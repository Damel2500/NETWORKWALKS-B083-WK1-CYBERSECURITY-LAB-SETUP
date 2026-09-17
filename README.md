# NETWORKWALKS B083 — Week 1 Cybersecurity Lab Setup

## Overview
This repository documents my Week 1 cybersecurity lab setup for the NetworkWalks B083 Cybersecurity Internship.

The lab was built as an authorized learning environment using VirtualBox and Kali Linux.

## Project: WK1-PM1 — Cybersecurity Lab Setup

### Objectives
- Set up VirtualBox as the virtualization platform.
- Configure Kali Linux as the security-testing machine.
- Create a custom NAT Network using `10.0.0.0/24`.
- Configure Kali Linux with the required static address `10.0.0.2/24`.
- Verify Internet connectivity from Kali.
- Enable bidirectional clipboard and drag-and-drop.
- Configure and verify the host Downloads shared folder.
- Take a clean VM snapshot after successful configuration.

## Lab Architecture

| Component | Configuration |
|---|---|
| Hypervisor | Oracle VirtualBox |
| Security-testing VM | Kali Linux |
| Network type | VirtualBox NAT Network |
| NAT Network | `NatNetwork` |
| Network | `10.0.0.0/24` |
| Kali IP | `10.0.0.2/24` |
| Gateway | `10.0.0.1` |
| DNS | `8.8.8.8` |
| Shared folder | Host `Downloads` → Kali `/media/sf_Downloads` |
| Clipboard | Bidirectional |
| Drag & Drop | Bidirectional |
| Snapshot | `Project1-Phase1-Baseline` |

## Completed Setup

- [x] VirtualBox installed and configured
- [x] Kali Linux configured
- [x] Custom NAT Network created with `10.0.0.0/24`
- [x] Kali configured with `10.0.0.2/24`
- [x] Internet access verified
- [x] Bidirectional clipboard enabled and tested
- [x] Bidirectional drag-and-drop enabled and tested
- [x] Host Downloads shared folder configured with full access and auto-mount
- [x] Shared folder access verified from Kali
- [x] Clean baseline snapshot created

## Network Verification

Kali's network configuration was verified with:

```bash
ip -br addr
```

The resulting configuration included:

```text
eth0    UP    10.0.0.2/24
```

Internet connectivity was also verified during the lab setup.

## Shared Folder Verification

The VirtualBox shared-folder module was confirmed to be active:

```bash
lsmod | grep vboxsf
```

The Kali user was also confirmed to belong to the `vboxsf` group.

VirtualBox reported the shared folder as:

```text
Downloads
```

The automatically mounted directory was:

```text
/media/sf_Downloads
```

### Troubleshooting Experience

The initial check used:

```text
/media/sf_downloads
```

and returned a "No such file or directory" error. The issue was Linux case sensitivity: the actual mount directory was `sf_Downloads`, with a capital `D`.

The correct path was confirmed with:

```bash
ls -la /media
```

Access was then successfully verified using `/media/sf_Downloads`, including creation and removal of a test file.

### Lesson Learned

Linux paths are case-sensitive. When troubleshooting VirtualBox shared folders, verify the actual mount point instead of assuming the folder name's capitalization.

## Evidence / Screenshots

The following evidence is stored directly in this repository. Each item links to its corresponding screenshot.

1. **NAT Network configuration** — [`01-natnetwork-configuration.png`](./01-natnetwork-configuration.png)
2. **Kali network adapter configuration** — [`02-kali-network-adapter.png`](./02-kali-network-adapter.png)
3. **Kali IP configuration** — [`03-kali-ip-configuration.png.png`](./03-kali-ip-configuration.png.png)
4. **Internet connectivity** — [`04-internet-connectivity.png.png`](./04-internet-connectivity.png.png)
5. **Clipboard & Drag-and-Drop — Bidirectional** — [`05-clipboard-bidirectional.png.png`](./05-clipboard-bidirectional.png.png)
6. **Shared folder verification** — [`07-shared-folder-verification.png.png`](./07-shared-folder-verification.png.png)
7. **Baseline snapshot** — [`08-baseline-snapshot.png.png`](./08-baseline-snapshot.png.png)

> Screenshot 5 documents both Clipboard and Drag-and-Drop settings, so a separate screenshot 6 is not required.

> Only information appropriate for public sharing should be included in screenshots. Do not publish credentials, personal data, or unrelated sensitive host information.

## Snapshot

After configuration and verification, a clean baseline snapshot was created:

**`Project1-Phase1-Baseline`**

This snapshot provides a known-good rollback point before further lab changes.

## Optional Week 1 Extensions

The Week 1 material also provides optional additional VM projects:

- Windows 10 lab VM — `10.0.0.10/24`
- Android-x86 9.0 lab VM — `10.0.0.9/24`

These are separate from the completed core WK1-PM1 setup and will only be documented if completed.

## Status

**WK1-PM1 Core Lab Setup: Complete**

## Learning Outcome

This project established a controlled virtual cybersecurity laboratory with a dedicated Kali Linux testing machine, an isolated NAT Network, verified Internet connectivity, host-to-guest file sharing, and a clean recovery snapshot. It also provided practical troubleshooting experience with VirtualBox shared-folder mounting and Linux path case sensitivity.

## Ethics and Authorization

All testing described in this repository is intended for authorized cybersecurity education and research in a lab environment. Security testing should only be performed on systems and networks that are owned by the tester or covered by explicit authorization and an agreed scope.