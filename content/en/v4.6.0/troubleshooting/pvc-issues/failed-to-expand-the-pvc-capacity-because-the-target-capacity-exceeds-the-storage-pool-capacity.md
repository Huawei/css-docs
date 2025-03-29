---
title: "Failed to Expand the PVC Capacity Because the Target Capacity Exceeds the Storage Pool Capacity"
linkTitle: "Failed to Expand the PVC Capacity Because the Target Capacity Exceeds the Storage Pool Capacity"
description: 
weight: 4
---

## Symptom{#en-us_topic_0000001279996521_section1566717121452}

In a Kubernetes environment earlier than 1.23, PVC capacity expansion fails when the target capacity exceeds the storage pool capacity.

## Root Cause Analysis{#en-us_topic_0000001279996521_section1425013451056}

This is a known issue in the Kubernetes community. For details, see  [Recovering from Failure when Expanding Volumes](https://kubernetes.io/docs/concepts/storage/persistent-volumes/#recovering-from-failure-when-expanding-volumes).

## Solution or Workaround{#section1730118471221}

For details, see  [Recovering from Failure when Expanding Volumes](https://kubernetes.io/docs/concepts/storage/persistent-volumes/#recovering-from-failure-when-expanding-volumes).

