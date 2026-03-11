***Smart Media Analytics*** is a high-performance, event-driven web application that uses AWS Rekognition to automatically analyze images and provide object detection with confidence scores. Built with a "Serverless First" mindset.

🏗️ Architecture Overview
The system is designed for high scalability and security, utilizing a "Direct-to-S3" upload pattern to minimize server overhead and maximize performance.

🛰️ The Data Journey:-

1) Secure Handshake: The React (Vite) frontend requests a temporary "Upload Ticket" from an AWS Lambda via API Gateway.

2) Direct-to-Cloud Upload: Using a Presigned POST URL, the frontend pushes the image directly to Amazon S3, bypassing the need for a heavy backend server.

3) Event-Driven Trigger: S3 detects the new file and immediately fires an S3 Event Notification to the Processing Lambda.

4) Computer Vision: The Lambda calls Amazon Rekognition to extract high-confidence labels (e.g., "Architecture," "Skyscraper," "98% Match").

5) Metadata Persistence: Results are indexed in Amazon DynamoDB for sub-second retrieval.

6) Real-Time Gallery: The frontend fetches the analyzed results via a REST API to display the intelligent 4-column grid.





