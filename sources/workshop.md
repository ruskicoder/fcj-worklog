# InsightHR - Complete Codebase Summary for Workshop

**Last Updated**: December 9, 2025  
**AWS Account**: 477059411501 (New Account - Migration in Progress)  
**Region**: ap-southeast-1 (Singapore)

---

## Table of Contents

1. [Project Overview](#project-overview)
2. [Architecture](#architecture)
3. [Technology Stack](#technology-stack)
4. [AWS Resources](#aws-resources)
5. [Frontend Application](#frontend-application)
6. [Backend Services](#backend-services)
7. [Database Schema](#database-schema)
8. [Deployment](#deployment)
9. [Testing](#testing)
10. [Migration Status](#migration-status)

---

## Project Overview

**InsightHR** is a modern, serverless HR automation platform that provides:

- **Employee Management**: CRUD operations for employee records
- **Performance Tracking**: Quarterly performance scores and KPI management
- **Attendance System**: Check-in/check-out with history tracking
- **AI Chatbot**: Natural language queries powered by AWS Bedrock (Claude 3)
- **Dashboard Analytics**: Performance visualization with charts and tables
- **Role-Based Access Control**: Admin, Manager, and Employee roles
- **Authentication**: Email/password and Google OAuth via AWS Cognito

**Key Features**:
- ✅ Fully serverless architecture (no EC2 instances)
- ✅ Real-time data synchronization
- ✅ CSV/Excel bulk import capabilities
- ✅ Custom domain with SSL (insight-hr.io.vn)
- ✅ CloudWatch monitoring and synthetic canaries
- ✅ Responsive UI with Frutiger Aero theme

---

## Architecture

```
┌─────────────────────────────────────────────────────────────────┐
│                         User Browser                             │
└────────────────────────┬────────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────────┐
│                    CloudFront CDN                                │
│              (d2z6tht6rq32uy.cloudfront.net)                    │
│                  Custom Domain: insight-hr.io.vn                 │
└────────────────────────┬────────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────────┐
│                    S3 Static Website                             │
│                  (insighthr-web-app-sg)                          │
│              React SPA (Vite + TypeScript)                       │
└─────────────────────────────────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────────┐
│                    API Gateway (REST)                            │
│              (lqk4t6qzag.execute-api...)                         │
│                  Cognito Authorizer                              │
└────────────────────────┬────────────────────────────────────────┘
                         │
         ┌───────────────┼───────────────┐
         ▼               ▼               ▼
┌─────────────┐  ┌─────────────┐  ┌─────────────┐
│   Lambda     │  │   Lambda     │  │   Lambda     │
│   Auth       │  │  Employees   │  │  Chatbot     │
└──────┬───────┘  └──────┬───────┘  └──────┬───────┘
       │                 │                 │
       ▼                 ▼                 ▼
┌─────────────────────────────────────────────────────────────────┐
│                        DynamoDB                                  │
│  ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────┐          │
│  │  Users   │ │Employees │ │  Scores  │ │Attendance│          │
│  └──────────┘ └──────────┘ └──────────┘ └──────────┘          │
└─────────────────────────────────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────────┐
│                    AWS Bedrock                                   │
│              (Claude 3 Haiku Model)                              │
└─────────────────────────────────────────────────────────────────┘
```

---

## Technology Stack

### Frontend
- **Framework**: React 18 with TypeScript
- **Build Tool**: Vite 7.2
- **Styling**: Tailwind CSS 3.4 (Frutiger Aero theme)
- **State Management**: Zustand 5.0
- **Forms**: React Hook Form + Zod validation
- **HTTP Client**: Axios 1.13
- **Charts**: Recharts 3.4
- **Routing**: React Router v7
- **Icons**: Lucide React
- **OAuth**: @react-oauth/google

### Backend
- **Runtime**: Python 3.11
- **Framework**: AWS Lambda (serverless)
- **API**: AWS API Gateway (REST)
- **Database**: AWS DynamoDB (NoSQL)
- **Authentication**: AWS Cognito
- **AI**: AWS Bedrock (Claude 3 Haiku)
- **Storage**: AWS S3
- **CDN**: AWS CloudFront
- **DNS**: AWS Route53
- **Monitoring**: AWS CloudWatch

### Development Tools
- **Package Manager**: npm
- **Linting**: ESLint 9 + Prettier
- **Type Checking**: TypeScript 5.9
- **Deployment**: AWS CLI + PowerShell scripts

---

## AWS Resources

### Current Status (Migration in Progress)
- **Old Account**: 151507815244 (deprecated)
- **New Account**: 477059411501 (active)
- **Region**: ap-southeast-1 (Singapore)

### DynamoDB Tables (9 tables)

1. **insighthr-users-dev**
   - Primary Key: `userId` (String)
   - GSI: `email-index` on `email`
   - Records: 24 users
   - Purpose: User authentication and profiles

2. **insighthr-employees-dev**
   - Primary Key: `employeeId` (String)
   - GSI: `department-index` on `department`
   - Records: 50 employees
   - Purpose: Employee master data

3. **insighthr-performance-scores-dev**
   - Primary Key: `employeeId` (String)
   - Sort Key: `period` (String)
   - GSI: `department-period-index`
   - Records: 50 scores
   - Purpose: Quarterly performance scores

4. **insighthr-attendance-history-dev**
   - Primary Key: `employeeId` (String)
   - Sort Key: `date` (String)
   - GSI: `date-index`, `department-date-index`
   - Records: 50 records
   - Purpose: Check-in/check-out history

5. **insighthr-password-reset-requests-dev**
   - Primary Key: `requestId` (String)
   - GSI: `status-index`, `userId-index`
   - Records: 16 requests
   - Purpose: Password reset workflow

6. **insighthr-kpis-dev**
   - Primary Key: `kpiId` (String)
   - GSI: `category-index`
   - Records: 0 (empty)
   - Purpose: KPI definitions

7. **insighthr-formulas-dev**
   - Primary Key: `formulaId` (String)
   - GSI: `department-index`
   - Records: 0 (empty)
   - Purpose: Performance calculation formulas

8. **insighthr-data-tables-dev**
   - Primary Key: `tableId` (String)
   - Records: 0 (empty)
   - Purpose: Custom data tables

9. **insighthr-notification-rules-dev**
   - Primary Key: `ruleId` (String)
   - Records: 0 (empty)
   - Purpose: Notification automation rules

### Lambda Functions (8 functions)

1. **insighthr-auth-login-handler**
   - Runtime: Python 3.11
   - Memory: 256 MB
   - Timeout: 30s
   - Purpose: User login with Cognito

2. **insighthr-auth-register-handler**
   - Runtime: Python 3.11
   - Memory: 256 MB
   - Timeout: 30s
   - Purpose: User registration

3. **insighthr-auth-google-handler**
   - Runtime: Python 3.11
   - Memory: 256 MB
   - Timeout: 30s
   - Purpose: Google OAuth authentication

4. **insighthr-employees-handler**
   - Runtime: Python 3.11
   - Memory: 256 MB
   - Timeout: 30s
   - Purpose: Employee CRUD operations

5. **insighthr-employees-bulk-handler**
   - Runtime: Python 3.11
   - Memory: 256 MB
   - Timeout: 60s
   - Purpose: Bulk employee import from CSV

6. **insighthr-performance-scores-handler**
   - Runtime: Python 3.11
   - Memory: 256 MB
   - Timeout: 30s
   - Purpose: Performance score management

7. **insighthr-chatbot-handler**
   - Runtime: Python 3.11
   - Memory: 512 MB
   - Timeout: 60s
   - Purpose: AI chatbot with Bedrock integration

8. **insighthr-attendance-handler**
   - Runtime: Python 3.11
   - Memory: 256 MB
   - Timeout: 30s
   - Purpose: Attendance tracking

### S3 Buckets
- **insighthr-web-app-sg**: Static website hosting
- **insighthr-canary-artifacts**: CloudWatch Synthetics artifacts

### CloudFront Distribution
- **Distribution ID**: E3MHW5VALWTOCI
- **Domain**: d2z6tht6rq32uy.cloudfront.net
- **Custom Domain**: insight-hr.io.vn, www.insight-hr.io.vn
- **SSL Certificate**: ACM (us-east-1)

### Route53
- **Hosted Zone**: insight-hr.io.vn
- **Nameservers**: Configured with Matbao.net registrar

---

## Frontend Application

### Directory Structure
```
insighthr-web/
├── src/
│   ├── components/
│   │   ├── auth/           # Login, Register, ProtectedRoute
│   │   ├── admin/          # User/Employee/Score Management
│   │   ├── dashboard/      # Charts, Tables, Filters
│   │   ├── attendance/     # Check-in/out, History
│   │   ├── chatbot/        # AI Chat Interface
│   │   ├── profile/        # User Profile
│   │   ├── common/         # Reusable UI components
│   │   └── layout/         # Header, Sidebar, Footer
│   ├── pages/              # Page components
│   ├── services/           # API service layer
│   ├── store/              # Zustand state stores
│   ├── types/              # TypeScript type definitions
│   ├── utils/              # Utility functions
│   └── styles/             # Global styles and theme
├── public/                 # Static assets
├── dist/                   # Production build output
└── package.json            # Dependencies
```

### Key Components

#### Authentication (`src/components/auth/`)
- **LoginForm.tsx**: Email/password and Google OAuth login
- **RegisterForm.tsx**: New user registration
- **ProtectedRoute.tsx**: Route guard for authenticated users
- **ChangePasswordModal.tsx**: Password change dialog

#### Admin Panel (`src/components/admin/`)
- **UserManagement.tsx**: User CRUD with role assignment
- **EmployeeManagement.tsx**: Employee CRUD with filters
- **PerformanceScoreManagement.tsx**: Score management with bulk import
- **PasswordRequestsPanel.tsx**: Password reset request handling

#### Dashboard (`src/components/dashboard/`)
- **PerformanceDashboard.tsx**: Main analytics dashboard
- **BarChart.tsx**: Department performance comparison
- **LineChart.tsx**: Trend analysis over time
- **PieChart.tsx**: Score distribution
- **DataTable.tsx**: Sortable, filterable data grid
- **FilterPanel.tsx**: Date range and department filters
- **ExportButton.tsx**: CSV/Excel export

#### Chatbot (`src/components/chatbot/`)
- **MessageList.tsx**: Conversation history display
- **MessageInput.tsx**: User input with send button
- **TypingIndicator.tsx**: Loading animation
- **ChatbotInstructions.tsx**: Usage guide

#### Attendance (`src/components/attendance/`)
- **CheckInCheckOut.tsx**: Quick check-in/out buttons
- **AttendanceManagement.tsx**: Full attendance interface
- **AttendanceCalendarView.tsx**: Calendar visualization
- **AttendanceRecordsList.tsx**: History table

### State Management (Zustand)

```typescript
// src/store/authStore.ts
interface AuthState {
  user: User | null;
  tokens: Tokens | null;
  isAuthenticated: boolean;
  login: (email: string, password: string) => Promise<void>;
  logout: () => void;
  googleLogin: (token: string) => Promise<void>;
}

// src/store/employeeStore.ts
interface EmployeeState {
  employees: Employee[];
  loading: boolean;
  error: string | null;
  fetchEmployees: (filters?: Filters) => Promise<void>;
  createEmployee: (data: EmployeeInput) => Promise<void>;
  updateEmployee: (id: string, data: EmployeeInput) => Promise<void>;
  deleteEmployee: (id: string) => Promise<void>;
}

// src/store/performanceScoreStore.ts
interface PerformanceScoreState {
  scores: PerformanceScore[];
  loading: boolean;
  error: string | null;
  fetchScores: (filters?: Filters) => Promise<void>;
  createScore: (data: ScoreInput) => Promise<void>;
  updateScore: (employeeId: string, period: string, data: ScoreInput) => Promise<void>;
  deleteScore: (employeeId: string, period: string) => Promise<void>;
}
```

### API Services

```typescript
// src/services/api.ts
const api = axios.create({
  baseURL: import.meta.env.VITE_API_BASE_URL,
  headers: {
    'Content-Type': 'application/json',
  },
});

// Interceptor to add auth token
api.interceptors.request.use((config) => {
  const token = localStorage.getItem('idToken');
  if (token) {
    config.headers.Authorization = `Bearer ${token}`;
  }
  return config;
});

// src/services/employeeService.ts
export const employeeService = {
  getAll: (filters?: Filters) => api.get('/employees', { params: filters }),
  getById: (id: string) => api.get(`/employees/${id}`),
  create: (data: EmployeeInput) => api.post('/employees', data),
  update: (id: string, data: EmployeeInput) => api.put(`/employees/${id}`, data),
  delete: (id: string) => api.delete(`/employees/${id}`),
  bulkImport: (csvData: string) => api.post('/employees/bulk', { csvData }),
};
```

### Routing

```typescript
// src/router.tsx
const router = createBrowserRouter([
  { path: '/login', element: <LoginPage /> },
  { path: '/register', element: <RegisterForm /> },
  {
    path: '/',
    element: <ProtectedRoute><Layout /></ProtectedRoute>,
    children: [
      { path: '/', element: <DashboardPage /> },
      { path: '/admin', element: <AdminPage /> },
      { path: '/employees', element: <EmployeesPage /> },
      { path: '/performance-scores', element: <PerformanceScoresPage /> },
      { path: '/attendance', element: <AttendancePage /> },
      { path: '/chatbot', element: <ChatbotPage /> },
      { path: '/profile', element: <ProfilePage /> },
    ],
  },
]);
```

---

## Backend Services

### Lambda Function Details

#### 1. Authentication Service (`lambda/auth/`)

**Files**:
- `auth_login_handler.py`: Login with Cognito
- `auth_register_handler.py`: User registration
- `auth_google_handler.py`: Google OAuth
- `password_reset_handler.py`: Password reset workflow

**API Endpoints**:
```
POST /auth/login
POST /auth/register
POST /auth/google
POST /auth/password-reset/request
POST /auth/password-reset/confirm
GET  /auth/password-reset/requests (Admin only)
```

**Key Features**:
- Cognito USER_PASSWORD_AUTH flow
- JWT token generation (access, refresh, ID tokens)
- Google token verification with google-auth library
- Auto-confirmation for development
- Role-based access control

#### 2. Employee Service (`lambda/employees/`)

**Files**:
- `employees_handler.py`: CRUD operations
- `employees_bulk_handler.py`: CSV bulk import

**API Endpoints**:
```
GET    /employees
GET    /employees/{employeeId}
POST   /employees
PUT    /employees/{employeeId}
DELETE /employees/{employeeId}
POST   /employees/bulk
```

**Key Features**:
- Department filtering (DEV, QA, DAT, SEC, AI)
- Position filtering (Junior, Mid, Senior, Lead, Manager)
- Status filtering (active, inactive)
- Search by name or employee ID
- CSV parsing with validation

#### 3. Performance Scores Service (`lambda/performance-scores/`)

**Files**:
- `performance_scores_handler.py`: Score management

**API Endpoints**:
```
GET    /performance-scores
GET    /performance-scores/{employeeId}/{period}
POST   /performance-scores
PUT    /performance-scores/{employeeId}/{period}
DELETE /performance-scores/{employeeId}/{period}
POST   /performance-scores/bulk
POST   /performance-scores/upload
```

**Key Features**:
- Automatic score calculation (average of KPI, completed_task, feedback_360)
- Department and period filtering
- Role-based data access (Admin: all, Manager: department, Employee: own)
- Denormalized employee data for performance
- Bulk import from CSV

#### 4. Chatbot Service (`lambda/chatbot/`)

**Files**:
- `chatbot_handler.py`: Bedrock integration

**API Endpoints**:
```
POST /chatbot/query
```

**Key Features**:
- AWS Bedrock integration (Claude 3 Haiku)
- Natural language query processing
- Context building from DynamoDB
- Role-based data filtering
- Detailed information responses
- Cost-effective ($0.000375 per query)

**Supported Queries**:
- Employee information ("Who is DEV-001?")
- Performance queries ("What's the average score for Q1 2025?")
- Department statistics ("Compare DEV and QA performance")
- Trend analysis ("Performance trends over quarters")

#### 5. Attendance Service (`lambda/attendance/`)

**Files**:
- `attendance_handler.py`: Check-in/out and history

**API Endpoints**:
```
GET    /attendance
GET    /attendance/{employeeId}/{date}
POST   /attendance/check-in
POST   /attendance/check-out
PUT    /attendance/{employeeId}/{date}
DELETE /attendance/{employeeId}/{date}
POST   /attendance/bulk
```

**Key Features**:
- Real-time check-in/check-out
- Date range filtering
- Department filtering
- Status tracking (present, absent, late, half-day)
- Bulk operations

---

## Database Schema

### Users Table
```json
{
  "userId": "uuid",
  "email": "user@example.com",
  "name": "User Name",
  "role": "Admin|Manager|Employee",
  "employeeId": "DEV-001",
  "department": "DEV",
  "isActive": true,
  "createdAt": "2025-01-01T00:00:00Z",
  "updatedAt": "2025-01-01T00:00:00Z"
}
```

### Employees Table
```json
{
  "employeeId": "DEV-001",
  "name": "Employee Name",
  "email": "employee@example.com",
  "department": "DEV",
  "position": "Senior",
  "status": "active",
  "hireDate": "2024-01-01",
  "managerId": "DEV-000",
  "createdAt": "2025-01-01T00:00:00Z",
  "updatedAt": "2025-01-01T00:00:00Z"
}
```

### Performance Scores Table
```json
{
  "scoreId": "uuid",
  "employeeId": "DEV-001",
  "period": "2025-1",
  "employeeName": "Employee Name",
  "department": "DEV",
  "position": "Senior",
  "overallScore": 85.5,
  "kpiScores": {
    "KPI": 85.0,
    "completed_task": 88.0,
    "feedback_360": 83.5
  },
  "calculatedAt": "2025-11-22T20:19:37Z",
  "createdAt": "2025-11-22T20:19:37Z",
  "updatedAt": "2025-11-22T20:19:37Z"
}
```

### Attendance History Table
```json
{
  "employeeId": "DEV-001",
  "date": "2025-12-09",
  "employeeName": "Employee Name",
  "department": "DEV",
  "checkInTime": "09:00:00",
  "checkOutTime": "18:00:00",
  "status": "present",
  "notes": "On time",
  "createdAt": "2025-12-09T09:00:00Z",
  "updatedAt": "2025-12-09T18:00:00Z"
}
```

---

## Deployment

### Frontend Deployment

```bash
# 1. Build production bundle
cd insighthr-web
npm run build

# 2. Upload to S3
aws s3 sync dist/ s3://insighthr-web-app-sg --region ap-southeast-1

# 3. Invalidate CloudFront cache
aws cloudfront create-invalidation \
  --distribution-id E3MHW5VALWTOCI \
  --paths "/*"
```

### Lambda Deployment

```powershell
# Deploy all Lambda functions
cd lambda/auth
.\deploy-lambdas.ps1

cd ../employees
.\deploy-lambdas.ps1

cd ../performance-scores
.\deploy-lambda.ps1

cd ../chatbot
.\deploy.ps1

cd ../attendance
.\deploy-lambda.ps1
```

### API Gateway Setup

```powershell
# Setup API Gateway endpoints
cd lambda/auth
.\setup-api-gateway.ps1

cd ../employees
.\setup-api-gateway.ps1

cd ../performance-scores
.\setup-api-gateway.ps1

cd ../chatbot
.\setup-api-gateway.ps1

cd ../attendance
.\setup-api-gateway.ps1
```

### Environment Variables

**Frontend (.env)**:
```bash
VITE_API_BASE_URL=https://lqk4t6qzag.execute-api.ap-southeast-1.amazonaws.com/dev
VITE_GOOGLE_CLIENT_ID=your-google-client-id
VITE_AWS_REGION=ap-southeast-1
VITE_COGNITO_USER_POOL_ID=ap-southeast-1_rzDtdAhvp
VITE_COGNITO_CLIENT_ID=6suhk5huhe40o6iuqgsnmuucj5
```

**Lambda (Environment Variables)**:
```bash
AWS_REGION=ap-southeast-1
USER_POOL_ID=ap-southeast-1_rzDtdAhvp
CLIENT_ID=6suhk5huhe40o6iuqgsnmuucj5
DYNAMODB_USERS_TABLE=insighthr-users-dev
EMPLOYEES_TABLE=insighthr-employees-dev
PERFORMANCE_SCORES_TABLE=insighthr-performance-scores-dev
ATTENDANCE_HISTORY_TABLE=insighthr-attendance-history-dev
BEDROCK_MODEL_ID=anthropic.claude-3-haiku-20240307-v1:0
BEDROCK_REGION=ap-southeast-1
```

---

## Testing

### CloudWatch Synthetics Canaries

Located in `cloudwatch/canaries/`:

1. **login-canary.js**: Tests login flow
2. **dashboard-canary.js**: Tests dashboard loading
3. **chatbot-canary.js**: Tests chatbot queries
4. **autoscoring-canary.js**: Tests performance calculations

**Deployment**:
```powershell
cd cloudwatch/canaries
.\deploy-all-canaries.ps1
```

### Manual Testing Scripts

```powershell
# Test authentication endpoints
cd lambda/auth
.\test-endpoints.ps1

# Test employee endpoints
cd lambda/employees
.\test-endpoints.ps1

# Test performance scores
cd lambda/performance-scores
.\test-endpoints.ps1

# Test chatbot
cd lambda/chatbot
.\test-detailed-info.ps1
```

### Local Development

```bash
# Start stub API (mock backend)
cd stub-api
npm install
npm start

# Start frontend with stub API
cd insighthr-web
npm install
npm run dev
```

---

## Migration Status

### Completed Tasks (✓)

- **Task 12.1**: Configure new AWS credentials and verify access
  - New account: 477059411501
  - Region: ap-southeast-1
  - User: admin-user

- **Task 12.2**: Recreate DynamoDB tables with data restoration
  - 9 tables created
  - 190 records restored from CSV backups
  - All tables ACTIVE

### Pending Tasks

- **Task 12.3**: Create S3 buckets
- **Task 12.4**: Setup Cognito User Pool
- **Task 12.5**: Create IAM roles and policies
- **Task 12.6**: Deploy Lambda functions
- **Task 12.7**: Setup API Gateway
- **Task 12.8**: Configure CloudWatch monitoring
- **Task 12.9**: Setup CloudFront distribution
- **Task 12.10**: Configure Route53 DNS
- **Task 12.11**: Deploy frontend to S3
- **Task 12.12**: Final testing and verification

---

## Production URLs

- **Custom Domain**: https://insight-hr.io.vn
- **www**: https://www.insight-hr.io.vn
- **CloudFront**: https://d2z6tht6rq32uy.cloudfront.net
- **API Gateway**: https://lqk4t6qzag.execute-api.ap-southeast-1.amazonaws.com/dev

---

## Key Documentation Files

- **Main README**: `README.md`
- **Frontend README**: `insighthr-web/README.md`
- **Lambda READMEs**: `lambda/*/README.md`
- **Domain Setup**: `scripts/DOMAIN-SETUP-GUIDE.md`
- **CloudWatch Guide**: `cloudwatch/QUICK_START.md`
- **Spec Documents**: `.kiro/specs/static-ui-web-interface/`

---

## Contact & Support

For questions or issues during the workshop, refer to:
- AWS Console: https://console.aws.amazon.com/
- Project Repository: (your git repository)
- Documentation: All README files in respective directories

---

**End of Workshop Summary**
