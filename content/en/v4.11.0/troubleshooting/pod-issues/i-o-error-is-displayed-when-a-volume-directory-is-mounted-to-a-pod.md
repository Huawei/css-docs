---
title: "\"I/O error\" Is Displayed When a Volume Directory Is Mounted to a Pod"
linkTitle: "\"I/O error\" Is Displayed When a Volume Directory Is Mounted to a Pod"
description: 
weight: 8
---

## Symptom{#section16564369537}

When a Pod reads or writes a mounted volume, message "I/O error" is displayed.

## Root Cause Analysis{#section135642617536}

When a protocol such as SCSI is used, if the Pod continuously writes data to the mount directory, the storage device will restart. As a result, the link between the device on the host and the storage device is interrupted, triggering an I/O error. When the storage device is restored, the mount directory is still read-only.

## Solution{#section75642613539}

Remount the volume. That is, reconstruct the Pod to trigger re-mounting.

