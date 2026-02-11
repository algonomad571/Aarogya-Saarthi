# Aarogya Saarthi - Comprehensive Project Description

## Overview

**Aarogya Saarthi** (formerly known as JHU_TechLions) is an advanced **AI-driven, Blockchain-protected Hospital Management System** designed to streamline hospital operations, optimize resource allocation, and enhance patient care through intelligent predictions and secure data management.

## Project Name

- **Current Name**: Aarogya Saarthi
- **Original Name**: JHU_TechLions
- **Repository**: algonomad571/Aarogya-Saarthi

## Core Concept

Aarogya Saarthi combines three cutting-edge technologies to create a comprehensive hospital management solution:

1. **Artificial Intelligence (AI)**: Machine learning models for predictive analytics and resource optimization
2. **Blockchain**: Smart contracts for data integrity and security
3. **Modern Web Stack**: Full-stack web application with React frontend and Express.js backend

## Architecture

The project follows a modern full-stack architecture with four major components:

### 1. Frontend (React + Vite)

**Technology Stack:**
- React.js with Vite for fast development and optimized builds
- React Router for navigation
- Responsive UI design

**Key Features:**
- **Authentication System**: Secure login with JWT token-based authentication
- **Main Dashboard**: Central hub for hospital operations management
- **Staff Management**: Add, view, and manage hospital staff
- **Patient Management**: 
  - Add new patients
  - View current patients
  - Track past patients
- **Resource Management**: 
  - Add and track hospital resources
  - View currently available resources
- **Prediction Modules**:
  - AI-based workload prediction
  - Bed requirement forecasting
  - Ventilator requirement prediction
  - PPE kit demand prediction
  - Diagnostic equipment needs
  - Blood bank management
- **Public Pages**:
  - Home page
  - About page
  - Services page
  - Contact us page
  - Terms and Conditions

### 2. Backend (Express.js + MongoDB)

**Technology Stack:**
- Node.js with Express.js framework
- MongoDB with both native driver and Mongoose ODM
- JWT for authentication
- Cron jobs for automated tasks

**Database**: 
- MongoDB database named "AarogyaSaarthi"
- Collections include:
  - Login Info
  - Staff
  - Patient
  - PastPatient
  - Resources
  - BloodBank

**Key Features:**

**Authentication & Security:**
- JWT token-based authentication
- Token expiration (7 days)
- Protected routes with middleware

**Staff Management:**
- Employee registration with unique IDs
- Employee details tracking (name, email, age, phone, gender)
- Duplicate prevention system

**Patient Management:**
- Patient registration with comprehensive medical data
- Track patient ID, medical conditions, blood type, medications
- Admission details (type, date, doctor, room)
- Insurance provider information
- Test results tracking
- Historical patient data

**Resource Management:**
- Dynamic resource tracking
- Quantity-based updates
- User-specific resource allocation

**Automated Payroll System:**
- Indian tax slab calculation
- Monthly salary processing with cron jobs
- Automatic deduction from hospital bank balance
- Net salary calculation after tax
- Scheduled payment on 1st of every month
- Employee bank account management

**API Endpoints:**
- POST `/login` - User authentication
- POST `/add_staff` - Add new staff member
- POST `/add_patient` - Register new patient
- POST `/add_resources` - Update resource inventory
- POST `/process_salaries` - Manual salary processing
- GET `/patients` - Fetch current patients
- GET `/past_patients` - Fetch past patients
- GET `/staff` - Fetch staff members
- GET `/all_resources` - Fetch available resources
- GET `/auth` - Verify authentication token

### 3. Machine Learning Models (7 Different Prediction Systems)

The application includes seven independent ML microservices, each serving specific prediction needs:

#### 3.1 AI Testing (`ai_testing/`)
**Purpose**: Patient priority assignment and triage
**Technology**: Python with pandas, MongoDB integration
**Features**:
- Calculates priority scores based on:
  - Admission type (Emergency: 3, Urgent: 2, Elective: 1)
  - Sepsis status (+15 points)
  - Heart rate abnormalities (+5 points)
  - Glucose levels (+5 points)
  - Potassium levels (+5 points)
  - Lactate levels (+5 points)
- Sorts and displays top 100 high-priority patients
- Real-time patient data from MongoDB

#### 3.2 Bed Requirement Prediction (`bed_testing/`)
**Purpose**: Forecast hospital bed requirements
**Technology**: 
- Python with scikit-learn, TensorFlow
- Linear Regression model
**Features**:
- Predicts bed requirements for next 3 months
- Uses historical data (Oct-Feb) to predict (Mar-May)
- Time-series analysis
- Visualization with matplotlib
- Helps prevent bed shortages

#### 3.3 Blood Bank Management (`blood_bank/`)
**Purpose**: Predict blood demand by type
**Technology**:
- Python with scikit-learn
- Linear Regression with Label Encoding
**Features**:
- Predicts demand for different blood types (A+, A-, B+, B-, O+, O-, AB+, AB-)
- Historical trend analysis (Oct-Feb)
- Trained model persistence (blood_demand_model.pkl)
- Label encoder for blood type categorization
- MongoDB integration for live data

#### 3.4 Diagnostic Equipment Prediction (`diagnostic_testing/`)
**Purpose**: Predict requirements for 20+ diagnostic equipment types
**Technology**: 
- Python with scikit-learn (joblib)
- Multiple trained models for each equipment
**Equipment Categories**:
- Imaging: CT Scan, MRI, X-Ray, Ultrasound
- Monitoring: ECG, Bedside monitors, Blood pressure monitors, Pulse oximeters
- Laboratory: Centrifuge, ESR analyzer, Laboratory analyzers
- Clinical: Stethoscopes, Thermometers, Scales, Otoscopes, Ophthalmoscopes
- Specialized: Dopplers, Incubators, Diagnostic sets, Binocular loupes
**Features**:
- Individual models for each equipment type (20+ .joblib files)
- Accurate demand forecasting
- Prevents equipment shortages

#### 3.5 Medical Equipment Prediction (`medical_testing/`)
**Purpose**: Predict surgical and medical instrument requirements
**Technology**: Python with scikit-learn
**Equipment Types**:
- Surgical instruments: Scalpels, Scissors, Forceps
- Specialized tools: Hemostats, Clamps, Retractors
- Precision instruments: Needle holders, Surgical hooks
- Support equipment: Suction devices
**Features**:
- 10+ individual trained models
- Comprehensive surgical inventory management
- Prevents critical instrument shortages

#### 3.6 PPE Kit Requirement (`ppe_testing/`)
**Purpose**: Predict Personal Protective Equipment demand
**Technology**: 
- Python with pandas, scikit-learn
- Machine learning model (ppe_model.pkl)
**Features**:
- PPE kit demand forecasting
- Dataset with 52,000+ records
- Critical for infection control
- Ensures staff safety
- Pandemic preparedness

#### 3.7 Ventilator Requirement (`ventilator_testing/`)
**Purpose**: Predict ventilator needs for critical care
**Technology**: Python with machine learning
**Features**:
- Critical care equipment forecasting
- Trained model (ventilator_model.pkl)
- Life-saving equipment availability prediction
- ICU capacity planning

**Common ML Infrastructure:**
- Each model deployed as independent microservice
- Express.js servers for API endpoints
- Flask/Python apps for ML inference
- Procfile for deployment (Render.com ready)
- render.yaml configuration files
- CORS enabled for frontend integration

### 4. Blockchain Component (Ethereum Smart Contract)

**Purpose**: Ensure data integrity and immutability
**Technology**: Solidity ^0.8.0

**Smart Contract: DataIntegrity**
```solidity
- Function: storeData(bytes32 dataHash, string collectionName)
- Event: DataStored(address user, bytes32 dataHash, string collectionName, uint256 timestamp)
```

**Features**:
- Cryptographic hashing of sensitive data
- Immutable audit trail
- Timestamp-based records
- User address tracking
- Collection-wise data segregation

**Integration**:
- Ethers.js library for blockchain interaction
- MongoDB integration (`mongo.js`)
- Environment-based configuration (`.env`)

## Technology Stack Summary

### Frontend
- React.js
- Vite
- React Router
- Axios (HTTP client)
- CSS/Modern styling

### Backend
- Node.js
- Express.js
- MongoDB (Native driver + Mongoose)
- JWT (jsonwebtoken)
- node-cron (scheduled tasks)
- body-parser
- CORS
- dotenv (environment variables)

### Machine Learning
- Python
- pandas
- NumPy
- scikit-learn
- TensorFlow
- matplotlib
- seaborn
- joblib (model persistence)
- pymongo (MongoDB integration)

### Blockchain
- Solidity ^0.8.0
- Ethers.js v5.7.2
- Ethereum blockchain

### DevOps & Deployment
- Render.com (deployment platform)
- Environment variables (.env)
- Package managers (npm, pip)

## Key Features & Capabilities

### 1. Intelligent Resource Management
- Real-time tracking of hospital resources
- AI-powered demand prediction
- Automated inventory alerts
- Resource optimization

### 2. Comprehensive Patient Care
- Complete patient lifecycle management
- Medical history tracking
- Current and past patient records
- Multi-parameter health monitoring

### 3. Staff Administration
- Employee database management
- Automated payroll with Indian tax compliance
- Monthly salary processing
- Staff performance tracking

### 4. Predictive Analytics
- 7 different ML models for various predictions
- Historical data analysis
- Future demand forecasting
- Workload optimization

### 5. Data Security & Integrity
- Blockchain-backed data immutability
- JWT-based authentication
- Encrypted data hashing
- Audit trail maintenance

### 6. Financial Management
- Automated salary calculations
- Tax computation (Indian tax slabs)
- Bank account management
- Budget tracking

## Use Cases

1. **Hospital Administrators**: Complete oversight of operations, resources, and staff
2. **Medical Staff**: Quick access to patient information and resource availability
3. **Resource Managers**: Inventory management and demand forecasting
4. **Financial Officers**: Automated payroll and financial tracking
5. **Emergency Response**: Priority-based patient triage and critical resource allocation

## Project Structure

```
Aarogya-Saarthi/
├── Backend/
│   ├── server.js          # Main Express server
│   ├── payment.js         # Payment processing
│   └── package.json
├── Frontend/
│   ├── src/
│   │   ├── Pages/
│   │   │   └── Home/
│   │   │       ├── JHU Dashboard/
│   │   │       └── Main/
│   │   ├── App.jsx
│   │   └── main.jsx
│   ├── index.html
│   ├── vite.config.js
│   └── package.json
├── Blockchain/
│   ├── secure.sol         # Smart contract
│   ├── mongo.js           # MongoDB integration
│   └── package.json
├── ML models/
│   ├── ai_testing/        # Patient priority system
│   ├── bed_testing/       # Bed requirement prediction
│   ├── blood_bank/        # Blood demand prediction
│   ├── diagnostic_testing/# Diagnostic equipment prediction
│   ├── medical_testing/   # Medical equipment prediction
│   ├── ppe_testing/       # PPE kit prediction
│   └── ventilator_testing/# Ventilator prediction
├── package.json           # Root package
└── README.md
```

## Database Schema

### Collections in MongoDB (AarogyaSaarthi database)

1. **Login Info**
   - user (username)
   - password (hashed)
   - is_active (boolean)
   - _id (userId)

2. **Staff**
   - emp_id (unique identifier)
   - f_name, l_name
   - email, phone
   - age, gender, date
   - Salary, bank_account
   - Net_Salary (calculated)
   - createdAt

3. **Patient**
   - Patient ID (unique)
   - Name, Age, Gender
   - Blood Type
   - Medical Condition
   - Date of Admission
   - Doctor, Room Number, Room type
   - Admission Type
   - Insurance Provider
   - Medication, Test Results
   - createdAt

4. **PastPatient**
   - Same schema as Patient
   - Historical records

5. **Resources**
   - Dynamic fields for various resources
   - Quantity tracking
   - userId association

6. **BloodBank**
   - Types of blood (A+, A-, B+, B-, O+, O-, AB+, AB-)
   - Monthly data (October - February)
   - Output (predicted demand)

## Deployment & Configuration

### Environment Variables Required

**Backend:**
- `MONGODB_URI`: MongoDB connection string
- `PORT`: Server port (default: 3000)
- `JWT_SECRET`: Secret key for JWT (currently hardcoded as 'love')

**Blockchain:**
- `.env` configuration for Ethereum network
- Smart contract deployment parameters

**ML Models:**
- MongoDB connection strings
- Model file paths
- API endpoint configurations

### Deployment Platforms
- **Primary**: Render.com (configured with render.yaml)
- **Frontend**: Vite build for production
- **Backend**: Node.js server
- **ML Models**: Independent Python microservices

## Security Features

1. **Authentication**: JWT-based token system with 7-day expiration
2. **Authorization**: Protected routes with middleware
3. **Data Integrity**: Blockchain hashing for critical data
4. **Input Validation**: Server-side validation for all inputs
5. **Environment Security**: Sensitive data in .env files (gitignored)

## Future Enhancements Potential

1. Role-based access control (RBAC)
2. Real-time notifications
3. Mobile application
4. Integration with medical devices
5. Telemedicine features
6. Advanced analytics dashboard
7. Multi-hospital network support
8. AI-powered diagnosis assistance
9. Enhanced blockchain integration
10. Cloud storage for medical images

## Development Workflow

1. **Frontend Development**: Vite dev server for hot module replacement
2. **Backend Development**: Node.js with auto-restart
3. **ML Model Training**: Jupyter notebooks or Python scripts
4. **Testing**: Currently configured but not implemented
5. **Deployment**: Git push to Render.com for automatic deployment

## Project Impact

Aarogya Saarthi addresses critical challenges in hospital management:

- **Reduces waste**: AI predictions prevent over-ordering and shortages
- **Saves lives**: Priority-based patient care and critical equipment availability
- **Increases efficiency**: Automated processes reduce administrative burden
- **Ensures compliance**: Automated tax calculations and payroll
- **Enhances security**: Blockchain provides immutable audit trails
- **Improves planning**: Predictive analytics for resource allocation

## Conclusion

Aarogya Saarthi represents a comprehensive, modern approach to hospital management, leveraging AI, blockchain, and full-stack web technologies to create an efficient, secure, and intelligent healthcare management system. The project demonstrates the successful integration of multiple cutting-edge technologies to solve real-world healthcare challenges.

---

**Project Status**: Active Development
**License**: ISC
**Original Repository**: github.com/muskan171105/JHU_TechLions
**Current Repository**: github.com/algonomad571/Aarogya-Saarthi
