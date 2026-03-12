# EcoTour Jharkhand - Project Specification

## 1. Project Overview

**Project Name:** EcoTour Jharkhand  
**Type:** Full-stack Web Application (Smart India Hackathon)  
**Core Functionality:** A responsive tourism platform promoting eco and cultural tourism in Jharkhand with interactive maps, multilingual support, AI-powered itinerary planning, and user reviews.  
**Target Users:** Domestic and international tourists, travel enthusiasts, and local tour operators.

---

## 2. Technology Stack

### Frontend
- **Framework:** React 18 with Vite
- **Styling:** Custom CSS with CSS Variables
- **Maps:** Google Maps JavaScript API
- **HTTP Client:** Axios
- **Internationalization:** i18next

### Backend
- **Runtime:** Node.js
- **Framework:** Express.js
- **Database:** MongoDB with Mongoose ODM
- **Authentication:** JWT (JSON Web Tokens)

### Database
- **MongoDB:** Cloud-hosted or local instance
- **Collections:** destinations, users, reviews, itineraries

---

## 3. UI/UX Specification

### Color Palette
- **Primary:** `#1a472a` (Forest Green - represents eco-tourism)
- **Secondary:** `#8B4513` (Saddle Brown - represents tribal culture)
- **Accent:** `#FFB347` (Saffron/Orange - represents warmth)
- **Background:** `#FDF8F3` (Warm off-white)
- **Dark:** `#2D2D2D` (Charcoal)
- **Light:** `#FFFFFF`
- **Success:** `#4CAF50`
- **Warning:** `#FF9800`
- **Error:** `#F44336`

### Typography
- **Headings:** 'Playfair Display', serif (elegant, cultural feel)
- **Body:** 'Nunito', sans-serif (readable, friendly)
- **Hindi Text:** 'Noto Sans Devanagari', sans-serif

### Font Sizes
- H1: 3rem (48px)
- H2: 2.25rem (36px)
- H3: 1.75rem (28px)
- Body: 1rem (16px)
- Small: 0.875rem (14px)

### Spacing System
- xs: 4px
- sm: 8px
- md: 16px
- lg: 24px
- xl: 32px
- xxl: 48px

### Responsive Breakpoints
- Mobile: < 576px
- Tablet: 576px - 992px
- Desktop: > 992px

### Visual Effects
- Box shadows: `0 4px 20px rgba(26, 71, 42, 0.15)`
- Border radius: 12px (cards), 8px (buttons), 50% (avatars)
- Transitions: 0.3s ease-in-out
- Hover effects: Scale 1.02 on cards, color shift on buttons

---

## 4. Page Structure

### 4.1 Header/Navigation
- Logo (EcoTour Jharkhand with leaf icon)
- Navigation links: Home, Destinations, Map, Itinerary, Reviews
- Language toggle (EN/HI)
- Mobile hamburger menu

### 4.2 Home Page (/)
- Hero section with background image of Jharkhand landscapes
- Tagline: "Discover the Hidden Treasures of Jharkhand"
- Quick search bar
- Featured destinations carousel
- Cultural highlights section
- Testimonials
- Call-to-action for itinerary planning

### 4.3 Destinations Page (/destinations)
- Grid of destination cards
- Filter by: Category (Nature, Wildlife, Cultural, Adventure)
- Sort by: Rating, Popularity
- Each card shows: Image, Name, Location, Rating, Category badge

### 4.4 Destination Detail Page (/destination/:id)
- Hero image gallery
- Destination name and location
- Category and rating
- Description (English/Hindi)
- Cultural information section
- Key highlights (list)
- Best time to visit
- How to reach
- Nearby attractions
- User reviews section
- Book now / Add to itinerary button

### 4.5 Map Page (/map)
- Full-screen Google Map
- Custom markers for each destination
- Marker clusters for dense areas
- Info windows on click showing destination preview
- Filter controls on sidebar
- List view toggle

### 4.6 Itinerary Generator Page (/itinerary)
- Form inputs:
  - Number of days (1-10)
  - Start date
  - Interests checkboxes (Nature, Wildlife, Culture, Adventure, Spiritual)
  - Travel style (Relaxed, Moderate, Adventurous)
  - Budget (Budget, Mid-range, Luxury)
- Generate button
- AI-generated day-by-day itinerary display
- Save itinerary option

### 4.7 Reviews Page (/reviews)
- List of user reviews
- Filter by destination
- Add review form (rating, comment)
- Login required for posting

### 4.8 Login/Register Modal
- Email/password fields
- Social login buttons (Google)
- Register link

---

## 5. Functionality Specification

### 5.1 Interactive Tourism Map
- Display all destinations on Google Maps
- Custom markers with category icons
- Click marker to show info window
- Info window has: Image, Name, Rating, "View Details" link
- Filter markers by category
- Geolocation to show user's current position

### 5.2 Multilingual Support
- Toggle between English and Hindi
- All UI text translated
- Destination content in both languages
- Persistent language preference (localStorage)
- RTL support not needed for Hindi (left-to-right)

### 5.3 Tourist Destination Pages
- Dynamic routing based on destination ID
- Image gallery with lightbox
- Tabbed content sections
- Related destinations suggestions
- Share buttons (WhatsApp, Facebook)

### 5.4 User Review System
- Star rating (1-5)
- Text comment (required, min 10 chars)
- Date of visit
- Helpful votes
- User can edit/delete own review
- Admin can moderate reviews

### 5.5 AI-Powered Itinerary Generator
- Form collects user preferences
- Algorithm selects destinations matching interests
- Organizes by day based on travel time
- Includes:
  - Morning, afternoon, evening slots
  - Estimated travel time between spots
  - Recommended restaurants
  - Accommodation suggestions
- Export as PDF (optional)

### 5.6 Mobile Responsive Design
- Fluid typography
- Touch-friendly navigation
- Collapsible sections
- Bottom navigation on mobile
- Optimized images for mobile

---

## 6. API Endpoints

### Destinations
- `GET /api/destinations` - List all destinations
- `GET /api/destinations/:id` - Get destination details
- `GET /api/destinations/category/:category` - Filter by category

### Reviews
- `GET /api/reviews` - List reviews (with pagination)
- `GET /api/reviews/destination/:id` - Reviews for specific destination
- `POST /api/reviews` - Create review (auth required)
- `PUT /api/reviews/:id` - Update review (auth required)
- `DELETE /api/reviews/:id` - Delete review (auth required)

### Users
- `POST /api/auth/register` - User registration
- `POST /api/auth/login` - User login
- `GET /api/auth/profile` - Get user profile (auth required)

### Itinerary
- `POST /api/itinerary/generate` - Generate itinerary based on preferences

---

## 7. Database Schema

### Destination Collection
```javascript
{
  _id: ObjectId,
  name: {
    en: String,
    hi: String
  },
  slug: String,
  location: {
    city: String,
    district: String,
    coordinates: {
      lat: Number,
      lng: Number
    }
  },
  category: String, // nature, wildlife, cultural, adventure, spiritual
  images: [String],
  description: {
    en: String,
    hi: String
  },
  culturalInfo: {
    en: String,
    hi: String
  },
  highlights: {
    en: [String],
    hi: [String]
  },
  bestTimeToVisit: String,
  howToReach: String,
  rating: Number,
  reviewCount: Number,
  featured: Boolean,
  createdAt: Date,
  updatedAt: Date
}
```

### User Collection
```javascript
{
  _id: ObjectId,
  name: String,
  email: String,
  password: String (hashed),
  avatar: String,
  role: String, // user, admin
  createdAt: Date
}
```

### Review Collection
```javascript
{
  _id: ObjectId,
  destinationId: ObjectId,
  userId: ObjectId,
  rating: Number, // 1-5
  comment: String,
  dateOfVisit: Date,
  helpful: Number,
  createdAt: Date,
  updatedAt: Date
}
```

---

## 8. Folder Structure

```
ecotour-jharkhand/
├── client/                    # React Frontend
│   ├── public/
│   │   └── images/
│   ├── src/
│   │   ├── components/
│   │   │   ├── common/
│   │   │   │   ├── Header.jsx
│   │   │   │   ├── Footer.jsx
│   │   │   │   ├── Loader.jsx
│   │   │   │   └── LanguageToggle.jsx
│   │   │   ├── home/
│   │   │   │   ├── Hero.jsx
│   │   │   │   ├── FeaturedDestinations.jsx
│   │   │   │   └── Testimonials.jsx
│   │   │   ├── destinations/
│   │   │   │   ├── DestinationCard.jsx
│   │   │   │   ├── DestinationList.jsx
│   │   │   │   └── DestinationDetail.jsx
│   │   │   ├── map/
│   │   │   │   ├── TourismMap.jsx
│   │   │   │   └── MapFilters.jsx
│   │   │   ├── itinerary/
│   │   │   │   ├── ItineraryForm.jsx
│   │   │   │   └── ItineraryDisplay.jsx
│   │   │   └── reviews/
│   │   │       ├── ReviewCard.jsx
│   │   │       ├── ReviewForm.jsx
│   │   │       └── ReviewList.jsx
│   │   ├── pages/
│   │   │   ├── Home.jsx
│   │   │   ├── Destinations.jsx
│   │   │   ├── DestinationDetail.jsx
│   │   │   ├── Map.jsx
│   │   │   ├── Itinerary.jsx
│   │   │   └── Reviews.jsx
│   │   ├── context/
│   │   │   ├── AuthContext.jsx
│   │   │   └── LanguageContext.jsx
│   │   ├── hooks/
│   │   ├── services/
│   │   │   ├── api.js
│   │   │   ├── destinationService.js
│   │   │   ├── reviewService.js
│   │   │   └── itineraryService.js
│   │   ├── locales/
│   │   │   ├── en/
│   │   │   │   └── translation.json
│   │   │   └── hi/
│   │   │       └── translation.json
│   │   ├── styles/
│   │   │   ├── variables.css
│   │   │   ├── global.css
│   │   │   └── components/
│   │   ├── utils/
│   │   ├── App.jsx
│   │   ├── main.jsx
│   │   └── index.css
│   ├── package.json
│   └── vite.config.js
│
├── server/                    # Node.js Backend
│   ├── config/
│   │   └── db.js
│   ├── controllers/
│   │   ├── destinationController.js
│   │   ├── reviewController.js
│   │   ├── authController.js
│   │   └── itineraryController.js
│   ├── models/
│   │   ├── Destination.js
│   │   ├── User.js
│   │   └── Review.js
│   ├── routes/
│   │   ├── destinationRoutes.js
│   │   ├── reviewRoutes.js
│   │   ├── authRoutes.js
│   │   └── itineraryRoutes.js
│   ├── middleware/
│   │   └── auth.js
│   ├── seed/
│   │   └── destinations.js
│   ├── .env
│   ├── package.json
│   └── server.js
│
├── README.md
└── SPEC.md
```

---

## 9. Acceptance Criteria

### Visual Checkpoints
- [ ] Home page loads with hero image and featured destinations
- [ ] Navigation is visible and functional on all screen sizes
- [ ] Language toggle switches all text between English and Hindi
- [ ] Destination cards display correctly in grid layout
- [ ] Map displays with custom markers
- [ ] Itinerary form captures all required inputs
- [ ] Reviews display with star ratings

### Functional Checkpoints
- [ ] API endpoints return correct data
- [ ] User can register and login
- [ ] User can post reviews (when logged in)
- [ ] Itinerary generates based on selected preferences
- [ ] Map markers are filterable
- [ ] Mobile navigation works correctly
- [ ] All pages are responsive

### Performance
- [ ] Initial page load < 3 seconds
- [ ] Images are optimized
- [ ] No console errors
- [ ] Smooth animations and transitions

