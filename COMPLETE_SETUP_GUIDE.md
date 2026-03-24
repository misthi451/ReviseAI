# 🎓 ReviseAI - Complete Setup Guide 2024

## 📋 Table of Contents
1. [Quick Start](#quick-start)
2. [Frontend Setup](#frontend-setup)
3. [Backend Setup](#backend-setup)
4. [API Configuration](#api-configuration)
5. [Testing](#testing)
6. [Troubleshooting](#troubleshooting)
7. [Deployment](#deployment)

---

## 🚀 Quick Start (2 Minutes)

### Option A: Frontend Only (Demo Mode - No Backend Needed)
```bash
1. Download: reviseai_ultimate.html
2. Open in browser: Double-click the file OR right-click → Open with → Browser
3. Start studying immediately! ✨
```

### Option B: Full Setup (With AI Backend)
```bash
1. Install Node.js (if not installed)
2. Setup backend (see Backend Setup below)
3. Open reviseai_ultimate.html in browser
4. It automatically connects to your backend
```

---

## 💻 Frontend Setup

### What You Get:
✅ Beautiful modern UI with gradient backgrounds  
✅ 4 input methods: Text, YouTube, Search Topic, File Upload  
✅ 3 output types: Detailed Notes, Flashcards, Quick Summary  
✅ Smooth animations and responsive design  
✅ Works on desktop & mobile  

### Installation:
```bash
# No installation needed!
# Just open reviseai_ultimate.html in any modern browser
```

### Browser Requirements:
- Chrome 90+
- Firefox 88+
- Safari 14+
- Edge 90+

---

## 🔧 Backend Setup

### Prerequisites:
- Node.js 16+ ([Download](https://nodejs.org))
- Claude API Key ([Get here](https://console.anthropic.com))
- npm (comes with Node.js)

### Step-by-Step Setup:

#### Step 1: Create Project Folder
```bash
# Create and navigate to project folder
mkdir reviseai-backend
cd reviseai-backend
```

#### Step 2: Initialize Node Project
```bash
npm init -y
```

#### Step 3: Install Dependencies
```bash
npm install express cors dotenv axios @anthropic-ai/sdk
npm install -D nodemon  # For auto-reload during development
```

#### Step 4: Create .env File
```bash
# Windows (PowerShell):
echo 'CLAUDE_API_KEY=sk-ant-xxx' > .env
echo 'PORT=5000' >> .env

# Mac/Linux:
echo "CLAUDE_API_KEY=sk-ant-xxx" > .env
echo "PORT=5000" >> .env
```

Replace `sk-ant-xxx` with your actual Claude API key!

#### Step 5: Create server.js
Copy the code from `BACKEND_SETUP_COMPLETE.js` into a new file named `server.js`

#### Step 6: Update package.json
Add these scripts to your `package.json`:
```json
"scripts": {
  "start": "node server.js",
  "dev": "nodemon server.js"
}
```

#### Step 7: Start the Server
```bash
# For development (auto-reload):
npm run dev

# For production:
npm start
```

You should see:
```
╔════════════════════════════════════════╗
║        ReviseAI Backend Ready!         ║
╚════════════════════════════════════════╝

🚀 Server running on http://localhost:5000
```

---

## 🔑 API Configuration

### Getting Claude API Key:

1. **Visit Console**: https://console.anthropic.com
2. **Login** with your Anthropic account (or create one)
3. **Navigate to**: API Keys section
4. **Click**: "Create New API Key"
5. **Copy**: The API key starting with `sk-ant-`
6. **Paste into**: Your `.env` file

### Your API Keys Should Look Like:
```
CLAUDE_API_KEY=sk-ant-xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
PORT=5000
```

### Check API Key is Working:
```bash
# Test health endpoint
curl http://localhost:5000/api/health

# Expected response:
# {"status":"OK","service":"ReviseAI Backend","apiKey":"✓ Configured"}
```

---

## 🧪 Testing

### Test 1: Health Check
```bash
curl http://localhost:5000/api/health
```

Expected response:
```json
{
  "status": "OK",
  "service": "ReviseAI Backend",
  "version": "1.0.0",
  "apiKey": "✓ Configured"
}
```

### Test 2: Process Text
```bash
curl -X POST http://localhost:5000/api/process-text \
  -H "Content-Type: application/json" \
  -d '{"text": "Photosynthesis is the process by which plants convert light energy into chemical energy..."}'
```

### Test 3: Search Topic
```bash
curl -X POST http://localhost:5000/api/search \
  -H "Content-Type: application/json" \
  -d '{"topic": "Photosynthesis"}'
```

### Test in Frontend:
1. Open `reviseai_ultimate.html`
2. Enter some text or topic
3. Click "Generate Study Pack"
4. Watch the magic happen! ✨

---

## 🐛 Troubleshooting

### Problem 1: "Cannot find module 'express'"
```bash
# Solution:
npm install
npm install express cors dotenv axios @anthropic-ai/sdk
```

### Problem 2: "Error: listen EADDRINUSE: address already in use :::5000"
```bash
# Solution: Port is already in use. Change port in .env:
PORT=5001

# Or kill the process using port 5000:
# Mac/Linux:
lsof -i :5000
kill -9 <PID>

# Windows:
netstat -ano | findstr :5000
taskkill /PID <PID> /F
```

### Problem 3: "401 Unauthorized" / "Invalid API Key"
```bash
# Check your Claude API key:
1. Go to https://console.anthropic.com
2. Verify key is active and not revoked
3. Copy exact key (no spaces, no extra characters)
4. Paste in .env file exactly as:
   CLAUDE_API_KEY=sk-ant-xxxxxxx
5. Save file
6. Restart server (press Ctrl+C, then npm run dev)
```

### Problem 4: CORS Error in Browser
```bash
# Make sure these CORS settings are in server.js:
app.use(cors({
  origin: ['http://localhost:3000', 'http://localhost:5000', '*'],
  methods: ['GET', 'POST', 'OPTIONS'],
  credentials: true
}));
```

### Problem 5: Frontend Not Connecting to Backend
```bash
# Edit frontend (reviseai_ultimate.html)
# In the generatePack() function, change:
let endpoint = 'http://localhost:5000/api';

# To match your backend URL (if running on different port):
let endpoint = 'http://localhost:5001/api';  // if using port 5001
```

### Problem 6: YouTube Not Working
```bash
# Requires youtube-transcript-api
npm install youtube-transcript-api

# For Node.js, you may need to use alternative method:
# The current implementation uses fallback method
# For production, integrate youtube-transcript-api properly
```

---

## 🚀 Deployment

### Deploy to Heroku (Free):

1. **Create Heroku Account**: https://www.heroku.com
2. **Install Heroku CLI**: https://devcenter.heroku.com/articles/heroku-cli
3. **Login**: 
   ```bash
   heroku login
   ```
4. **Create app**:
   ```bash
   heroku create reviseai-backend
   ```
5. **Set environment variables**:
   ```bash
   heroku config:set CLAUDE_API_KEY=sk-ant-xxx
   heroku config:set NODE_ENV=production
   ```
6. **Deploy**:
   ```bash
   git push heroku main
   ```

### Deploy to Railway (Recommended):

1. **Signup**: https://railway.app
2. **Connect GitHub**: Link your repository
3. **Add Environment Variables**: 
   - `CLAUDE_API_KEY=sk-ant-xxx`
   - `PORT=5000`
4. **Deploy**: Push to GitHub, Railway auto-deploys

### Deploy to DigitalOcean:

1. **Create Droplet** with Node.js
2. **SSH into server**
3. **Clone your repository**
4. **Setup environment**
5. **Use PM2 for process management**:
   ```bash
   npm install -g pm2
   pm2 start server.js
   pm2 startup
   pm2 save
   ```

### Update Frontend for Production:
In `reviseai_ultimate.html`, update the API endpoint:
```javascript
// Change from:
let endpoint = 'http://localhost:5000/api';

// To:
let endpoint = 'https://your-backend-url/api';
// Example: https://reviseai-backend.railway.app/api
```

---

## 📊 API Endpoints

### 1. Process Text
**POST** `/api/process-text`

Request:
```json
{
  "text": "Your text content here..."
}
```

Response:
```json
{
  "success": true,
  "notes": "<h3>Title</h3><p>Notes...</p>",
  "flashcards": [
    {"q": "Question?", "a": "Answer"},
    {"q": "Q2?", "a": "A2"}
  ],
  "summary": "<h3>Summary</h3><p>Key points...</p>"
}
```

### 2. Process YouTube Video
**POST** `/api/youtube`

Request:
```json
{
  "url": "https://www.youtube.com/watch?v=dQw4w9WgXcQ"
}
```

Response:
```json
{
  "success": true,
  "videoId": "dQw4w9WgXcQ",
  "transcript": "Video transcript...",
  "notes": "...",
  "flashcards": [...],
  "summary": "..."
}
```

### 3. Search Topic
**POST** `/api/search`

Request:
```json
{
  "topic": "Photosynthesis"
}
```

Response:
```json
{
  "success": true,
  "topic": "Photosynthesis",
  "source": "Wikipedia API",
  "notes": "...",
  "flashcards": [...],
  "summary": "..."
}
```

### 4. Health Check
**GET** `/api/health`

Response:
```json
{
  "status": "OK",
  "service": "ReviseAI Backend",
  "version": "1.0.0",
  "timestamp": "2024-01-20T10:30:00Z",
  "apiKey": "✓ Configured"
}
```

---

## 🎯 Features Explained

### Input Methods:
- **📝 Text Input**: Paste lecture notes, articles, or any text
- **▶️ YouTube**: Link to educational videos for transcript extraction
- **🔍 Search**: Search topics (Wikipedia powered) for automatic content
- **📁 File Upload**: Upload PDF, DOC, DOCX, or TXT files

### Output Formats:
- **📖 Detailed Notes**: Comprehensive notes with key concepts highlighted
- **🎴 Flashcards**: Interactive flashcards (click to flip Q/A)
- **⚡ Quick Summary**: 5-point quick revision summary

---

## 💡 Pro Tips

### 1. Better Results:
- Use detailed, academic content
- Provide complete context (not fragments)
- Use good quality YouTube videos
- Be specific with search topics

### 2. Optimize API Usage:
- Batch similar requests together
- Cache popular topics
- Implement rate limiting to avoid API abuse

### 3. Frontend Customization:
- Change colors in CSS `:root` variables
- Modify sample text/flashcards
- Add your branding

### 4. Security:
- Never expose API key in frontend
- Use environment variables
- Enable CORS only for trusted origins
- Implement API rate limiting in production

---

## 📚 Sample Topics to Test:

```
✓ Photosynthesis
✓ French Revolution
✓ Calculus Integration
✓ World War 2
✓ Quantum Physics
✓ Mitochondria
✓ Shakespeare
✓ Photosynthesis
✓ Machine Learning
✓ DNA Replication
```

---

## 🆘 Need Help?

### Check These First:
1. **Browser Console**: Press F12 → Console tab for errors
2. **Backend Logs**: Watch terminal where you ran `npm run dev`
3. **Network Tab**: F12 → Network tab to see API requests
4. **Health Check**: `curl http://localhost:5000/api/health`

### Common Issues Checklist:
- [ ] API key is set in .env
- [ ] Backend is running (server.js started)
- [ ] Port 5000 is not blocked
- [ ] Frontend endpoint URL matches backend URL
- [ ] Browser is up-to-date
- [ ] Internet connection is working

---

## 🎓 Next Steps:

1. ✅ Get Claude API key
2. ✅ Setup backend (Node.js + Express)
3. ✅ Open frontend HTML file
4. ✅ Test with sample content
5. ✅ Customize and deploy

---

## 📝 Version Information

- **ReviseAI Version**: 2.0
- **Created**: January 2024
- **Backend**: Node.js + Express
- **AI**: Claude API (Anthropic)
- **Frontend**: HTML5 + CSS3 + JavaScript

---

## 📄 License

Free to use, modify, and distribute for educational purposes.

---

**Happy Studying! 🚀**

For updates and more features, check the GitHub repository.

Need a feature? Found a bug? Create an issue or pull request!

