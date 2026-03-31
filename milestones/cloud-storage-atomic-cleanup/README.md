# Case Study: Atomic Cloud Storage Deletion & Resource Cleanup

## 📌 Overview
In decoupled Serverless architectures, referential integrity is not automatic. This milestone addresses the management of "orphaned" multimedia assets in **Cloud Storage** following the deletion of records in **Firestore**.

## ❌ The Problem
Originally, deleting a post only removed the text document. This caused:
1. **Ghost Storage Costs:** Binary files remained in the bucket without any reference.
2. **Data Inconsistency:** Clutter in the company's file system and storage infrastructure.

## 🛠️ The Solution (Architectural Approach)
I implemented a **Sequential Deletion Pipeline**. We inverted the logical order to ensure the asset's URL is not lost before the physical deletion is confirmed.

### Logical Flow (Atomic Sequence)

```mermaid
graph TD
    A[Trigger Delete] --> B{Has mediaUrl?}
    B -- Yes --> C[Delete from Cloud Storage]
    C --> D[Delete Firestore Document]
    B -- No --> D
    D --> E[Update UI State]

💻 Technical Implementation Highlights
Decoupled Cleanup: The service is agnostic; if no mediaUrl exists, the pipeline continues without errors.

UI Synchronization: Refactored PostCard and PostDetailModal to emit events with multimedia payloads.

Error Handling: Prevents network failures from leaving documents locked or files orphaned by using a try-catch-finally block in the service layer.

📈 Impact
Cost Optimization: Guaranteed 1:1 ratio between database documents and binary files.

Infrastructure Scalability: Clean storage architecture ready for MVP market launch.
