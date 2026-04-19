# 🚀 Telegram Earning Mini-App (MERN Stack)

A comprehensive Telegram Mini-App for earning rewards through faucet claims, tasks, ads, referrals, and more. Built with React.js, Node.js, Express.js, and MongoDB. Features a modern, professional UI for both users and admins.

![Version](https://img.shields.io/badge/version-2.0.0-blue.svg)
![License](https://img.shields.io/badge/license-MIT-green.svg)

## ✨ Features

### 📱 Client Side (Telegram Mini-App)

#### Authentication & Dashboard

- ✅ Auto login via Telegram Web App SDK
- ✅ User Dashboard with balance, earnings, and stats
- ✅ Real-time balance updates
- ✅ Beautiful, responsive UI optimized for mobile

#### Earning Methods

- 💧 **Faucet System** - Claim rewards with configurable cooldown timer
- ✅ **Task System** - Complete tasks to earn (with proof submission)
- 📺 **Ads System** - Watch ads from multiple providers:
  - Adsgram integration
  - Monetag integration
  - Gigapub integration
  - Onclicka integration
- 👥 **Referral System** - Invite friends and earn commission on their earnings

#### Withdrawals

- 💸 Multiple withdrawal methods (FaucetPay, Crypto Wallet, etc.)
- 📊 Withdrawal history with status tracking
- ⚙️ Configurable minimum withdrawal and fees

#### User Experience

- 🔔 In-app notifications
- 📋 Complete earnings history with filtering
- 🎨 Modern, professional UI design
- 📱 Mobile-first responsive design

### 🛠️ Admin Dashboard

#### Dashboard & Analytics

- 📊 Real-time statistics and analytics
- 📈 Daily breakdown charts
- 🏆 Top referrers and earners leaderboards
- 📅 Custom date range analytics

#### User Management

- 👥 View all users with search and filtering
- ⚖️ Adjust user balances with reason
- 🚫 Ban/Suspend/Activate users
- 📊 User earning history

#### Task Management

- ✅ Create, edit, delete tasks
- 📝 Review task submissions
- ✓ Approve/Reject with bulk actions
- 🏷️ Task types: Social, Survey, Download, Sign Up, etc.

#### Withdrawal Management

- 💸 View all withdrawal requests
- ✓ Approve/Reject with transaction ID
- 📊 Withdrawal summary statistics
- 📤 Export withdrawals to CSV

#### Settings (All Configurable)

- 🏠 **App Settings**: App name, currency name
- 💧 **Faucet Settings**: Reward amount, cooldown timer
- 👥 **Referral Settings**: Commission percentage, welcome bonus
- 💸 **Withdrawal Settings**: Minimum amount, fee percentage, methods
- 📺 **Ads Settings**:
  - Enable/disable ads globally
  - Per-ad reward amount
  - Cooldown between ads
  - Daily ad limit
  - **Adsgram**: Enable/disable, Block ID
  - **Monetag**: Enable/disable, Zone ID
  - **Gigapub**: Enable/disable, Project ID
  - **Onclicka**: Enable/disable, Ad Code ID

#### Notifications

- 📢 Send broadcast notifications to all users
- 🔔 Priority levels (Low, Normal, High, Urgent)
- 📊 Notification history

## 📋 Tech Stack

| Component        | Technology                       |
| ---------------- | -------------------------------- |
| Frontend         | React.js 18 + React Router 6     |
| Backend          | Node.js + Express.js             |
| Database         | MongoDB + Mongoose               |
| Authentication   | JWT (30-day user, 24-hour admin) |
| Telegram SDK     | @twa-dev/sdk                     |
| Rate Limiting    | express-rate-limit               |
| Password Hashing | bcryptjs                         |

## 🛠️ Installation

### Prerequisites

- Node.js v14 or higher
- MongoDB (local or MongoDB Atlas)
- Telegram Bot (for production)

### Step 1: Clone and Install Dependencies

```bash
# Clone the repository
git clone <repository-url>
cd minifaucet

# Install root dependencies
npm install

# Install frontend dependencies
cd frontend
npm install
cd ..
```

### Step 2: Environment Configuration

Create a `.env` file in the root directory:

```env
# Server Configuration
PORT=5000
NODE_ENV=development

# MongoDB Connection
MONGODB_URI=mongodb://localhost:27017/minifaucet

# JWT Secrets
JWT_SECRET=your_super_secret_jwt_key_here
ADMIN_JWT_SECRET=your_admin_jwt_secret_here

# App Settings
APP_NAME=Telegram Earning App
CURRENCY_SYMBOL=Coins

# Faucet Settings
FAUCET_REWARD=1
FAUCET_COOLDOWN=300

# Referral Settings
REFERRAL_COMMISSION=10
WELCOME_BONUS=5

# Withdrawal Settings
MIN_WITHDRAWAL_AMOUNT=10
WITHDRAWAL_FEE=0

# Ad Settings
ADS_ENABLED=true
AD_REWARD=0.5
AD_COOLDOWN=60
DAILY_AD_LIMIT=50

# Ad Provider Settings (Optional - can be configured via admin panel)
ADSGRAM_BLOCK_ID=your_adsgram_block_id
MONETAG_ZONE_ID=your_monetag_zone_id
GIGAPUB_PROJECT_ID=your_gigapub_project_id
ONCLICKA_AD_CODE_ID=your_onclicka_ad_code_id

# Telegram Bot (for production)
TELEGRAM_BOT_TOKEN=your_telegram_bot_token
```

Create `.env` in the `frontend` directory:

```env
REACT_APP_API_URL=http://localhost:5000/api
```

### Step 3: Initialize Admin Account

```bash
npm run init-admin
```

This creates a default admin account:

- Username: `admin`
- Password: `admin123`

**⚠️ Change these credentials immediately after first login!**

### Step 4: Run the Application

```bash
# Development mode (runs both backend and frontend)
npm run dev

# Or run separately:
npm run server  # Backend only
npm run client  # Frontend only

# Production build
cd frontend && npm run build
npm start
```

## 📁 Project Structure

```
minifaucet/
├── backend/
│   ├── server.js              # Express server entry point
│   ├── middleware/
│   │   ├── auth.js            # JWT authentication middleware
│   │   └── referralReward.js  # Referral commission middleware
│   ├── models/
│   │   ├── Admin.js           # Admin user model
│   │   ├── AdSession.js       # Ad viewing session model
│   │   ├── Earning.js         # Earning transaction model
│   │   ├── Notification.js    # Notification model
│   │   ├── Settings.js        # App settings model
│   │   ├── Task.js            # Task definition model
│   │   ├── TaskSubmission.js  # Task submission model
│   │   ├── User.js            # User model
│   │   └── Withdrawal.js      # Withdrawal request model
│   ├── routes/
│   │   ├── admin.js           # Admin dashboard routes
│   │   ├── ads.js             # Ad provider routes
│   │   ├── auth.js            # Authentication routes
│   │   ├── earnings.js        # Faucet/earnings routes
│   │   ├── notifications.js   # Notification routes
│   │   ├── referrals.js       # Referral system routes
│   │   ├── settings.js        # Public settings routes
│   │   ├── tasks.js           # Task system routes
│   │   ├── user.js            # User profile routes
│   │   └── withdrawals.js     # Withdrawal routes
│   └── scripts/
│       └── initAdmin.js       # Admin initialization script
├── frontend/
│   ├── public/
│   │   └── index.html
│   └── src/
│       ├── App.js             # Main React app
│       ├── App.css            # Modern UI styles
│       ├── components/
│       │   ├── admin/
│       │   │   ├── AdminDashboard.js  # Full admin panel
│       │   │   └── AdminLogin.js      # Admin login
│       │   ├── common/
│       │   │   ├── BottomNav.js       # Mobile bottom navigation
│       │   │   └── Navbar.js          # Top navigation
│       │   └── user/
│       │       ├── Ads.js             # Watch ads page
│       │       ├── Dashboard.js       # User dashboard
│       │       ├── Earnings.js        # Earnings history
│       │       ├── Referrals.js       # Referral program
│       │       ├── Tasks.js           # Task completion
│       │       └── Withdrawals.js     # Withdrawal requests
│       └── context/
│           └── AuthContext.js  # Authentication context
└── package.json
```

## 🔒 API Endpoints

### Authentication

| Method | Endpoint             | Description      |
| ------ | -------------------- | ---------------- |
| POST   | `/api/auth/telegram` | Telegram login   |
| GET    | `/api/auth/verify`   | Verify JWT token |
| POST   | `/api/admin/login`   | Admin login      |

### User

| Method | Endpoint                | Description            |
| ------ | ----------------------- | ---------------------- |
| GET    | `/api/user/dashboard`   | Get dashboard data     |
| GET    | `/api/user/earnings`    | Get earnings history   |
| GET    | `/api/user/withdrawals` | Get withdrawal history |

### Earnings

| Method | Endpoint                      | Description         |
| ------ | ----------------------------- | ------------------- |
| GET    | `/api/earnings/faucet/status` | Get faucet status   |
| POST   | `/api/earnings/faucet/claim`  | Claim faucet reward |

### Tasks

| Method | Endpoint               | Description            |
| ------ | ---------------------- | ---------------------- |
| GET    | `/api/tasks/available` | Get available tasks    |
| POST   | `/api/tasks/submit`    | Submit task completion |

### Ads

| Method | Endpoint             | Description                  |
| ------ | -------------------- | ---------------------------- |
| GET    | `/api/ads/providers` | Get available ad providers   |
| POST   | `/api/ads/start`     | Start ad session             |
| POST   | `/api/ads/complete`  | Complete ad and claim reward |
| GET    | `/api/ads/history`   | Get ad history               |

### Referrals

| Method | Endpoint               | Description             |
| ------ | ---------------------- | ----------------------- |
| GET    | `/api/referrals/stats` | Get referral statistics |

### Withdrawals

| Method | Endpoint                   | Description         |
| ------ | -------------------------- | ------------------- |
| GET    | `/api/withdrawals/info`    | Get withdrawal info |
| POST   | `/api/withdrawals/request` | Request withdrawal  |

### Admin

| Method | Endpoint                             | Description         |
| ------ | ------------------------------------ | ------------------- |
| GET    | `/api/admin/dashboard`               | Get admin dashboard |
| GET    | `/api/admin/analytics`               | Get analytics data  |
| GET    | `/api/admin/users`                   | Get all users       |
| GET    | `/api/admin/tasks`                   | Get all tasks       |
| GET    | `/api/admin/withdrawals`             | Get all withdrawals |
| GET    | `/api/admin/settings`                | Get all settings    |
| PUT    | `/api/admin/settings`                | Update settings     |
| POST   | `/api/admin/notifications/broadcast` | Send broadcast      |

## 📺 Ad Provider Integration

### Adsgram

1. Register at [Adsgram](https://adsgram.ai)
2. Create an ad unit and get the Block ID
3. Enable Adsgram in Admin Settings
4. Enter the Block ID

### Monetag

1. Register at [Monetag](https://monetag.com)
2. Create a zone and get the Zone ID
3. Enable Monetag in Admin Settings
4. Enter the Zone ID

### Gigapub

1. Register at [Gigapub](https://giga.pub)
2. Create a project and get the Project ID
3. Enable Gigapub in Admin Settings
4. Enter the Project ID

### Onclicka

1. Register at [Onclicka](https://onclicka.com)
2. Create a Tg-Interstitial ad unit and get the Ad Code ID
3. Enable Onclicka in Admin Settings
4. Enter the Ad Code ID


## 🚀 Deployment

### Telegram Bot Setup

1. Create a bot with [@BotFather](https://t.me/BotFather)
2. Enable Web App for your bot
3. Set the Web App URL to your deployed frontend URL

### Deployment Options

- **Frontend**: Vercel, Netlify, or any static hosting
- **Backend**: Railway, Render, DigitalOcean, AWS
- **Database**: MongoDB Atlas (recommended)

## 🔐 Security Features

- JWT token authentication with expiration
- Rate limiting (100 requests per 15 minutes)
- Input validation and sanitization
- Password hashing with bcrypt
- Anti-fraud measures for ads (cooldown, daily limits, IP tracking)
- Admin session management

## 📄 License

MIT License - feel free to use this project for your own purposes.

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

---

Built with ❤️ for the Telegram community
