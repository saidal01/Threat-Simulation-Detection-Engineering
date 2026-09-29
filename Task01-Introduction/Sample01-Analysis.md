# Task 1 - Hash-Based Malware Detection

## Objective

Analyze the malware sample provided by the penetration tester and identify a unique indicator that can be used to detect and prevent execution.

## Malware Sample

- File Name: sample1.exe
- Classification: Trojan.Metasploit.A
- File Type: PE32+ Executable (x86-64)

## Static Analysis

The malware sample was submitted to the Malware Sandbox for analysis. The report identified the sample as malicious and revealed multiple suspicious behaviors:

### Malicious Activity

- Metasploit payload detected
- Connected to an unusual network port
- Read MachineGuid from the registry
- Checked LSA protection
- Retrieved computer name
- Enumerated supported languages

## Indicator of Compromise (IOC)

| Type | Value |
|--------|--------|
| SHA1 | 83d2791ca93e58688598485aa62597c0ebbf7610 |

## Detection Engineering

The SHA1 hash extracted from the sandbox report was added to PicoSecure's hash blocklist through the IOC Management console.

### Action Taken

1. Submitted sample to Malware Sandbox.
2. Reviewed generated analysis report.
3. Extracted unique SHA1 hash.
4. Added hash to the EDR blocklist.
5. Verified malware execution was prevented.

## Pyramid of Pain Mapping

| Pyramid Level | Indicator |
|---------------|-----------|
| Hash Values | SHA1 file hash |

### Why This Detection Works

Hash-based detection is effective against a specific malware sample because it uniquely identifies the file. However, attackers can easily evade this control by recompiling or modifying the malware to generate a different hash.

## Outcome

✅ Malware detected

✅ SHA1 IOC added to blocklist

✅ sample1.exe prevented from executing

✅ Initial detection rule successfully deployed