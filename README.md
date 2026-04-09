Here is the updated `README.md` file, tailored specifically for the **Instagram 2021 Clone** with the sidebar layout, male-focused stories, and optimized feed.

```markdown
<img src="https://ik.imagekit.io/xvqovhmcyr/labsadik_instagram_clone%20-%20Google%20Chrome%204_9_2026%206_52_24%20PM.png">

---

# 📸 Instagram 2021 Clone

A fully functional, professional-grade Instagram clone replicating the 2021 Web & Mobile UI. Features a responsive sidebar navigation, infinite scroll feed, real-time interactions, and secure user authentication.

---

## ✨ **FEATURES**

### 🔐 Authentication
- User Signup & Login
- JWT Token Authentication
- Secure Password Hashing (bcrypt)
- Session Management via LocalStorage

### 📸 Content System
- Upload Images & Videos
- Bunny CDN Integration (Fast Global Delivery)
- Auto File Type Detection
- Multi-format Support (PNG, JPG, GIF, MP4)
- Real-time Upload Progress Bar

### 🖼️ Feed System
- **Professional Sidebar Layout** (Desktop)
- **Mobile Bottom Navigation** (Responsive)
- Vertical Infinite Scroll Feed
- Double-Tap to Like (with Heart Animation)
- Video Play/Pause Controls
- "Suggestions For You" Sidebar (Desktop)
- Stories Rail (Horizontal Scroll)

### 👤 User Profiles
- Dynamic Username Display (`post.userId.username`)
- Avatar Generation with Initials
- Individual User Post Filtering

### 🎨 UI/UX (Instagram 2021 Style)
- 100% Responsive (Mobile/Tablet/Desktop)
- Clean White/Gray Aesthetic
- Hover Effects on Desktop Nav
- Save/Share/Comment Actions
- Toast Notifications
- Modal Dialogs for Upload & Preview
- Broken Image Handling & Caching

---

## 🛠️ **TECH STACK**

**Frontend:** HTML5, CSS3, JavaScript ES6+, Tailwind CSS, Font Awesome  
**Backend:** Node.js, Express.js  
**Database:** MongoDB with Mongoose  
**Auth:** JWT + bcryptjs  
**Storage:** Bunny.net CDN  
**File Upload:** Multer + Axios  

---

## 📁 **PROJECT STRUCTURE**

```
instagram-clone/
├── server.js              # Main server entry point
├── .env                   # Environment variables
│
├── models/
│   ├── User.js            # User schema (username, email, password)
│   └── Post.js            # Post schema (title, fileUrl, type, userId)
│
├── routes/
│   ├── auth.js            # Auth routes (signup/login)
│   └── post.js            # Post routes (upload/feed)
│
├── middleware/
│   └── auth.js            # JWT verification middleware
│
├── utils/
│   └── bunny.js           # Bunny CDN upload utility
│
└── public/
    ├── login.html         # Login page
    ├── signup.html        # Registration page
    ├── index.html         # HOME - Main Feed ⭐ (Sidebar + Feed)
```

---

## ⚙️ **INSTALLATION**

### **1. Install Dependencies**
```bash
npm install express mongoose cors bcryptjs jsonwebtoken multer axios dotenv
```

### **2. Create .env File**
```env
MONGO_URI=mongodb://localhost:27017/instagram_clone
JWT_SECRET=your-super-secret-key
PORT=5000
BUNNY_STORAGE_ZONE=your-zone-name
BUNNY_API_KEY=your-api-key
BUNNY_PULL_ZONE=https://your-zone.b-cdn.net
```

### **3. Run Server**
```bash
node server.js
```
Visit: `http://localhost:5000`

---

## 🌐 **API ENDPOINTS**

### **Auth**
```
POST /auth/signup  - Register new user
POST /auth/login   - Login user
```

**Signup Body:**
```json
{
  "username": "johndoe",
  "email": "john@example.com",
  "password": "password123"
}
```

**Login Response:**
```json
{
  "token": "eyJhbGci...",
  "user": {
    "_id": "...",
    "username": "johndoe",
    "email": "john@example.com"
  }
}
```

### **Posts**
```
POST /post/upload      - Upload post (Auth required)
GET  /post/all?page=1  - Get global feed (Paginated)
GET  /post/user/:id    - Get specific user's posts
```

**Upload Headers:**
```
Authorization: YOUR_JWT_TOKEN
Content-Type: multipart/form-data
```

**Upload Form Data:**
- `file`: Image/Video file (required)
- `title`: Caption (optional)

---

## 📱 **PAGES & UI**

### **1. Login Page** (`/login.html`)
- Clean centered card
- Email & Password fields
- Redirects to Feed on success

### **2. Signup Page** (`/signup.html`)  
- Username, Email, Password
- Creates new account in MongoDB

### **3. Home Feed** (`/index.html`) ⭐ **MAIN PAGE**

**Desktop Layout:**
- **Left Sidebar:** Navigation (Home, Search, Explore, Reels, Messages, Notifications, Create, Profile).
- **Center Feed:** Stories Rail → Infinite Post Feed.
- **Right Sidebar:** Current User Switcher & "Suggestions For You".

**Mobile Layout:**
- **Top Header:** Logo & Message/Create icons.
- **Center Feed:** Stories → Posts.
- **Bottom Nav:** Home, Search, Create, Reels, Profile.

**Feed Features:**
- **Stories:** Horizontal scroll with gradient rings (Male avatars included).
- **Post Card:**
  - Header: User Avatar + Username + Options.
  - Media: Image (max-h-[500px]) or Video with Play controls.
  - Actions: Like (Heart), Comment, Share, Save.
  - Footer: Likes count, Caption, "View all comments", Timestamp.
  - Input: "Add a comment..." field.

---

## 🎯 **HOW TO USE**

### **For Users:**

**1. Register**
- Go to `/signup.html`
- Fill username, email, password
- Click Signup

**2. Login**
- Go to `/login.html`  
- Enter credentials
- Click Login → Redirected to Feed

**3. Upload Posts**
- Click **Create** (Sidebar) or **+** (Mobile Nav)
- Drag & Drop or Select File
- Add Caption
- Click **Share**

**4. Interact with Feed**
- **Double Click** image/video to Like ❤️
- **Click** Play button on videos ▶️
- **Click** Bookmark icon to Save 🔖
- **Scroll** down for Infinite Loading

**5. Logout**
- Click **More** → **Log Out** (Desktop)
- Or clear LocalStorage manually

---

## 🗄️ **DATABASE SCHEMAS**

### **User Model**
```javascript
{
  _id: ObjectId,
  username: String,       // Displayed in feed
  email: String,
  password: String,       // Hashed
  createdAt: Date
}
```

### **Post Model**
```javascript
{
  _id: ObjectId,
  title: String,          // Caption
  fileUrl: String,        // Bunny CDN URL
  type: String,           // "image" or "video"
  userId: ObjectId,       // Reference to User model
  createdAt: Date
}
```

---

## 🚀 **DEPLOYMENT**

### **Quick Deploy (Render/Railway)**
1. Push code to GitHub
2. Connect repo to Render/Railway
3. Set environment variables (`MONGO_URI`, `JWT_SECRET`, `BUNNY_*`)
4. Deploy! 🎉

### **VPS Deployment**
```bash
# Install PM2
npm install -g pm2

# Start Server
pm2 start server.js --name "instagram-clone"

# Save Process
pm2 save
```

---

## 🎨 **CUSTOMIZATION**

### **Change Theme Colors**
In `public/index.html`, Tailwind classes are used. You can customize colors by editing the Tailwind config script or adding custom CSS variables.

### **Adjust Image Height**
To change the max height of images in the feed:
```css
/* In index.html style block or tailwind class */
.max-h-[500px] /* Change to desired height */
```

---

## 🐛 **TROUBLESHOOTING**

| Problem | Solution |
|---------|----------|
| MongoDB connection error | Check `MONGO_URI` in `.env` |
| Upload fails (401/403) | Verify `BUNNY_API_KEY` and Storage Zone permissions |
| Images not showing | Check `BUNNY_PULL_ZONE` URL in `.env` |
| JWT Invalid | Clear LocalStorage and Login again |
| CORS Error | Ensure `cors()` middleware is enabled in `server.js` |

---

## 📊 **KEY FEATURES SUMMARY**

✅ **Professional Instagram 2021 UI/UX**  
✅ **Responsive Sidebar (Desktop) & Bottom Nav (Mobile)**  
✅ **Real-time Username Display from MongoDB**  
✅ **Optimized Image Sizing (Uniform Feed)**  
✅ **Male-Focused Stories Rail**  
✅ **Double-Tap to Like Animation**  
✅ **Video Play/Pause Controls**  
✅ **Infinite Scroll Pagination**  
✅ **Secure Auth & Bunny CDN Storage**  

---

<div align="center">

## ⭐ **Thanks for using this project!**

Made with ❤️ | Powered by Node.js + MongoDB + Bunny CDN

**Happy Coding! 🚀**

</div>
```