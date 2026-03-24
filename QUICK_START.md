# ⚡ ReviseAI - Quick Start (5 Minutes)

## Option 1: No Setup Needed (Instant Demo) ✨

```
1. Open reviseai_ultimate.html in your browser
2. Enter any text, YouTube link, or search topic
3. Click "Generate Study Pack"
4. Get instant notes, flashcards & summary
✓ Works immediately - No installation needed!
```

---

## Option 2: With AI Backend (Full Power) 🚀

### Step 1: Get Claude API Key (1 min)
```
1. Go to: https://console.anthropic.com
2. Click: Create new API key
3. Copy: The key (starts with sk-ant-)
4. Save it somewhere safe
```

### Step 2: Setup Backend (3 mins)

#### Windows:
```powershell
# Copy and paste these commands in PowerShell

# 1. Create folder
mkdir reviseai-backend
cd reviseai-backend

# 2. Initialize
npm init -y

# 3. Install dependencies
npm install express cors dotenv axios @anthropic-ai/sdk

# 4. Create .env file
echo 'CLAUDE_API_KEY=sk-ant-YOUR_KEY_HERE' > .env
echo 'PORT=5000' >> .env

# 5. Create server.js - copy code from BACKEND_SETUP_COMPLETE.js
# (Create new file, paste the code)

# 6. Start server
npm start
```

#### Mac/Linux:
```bash
# 1. Create folder
mkdir reviseai-backend && cd reviseai-backend

# 2. Initialize
npm init -y

# 3. Install
npm install express cors dotenv axios @anthropic-ai/sdk

# 4. Create .env
echo "CLAUDE_API_KEY=sk-ant-YOUR_KEY_HERE" > .env
echo "PORT=5000" >> .env

# 5. Create server.js and paste code

# 6. Start
npm start
```

### Step 3: Test It Works ✓
```bash
# In another terminal/command prompt:
curl http://localhost:5000/api/health

# You should see:
# {"status":"OK","service":"ReviseAI Backend"...}
```

### Step 4: Open Frontend
```
Open reviseai_ultimate.html in browser
It will automatically connect to your backend!
```

---

## 🎯 Using ReviseAI

### Text Input:
1. Paste any study material
2. Click "Generate Study Pack"
3. Get instant notes + flashcards

### YouTube:
1. Paste video URL
2. Click Generate
3. Get transcript-based notes

### Search Topic:
1. Enter topic (e.g., "Photosynthesis")
2. Click Generate
3. Get Wikipedia-sourced content

### File Upload:
1. Upload PDF or Document
2. Click Generate
3. Get AI-processed notes

---

## 🐛 Troubleshooting (Quick Fixes)

### "Backend not connecting"
```
1. Make sure backend is running (npm start)
2. Check port 5000 is free
3. Check API key in .env file is correct
```

### "API Key Invalid"
```
1. Go to https://console.anthropic.com
2. Generate new key
3. Copy EXACT key (no spaces)
4. Update .env file
5. Restart backend
```

### "Port already in use"
```
# Kill existing process:
# Windows:
netstat -ano | findstr :5000
taskkill /PID <number> /F

# Mac/Linux:
lsof -i :5000
kill -9 <PID>
```

---

## 📊 What's Included

✅ **reviseai_ultimate.html** - Beautiful frontend (ready to use)
✅ **BACKEND_SETUP_COMPLETE.js** - Full backend code
✅ **COMPLETE_SETUP_GUIDE.md** - Detailed guide
✅ **This file** - Quick start guide

---

## 🎓 Example Topics to Try

```
• Photosynthesis
• World War 2
• Calculus
• Quantum Physics
• Shakespeare
• French Revolution
• Biology
• History
```

---

## ✨ Features

🎨 Beautiful gradient UI  
📝 Detailed AI-generated notes  
🎴 Interactive flashcards  
⚡ Quick summaries  
📁 File upload support  
▶️ YouTube video support  
🔍 Topic search  
📱 Mobile responsive  

---

## 🚀 Next Steps

1. ✅ Open reviseai_ultimate.html
2. ✅ Test with some text
3. ✅ Setup backend for full features
4. ✅ Share with friends!

---

## 📞 Support

**Something not working?**
1. Check browser console (F12)
2. Check backend logs
3. See COMPLETE_SETUP_GUIDE.md for detailed help

---

**Enjoy! Happy Studying! 🎓**

