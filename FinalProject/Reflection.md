# Reflection: Lec Task

## What I Learned
* **Event-Driven Design:** I learned how to build systems that react to data in real-time using serverless triggers.
* **Storage Optimization:** I gained a deep understanding of why columnar formats like Parquet are essential for handling Big Data compared to standard CSVs.
* **Resilient Engineering:** I learned the importance of implementing Dead Letter Queues (DLQ) to ensure no data is "silently lost" during ingestion.

## What was Challenging
* **Orchestration Logic:** Coordinating the flow between three different transformation workers while maintaining state and handling potential failures was the most complex part of the design.
* **Business Rule Implementation:** Developing the logic for data interpolation to fill missing IoT readings required careful consideration of time-series integrity.

## What I Improved from Previous Tasks
* **End-to-End Thinking:** While previous projects focused on visualization, this project allowed me to design the entire underlying infrastructure (The ETL Pipeline).
* **Professional Standards:** I improved my ability to document complex technical architectures, focusing on both the business case and the technical implementation.
