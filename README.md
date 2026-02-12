# 🚗 Uber Clone - Ride Sharing Application

A full-stack ride-sharing application built with the MERN stack, featuring real-time location tracking, ride matching, and Socket.IO for live updates.

## 🌟 Features

### For Users
- 📱 User registration and authentication
- 📍 Real-time location-based ride booking
- 💰 Instant fare calculation (distance + time based)
- 🚖 Live captain tracking during rides
- 🔔 Real-time ride status updates via Socket.IO
- 🔐 Secure OTP verification system

### For Captains (Drivers)
- 👨‍✈️ Captain registration with vehicle details (car/motorcycle/auto)
- 📍 Real-time location sharing and updates
- 🔔 Instant ride request notifications to nearby captains
- ✅ Accept/reject ride requests
- 🔐 6-digit OTP-based ride start verification
- 📊 Active/Inactive status management

## 🛠️ Tech Stack

### Backend
- **Runtime:** Node.js
- **Framework:** Express.js
- **Database:** MongoDB with Mongoose ODM
- **Authentication:** JWT (JSON Web Tokens)
- **Real-time:** Socket.IO
- **Security:** bcrypt for password hashing
- **Validation:** express-validator
- **APIs:** Google Maps API for location services

### Frontend
- **Framework:** React 18
- **Build Tool:** Vite
- **Routing:** React Router DOM v6
- **Styling:** Tailwind CSS
- **Animations:** GSAP
- **HTTP Client:** Axios
- **Real-time:** Socket.IO Client
- **Maps:** Google Maps API (@react-google-maps/api)
- **Icons:** Remix Icon

## 📁 Project Structure

```
Uber_Project/
├── Backend/
│   ├── controllers/      # Request handlers
│   ├── models/          # MongoDB schemas
│   ├── routes/          # API routes
│   ├── services/        # Business logic
│   ├── middlewares/     # Auth & validation
│   ├── db/             # Database connection
│   ├── app.js          # Express app setup
│   ├── server.js       # Server entry point
│   └── socket.js       # Socket.IO configuration
│
└── frontend/
    ├── src/
    │   ├── components/  # Reusable components
    │   ├── pages/       # Route pages
    │   ├── context/     # React Context (State)
    │   └── assets/      # Static assets
    ├── public/          # Public assets
    └── index.html       # Entry HTML
```

## 🚀 Getting Started

### Prerequisites
- Node.js (v14 or higher)
- MongoDB (local or Atlas)
- Google Maps API Key
- npm or yarn

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/WhiteC0der/Uber_Clone.git
   cd Uber_Project
   ```

2. **Backend Setup**
   ```bash
   cd Backend
   npm install
   ```

   Create `.env` file in Backend directory:
   ```env
   PORT=3000
   DB_CONNECT=your_mongodb_connection_string
   JWT_SECRET=your_jwt_secret_key
   GOOGLE_MAPS_API=your_google_maps_api_key
   ```

3. **Frontend Setup**
   ```bash
   cd ../frontend
   npm install
   ```

   Create `.env` file in frontend directory:
   ```env
   VITE_BASE_URL=http://localhost:3000
   VITE_API_URL=http://localhost:3000
   VITE_GOOGLE_MAPS_API_KEY=your_google_maps_api_key
   ```

### Running the Application

1. **Start MongoDB** (if running locally)
   ```bash
   mongod
   ```

2. **Start Backend Server**
   ```bash
   cd Backend
   npm start
   ```
   Server runs on http://localhost:3000

3. **Start Frontend Development Server**
   ```bash
   cd frontend
   npm run dev
   ```
   App runs on http://localhost:5173

## 🔑 API Endpoints

### User Routes (`/users`)
- `POST /users/register` - Register new user
- `POST /users/login` - User login
- `GET /users/profile` - Get user profile (Protected)
- `GET /users/logout` - Logout user (Protected)

### Captain Routes (`/captains`)
- `POST /captains/register` - Register new captain
- `POST /captains/login` - Captain login
- `GET /captains/profile` - Get captain profile (Protected)
- `GET /captains/logout` - Logout captain (Protected)

### Ride Routes (`/rides`)
- `POST /rides/create` - Create new ride (Protected)
- `GET /rides/get-fare` - Calculate fare
- `POST /rides/confirm` - Confirm ride (Captain, Protected)
- `GET /rides/start-ride` - Start ride with OTP (Captain, Protected)
- `POST /rides/end-ride` - End ride (Captain, Protected)

### Maps Routes (`/maps`)
- `GET /maps/get-coordinates` - Get coordinates from address
- `GET /maps/get-distance-time` - Calculate distance and time
- `GET /maps/get-suggestions` - Get address suggestions

## 🔐 Environment Variables

### Backend (.env)
| Variable | Description | Example |
|----------|-------------|---------|
| PORT | Server port | 3000 |
| DB_CONNECT | MongoDB connection string | mongodb://localhost:27017/uber |
| JWT_SECRET | Secret for JWT signing | your_secret_key_here |
| GOOGLE_MAPS_API | Google Maps API key | AIza... |

### Frontend (.env)
| Variable | Description | Example |
|----------|-------------|---------|
| VITE_BASE_URL | Backend API URL | http://localhost:3000 |
| VITE_API_URL | Backend API URL | http://localhost:3000 |
| VITE_GOOGLE_MAPS_API_KEY | Google Maps API key | AIza... |

## 🔌 Real-time Events (Socket.IO)

### Client → Server
- `join` - User/Captain joins with socketId
- `update-location-captain` - Captain updates location

### Server → Client
- `new-ride` - New ride notification to captains
- `ride-confirmed` - Ride confirmed by captain
- `ride-started` - Ride started notification
- `ride-ended` - Ride completed notification

## 🎯 Implemented Features

### Core Functionality
- ✅ User & Captain authentication (JWT-based)
- ✅ Real-time ride matching within 2km radius
- ✅ **6-digit OTP generation and verification** for ride start
- ✅ Dynamic fare calculation (base fare + distance + time)
- ✅ Live location tracking (Socket.IO)
- ✅ Ride status management (pending → accepted → ongoing → completed)
- ✅ Google Maps integration (geocoding, distance matrix, autocomplete)

### Security Features
- ✅ Password hashing with bcrypt
- ✅ JWT token authentication
- ✅ Token blacklisting on logout
- ✅ Protected API routes
- ✅ OTP validation for ride verification

## 📝 Features in Development
- [ ] Payment gateway integration (Razorpay/Stripe)
- [ ] Rating and review system
- [ ] Ride history dashboard
- [ ] Email/SMS notifications
- [ ] Push notifications
- [ ] Multi-language support
- [ ] Advanced analytics and reports
- [ ] Ride cancellation with refund logic
- [ ] Surge pricing during peak hours

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the project
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the ISC License.

## 👨‍💻 Author

**WhiteC0der**
- GitHub: [@WhiteC0der](https://github.com/WhiteC0der)

## 🙏 Acknowledgments

- Google Maps API for location services
- Socket.IO for real-time communication
- MongoDB for database
- React and Vite for frontend development

---

⭐ Star this repo if you find it helpful!
