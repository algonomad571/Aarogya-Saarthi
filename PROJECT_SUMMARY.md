# Aarogya Saarthi - Project Summary

## Executive Summary

**Aarogya Saarthi** is a comprehensive hospital management system that leverages cutting-edge technologies including Artificial Intelligence, Blockchain, and modern web development to streamline healthcare operations and improve patient care.

## Project Overview

| Aspect | Details |
|--------|---------|
| **Project Name** | Aarogya Saarthi (formerly JHU_TechLions) |
| **Type** | AI-Driven, Blockchain-Protected Hospital Management System |
| **Repository** | algonomad571/Aarogya-Saarthi |
| **License** | ISC |
| **Status** | Active Development |

## Key Statistics

- **Total Documentation**: 1,450+ lines across 4 comprehensive documents
- **ML Models**: 7 independent prediction systems
- **API Endpoints**: 10+ RESTful endpoints
- **Database Collections**: 6 primary collections
- **Technology Stack**: 4 major layers (Frontend, Backend, ML, Blockchain)

## Technology Breakdown

### Frontend
- **Framework**: React 18+ with Vite
- **Features**: 15+ pages including dashboard, patient management, staff management, and 7 prediction modules
- **Navigation**: React Router with protected routes

### Backend
- **Runtime**: Node.js with Express.js
- **Database**: MongoDB Atlas (AarogyaSaarthi database)
- **Authentication**: JWT with 7-day token expiration
- **Automation**: Cron jobs for monthly payroll processing

### Machine Learning (7 Models)
1. **Patient Priority System** - AI-based triage
2. **Bed Requirement** - 3-month forecast using Linear Regression
3. **Blood Bank** - Blood type demand prediction
4. **Diagnostic Equipment** - 20+ equipment types
5. **Medical Equipment** - Surgical tools forecasting
6. **PPE Kits** - Demand prediction (52K+ data points)
7. **Ventilators** - Critical care equipment planning

### Blockchain
- **Platform**: Ethereum
- **Smart Contract**: DataIntegrity (Solidity 0.8)
- **Purpose**: Immutable data audit trail

## Core Features

### 1. Patient Management
- Complete patient lifecycle tracking
- Current and historical patient records
- Medical conditions, medications, test results
- Insurance provider integration
- AI-based priority assignment for triage

### 2. Staff Administration
- Employee database with unique IDs
- Automated monthly payroll with Indian tax calculations
  - Tax slabs: 0%, 5%, 20%, 30%
  - Standard deduction: ₹50,000
  - Net salary calculation
- Scheduled processing on 1st of every month
- Bank account management

### 3. Resource Management
- Real-time inventory tracking
- Dynamic resource allocation
- Quantity-based updates
- Critical equipment monitoring
- AI-powered demand forecasting

### 4. Predictive Analytics
- Historical data analysis (Oct-Feb)
- Future demand forecasting (Mar-May)
- Time-series predictions
- Multiple specialized models
- Prevents resource shortages

### 5. Security & Compliance
- JWT authentication with middleware protection
- Blockchain-backed data integrity
- Cryptographic hashing of sensitive data
- Audit trail with timestamps
- Environment-based configuration

## Database Schema

### Collections

1. **Login Info**
   - User credentials
   - Active status
   - User ID reference

2. **Staff**
   - Employee details (ID, name, email, phone)
   - Salary information
   - Bank account details
   - Net salary (calculated)

3. **Patient**
   - Patient ID and demographics
   - Medical conditions
   - Admission details
   - Doctor assignments
   - Room allocation
   - Test results

4. **PastPatient**
   - Historical patient records
   - Same schema as Patient

5. **Resources**
   - Dynamic resource fields
   - Quantity tracking
   - User-specific allocation

6. **BloodBank**
   - Blood types (A+, A-, B+, B-, O+, O-, AB+, AB-)
   - Monthly historical data
   - Demand predictions

## API Endpoints

| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| POST | `/login` | User authentication | No |
| POST | `/add_staff` | Add new staff member | Yes |
| POST | `/add_patient` | Register new patient | Yes |
| POST | `/add_resources` | Update inventory | Yes |
| POST | `/process_salaries` | Manual payroll processing | Yes |
| GET | `/patients` | Fetch current patients | No |
| GET | `/past_patients` | Fetch patient history | No |
| GET | `/staff` | Fetch all staff | No |
| GET | `/all_resources` | Fetch available resources | No |
| GET | `/auth` | Verify authentication | Yes |

## ML Model Details

### Model 1: AI Testing (Patient Priority)
- **Purpose**: Triage and priority assignment
- **Algorithm**: Rule-based scoring system
- **Factors**: Admission type, sepsis, vital signs (heart rate, glucose, potassium, lactate)
- **Output**: Priority score, sorted patient list

### Model 2: Bed Testing
- **Purpose**: Hospital bed requirement prediction
- **Algorithm**: Linear Regression + TensorFlow
- **Input**: 5 months historical data (Oct-Feb)
- **Output**: 3-month forecast + visualization
- **Accuracy**: Time-series analysis

### Model 3: Blood Bank
- **Purpose**: Blood demand forecasting by type
- **Algorithm**: Linear Regression with Label Encoding
- **Input**: Blood type + 5 months data
- **Output**: Predicted demand per blood type
- **Models**: Trained model + label encoder (saved as .pkl)

### Model 4: Diagnostic Testing
- **Purpose**: Equipment requirement prediction
- **Algorithm**: Multiple joblib models (20+ equipment types)
- **Equipment**: CT, MRI, X-Ray, Ultrasound, ECG, monitors, analyzers
- **Output**: Individual predictions per equipment

### Model 5: Medical Testing
- **Purpose**: Surgical instrument forecasting
- **Algorithm**: Multiple joblib models (10+ tool types)
- **Tools**: Scalpels, scissors, forceps, hemostats, clamps, retractors
- **Output**: Quantity predictions per tool type

### Model 6: PPE Testing
- **Purpose**: Personal Protective Equipment demand
- **Algorithm**: Machine learning model
- **Dataset**: 52,000+ historical records
- **Output**: PPE kit requirements
- **Critical**: Infection control and staff safety

### Model 7: Ventilator Testing
- **Purpose**: Critical care equipment planning
- **Algorithm**: Machine learning model
- **Output**: Ventilator requirements
- **Priority**: Life-saving equipment availability

## Deployment

### Platform
- **Primary**: Render.com
- **Configuration**: render.yaml files
- **Process**: Procfile for each service

### Architecture
- **Frontend**: Static build deployment
- **Backend**: Node.js service
- **ML Services**: 7 independent Python microservices
- **Database**: MongoDB Atlas (cloud-hosted)
- **Blockchain**: Ethereum network

## Documentation Structure

1. **README.md** (211 lines)
   - Quick overview
   - Key features
   - Installation instructions
   - Technology stack summary

2. **PROJECT_DESCRIPTION.md** (482 lines)
   - Comprehensive project details
   - All features explained
   - Database schema
   - Technology stack breakdown
   - Use cases and impact

3. **ARCHITECTURE.md** (328 lines)
   - System architecture diagrams
   - Data flow diagrams
   - Technology layers
   - Microservices architecture
   - Security architecture
   - Deployment strategy

4. **DEVELOPER_GUIDE.md** (429 lines)
   - Quick start instructions
   - Environment setup
   - Development workflow
   - Common issues and solutions
   - Git workflow
   - Testing procedures

## Project Impact

### Benefits
- **Efficiency**: Automated processes reduce administrative burden
- **Cost Savings**: AI predictions prevent over-ordering and shortages
- **Patient Care**: Priority-based triage and better resource allocation
- **Compliance**: Automated tax calculations and payroll
- **Security**: Blockchain ensures data integrity
- **Planning**: Predictive analytics for resource allocation

### Target Users
1. **Hospital Administrators** - Complete operational oversight
2. **Medical Staff** - Quick access to patient information
3. **Resource Managers** - Inventory and forecasting
4. **Financial Officers** - Automated payroll and tracking
5. **Emergency Response** - Priority-based patient management

## Development Status

### Completed
✅ Full-stack web application (Frontend + Backend)
✅ Authentication system with JWT
✅ Patient management system
✅ Staff administration
✅ Resource tracking
✅ 7 ML prediction models
✅ Blockchain integration
✅ Automated payroll system
✅ MongoDB database integration
✅ Comprehensive documentation

### Potential Enhancements
- Role-based access control (RBAC)
- Real-time notifications
- Mobile application
- Telemedicine features
- Advanced analytics dashboard
- Multi-hospital network support
- Cloud storage for medical images
- Integration with medical devices

## File Structure Summary

```
Aarogya-Saarthi/
├── Documentation (4 files, 1,450+ lines)
│   ├── README.md
│   ├── PROJECT_DESCRIPTION.md
│   ├── ARCHITECTURE.md
│   └── DEVELOPER_GUIDE.md
│
├── Backend/ (Express.js server)
│   ├── server.js (390 lines)
│   └── payment.js
│
├── Frontend/ (React application)
│   ├── src/
│   │   ├── App.jsx
│   │   └── Pages/ (15+ page components)
│   └── vite.config.js
│
├── ML models/ (7 microservices)
│   ├── ai_testing/
│   ├── bed_testing/
│   ├── blood_bank/
│   ├── diagnostic_testing/
│   ├── medical_testing/
│   ├── ppe_testing/
│   └── ventilator_testing/
│
└── Blockchain/
    ├── secure.sol (Smart contract)
    └── mongo.js
```

## Quick Access Links

- **Main Documentation**: [README.md](./README.md)
- **Detailed Description**: [PROJECT_DESCRIPTION.md](./PROJECT_DESCRIPTION.md)
- **Architecture**: [ARCHITECTURE.md](./ARCHITECTURE.md)
- **Developer Guide**: [DEVELOPER_GUIDE.md](./DEVELOPER_GUIDE.md)

## Conclusion

Aarogya Saarthi represents a modern, comprehensive approach to hospital management, successfully integrating AI, blockchain, and full-stack web technologies. The system is production-ready with comprehensive documentation, automated processes, and intelligent predictions that solve real-world healthcare challenges.

---

**Last Updated**: February 11, 2026
**Version**: 1.0.0
**Status**: Active Development
