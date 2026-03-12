# EcoTour Jharkhand

A responsive web platform for promoting eco and cultural tourism in Jharkhand, India. Built for the Smart India Hackathon.

## Features

- 🗺️ **Interactive Tourism Map** - Explore destinations across Jharkhand with our interactive map
- 🌐 **Multilingual Support** - Available in English and Hindi
- 📱 **Mobile Responsive** - Works perfectly on all devices
- ⭐ **User Reviews & Ratings** - Share your experiences with other travelers
- 🤖 **AI-Powered Itinerary Generator** - Plan your trip based on your interests and preferences
- 🏛️ **Destination Pages** - Detailed information with images and cultural context

## Tech Stack

### Frontend
- React 18 with Vite
- React Router DOM
- i18next for internationalization
- Axios for API calls

### Backend
- Node.js with Express
- MongoDB with Mongoose

## Project Structure

```
ecotour-jharkhand/
├── client/                 # React Frontend
│   ├── src/
│   │   ├── components/    # Reusable components
│   │   ├── pages/         # Page components
│   │   ├── services/      # API services
│   │   ├── App.jsx        # Main app component
│   │   ├── index.css      # Global styles
│   │   └── i18n.js       # Internationalization config
│   └── package.json
├── server/                 # Node.js Backend
│   ├── config/            # Database config
│   ├── controllers/       # Route controllers
│   ├── models/           # Mongoose models
│   ├── routes/           # API routes
│   ├── middleware/       # Auth middleware
│   ├── seed/            # Seed data
│   └── package.json
├── SPEC.md               # Project specification
└── README.md
```

## Getting Started

### Prerequisites

- Node.js (v14 or higher)
- MongoDB (local or cloud instance)
- npm or yarn

### Backend Setup

1. Navigate to the server directory:
```bash
cd server
```

2. Install dependencies:
```bash
npm install
```

3. Create a `.env` file in the server directory:
```env
PORT=5000
MONGODB_URI=mongodb://localhost:27017/ecotour-jharkhand
JWT_SECRET=your_secret_key_here
GOOGLE_MAPS_API_KEY=your_google_maps_api_key
```

4. Start the backend server:
```bash
npm start
```

The server will run on http://localhost:5000

### Frontend Setup

1. Navigate to the client directory:
```bash
cd client
```

2. Install dependencies:
```bash
npm install
```

3. Start the development server:
```bash
npm run dev
```

The frontend will run on http://localhost:3000

## API Endpoints

### Destinations
- `GET /api/destinations` - Get all destinations
- `GET /api/destinations/:id` - Get destination by ID
- `GET /api/destinations/featured/list` - Get featured destinations
- `GET /api/destinations/category/:category` - Filter by category

### Reviews
- `GET /api/reviews` - Get all reviews
- `GET /api/reviews/destination/:id` - Get reviews for a destination
- `POST /api/reviews` - Create a review (requires auth)
- `PUT /api/reviews/:id` - Update a review
- `DELETE /api/reviews/:id` - Delete a review

### Authentication
- `POST /api/auth/register` - Register a new user
- `POST /api/auth/login` - Login user
- `GET /api/auth/profile` - Get user profile (requires auth)

### Itinerary
- `POST /api/itinerary/generate` - Generate AI-powered itinerary

## Environment Variables

### Server (.env)
```
PORT=5000
MONGODB_URI=mongodb://localhost:27017/ecotour-jharkhand
JWT_SECRET=your_secret_key
GOOGLE_MAPS_API_KEY=your_google_maps_key
```

### Client (.env)
```
VITE_API_URL=http://localhost:5000/api
```

## License

MIT License

## Authors

- Smart India Hackathon Team

## Acknowledgments

- Unsplash for images
- Jharkhand Tourism Department for inspiration

