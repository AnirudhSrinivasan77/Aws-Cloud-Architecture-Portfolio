📸***VisionAnalytics: Serverless AI Image Processor***
VisionAnalytics is a high-performance, event-driven web application that uses AWS Rekognition to automatically analyze images and provide object detection with confidence scores. Built with a "Serverless First" mindset.

🏗️ Architecture Overview
The system is designed for high scalability and security, utilizing a "Direct-to-S3" upload pattern to minimize server overhead and maximize performance.

🛰️ The Data Journey:-

1) Secure Handshake: The React (Vite) frontend requests a temporary "Upload Ticket" from an AWS Lambda via API Gateway.

2) Direct-to-Cloud Upload: Using a Presigned POST URL, the frontend pushes the image directly to Amazon S3, bypassing the need for a heavy backend server.

3) Event-Driven Trigger: S3 detects the new file and immediately fires an S3 Event Notification to the Processing Lambda.

4) Computer Vision: The Lambda calls Amazon Rekognition to extract high-confidence labels (e.g., "Architecture," "Skyscraper," "98% Match").

5) Metadata Persistence: Results are indexed in Amazon DynamoDB for sub-second retrieval.

6) Real-Time Gallery: The frontend fetches the analyzed results via a REST API to display the intelligent 4-column grid.


🛠️ The Tech Stack
Frontend: React.js, CSS3 (Custom 4-Column Grid), Vite
Storage: Amazon S3 (Image Hosting)
Database: Amazon DynamoDB (Metadata storage)
Compute: AWS Lambda (Python 3.9)
AI Service: AWS Rekognition (Computer Vision)
API Layer: AWS API Gateway (REST)



🚀 Key Features & Engineering Wins :-

🔐 Security: Presigned URLs
Instead of opening the S3 bucket to the public, I implemented Presigned POST URLs. This ensures that only authenticated users can upload files, and they can only do so within a 60-second window.

⚡ Performance: Event-Driven Scaling
By using S3 Triggers, the AI analysis only runs when a file is actually uploaded. There are no idle servers, making the architecture nearly 100% cost-efficient.

💅 Frontend: Responsive 4-Column Grid
The UI uses a custom-built CSS grid that handles dynamic image aspect ratios and displays AI-generated tags in a clean, modern interface.


