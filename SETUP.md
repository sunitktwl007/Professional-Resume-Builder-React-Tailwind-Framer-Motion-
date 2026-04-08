# 🚀 Setup Guide - Professional Resume Builder

This guide will walk you through installing and running the Professional Resume Builder application on your system.

## 📋 Prerequisites

Before you begin, ensure you have the following installed:

### 1. Node.js and npm
- **Download**: [nodejs.org](https://nodejs.org/)
- **Version Required**: Node.js 14.0.0 or higher
- **Verify Installation**:
  ```bash
  node --version
  npm --version
  ```

### 2. Git (Optional but Recommended)
- **Download**: [git-scm.com](https://git-scm.com/)
- **Verify Installation**:
  ```bash
  git --version
  ```

## 💻 Installation Steps

### Step 1: Navigate to Project Directory

Open your terminal/command prompt and navigate to the project folder:

```bash
cd "path/to/Professional CV maker ( resume )"
```

**Example for Windows:**
```bash
cd "C:\Users\YourUsername\Pictures\Professional CV maker ( resume )"
```

**Example for Mac/Linux:**
```bash
cd ~/Pictures/"Professional CV maker ( resume )"
```

### Step 2: Install Dependencies

Run the following command to install all required packages:

```bash
npm install
```

This will:
- Install React and React DOM
- Install Tailwind CSS and PostCSS
- Install Framer Motion for animations
- Install additional libraries (uuid, lucide-react, etc.)
- Create a `node_modules` folder

**Note**: First installation may take 2-5 minutes depending on your internet speed.

### Step 3: Start the Development Server

Once installation is complete, start the development server:

```bash
npm start
```

### Step 4: Access the Application

The application will automatically open in your default browser at:
```
http://localhost:3000
```

If it doesn't open automatically, manually go to `http://localhost:3000` in your browser.

## ✅ Verify Everything Works

1. You should see the Resume Builder interface
2. The app should load without errors in the browser console
3. You should be able to:
   - Type in the form fields
   - See live preview (on desktop)
   - Switch between templates
   - Toggle dark mode

## 🏗️ Available Scripts

### Development
```bash
npm start
```
- Runs the app in development mode
- Open [http://localhost:3000](http://localhost:3000) to view it in the browser
- The page will reload when you make changes
- Errors will be displayed in the console

### Build for Production
```bash
npm run build
```
- Builds the app for production to the `build` folder
- Correctly bundles React in production mode
- Optimizes the build for the best performance
- Ready to deploy

### Testing
```bash
npm test
```
- Displays interactive watch mode test runner

### Eject Configuration
```bash
npm run eject
```
- **⚠️ WARNING**: This is a one-way operation. Once you eject, you can't go back!
- Exposes all configuration files and dependencies

## 🐛 Troubleshooting

### Issue: Port 3000 Already in Use

**Solution 1**: Use a different port
```bash
PORT=3001 npm start
```

**Solution 2**: Kill the process using port 3000
- **Windows**: `netstat -ano | findstr :3000` then `taskkill /PID <PID> /F`
- **Mac/Linux**: `lsof -i :3000` then `kill -9 <PID>`

### Issue: npm install fails

**Solutions**:
```bash
# Clear npm cache
npm cache clean --force

# Try installing again
npm install

# If still failing, try deleting node_modules and package-lock.json
rm -rf node_modules package-lock.json
npm install
```

### Issue: "React is not defined" Error

**Solution**: Clear cache and reload
```bash
npm start
# Press CTRL+C to stop
# Delete node_modules folder
# Run: npm install
# Run: npm start again
```

### Issue: Tailwind Styles Not Applying

**Solution**: Rebuild Tailwind CSS
```bash
npm run build
# or restart with
npm start
```

### Issue: Dark Mode Not Working

**Solution**: 
- Clear browser cache
- Hard refresh: `Ctrl+Shift+Delete` (Windows) or `Cmd+Shift+Delete` (Mac)
- Clear localStorage: Open DevTools console and run:
  ```javascript
  localStorage.clear();
  location.reload();
  ```

### Issue: Cannot Find Module

**Solutions**:
```bash
# Reinstall dependencies
rm -rf node_modules
npm install

# Clear npm cache
npm cache clean --force
npm install
```

## 📦 Production Deployment

### Build the Project
```bash
npm run build
```

### Deploy to Hosting Services

#### Vercel (Recommended)
```bash
npm install -g vercel
vercel
```

#### Netlify
```bash
npm install -g netlify-cli
netlify deploy --prod --dir=build
```

#### GitHub Pages
1. Update `package.json`:
   ```json
   "homepage": "https://yourusername.github.io/resume-builder"
   ```
2. Install gh-pages:
   ```bash
   npm install --save-dev gh-pages
   ```
3. Add scripts to package.json:
   ```json
   "predeploy": "npm run build",
   "deploy": "gh-pages -d build"
   ```
4. Deploy:
   ```bash
   npm run deploy
   ```

## 🔧 Configuration

### Change Port
Edit or create `.env.local`:
```
PORT=3001
```

### Environment Variables
Create `.env.local` in project root:
```
REACT_APP_VERSION=1.0.0
REACT_APP_NAME=ResumeMaker
```

### Customize Tailwind Colors
Edit `tailwind.config.js`:
```js
theme: {
  extend: {
    colors: {
      primary: '#your-color',
    },
  },
}
```

## 📚 Project Structure Quick Reference

```
project/
├── public/          # Static files
├── src/
│   ├── components/  # React components
│   ├── templates/   # Resume templates
│   ├── context/     # Context API
│   ├── hooks/       # Custom hooks
│   ├── utils/       # Helper functions
│   ├── App.jsx      # Main component
│   └── index.js     # Entry point
├── package.json     # Dependencies
├── tailwind.config.js
├── postcss.config.js
└── README.md
```

## 🎯 Common Tasks

### Add a New Template
1. Create component in `src/templates/`
2. Export from `src/templates/index.js`
3. Add to TEMPLATE_LIST

### Add a New Form Section
1. Create component in `src/components/Forms.jsx`
2. Import in `ResumeEditor.jsx`
3. Add to sections array

### Modify Styling
- Update `src/index.css` for global styles
- Modify `tailwind.config.js` for theme
- Use Tailwind classes in JSX

### Add New Features
- Create new components in `src/components/`
- Add hooks if needed in `src/hooks/`
- Update context if needed in `src/context/`

## 📱 Testing on Different Devices

### Test Responsiveness
- Use Chrome DevTools (F12)
- Click device toolbar icon
- Select different device presets

### Test on Actual Mobile Device
1. Find your computer's IP:
   - Windows: `ipconfig` → IPv4 Address
   - Mac/Linux: `ifconfig` → inet

2. On mobile on same network:
   - Open: `http://<your-ip>:3000`

## ⚡ Performance Tips

- Disable browser extensions that modify CSS/JS
- Use Chrome DevTools to check performance
- Clear cache if experiencing slow builds
- Close unnecessary browser tabs
- Ensure adequate RAM (min 2GB free)

## 🔐 Security Notes

- Never commit sensitive data to git
- Use `.env` files for secrets
- Keep dependencies updated: `npm update`
- Check for vulnerabilities: `npm audit`

## 📞 Getting Help

### Check Errors
1. Open browser console (F12)
2. Look for red error messages
3. Search error message online

### Clear Everything
```bash
# Stop development server (Ctrl+C)
# Delete these folders:
rm -rf node_modules
rm package-lock.json

# Reinstall:
npm install

# Restart:
npm start
```

### Debug Mode
Add this to React components for logging:
```jsx
useEffect(() => {
  console.log('Component mounted', props);
}, [props]);
```

## 📖 Useful Resources

- [Node.js Docs](https://nodejs.org/docs/)
- [npm Documentation](https://docs.npmjs.com/)
- [Create React App Documentation](https://create-react-app.dev/)
- [Tailwind CSS Docs](https://tailwindcss.com/docs)
- [Framer Motion Docs](https://www.framer.com/motion/)

## ✨ Next Steps

1. ✅ Install and run the project
2. 📝 Create your first resume
3. 🎨 Explore different templates
4. 💾 Export your resume
5. 🌟 Share with others

---

**Congratulations! Your Resume Builder is now ready to use. Happy building! 🎉**

For more information, see `README.md`
