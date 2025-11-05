# Restaurant Recommender 🍴

![MongoDB](https://img.shields.io/badge/MongoDB-47A248?style=for-the-badge&logo=mongodb&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)

## 📋 Project Overview

A MongoDB-based web application that recommends restaurants based on user preferences such as cuisine type, price range, and amenities. This project showcases NoSQL database design, advanced query optimization, and efficient data-driven recommendations without relying on AI/ML algorithms.

Built as part of an Advanced Database Concepts course, this application demonstrates practical implementation of:
- NoSQL database architecture
- Query optimization techniques
- Efficient indexing strategies
- Dynamic filtering and search capabilities
- Real-world database integration

## ✨ Features

- **🔍 Advanced Search & Filtering**
  - Filter restaurants by cuisine type (Italian, Chinese, Indian, Mexican, etc.)
  - Price range selection ($, $$, $$$, $$$$)
  - Amenity filtering (parking, WiFi, outdoor seating, delivery)
  - Location-based search

- **📊 Smart Recommendations**
  - Data-driven suggestions based on user preferences
  - Multi-criteria matching algorithm
  - Rating-based sorting
  - Distance and location consideration

- **⚡ Performance Optimization**
  - Efficient MongoDB indexing for fast queries
  - Optimized aggregation pipelines
  - Cached frequently accessed data
  - Responsive query execution

- **📱 User-Friendly Interface**
  - Clean and intuitive web interface
  - Real-time search results
  - Detailed restaurant information display
  - Interactive filters and sorting options

## 🛠️ Technologies Used

### Backend
- **MongoDB**: NoSQL database for storing restaurant data
- **Python/Flask or Node.js**: Server-side application logic
- **PyMongo/Mongoose**: MongoDB driver for database operations

### Frontend
- **HTML5**: Structure and semantic markup
- **CSS3**: Styling and responsive design
- **JavaScript**: Interactive functionality and AJAX requests
- **Bootstrap**: UI framework for responsive components

### Database Features
- **Indexing**: Single-field and compound indexes for optimization
- **Aggregation Pipelines**: Complex data processing and analysis
- **Text Search**: Full-text search capabilities
- **GeoSpatial Queries**: Location-based restaurant discovery

## 🚀 Getting Started

### Prerequisites

```bash
MongoDB 4.0+
Python 3.7+ (or Node.js 12+)
pip (Python package manager) or npm
```

### Installation

1. **Clone the repository**:
```bash
git clone https://github.com/aditi-akhilesh/RestaurantRecommender.git
cd RestaurantRecommender
```

2. **Install dependencies**:

For Python/Flask:
```bash
pip install -r requirements.txt
```

For Node.js:
```bash
npm install
```

3. **Set up MongoDB**:
```bash
# Start MongoDB service
mongod

# Import sample restaurant data
mongoimport --db restaurantDB --collection restaurants --file data/restaurants.json
```

4. **Configure database connection**:
```bash
cp .env.example .env
# Edit .env with your MongoDB connection string
```

### Running the Application

**Development mode**:
```bash
python app.py
# or
npm start
```

Access the application at: `http://localhost:5000` (or configured port)

## 📊 Database Schema

### Restaurant Collection

```json
{
  "_id": ObjectId,
  "name": "Restaurant Name",
  "cuisine": "Italian",
  "price_range": "$$",
  "rating": 4.5,
  "location": {
    "address": "123 Main St",
    "city": "New York",
    "coordinates": [40.7128, -74.0060]
  },
  "amenities": ["parking", "wifi", "outdoor_seating"],
  "hours": {},
  "reviews_count": 150
}
```

### Optimized Indexes

```javascript
// Compound index for common queries
db.restaurants.createIndex({ "cuisine": 1, "price_range": 1, "rating": -1 })

// Text index for search
db.restaurants.createIndex({ "name": "text", "cuisine": "text" })

// GeoSpatial index for location queries
db.restaurants.createIndex({ "location.coordinates": "2dsphere" })
```

## 🔧 Key Query Examples

### Find restaurants by cuisine and price range
```javascript
db.restaurants.find({
  cuisine: "Italian",
  price_range: { $in: ["$", "$$"] },
  rating: { $gte: 4.0 }
}).sort({ rating: -1 }).limit(10)
```

### Aggregation for recommendations
```javascript
db.restaurants.aggregate([
  { $match: { cuisine: { $in: userPreferences } } },
  { $sort: { rating: -1 } },
  { $limit: 20 }
])
```

## 💡 Use Cases

- Restaurant discovery based on personal preferences
- Meal planning and dining decisions
- Exploring new cuisines in an area
- Finding restaurants with specific amenities
- Budget-conscious dining options
- Educational tool for database concepts

## 🏆 Key Learning Outcomes

- **NoSQL Design Patterns**: Flexible schema design for restaurant data
- **Query Optimization**: Using indexes and aggregation for performance
- **Data Modeling**: Embedding vs. referencing strategies
- **Web Integration**: Connecting frontend with database backend
- **Real-world Application**: Practical database concepts implementation

## 📚 Documentation

For detailed documentation on:
- Database schema design
- Query optimization strategies
- API endpoints
- Deployment instructions

Please refer to the `/docs` directory.

## 🤝 Contributing

Contributions, issues, and feature requests are welcome! Feel free to check the issues page.

## 📝 License

This project is open source and available under the MIT License.

## 👤 Author

**Aditi Akhilesh**
- GitHub: [@aditi-akhilesh](https://github.com/aditi-akhilesh)
- LinkedIn: [aditi-akhilesh](https://www.linkedin.com/in/aditi-akhilesh/)

## 🚀 Future Enhancements

- [ ] User authentication and personalized recommendations
- [ ] Review and rating system
- [ ] Interactive maps integration
- [ ] Mobile app version
- [ ] Advanced ML-based recommendations
- [ ] Social features (favorites, sharing)

## 🌟 Acknowledgments

- Built for Advanced Database Concepts course
- Demonstrates practical NoSQL database applications
- Inspired by real-world restaurant recommendation systems

---

⭐ If you find this project helpful, please give it a star!
