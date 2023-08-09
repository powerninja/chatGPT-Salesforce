# DevOpsCenter について

![qrcode](contents/ja/images/qr-code.jpg)

- スライド:https://powerninja.github.io/chatGPT-Salesforce/ja/index
- リポジトリ:https://github.com/powerninja/chatGPT-Salesforce

graph TD
User(User) -->|HTTP/HTTPS| CF(CloudFront)
CF --> S3(S3 for Images)
CF --> ELB(Elastic Load Balancing)
ELB --> EC2_A[EC2 Instance A]
ELB --> EC2_B[EC2 Instance B]
EC2_A --> RDS[Amazon RDS (MySQL)]
EC2_B --> RDS
User -->|API Calls| AGW(API Gateway)
AGW --> ExternalAPI[External SaaS API]
User -->|Authentication| Cognito(Cognito)
User --> Lambda[AWS Lambda for Cart & Purchase]
Lambda --> DynamoDB(DynamoDB for Sessions)
subgraph Availability Zone A
EC2_A
RDS
end
subgraph Availability Zone B
EC2_B
end
classDef aws fill:#FF9900
class User,CF,S3,ELB,EC2_A,EC2_B,RDS,AGW,ExternalAPI,Cognito,Lambda,DynamoDB aws
