# 🚀 Blockchain-Powered Healthcare Records (EHR System)

A complete, production-ready electronic health record (EHR) system built with blockchain principles for secure data ownership, access control, and auditability.

## 🌟 Features

### 🔐 Security & Privacy
- **Blockchain-based audit trail** - Immutable record of all data access and modifications
- **AES-256 encryption** - All medical records are encrypted before storage
- **Role-based access control** - Patients control who can access their data
- **JWT authentication** - Secure session management
- **Comprehensive audit logging** - Every action is tracked and logged

### 👥 Multi-Role System
- **👤 Patients** - Upload records, manage consent, view audit trails
- **👨‍⚕️ Doctors** - Request access, view patient records, add notes
- **🏥 Hospitals** - Manage doctors, store patient records
- **🛡️ Admins** - Approve users, monitor system, view analytics

### 🔗 Blockchain Features
- **Consent management** - All consent grants/revokes recorded on blockchain
- **Data integrity** - File hashes stored on blockchain for verification
- **Access tracking** - Every data access logged immutably
- **Proof of work** - Simple mining simulation for block creation

## 🏗️ Architecture

### Backend (Node.js + Express)
- **RESTful API** with comprehensive endpoints
- **MongoDB** for primary data storage
- **Custom blockchain** simulation for audit trails
- **Encryption utilities** for data protection
- **Role-based middleware** for access control

### Frontend (React + Vite)
- **Modern React** with hooks and context
- **Tailwind CSS** for responsive design
- **Role-based routing** and components
- **Real-time notifications** with react-hot-toast
- **Form handling** with react-hook-form

### Database (MongoDB)
- **User management** with role-based permissions
- **Encrypted record storage** with metadata
- **Consent tracking** with expiration dates
- **Comprehensive audit logs** with blockchain hashes

## 🚀 Quick Start

### Prerequisites
- Node.js 18+ 
- MongoDB 7.0+
- Docker & Docker Compose (optional)

### Option 1: Docker Setup (Recommended)

1. **Clone the repository**
```bash
git clone <repository-url>
cd blockchain-ehr
```

2. **Start with Docker Compose**
```bash
docker-compose up -d
```

3. **Access the application**
- Frontend: http://localhost:3000
- Backend API: https://electronic-health-record-6s09.onrender.com
- MongoDB: localhost:27017

### Option 2: Manual Setup

1. **Backend Setup**
```bash
cd backend
npm install
cp .env.example .env
# Edit .env with your configuration
npm run seed  # Load sample data
npm start
```

2. **Frontend Setup**
```bash
cd frontend
npm install
npm run dev
```

3. **MongoDB Setup**
```bash
# Install and start MongoDB
mongod --dbpath /path/to/data
```

## 🔑 Demo Credentials

The system comes with pre-seeded demo accounts:

| Role | Email | Password | Status |
|------|-------|----------|---------|
| **Admin** | admin@ehrsystem.com | admin123 | Active |
| **Patient** | john.doe@email.com | patient123 | Active |
| **Doctor** | dr.wilson@hospital.com | doctor123 | Approved |
| **Hospital** | admin@generalhospital.com | hospital123 | Approved |

## 📁 Project Structure

```
blockchain-ehr/
├── backend/                 # Node.js backend
│   ├── blockchain.js       # Blockchain simulation
│   ├── server.js          # Express server
│   ├── config/            # Database & configuration
│   ├── models/            # MongoDB schemas
│   ├── controllers/       # Business logic
│   ├── routes/            # API endpoints
│   ├── middleware/        # Authentication & validation
│   └── utils/             # Encryption utilities
├── frontend/               # React frontend
│   ├── src/
│   │   ├── components/    # Reusable components
│   │   ├── pages/         # Role-based pages
│   │   ├── context/       # React context
│   │   └── App.jsx        # Main application
│   ├── index.html         # HTML template
│   └── vite.config.js     # Vite configuration
├── docker-compose.yml      # Docker orchestration
├── nginx.conf             # Reverse proxy config
└── README.md              # This file
```

## 🔄 API Endpoints

### Authentication
- `POST /api/auth/register` - Register new user
- `POST /api/auth/login` - User login
- `GET /api/auth/profile` - Get user profile
- `PUT /api/auth/profile` - Update profile

### Patient Endpoints
- `POST /api/patient/upload` - Upload medical record
- `GET /api/patient/records` - Get patient records
- `POST /api/patient/grant-consent` - Grant doctor access
- `POST /api/patient/revoke-consent` - Revoke doctor access
- `GET /api/patient/audit` - Get audit trail

### Doctor Endpoints
- `POST /api/doctor/request-access` - Request patient access
- `GET /api/doctor/records/:patientId` - View patient records
- `GET /api/doctor/record/:recordId/content` - Get decrypted content
- `POST /api/doctor/records/:patientId/update` - Add record notes

### Hospital Endpoints
- `POST /api/hospital/add-doctor` - Add doctor to hospital
- `GET /api/hospital/doctors` - Get hospital doctors
- `POST /api/hospital/store-record` - Store patient record
- `GET /api/hospital/search-patients` - Search patients

### Admin Endpoints
- `GET /api/admin/pending-users` - Get pending approvals
- `POST /api/admin/approve-user/:userId` - Approve user
- `GET /api/admin/audit` - System audit logs
- `GET /api/admin/stats` - System statistics

## 🔐 Security Features

### Data Encryption
- **AES-256-GCM** encryption for all medical records
- **bcrypt** password hashing with salt rounds
- **JWT tokens** with expiration for session management
- **SHA-256 hashing** for blockchain integrity

### Access Control
- **Role-based permissions** with middleware validation
- **Consent-based access** for doctor-patient relationships
- **Time-limited permissions** with automatic expiration
- **IP address logging** for all access attempts

### Blockchain Security
- **Immutable audit trail** for critical operations
- **Hash verification** for data integrity
- **Proof of work** mining simulation
- **Chain validation** to detect tampering

## 📊 Monitoring & Analytics

### Audit Logging
- **Database logs** for detailed activity tracking
- **Blockchain records** for immutable critical events
- **Security alerts** for suspicious activities
- **Access patterns** for compliance reporting

### System Monitoring
- **Health checks** for all services
- **Performance metrics** tracking
- **User activity** statistics
- **Blockchain status** monitoring

## 🔧 Configuration

### Environment Variables

**Backend (.env)**
```env
PORT=5000
MONGODB_URI=mongodb://localhost:27017/blockchain-ehr
JWT_SECRET=your-super-secret-jwt-key
ENCRYPTION_KEY=32-character-secret-key-for-aes-256
NODE_ENV=development
```

**Frontend**
```env
VITE_API_URL=https://electronic-health-record-6s09.onrender.com
```

### Database Configuration
- **Connection pooling** for optimal performance
- **Indexes** on frequently queried fields
- **TTL indexes** for session cleanup
- **Replica set** support for production

## 🚀 Deployment

### Production Deployment

1. **Environment Setup**
```bash
# Update environment variables
cp .env.example .env.production
# Configure production values
```

2. **Build & Deploy**
```bash
# Build frontend
cd frontend && npm run build

# Start production services
docker-compose -f docker-compose.prod.yml up -d
```

3. **SSL Configuration**
```bash
# Add SSL certificates to ./ssl/
# Update nginx.conf for HTTPS
```

### Scaling Considerations
- **Load balancing** with multiple backend instances
- **Database sharding** for large datasets
- **CDN integration** for static assets
- **Monitoring** with Prometheus/Grafana

## 🧪 Testing

### Running Tests
```bash
# Backend tests
cd backend && npm test

# Frontend tests
cd frontend && npm test

# Integration tests
npm run test:integration
```

### Test Coverage
- **Unit tests** for all business logic
- **Integration tests** for API endpoints
- **E2E tests** for critical user flows
- **Security tests** for vulnerability assessment

## 🤝 Contributing

1. **Fork the repository**
2. **Create feature branch** (`git checkout -b feature/amazing-feature`)
3. **Commit changes** (`git commit -m 'Add amazing feature'`)
4. **Push to branch** (`git push origin feature/amazing-feature`)
5. **Open Pull Request**

### Development Guidelines
- **Code style** - ESLint + Prettier configuration
- **Commit messages** - Conventional commits format
- **Testing** - All new features must include tests
- **Documentation** - Update README for new features

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🆘 Support

### Common Issues

**Connection Issues**
```bash
# Check if services are running
docker-compose ps

# View logs
docker-compose logs backend
docker-compose logs frontend
```

**Database Issues**
```bash
# Reset database
docker-compose down -v
docker-compose up -d

# Reseed data
docker-compose exec backend npm run seed
```

### Getting Help
- **Documentation** - Check this README and inline code comments
- **Issues** - Create GitHub issue for bugs or feature requests
- **Discussions** - Use GitHub discussions for questions

## 🎯 Roadmap

### Phase 1 (Current)
- ✅ Basic EHR functionality
- ✅ Blockchain audit trail
- ✅ Role-based access control
- ✅ Docker deployment

### Phase 2 (Planned)
- 🔄 Advanced analytics dashboard
- 🔄 Mobile application
- 🔄 FHIR compliance
- 🔄 Integration APIs

### Phase 3 (Future)
- 📋 AI-powered insights
- 📋 Telemedicine integration
- 📋 IoT device connectivity
- 📋 Multi-tenant architecture

---

**Built with ❤️ for secure healthcare data management**

For more information, visit our [documentation](docs/) or contact the development team.
