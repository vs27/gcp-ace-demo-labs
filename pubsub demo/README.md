## GCP ACE Demo 2 – Pub/Sub Messaging (Pull Model)

### 🎯 Objective
Hands-on demonstration of Google Cloud Pub/Sub fundamentals aligned to the Associate Cloud Engineer (ACE) certification.

### 🧠 What this demo validates
- Topic and subscription creation via CLI
- Message publish and pull consumption
- Understanding of at-least-once delivery and acknowledgements
- Awareness of push vs pull models and message redelivery behavior
- Cost-safe cleanup after verification

### 🏗️ Demo Architecture Decision
Pub/Sub was chosen to demonstrate:
- Serverless, managed messaging
- Decoupled producer–consumer communication
- Horizontal scalability without server provisioning
- Event-driven design patterns used in cloud-native applications

### ⚙ CLI Commands Executed
```bash
gcloud config set project glowing-sanctum-482200-f5
gcloud pubsub topics create ace-demo-topic
gcloud pubsub subscriptions create ace-demo-sub --topic=ace-demo-topic --ack-deadline=20
gcloud pubsub topics publish ace-demo-topic --message="Hello ACE - 1"
gcloud pubsub topics publish ace-demo-topic --message="Hello ACE - 2"
gcloud pubsub subscriptions pull ace-demo-sub --limit=5 --auto-ack
gcloud pubsub subscriptions delete ace-demo-sub --quiet
gcloud pubsub topics delete ace-demo-topic --quiet
