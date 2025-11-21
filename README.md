# TIMS - Ticketing and Issue Management System

A modern, enterprise-grade full-stack application for ticketing and issue management, designed for multinational corporations with support for multiple roles, departments, and workflows.

## 🚀 Features

### Authentication & Authorization
- Standard login and SSO integration
- Role-based access control (User, Agent, Manager, Admin)
- Secure JWT token-based authentication
- Automatic token refresh

### Ticket Management
- Create, view, update, and delete tickets
- Advanced filtering and search capabilities
- Real-time status tracking
- Comment system with file attachments
- Priority and category management
- Ticket assignment workflow
- Activity timeline

### Dashboard & Analytics
- Comprehensive KPI metrics
- Real-time statistics and reporting
- Interactive charts and visualizations
- Performance tracking (MTTR, SLA compliance)
- Agent performance reports
- Department-wise analytics

### User Management
- User CRUD operations (Admin only)
- Role and permission management
- Department assignment
- Profile management with avatar support

### Additional Features
- Multi-language support (i18n)
- Knowledge base for self-service
- Responsive design (mobile, tablet, desktop)
- Email notifications
- File upload support
- Dark/Light theme support

## 🛠️ Technology Stack

### Frontend
- **React 18.2** - UI library
- **Vite** - Build tool and dev server
- **React Router v6** - Client-side routing
- **Zustand** - State management
- **React Query** - Server state management
- **Axios** - HTTP client
- **React Hook Form** - Form management
- **Tailwind CSS** - Utility-first CSS framework
- **Headless UI** - Accessible UI components
- **Chart.js** - Data visualization
- **i18next** - Internationalization

### Backend
- **Node.js** - Runtime environment
- **Express.js** - Web framework
- **MongoDB** - Database
- **Mongoose** - ODM
- **JWT** - Authentication
- **Bcrypt** - Password hashing
- **Multer** - File uploads
- **Nodemailer** - Email service

## 📋 Prerequisites

Before you begin, ensure you have the following installed:

- **Node.js** (v16.x or higher) - [Download here](https://nodejs.org/)
- **MongoDB** (v6.x or higher) - [Download here](https://www.mongodb.com/try/download/community)
- **npm** or **yarn** package manager
- **Git** - [Download here](https://git-scm.com/)

To verify installations:
```bash
node --version
npm --version
mongod --version
git --version
```

## 🚀 Installation & Setup

### Step 1: Clone the Repository

```bash
git clone https://github.com/sanjayy-gowdaa/tims.git
cd tims
```

### Step 2: Backend Setup

1. Navigate to the backend directory:
```bash
cd backend
```

2. Install backend dependencies:
```bash
npm install
```

3. Create environment file:
```bash
# Windows (PowerShell)
Copy-Item .env.example .env

# Linux/Mac
cp .env.example .env
```

4. Configure backend environment variables in `backend/.env`:
```env
# Server Configuration
NODE_ENV=development
PORT=5000

# Database
MONGODB_URI=mongodb://localhost:27017/tims

# JWT Secrets (Change these in production!)
JWT_SECRET=your-super-secret-jwt-key-change-this-in-production
JWT_EXPIRE=7d
JWT_REFRESH_SECRET=your-refresh-token-secret-key
JWT_REFRESH_EXPIRE=30d

# CORS
CORS_ORIGIN=http://localhost:5173

# Email Configuration (Optional)
EMAIL_HOST=smtp.gmail.com
EMAIL_PORT=587
EMAIL_USER=your-email@gmail.com
EMAIL_PASSWORD=your-app-password
EMAIL_FROM=TIMS <noreply@tims.com>

# File Upload
MAX_FILE_SIZE=10485760
UPLOAD_PATH=./uploads

# SSO (Optional)
SSO_ENABLED=false
SSO_PROVIDER_URL=https://sso.company.com
SSO_CLIENT_ID=your-client-id
SSO_CLIENT_SECRET=your-client-secret
```

5. Start MongoDB service:
```bash
# Windows (Run as Administrator)
net start MongoDB

# Linux
sudo systemctl start mongod

# Mac
brew services start mongodb-community
```

6. Seed the database with sample data (Optional):
```bash
npm run seed
```

This will create:
- Sample users with different roles (admin, manager, agent, user)
- Sample tickets with various statuses
- Department data

Default credentials after seeding:
- Admin: `admin@tims.com` / `Admin@123`
- Manager: `manager@tims.com` / `Manager@123`
- Agent: `agent@tims.com` / `Agent@123`
- User: `user@tims.com` / `User@123`

7. Start the backend server:
```bash
# Development mode with auto-reload
npm run dev

# Production mode
npm start
```

Backend will run on `http://localhost:5000`

### Step 3: Frontend Setup

1. Open a new terminal and navigate to the project root:
```bash
cd ..
# You should now be in the tims directory
```

2. Install frontend dependencies:
```bash
npm install
```

3. Create environment file:
```bash
# Windows (PowerShell)
Copy-Item .env.example .env

# Linux/Mac
cp .env.example .env
```

4. Configure frontend environment variables in `.env`:
```env
VITE_API_BASE_URL=http://localhost:5000/api
VITE_SSO_ENABLED=false
VITE_SSO_PROVIDER_URL=https://sso.company.com
VITE_APP_NAME=TIMS
VITE_DEFAULT_LANGUAGE=en
VITE_ENABLE_ANALYTICS=true
```

5. Start the frontend development server:
```bash
npm run dev
```

Frontend will run on `http://localhost:5173`

### Step 4: Access the Application

1. Open your browser and navigate to: `http://localhost:5173`
2. Log in with one of the seeded user credentials or create a new account
3. Start managing tickets!

## 🏗️ Build for Production

### Frontend Build

```bash
# In the root directory
npm run build
```

Production files will be in the `dist` directory.

Preview the production build:
```bash
npm run preview
```

### Backend Production

Set `NODE_ENV=production` in `backend/.env` and ensure all production secrets are configured.

```bash
cd backend
npm start
```

## 📁 Project Structure

```
tims/
├── backend/                 # Backend API
│   ├── controllers/        # Request handlers
│   ├── models/             # Mongoose models
│   ├── routes/             # API routes
│   ├── middleware/         # Custom middleware
│   ├── scripts/            # Utility scripts (seeding, etc.)
│   ├── uploads/            # File upload directory
│   ├── server.js           # Entry point
│   └── package.json
│
├── src/                    # Frontend source
│   ├── components/         # Reusable components
│   │   ├── Common/         # Common UI components
│   │   ├── Layout/         # Layout components
│   │   ├── Tickets/        # Ticket components
│   │   ├── Dashboard/      # Dashboard components
│   │   └── Admin/          # Admin components
│   ├── pages/              # Page components
│   │   ├── Auth/           # Authentication pages
│   │   ├── Dashboard/      # Dashboard
│   │   ├── Tickets/        # Ticket pages
│   │   ├── User/           # User profile
│   │   ├── Admin/          # Admin panel
│   │   ├── Analytics/      # Analytics
│   │   ├── Settings/       # Settings
│   │   └── KnowledgeBase/  # Knowledge base
│   ├── services/           # API services
│   ├── store/              # State management
│   ├── utils/              # Utilities
│   ├── App.jsx             # Main component
│   ├── main.jsx            # Entry point
│   └── i18n.js             # i18n config
│
├── index.html
├── package.json
├── vite.config.js
├── tailwind.config.js
└── README.md
```

## 🔧 Configuration

### MongoDB Connection

If MongoDB is running on a different host or port, update the `MONGODB_URI` in `backend/.env`:

```env
# Local MongoDB
MONGODB_URI=mongodb://localhost:27017/tims

# MongoDB Atlas (Cloud)
MONGODB_URI=mongodb+srv://username:password@cluster.mongodb.net/tims?retryWrites=true&w=majority

# MongoDB with authentication
MONGODB_URI=mongodb://username:password@localhost:27017/tims
```

### Email Configuration

For email notifications, configure SMTP settings in `backend/.env`:

```env
EMAIL_HOST=smtp.gmail.com
EMAIL_PORT=587
EMAIL_USER=your-email@gmail.com
EMAIL_PASSWORD=your-app-password  # Use App Password for Gmail
EMAIL_FROM=TIMS <noreply@tims.com>
```

**Note for Gmail users:** Generate an App Password from Google Account settings.

### File Upload Limits

Adjust file upload size in `backend/.env`:

```env
MAX_FILE_SIZE=10485760  # 10MB in bytes
UPLOAD_PATH=./uploads
```

## 🧪 Development

### Running in Development Mode

Terminal 1 - Backend:
```bash
cd backend
npm run dev
```

Terminal 2 - Frontend:
```bash
npm run dev
```

### Code Linting

```bash
npm run lint
```

## 🌐 API Documentation

The backend API runs on `http://localhost:5000/api` with the following main endpoints:

- **Auth**: `/api/auth` - Authentication & registration
- **Tickets**: `/api/tickets` - Ticket management
- **Users**: `/api/users` - User management (Admin)
- **Analytics**: `/api/analytics` - Analytics & reports

See `backend/routes/` for detailed endpoint documentation.

## 🔐 Security

- Passwords are hashed using bcrypt
- JWT tokens for authentication
- HTTP-only cookies for token storage
- CORS protection
- Rate limiting on API endpoints
- Input validation and sanitization
- Helmet.js for security headers
- File upload validation

## 🐛 Troubleshooting

### MongoDB Connection Error
```
Error: connect ECONNREFUSED 127.0.0.1:27017
```
**Solution**: Ensure MongoDB service is running:
```bash
# Windows
net start MongoDB

# Linux
sudo systemctl start mongod

# Mac
brew services start mongodb-community
```

### Port Already in Use
```
Error: listen EADDRINUSE: address already in use :::5000
```
**Solution**: Change the PORT in `backend/.env` or kill the process using the port:
```bash
# Windows
netstat -ano | findstr :5000
taskkill /PID <PID> /F

# Linux/Mac
lsof -ti:5000 | xargs kill -9
```

### Frontend Can't Connect to Backend
- Verify backend is running on `http://localhost:5000`
- Check `VITE_API_BASE_URL` in frontend `.env`
- Check `CORS_ORIGIN` in backend `.env` matches frontend URL

### Build Errors
```bash
# Clear node_modules and reinstall
rm -rf node_modules package-lock.json
npm install
```

## 📚 Available Scripts

### Frontend (root directory)
- `npm run dev` - Start development server
- `npm run build` - Build for production
- `npm run preview` - Preview production build
- `npm run lint` - Run ESLint

### Backend (backend directory)
- `npm run dev` - Start development server with nodemon
- `npm start` - Start production server
- `npm run seed` - Seed database with sample data

## 🎯 Usage Guide

### User Roles & Permissions

1. **Admin**
   - Full system access
   - User management
   - System configuration
   - All ticket operations
   - Analytics and reports

2. **Manager**
   - Department ticket management
   - Agent assignment
   - Performance reports
   - Ticket oversight

3. **Agent**
   - Assigned ticket management
   - Ticket resolution
   - Customer communication
   - Status updates

4. **User**
   - Create tickets
   - View own tickets
   - Update ticket details
   - Add comments

### Creating Your First Ticket

1. Log in to the application
2. Navigate to "Tickets" → "Create Ticket"
3. Fill in the ticket details:
   - Title and description
   - Category and priority
   - Department (if applicable)
   - Attach files (optional)
4. Submit the ticket
5. Track ticket status in Dashboard

### Managing Users (Admin Only)

1. Navigate to "Admin" → "User Management"
2. Click "Add User"
3. Fill in user details and assign role
4. User will receive login credentials via email

## 🌍 Deployment

### Deploying to Production

#### Frontend Deployment (Vercel/Netlify)

1. Build the application:
```bash
npm run build
```

2. Deploy the `dist` folder to your hosting service

**Vercel:**
```bash
npm i -g vercel
vercel --prod
```

**Netlify:**
```bash
npm i -g netlify-cli
netlify deploy --prod --dir=dist
```

#### Backend Deployment (Heroku/Railway/VPS)

1. Set environment variables in your hosting platform
2. Ensure MongoDB is accessible (use MongoDB Atlas for cloud)
3. Deploy using your platform's CLI or Git integration

**Environment Variables for Production:**
```env
NODE_ENV=production
PORT=5000
MONGODB_URI=mongodb+srv://user:pass@cluster.mongodb.net/tims
JWT_SECRET=your-production-secret-key
CORS_ORIGIN=https://your-frontend-domain.com
```

### Docker Deployment (Optional)

Create `Dockerfile` for containerized deployment:

```dockerfile
# Backend Dockerfile
FROM node:18-alpine
WORKDIR /app
COPY backend/package*.json ./
RUN npm install --production
COPY backend/ ./
EXPOSE 5000
CMD ["node", "server.js"]
```

## 🔄 Development Workflow

### Git Workflow

1. Create feature branch:
```bash
git checkout -b feature/your-feature-name
```

2. Make changes and commit:
```bash
git add .
git commit -m "feat: add new feature"
```

3. Push to remote:
```bash
git push origin feature/your-feature-name
```

4. Create pull request on GitHub

### Commit Message Convention

- `feat:` - New feature
- `fix:` - Bug fix
- `docs:` - Documentation changes
- `style:` - Code style changes (formatting)
- `refactor:` - Code refactoring
- `test:` - Adding tests
- `chore:` - Maintenance tasks

## 🧪 Testing

### Manual Testing Checklist

- [ ] User registration and login
- [ ] Ticket creation with attachments
- [ ] Ticket status updates
- [ ] Comment functionality
- [ ] User role permissions
- [ ] Dashboard analytics
- [ ] Search and filtering
- [ ] File upload/download
- [ ] Email notifications
- [ ] Mobile responsiveness

## 📊 Database Schema

### User Model
```javascript
{
  name: String,
  email: String (unique),
  password: String (hashed),
  role: ['user', 'agent', 'manager', 'admin'],
  department: String,
  avatar: String,
  isActive: Boolean,
  createdAt: Date,
  updatedAt: Date
}
```

### Ticket Model
```javascript
{
  title: String,
  description: String,
  category: String,
  priority: ['low', 'medium', 'high', 'critical'],
  status: ['open', 'in-progress', 'resolved', 'closed'],
  creator: ObjectId (User),
  assignedTo: ObjectId (User),
  department: String,
  attachments: [String],
  comments: [{
    user: ObjectId,
    text: String,
    createdAt: Date
  }],
  createdAt: Date,
  updatedAt: Date,
  resolvedAt: Date
}
```

## 🤝 Contributing

We welcome contributions! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'feat: Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

### Development Guidelines

- Follow existing code style and conventions
- Write meaningful commit messages
- Update documentation for new features
- Test your changes thoroughly
- Keep pull requests focused and small

## 📝 License

Copyright © 2025 - All rights reserved

## 📧 Support & Contact

- **Issues**: [GitHub Issues](https://github.com/sanjayy-gowdaa/tims/issues)
- **Discussions**: [GitHub Discussions](https://github.com/sanjayy-gowdaa/tims/discussions)
- **Email**: support@tims.com

## 🙏 Acknowledgments

- React team for the amazing framework
- MongoDB team for the robust database
- All open-source contributors

## 📌 Roadmap

- [ ] Real-time notifications using WebSockets
- [ ] Advanced reporting and exports (PDF, Excel)
- [ ] Integration with third-party tools (Slack, Teams)
- [ ] Mobile app (React Native)
- [ ] AI-powered ticket categorization
- [ ] Multi-tenant support
- [ ] Custom workflows and SLA management

---

**Built with ❤️ for efficient ticket management**
