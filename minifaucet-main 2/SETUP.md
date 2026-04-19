# Quick Setup Guide

## 1. Install Dependencies

```bash
# Install root dependencies
npm install

# Install frontend dependencies
cd frontend && npm install && cd ..
```

Or use the convenience script:
```bash
npm run install-all
```

## 2. Configure Environment

Create a `.env` file in the root directory:

```bash
cp .env.example .env
```

Edit `.env` and update at minimum:
- `MONGODB_URI` - Your MongoDB connection string
- `JWT_SECRET` - A random secret string for JWT tokens
- `ADMIN_USERNAME` and `ADMIN_PASSWORD` - Your admin credentials

## 3. Start MongoDB

Make sure MongoDB is running on your system or use a cloud MongoDB instance (MongoDB Atlas).

## 4. Initialize Admin User

```bash
npm run init-admin
```

This creates the default admin user. **Change the password in production!**

## 5. Start the Application

### Development Mode (Both servers)
```bash
npm run dev
```

### Or start separately:

**Terminal 1 - Backend:**
```bash
npm run server
```

**Terminal 2 - Frontend:**
```bash
npm run client
```

## 6. Access the Application

- **User Mini-App**: http://localhost:3000
- **Admin Dashboard**: http://localhost:3000/admin/login
- **Backend API**: http://localhost:5000/api

## 7. Test Admin Login

- Username: `admin` (or your configured username)
- Password: `admin123` (or your configured password)

## Next Steps

1. Create tasks in the admin dashboard
2. Configure faucet settings
3. Set up withdrawal methods
4. Deploy to production (see README.md)

## Troubleshooting

### MongoDB Connection Error
- Ensure MongoDB is running
- Check `MONGODB_URI` in `.env`
- For local MongoDB: `mongodb://localhost:27017/telegram_earning_app`

### Port Already in Use
- Change `PORT` in `.env` (backend)
- Change port in `frontend/package.json` scripts (frontend)

### Admin Login Fails
- Run `npm run init-admin` again
- Check username/password in `.env`
- Verify JWT_SECRET is set
