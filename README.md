# Aarogya Saarthi 🏥

**AI-Driven, Blockchain-Protected Hospital Management System**

[![License](https://img.shields.io/badge/license-ISC-blue.svg)](LICENSE)
[![Node.js](https://img.shields.io/badge/Node.js-v18+-green.svg)](https://nodejs.org/)
[![React](https://img.shields.io/badge/React-18+-blue.svg)](https://reactjs.org/)
[![MongoDB](https://img.shields.io/badge/MongoDB-Atlas-green.svg)](https://www.mongodb.com/)

## Overview

Aarogya Saarthi is an advanced hospital management system that combines **Artificial Intelligence**, **Blockchain Technology**, and **Modern Web Development** to revolutionize healthcare operations. The system provides comprehensive solutions for patient management, resource optimization, staff administration, and predictive analytics.

### Key Highlights

- 🤖 **7 AI/ML Models** for intelligent predictions (beds, ventilators, PPE, blood bank, equipment)
- 🔐 **Blockchain Integration** for data integrity and security
- 📊 **Real-time Dashboard** for hospital operations
- 💰 **Automated Payroll** with Indian tax compliance
- 🏥 **Complete Patient Lifecycle** management
- 📈 **Predictive Analytics** for resource planning

## Features

### Patient Management
- Add, view, and track current patients
- Maintain historical patient records
- Medical condition tracking
- Insurance and billing information
- AI-based patient priority assignment

### Resource Management
- Real-time inventory tracking
- AI-powered demand forecasting
- Automated resource allocation
- Critical equipment monitoring

### Staff Administration
- Employee database management
- Automated monthly payroll processing
- Indian tax slab calculations
- Performance tracking

### Predictive Analytics (7 ML Models)
1. **Bed Requirement Prediction** - Forecast bed needs for next 3 months
2. **Ventilator Prediction** - Critical care equipment planning
3. **PPE Kit Demand** - Infection control resource planning
4. **Blood Bank Management** - Blood type demand forecasting
5. **Diagnostic Equipment** - 20+ equipment type predictions
6. **Medical Equipment** - Surgical instrument forecasting
7. **Patient Priority** - AI-based triage system

### Security & Compliance
- JWT token-based authentication
- Blockchain-backed data integrity
- Secure API endpoints
- Encrypted data storage

## Technology Stack

### Frontend
- React.js with Vite
- React Router
- Axios for API calls

### Backend
- Node.js & Express.js
- MongoDB (Native driver + Mongoose)
- JWT Authentication
- Cron Jobs for automation

### Machine Learning
- Python with scikit-learn
- TensorFlow
- pandas, NumPy
- Multiple trained models (.pkl files)

### Blockchain
- Solidity ^0.8.0
- Ethers.js
- Ethereum smart contracts

## Documentation

📖 **[Complete Project Description](./PROJECT_DESCRIPTION.md)** - Comprehensive overview of features, technology stack, and capabilities

🏗️ **[System Architecture](./ARCHITECTURE.md)** - Detailed architecture diagrams, data flow, and technical design

👨‍💻 **[Developer Guide](./DEVELOPER_GUIDE.md)** - Quick start guide, setup instructions, and development workflow

## Quick Start

### Prerequisites
- Node.js v18+
- Python 3.8+
- MongoDB Atlas account
- npm or yarn

### Installation

1. **Clone the repository**
```bash
git clone https://github.com/algonomad571/Aarogya-Saarthi.git
cd Aarogya-Saarthi
```

2. **Install dependencies**
```bash
# Install root dependencies
npm install

# Install backend dependencies
cd Backend
npm install

# Install frontend dependencies
cd ../Frontend
npm install
```

3. **Configure environment variables**

Create `.env` file in the Backend directory:
```env
MONGODB_URI=your_mongodb_connection_string
PORT=3000
JWT_SECRET=your_secret_key
```

4. **Run the application**

Backend:
```bash
cd Backend
npm start
```

Frontend:
```bash
cd Frontend
npm run dev
```

ML Models (each directory):
```bash
cd "ML models/[model_name]"
pip install -r requirements.txt
python app.py
```

## Project Structure

```
Aarogya-Saarthi/
├── Backend/              # Express.js server
├── Frontend/             # React application
├── Blockchain/           # Solidity smart contracts
├── ML models/            # 7 ML prediction models
│   ├── ai_testing/      # Patient priority
│   ├── bed_testing/     # Bed prediction
│   ├── blood_bank/      # Blood demand
│   ├── diagnostic_testing/
│   ├── medical_testing/
│   ├── ppe_testing/
│   └── ventilator_testing/
└── PROJECT_DESCRIPTION.md
```

## API Endpoints

### Authentication
- `POST /login` - User authentication

### Staff Management
- `POST /add_staff` - Add new staff member
- `GET /staff` - Get all staff members
- `POST /process_salaries` - Process monthly salaries

### Patient Management
- `POST /add_patient` - Register new patient
- `GET /patients` - Get current patients
- `GET /past_patients` - Get patient history

### Resources
- `POST /add_resources` - Update inventory
- `GET /all_resources` - Get available resources

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

This project is licensed under the ISC License.

## Authors

Originally developed as **JHU_TechLions**

## Acknowledgments

- MongoDB Atlas for database hosting
- Render.com for deployment
- scikit-learn for ML frameworks
- Ethereum for blockchain infrastructure

---

**Note**: This is an active development project. Features and documentation are continuously being updated.

For detailed information, please refer to [PROJECT_DESCRIPTION.md](./PROJECT_DESCRIPTION.md).
