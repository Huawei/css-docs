---
title: "Configuring ALUA"
linkTitle: "Configuring ALUA"
description: 
weight: 10
---

Asymmetric Logical Unit Access \(ALUA\) is a model that supports access to multiple target ports. In the multipathing state, ALUA presents active/passive volumes to the host and provides a port access status switchover interface to switch over the working controllers for volumes. For example, when a volume of a controller fails, you can set the status of ports on the controller to  **Unavailable**. After the host multipathing software that supports ALUA detects the status, it switches subsequent I/Os from the failed controller to the peer controller.






