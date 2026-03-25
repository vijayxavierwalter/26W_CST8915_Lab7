Vijay Xavier Walter.     
041276252.     
CST8915 Full-stack Cloud-native Development.      
Winter 2026.      

---

## Demo Video

🎥 [Watch Demo Video] (https://youtu.be/pLpp_bueoxo)


# RabbitMQ Configuration Analysis

## 1. Stateless or Stateful?
RabbitMQ is a **stateful application** because it stores messages, queues, and broker data that must persist across restarts.

---

## 2. Implications of No Persistent Storage
- Data is stored in **ephemeral container storage**
- Messages and queues are **not saved permanently**
- Any failure or restart can cause **data loss**
- Not suitable for production workloads

---

## 3. What happens when the pod is deleted/restarted?
- Kubernetes creates a new pod automatically
- RabbitMQ starts with **empty state**
- All queues and messages are **lost**
- This happens because pods are **temporary by design**

---

## 4. Potential Solutions

### Add Persistent Storage
- Use **PersistentVolume (PV)** and **PersistentVolumeClaim (PVC)**
- Ensures data survives pod restart

### Use StatefulSet
- Provides stable identity and persistent storage
- Better suited for stateful applications

### Use RabbitMQ Operator / Helm
- Simplifies deployment and management
- Supports high availability and scaling

---

## 5. Does Azure Service Bus solve the issue?
Yes, Azure Service Bus is a **fully managed messaging service** that provides:
- Built-in persistence
- High availability
- No need to manage infrastructure

It solves the storage issue but replaces RabbitMQ instead of fixing its configuration.

---

## Conclusion
RabbitMQ is a stateful application, but in this lab it is deployed without persistent storage, which causes data loss when the pod restarts. This issue can be solved by adding persistent volumes or using a StatefulSet. Alternatively, Azure Service Bus avoids these issues by providing a fully managed and persistent messaging solution.
