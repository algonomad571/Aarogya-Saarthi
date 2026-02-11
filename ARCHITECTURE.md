# Aarogya Saarthi - System Architecture

## High-Level Architecture

```
┌─────────────────────────────────────────────────────────────────┐
│                        AAROGYA SAARTHI                          │
│              AI-Driven Hospital Management System                │
└─────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────┐
│                         PRESENTATION LAYER                       │
├─────────────────────────────────────────────────────────────────┤
│  React Frontend (Vite)                                          │
│  ┌──────────────┬──────────────┬──────────────┬──────────────┐ │
│  │  Dashboard   │   Patient    │    Staff     │  Resources   │ │
│  │              │  Management  │  Management  │  Management  │ │
│  └──────────────┴──────────────┴──────────────┴──────────────┘ │
│  ┌──────────────────────────────────────────────────────────┐  │
│  │           AI Prediction Modules (7 Models)                │  │
│  │  Beds | Ventilators | PPE | Blood | Equipment | Priority │  │
│  └──────────────────────────────────────────────────────────┘  │
└─────────────────────────────────────────────────────────────────┘
                              │
                              │ REST API (JWT Auth)
                              ▼
┌─────────────────────────────────────────────────────────────────┐
│                       APPLICATION LAYER                          │
├─────────────────────────────────────────────────────────────────┤
│  Express.js Backend Server (Node.js)                            │
│  ┌──────────────┬──────────────┬──────────────┬──────────────┐ │
│  │   Auth       │   Patient    │    Staff     │  Resource    │ │
│  │   Service    │   Service    │   Service    │  Service     │ │
│  └──────────────┴──────────────┴──────────────┴──────────────┘ │
│  ┌──────────────────────────────────────────────────────────┐  │
│  │     Automated Payroll Service (Cron Jobs)                 │  │
│  │     Indian Tax Calculation | Monthly Processing           │  │
│  └──────────────────────────────────────────────────────────┘  │
└─────────────────────────────────────────────────────────────────┘
                              │
                    ┌─────────┴─────────┐
                    │                   │
                    ▼                   ▼
┌──────────────────────────┐  ┌──────────────────────────┐
│   DATA LAYER             │  │   BLOCKCHAIN LAYER        │
├──────────────────────────┤  ├──────────────────────────┤
│  MongoDB (AarogyaSaarthi)│  │  Ethereum Smart Contract │
│  ┌────────────────────┐  │  │  ┌────────────────────┐  │
│  │ Patient Collection │  │  │  │  DataIntegrity     │  │
│  │ Staff Collection   │  │  │  │  Contract          │  │
│  │ Resources          │  │  │  │  (Solidity 0.8)    │  │
│  │ BloodBank          │  │  │  │                    │  │
│  │ Login Info         │  │  │  │  Event: DataStored │  │
│  └────────────────────┘  │  │  └────────────────────┘  │
└──────────────────────────┘  └──────────────────────────┘
                    │
                    ▼
┌─────────────────────────────────────────────────────────────────┐
│                    MACHINE LEARNING LAYER                        │
├─────────────────────────────────────────────────────────────────┤
│  Python ML Microservices (7 Independent Services)               │
│                                                                  │
│  ┌──────────────┬──────────────┬──────────────┬──────────────┐ │
│  │ AI Testing   │  Bed Testing │ Blood Bank   │ Diagnostic   │ │
│  │ (Priority)   │  (Prediction)│ (Prediction) │ Equipment    │ │
│  │              │              │              │              │ │
│  │ Linear Reg   │ Linear Reg + │ Linear Reg + │ 20+ Models   │ │
│  │ + Priority   │ TensorFlow   │ Label Encoder│ (joblib)     │ │
│  └──────────────┴──────────────┴──────────────┴──────────────┘ │
│  ┌──────────────┬──────────────┬──────────────┐                │
│  │ Medical      │ PPE Testing  │ Ventilator   │                │
│  │ Equipment    │ (Demand)     │ (Critical)   │                │
│  │              │              │              │                │
│  │ 10+ Models   │ ML Model     │ ML Model     │                │
│  │ (joblib)     │ (52K records)│ (pkl)        │                │
│  └──────────────┴──────────────┴──────────────┘                │
│                                                                  │
│  Each service runs independently with:                          │
│  • Flask/Express.js API                                         │
│  • Trained model (.pkl/.joblib)                                 │
│  • MongoDB integration                                          │
│  • CORS enabled                                                 │
└─────────────────────────────────────────────────────────────────┘
```

## Data Flow Diagram

### User Authentication Flow
```
User → Login Page → POST /login → JWT Token → 
Protected Routes → Dashboard Access
```

### Patient Management Flow
```
Admin → Add Patient Form → POST /add_patient → 
MongoDB (Patient Collection) → Blockchain Hash → 
Smart Contract Event Emitted
```

### Payroll Automation Flow
```
Cron Job (1st of month) → Fetch Staff from MongoDB → 
Calculate Tax (Indian Slabs) → Compute Net Salary → 
Update Staff Records → Deduct from Hospital Balance
```

### AI Prediction Flow
```
User Request → Prediction Module → ML Microservice API → 
Load Trained Model → Predict Using Historical Data → 
Return Forecast → Display in Dashboard
```

## Technology Stack Layers

### Layer 1: Frontend (Client-Side)
- **Framework**: React 18+ with Vite
- **Routing**: React Router v6
- **HTTP Client**: Axios
- **State Management**: React Hooks
- **Styling**: CSS + Responsive Design

### Layer 2: Backend (Server-Side)
- **Runtime**: Node.js v18+
- **Framework**: Express.js v4.21+
- **Database Driver**: MongoDB Native Driver + Mongoose v8.9+
- **Authentication**: JWT (jsonwebtoken)
- **Scheduling**: node-cron
- **Middleware**: CORS, body-parser

### Layer 3: Database (Persistence)
- **Database**: MongoDB Atlas
- **Database Name**: AarogyaSaarthi
- **Collections**: 6 main collections
- **Indexing**: Unique constraints on IDs
- **Backup**: Cloud-based automatic backups

### Layer 4: Blockchain (Security)
- **Platform**: Ethereum
- **Contract Language**: Solidity ^0.8.0
- **Library**: Ethers.js v5.7.2
- **Purpose**: Data integrity and audit trail

### Layer 5: Machine Learning (Intelligence)
- **Language**: Python 3.8+
- **Libraries**: 
  - scikit-learn (ML algorithms)
  - TensorFlow (deep learning)
  - pandas (data manipulation)
  - NumPy (numerical computing)
- **Model Storage**: joblib/pickle
- **APIs**: Flask/Express.js wrappers

## Microservices Architecture

### ML Microservices Design

Each ML service follows this pattern:

```
ML Service
├── app.py (Flask API)
├── server.js (Express.js wrapper)
├── model_file.pkl/.joblib (Trained model)
├── training_script.py (Model training)
├── dataset.csv (Training data)
├── requirements.txt (Python deps)
├── package.json (Node.js deps)
├── Procfile (Deployment config)
└── render.yaml (Platform config)
```

**Service Independence**:
- Each service runs on its own port
- Independent deployment
- Separate resource allocation
- Isolated failure domains
- Scalable horizontally

## Security Architecture

### Authentication & Authorization
```
┌─────────────┐
│   Client    │
└──────┬──────┘
       │ POST /login (credentials)
       ▼
┌─────────────┐
│   Server    │
│  Validates  │
└──────┬──────┘
       │ Valid credentials
       ▼
┌─────────────┐
│ JWT Token   │
│ (7 days)    │
└──────┬──────┘
       │ Token in header
       ▼
┌─────────────┐
│ Protected   │
│ Routes      │
└─────────────┘
```

### Data Security Layers
1. **Transport Security**: HTTPS/TLS
2. **Authentication**: JWT tokens
3. **Authorization**: Route middleware
4. **Data Integrity**: Blockchain hashing
5. **Input Validation**: Server-side checks
6. **Environment Security**: .env files (gitignored)

## Database Schema Design

### Collections & Relationships

```
┌─────────────────┐
│   Login Info    │
│  ┌───────────┐  │
│  │ user      │  │
│  │ password  │  │
│  │ is_active │  │
│  │ _id       │─────┐
│  └───────────┘  │   │ userId (reference)
└─────────────────┘   │
                      │
        ┌─────────────┴─────────────┬─────────────┐
        ▼                           ▼             ▼
┌─────────────────┐     ┌─────────────────┐  ┌─────────────┐
│     Staff       │     │    Patient      │  │  Resources  │
│  ┌───────────┐  │     │  ┌───────────┐  │  │             │
│  │ emp_id    │  │     │  │ pat_id    │  │  │ Dynamic     │
│  │ f_name    │  │     │  │ Name      │  │  │ Fields      │
│  │ l_name    │  │     │  │ Age       │  │  │             │
│  │ email     │  │     │  │ Blood Type│  │  │ Quantities  │
│  │ Salary    │  │     │  │ Condition │  │  │             │
│  │ Net_Salary│  │     │  │ Doctor    │  │  └─────────────┘
│  │ userID    │──┘     │  │ userID    │──┘
│  └───────────┘        │  └───────────┘
└─────────────────┘     └─────────────────┘
```

## Deployment Architecture

### Hosting Strategy
- **Platform**: Render.com
- **Frontend**: Static build deployment
- **Backend**: Node.js service
- **ML Services**: Python services (7 instances)
- **Database**: MongoDB Atlas (cloud)
- **Blockchain**: Ethereum network

### Environment Separation
```
Development → Staging → Production
     ↓            ↓          ↓
   Local      Test DB    Production DB
   Dev DB     Test Env   Live Environment
```

## Performance Optimization

### Frontend Optimization
- Vite for fast builds
- Code splitting
- Lazy loading routes
- Optimized bundle size

### Backend Optimization
- Database indexing
- Connection pooling
- Caching strategies
- Rate limiting

### ML Service Optimization
- Pre-trained models
- Model caching
- Efficient data loading
- Batch predictions

## Scalability Considerations

### Horizontal Scaling
- ML microservices can scale independently
- Stateless backend design
- Load balancer ready
- Database sharding possible

### Vertical Scaling
- Increase server resources
- Database performance tuning
- Model optimization
- Memory management

## Monitoring & Logging

### Application Monitoring
- Server health checks
- API endpoint monitoring
- Database connection status
- ML service availability

### Error Logging
- Console logging
- Database error tracking
- API error responses
- Client-side error boundaries

## Future Architecture Enhancements

1. **Containerization**: Docker for all services
2. **Orchestration**: Kubernetes for ML services
3. **API Gateway**: Centralized API management
4. **Caching Layer**: Redis for frequently accessed data
5. **Message Queue**: RabbitMQ/Kafka for async operations
6. **CDN**: Static asset delivery
7. **Monitoring**: Prometheus + Grafana
8. **Log Aggregation**: ELK stack
9. **CI/CD Pipeline**: Automated testing and deployment
10. **Multi-region Deployment**: Geographic distribution

---

This architecture supports the current functionality while being designed for future growth and scalability.
