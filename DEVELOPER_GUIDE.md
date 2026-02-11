# Developer Quick Start Guide

This guide will help you set up the Aarogya Saarthi development environment quickly.

## Prerequisites Checklist

Before you begin, ensure you have:

- [ ] Node.js v18 or higher ([Download](https://nodejs.org/))
- [ ] Python 3.8 or higher ([Download](https://www.python.org/))
- [ ] MongoDB Atlas account ([Sign up](https://www.mongodb.com/cloud/atlas))
- [ ] Git installed ([Download](https://git-scm.com/))
- [ ] Code editor (VS Code recommended)
- [ ] npm or yarn package manager

## Quick Setup (5 Minutes)

### 1. Clone the Repository

```bash
git clone https://github.com/algonomad571/Aarogya-Saarthi.git
cd Aarogya-Saarthi
```

### 2. Install Dependencies

**Root directory:**
```bash
npm install
```

**Backend:**
```bash
cd Backend
npm install
cd ..
```

**Frontend:**
```bash
cd Frontend
npm install
cd ..
```

**ML Models (Optional - for development):**
```bash
# Example for one model
cd "ML models/bed_testing"
pip install -r requirements.txt
cd ../..
```

### 3. Configure Environment Variables

Create a `.env` file in the `Backend` directory:

```bash
cd Backend
touch .env
```

Add the following to `Backend/.env`:

```env
# MongoDB Connection
MONGODB_URI=mongodb+srv://username:password@cluster.mongodb.net/AarogyaSaarthi?retryWrites=true&w=majority

# Server Configuration
PORT=3000
NODE_ENV=development

# JWT Secret (Change this to a secure random string in production)
JWT_SECRET=your-secret-key-here

# Optional: Additional configurations
CORS_ORIGIN=http://localhost:5173
```

**Important**: Replace `username`, `password`, and `cluster` with your actual MongoDB Atlas credentials.

### 4. Set Up MongoDB Database

1. Go to [MongoDB Atlas](https://cloud.mongodb.com/)
2. Create a new cluster (free tier is sufficient for development)
3. Create a database user with read/write permissions
4. Whitelist your IP address (or use 0.0.0.0/0 for development)
5. Get your connection string and update the `.env` file

**Database Name**: `AarogyaSaarthi`

**Required Collections** (will be created automatically):
- Login Info
- Staff
- Patient
- PastPatient
- Resources
- BloodBank

### 5. Seed Initial Data (Optional)

Create an initial admin user in MongoDB:

1. Connect to your MongoDB Atlas cluster
2. Select database: `AarogyaSaarthi`
3. Create collection: `Login Info`
4. Insert document:

```json
{
  "user": "admin",
  "password": "admin123",
  "is_active": true
}
```

**Note**: In production, passwords should be hashed!

## Running the Application

### Development Mode

Open **three separate terminals**:

**Terminal 1 - Backend Server:**
```bash
cd Backend
npm start
# Server runs on http://localhost:3000
```

**Terminal 2 - Frontend:**
```bash
cd Frontend
npm run dev
# Frontend runs on http://localhost:5173
```

**Terminal 3 - ML Service (Optional):**
```bash
cd "ML models/bed_testing"
python app.py
# ML service runs on specified port
```

### Access the Application

- **Frontend**: http://localhost:5173
- **Backend API**: http://localhost:3000
- **ML Services**: Various ports (check each app.py)

## Project Structure Overview

```
Aarogya-Saarthi/
├── Backend/
│   ├── server.js         # Main Express server
│   ├── payment.js        # Payment processing logic
│   ├── package.json      # Backend dependencies
│   └── .env             # Environment variables (create this)
│
├── Frontend/
│   ├── src/
│   │   ├── App.jsx      # Main app component
│   │   ├── Pages/       # All page components
│   │   └── main.jsx     # Entry point
│   ├── index.html       # HTML template
│   ├── vite.config.js   # Vite configuration
│   └── package.json     # Frontend dependencies
│
├── ML models/
│   ├── ai_testing/      # Patient priority system
│   ├── bed_testing/     # Bed prediction
│   ├── blood_bank/      # Blood demand prediction
│   ├── diagnostic_testing/  # Equipment prediction
│   ├── medical_testing/     # Surgical tools
│   ├── ppe_testing/     # PPE kit demand
│   └── ventilator_testing/ # Ventilator needs
│
├── Blockchain/
│   ├── secure.sol       # Solidity smart contract
│   └── mongo.js         # Blockchain-MongoDB integration
│
├── README.md            # Main documentation
├── PROJECT_DESCRIPTION.md  # Detailed description
└── ARCHITECTURE.md      # System architecture
```

## Development Workflow

### Making Changes

1. **Frontend Changes**:
   - Edit files in `Frontend/src/`
   - Hot reload will update automatically
   - Check browser console for errors

2. **Backend Changes**:
   - Edit `Backend/server.js` or related files
   - Restart the backend server (Ctrl+C, then `npm start`)
   - Use nodemon for auto-restart: `npm install -g nodemon`, then `nodemon server.js`

3. **Database Changes**:
   - Access MongoDB Atlas dashboard
   - Or use MongoDB Compass for GUI
   - Test queries before implementing

### Testing Your Changes

**API Testing with curl:**
```bash
# Test login
curl -X POST http://localhost:3000/login \
  -H "Content-Type: application/json" \
  -d '{"user":"admin","password":"admin123"}'

# Test protected route (replace TOKEN with actual JWT)
curl -X GET http://localhost:3000/patients \
  -H "Authorization: Bearer TOKEN"
```

**Using Postman/Insomnia:**
1. Import API endpoints
2. Test each route
3. Save example requests

## Common Issues & Solutions

### Issue 1: MongoDB Connection Error
**Error**: `MongoServerError: bad auth`

**Solution**:
- Check username/password in `.env`
- Verify database user exists in Atlas
- Check IP whitelist in Atlas

### Issue 2: Port Already in Use
**Error**: `Error: listen EADDRINUSE: address already in use :::3000`

**Solution**:
```bash
# Find process using port 3000
lsof -i :3000  # macOS/Linux
netstat -ano | findstr :3000  # Windows

# Kill the process or change port in .env
```

### Issue 3: Module Not Found
**Error**: `Error: Cannot find module 'express'`

**Solution**:
```bash
cd Backend  # or Frontend
rm -rf node_modules
rm package-lock.json
npm install
```

### Issue 4: CORS Error in Browser
**Error**: `Access to fetch at 'http://localhost:3000' from origin 'http://localhost:5173' has been blocked by CORS`

**Solution**:
- CORS is already configured in `server.js`
- Ensure backend is running
- Check if `cors` package is installed

### Issue 5: JWT Token Invalid
**Error**: `Invalid or expired token`

**Solution**:
- Get a fresh token by logging in again
- Check if JWT_SECRET matches in `.env`
- Token expires after 7 days

## Development Tools

### Recommended VS Code Extensions

```json
{
  "recommendations": [
    "esbenp.prettier-vscode",
    "dbaeumer.vscode-eslint",
    "mongodb.mongodb-vscode",
    "ms-python.python",
    "juanblanco.solidity"
  ]
}
```

### Useful Commands

**Backend:**
```bash
# Install nodemon for auto-restart
npm install -g nodemon

# Run with nodemon
cd Backend
nodemon server.js

# Check for outdated packages
npm outdated
```

**Frontend:**
```bash
# Build for production
npm run build

# Preview production build
npm run preview

# Lint code
npm run lint
```

**ML Models:**
```bash
# Install Python packages globally
pip install pandas numpy scikit-learn tensorflow

# Or use virtual environment
python -m venv venv
source venv/bin/activate  # macOS/Linux
venv\Scripts\activate     # Windows
pip install -r requirements.txt
```

## Environment Variables Reference

### Backend `.env` Template

```env
# Required
MONGODB_URI=mongodb+srv://user:pass@cluster.mongodb.net/AarogyaSaarthi
PORT=3000
JWT_SECRET=your-secret-key

# Optional
NODE_ENV=development
CORS_ORIGIN=http://localhost:5173
LOG_LEVEL=debug
```

### Blockchain `.env` Template

```env
ETHEREUM_NETWORK=sepolia
INFURA_API_KEY=your-infura-key
PRIVATE_KEY=your-wallet-private-key
CONTRACT_ADDRESS=deployed-contract-address
```

## Git Workflow

### Basic Workflow

```bash
# Create feature branch
git checkout -b feature/your-feature-name

# Make changes and commit
git add .
git commit -m "feat: add your feature description"

# Push to remote
git push origin feature/your-feature-name

# Create pull request on GitHub
```

### Commit Message Convention

Use conventional commits:
- `feat:` New feature
- `fix:` Bug fix
- `docs:` Documentation changes
- `style:` Code style changes
- `refactor:` Code refactoring
- `test:` Adding tests
- `chore:` Maintenance tasks

## Next Steps

After setup, explore these features:

1. **Login System**: Test with admin credentials
2. **Add Patient**: Use the dashboard to add a patient
3. **View Resources**: Check resource management
4. **ML Predictions**: Try bed prediction module
5. **Staff Management**: Add staff members
6. **Payroll**: Test salary processing

## Learning Resources

### Documentation
- [React Docs](https://react.dev/)
- [Express.js Guide](https://expressjs.com/en/guide/routing.html)
- [MongoDB Manual](https://docs.mongodb.com/)
- [Scikit-learn Tutorials](https://scikit-learn.org/stable/tutorial/index.html)
- [Solidity Docs](https://docs.soliditylang.org/)

### Project-Specific
- [README.md](./README.md) - Main documentation
- [PROJECT_DESCRIPTION.md](./PROJECT_DESCRIPTION.md) - Detailed description
- [ARCHITECTURE.md](./ARCHITECTURE.md) - System architecture

## Getting Help

- Check existing documentation
- Review code comments
- Search GitHub issues
- Contact the development team

## Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Write/update tests
5. Submit a pull request

---

**Happy coding!** 🚀

For detailed information, refer to [PROJECT_DESCRIPTION.md](./PROJECT_DESCRIPTION.md)
