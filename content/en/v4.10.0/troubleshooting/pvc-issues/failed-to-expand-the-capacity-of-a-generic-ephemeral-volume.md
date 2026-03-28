---
title: "Failed to Expand the Capacity of a Generic Ephemeral Volume"
linkTitle: "Failed to Expand the Capacity of a Generic Ephemeral Volume"
description: 
weight: 3
---

## Symptom{#en-us_topic_0000001279996521_section1566717121452}

In an environment where the Kubernetes version is earlier than 1.25, the capacity of a  [generic ephemeral volume](https://kubernetes.io/docs/concepts/storage/ephemeral-volumes/#generic-ephemeral-volumes)  of the LUN type fails to be expanded. The system displays a message indicating that the PV capacity has been expanded, but the PVC capacity fails to be updated.

## Root Cause Analysis{#en-us_topic_0000001279996521_section1425013451056}

This problem is caused by a Kubernetes  [bug](https://github.com/kubernetes/kubernetes/blob/master/CHANGELOG/CHANGELOG-1.25.md), which has been resolved in Kubernetes 1.25.

