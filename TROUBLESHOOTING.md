# 🔧 Troubleshooting Guide

Comprehensive troubleshooting guide for common issues in the Professional Resume Builder.

---

## Installation & Setup Issues

### Issue: npm install fails

**Symptoms:**
- Installation stops with error messages
- Dependencies not fully installed
- node_modules folder incomplete

**Solutions:**

```bash
# Solution 1: Clear npm cache and reinstall
npm cache clean --force
npm install

# Solution 2: Use different npm registry
npm config set registry https://registry.npmjs.org/
npm install

# Solution 3: Delete and reinstall
rm -rf node_modules package-lock.json
npm install

# Solution 4: Use specific npm version
npm install -g npm@latest
npm install

# Solution 5: Check if Node.js is properly installed
node --version
npm --version
```

**Prevention:**
- Keep Node.js up to date
- Use LTS (Long Term Support) version
- Check internet connection
- Ensure sufficient disk space

---

### Issue: Port 3000 is already in use

**Symptoms:**
- Error: "Port 3000 is already in use"
- Application won't start
- Different port needed

**Solutions:**

```bash
# Solution 1: Use different port
PORT=3001 npm start

# Solution 2: Kill process on port 3000 (Windows)
netstat -ano | findstr :3000
taskkill /PID <PID_NUMBER> /F

# Solution 3: Kill process on port 3000 (Mac/Linux)
lsof -i :3000
kill -9 <PID_NUMBER>

# Solution 4: Find and close other app using 3000
# Check if another instance is running
# Close it manually or restart computer
```

**Prevention:**
- Close other Node.js applications
- Use different ports for different projects
- Check package.json for port configuration

---

### Issue: "Node command not found" error

**Symptoms:**
- Terminal says "node" is not recognized
- npm fails to work
- Cannot run npm commands

**Solutions:**

1. **Reinstall Node.js**
   - Visit [nodejs.org](https://nodejs.org)
   - Download LTS version
   - Run installer
   - Follow installation wizard
   - Restart terminal/computer

2. **Add Node to PATH (Windows)**
   - Right-click "This PC" → Properties
   - Advanced system settings
   - Environment Variables
   - Add Node.js installation path to PATH

3. **Verify Installation**
   ```bash
   node --version
   npm --version
   ```

---

## Application Runtime Issues

### Issue: Application won't start (npm start fails)

**Symptoms:**
- Errors when running `npm start`
- Webpack compilation fails
- Port 3000 shows blank page

**Solutions:**

```bash
# Solution 1: Clear cache and restart
npm cache clean --force
npm start

# Solution 2: Delete node_modules and reinstall
rm -rf node_modules
npm install
npm start

# Solution 3: Kill old processes
# Close terminal with Ctrl+C
# Wait 5 seconds
npm start

# Solution 4: Check for syntax errors
npm test

# Solution 5: Use verbose mode to debug
npm start -- --verbose
```

---

### Issue: Page shows "Cannot find module" error

**Symptoms:**
- Console error: "Cannot find module 'react'"
- White screen with error
- Compilation fails

**Solutions:**

```bash
# Solution 1: Reinstall all dependencies
rm -rf node_modules
npm install

# Solution 2: Install missing package
npm install react react-dom

# Solution 3: Clear cache
npm cache clean --force
npm install

# Solution 4: Check for typos in imports
# Review component import paths
# Ensure file names match exactly
```

---

### Issue: Application loads but is blank or broken

**Symptoms:**
- Page loads but shows nothing
- Components not rendering
- Errors in console

**Solutions:**

1. **Clear Browser Cache**
   - Windows: `Ctrl+Shift+Delete`
   - Mac: `Cmd+Shift+Delete`
   - Select "All time"
   - Clear cache and cookies

2. **Hard Refresh**
   - Windows: `Ctrl+F5`
   - Mac: `Cmd+Shift+R`

3. **Check Console for Errors**
   - Open DevTools (F12)
   - Go to Console tab
   - Look for red error messages
   - Search for solutions

4. **Restart Development Server**
   - Stop: `Ctrl+C` in terminal
   - Wait 3 seconds
   - Run: `npm start`

---

## Data & Storage Issues

### Issue: Resume data not saving

**Symptoms:**
- Changes don't persist
- Data lost on refresh
- localStorage not working

**Solutions:**

```bash
# Solution 1: Check if localStorage is enabled
# In browser console:
localStorage.setItem('test', 'value');
localStorage.getItem('test');

# Solution 2: Check storage quota
# In console:
navigator.storage.estimate().then(estimate => {
  console.log(estimate.usage / estimate.quota);
});

# Solution 3: Clear localStorage and start fresh
localStorage.clear();
location.reload();

# Solution 4: Check browser privacy settings
# Ensure localStorage is not disabled
# Check private/incognito mode isn't on
```

**Browser Settings:**
- **Chrome**: Settings > Privacy > Clear data
- **Firefox**: Preferences > Privacy > Cookies
- **Safari**: Preferences > Privacy

---

### Issue: Cannot import/export resume

**Symptoms:**
- Import button doesn't work
- PDF export fails
- JSON export doesn't download

**Solutions:**

**For Import:**
```bash
# Ensure file is valid JSON
# Use file exported from this app
# Check file extension is .json
# Try smaller file first
```

**For Export:**
- Check popup blocker is disabled
- Use different browser
- Check file download folder
- Try exporting to different location

**Debug Steps:**
1. Open DevTools (F12)
2. Check Console tab for errors
3. Check Network tab for failures
4. Try different browsers

---

### Issue: Dark mode not working

**Symptoms:**
- Dark mode toggle doesn't work
- Theme doesn't persist
- Wrong colors showing

**Solutions:**

```bash
# Solution 1: Clear theme setting
localStorage.removeItem('theme');
location.reload();

# Solution 2: Check HTML element class
# In console:
document.documentElement.classList

# Solution 3: Force reload
location.reload(true);

# Solution 4: Check if CSS loads
# Open DevTools > Styles tab
# Look for dark mode styles

# Solution 5: Clear browser cache
# Ctrl+Shift+Delete (Windows)
# Cmd+Shift+Delete (Mac)
```

---

## Template & Preview Issues

### Issue: Templates not showing/loading

**Symptoms:**
- Template selector is empty
- Preview shows nothing
- Can't switch templates

**Solutions:**

```bash
# Solution 1: Verify templates loaded
# In console:
import { ALL_TEMPLATES } from './templates'
console.log(ALL_TEMPLATES);

# Solution 2: Check if template exists
# Ensure template name is correct
# Check src/templates/index.js

# Solution 3: Restart development server
npm start
```

---

### Issue: Incorrect template rendering

**Symptoms:**
- Template shows wrong data
- Layout looks broken
- Styles not applied

**Solutions:**

1. **Check data structure**
   ```bash
   # In console:
   localStorage.getItem('resumes')
   ```

2. **Verify template component**
   - Check if receiving correct props
   - Ensure data mapping is correct
   - Check for missing data validation

3. **Clear and reload**
   - Close DevTools
   - Refresh page (Ctrl+R)
   - Try different template

---

### Issue: PDF export looks wrong

**Symptoms:**
- PDF missing content
- Wrong formatting in PDF
- Colors don't match

**Solutions:**

1. **Check browser rendering**
   - View page in browser first
   - Verify it looks correct
   - Then export to PDF

2. **Try different export options**
   - Adjust print margins
   - Try different paper size
   - Use different browser

3. **Refresh and retry**
   - Hard refresh (Ctrl+F5)
   - Export again
   - Check download folder

---

## Performance Issues

### Issue: Application is slow/laggy

**Symptoms:**
- Page responds slowly to input
- Animations are jerky
- Typing feels delayed

**Solutions:**

```bash
# Solution 1: Check system resources
# Close other applications
# Free up RAM
# Close other browser tabs

# Solution 2: Disable extensions
# Disable browser extensions
# Try incognito/private mode
# Try different browser

# Solution 3: Clear cache
npm cache clean --force
npm start

# Solution 4: Check for memory leaks
# Open DevTools > Memory tab
# Take heap snapshot
# Look for growing memory usage
```

**Performance Tips:**
- Keep browser updated
- Close unnecessary tabs
- Disable extensions
- Use performance mode in DevTools

---

### Issue: High CPU usage / Fan running loud

**Symptoms:**
- Computer gets hot
- Fan running loudly
- CPU usage very high

**Solutions:**

```bash
# Solution 1: Restart development server
# Stop: Ctrl+C
# Wait 3 seconds
npm start

# Solution 2: Kill background processes
# Check Task Manager (Windows)
# Close unnecessary processes

# Solution 3: Rebuild application
npm run build
# Serve the build folder instead
```

---

## Browser-Specific Issues

### Chrome Issues

**Blank page:**
```javascript
// In console:
console.clear();
location.reload();
```

**Extensions causing issues:**
- Disable all extensions
- Test in Incognito mode
- Enable extensions one by one

### Firefox Issues

**Styles not loading:**
- Clear cache (Ctrl+Shift+Delete)
- Disable hardware acceleration (Preferences > Performance)

### Safari Issues

**LocalStorage not working:**
- Check Preferences > Privacy
- Allow local storage
- Disable "Prevent cross-site tracking" for localhost

---

## Development & Debugging

### Issue: Cannot debug code

**Symptoms:**
- Breakpoints don't work
- Can't inspect elements
- Can't view source code

**Solutions:**

1. **Open DevTools**
   - Windows/Linux: F12 or Ctrl+Shift+I
   - Mac: Cmd+Option+I

2. **Set Breakpoints**
   - Click line number in Sources tab
   - Breakpoint appears as blue dot
   - Refresh page to trigger

3. **Use Console Logging**
   ```javascript
   console.log('Variable:', variable);
   console.error('Error:', error);
   console.warn('Warning:', warning);
   ```

4. **React DevTools Extension**
   - Install React DevTools extension
   - Inspect component tree
   - Check props and state

---

### Issue: Component not re-rendering

**Symptoms:**
- Changes don't appear in UI
- State updates don't trigger render
- Data changes but display stays same

**Solutions:**

```javascript
// Check if state is actually changing
console.log('Current state:', currentState);

// Ensure state updates are immutable
// Wrong:
state.array.push(item);
// Right:
setState([...state, item]);

// Check component dependencies
useEffect(() => {
  console.log('Effect running');
}, [dependencies]); // Ensure dependencies are included
```

---

## File & Folder Issues

### Issue: Files not found

**Symptoms:**
- "File not found" errors
- Import errors
- Missing components

**Solutions:**

1. **Check file path**
   - Verify path is correct
   - Check capitalization (case-sensitive on Mac/Linux)
   - Ensure file exists

2. **Verify file structure**
   ```bash
   ls -la src/components/  # Mac/Linux
   dir src\components      # Windows
   ```

3. **Rebuild and restart**
   ```bash
   rm -rf node_modules
   npm install
   npm start
   ```

---

## Git & Version Control Issues

### Issue: Git commands not working

**Symptoms:**
- "git" command not found
- Git operations fail
- Cannot commit changes

**Solutions:**

1. **Install Git**
   - Visit [git-scm.com](https://git-scm.com)
   - Download and install
   - Add to PATH

2. **Configure Git**
   ```bash
   git config --global user.name "Your Name"
   git config --global user.email "your@email.com"
   ```

3. **Verify Installation**
   ```bash
   git --version
   ```

---

## Environment & Configuration

### Issue: Environment variables not loading

**Symptoms:**
- `process.env.REACT_APP_*` is undefined
- Configuration not working
- Features based on env vars don't work

**Solutions:**

1. **Create .env.local file**
   ```bash
   # Copy .env.example to .env.local
   cp .env.example .env.local
   
   # Edit .env.local with your values
   ```

2. **Restart development server**
   ```bash
   npm start
   ```

3. **Check variable naming**
   - Must start with `REACT_APP_`
   - Use uppercase
   - No spaces around equals

---

## Common Error Messages

### "Module parse failed"
```
Solution: Syntax error in file
- Check for missing semicolons
- Look for syntax errors
- Check import statements
```

### "Cannot read property 'X' of undefined"
```
Solution: Trying to access property of undefined
- Check if object exists first
- Use optional chaining (?.
- Check data structure
```

### "Line X: Unexpected token"
```
Solution: Syntax error in code
- Check for missing commas
- Verify brackets are balanced
- Check quotes are matched
```

### "Failed to compile"
```
Solution: Build failed
- Check console for specific error
- Fix syntax errors
- Restart development server
```

---

## Getting Additional Help

### Steps to Troubleshoot

1. **Read the error message carefully**
   - Look for file names and line numbers
   - Search for the exact error online

2. **Check documentation**
   - README.md
   - SETUP.md
   - ARCHITECTURE.md

3. **Google the error**
   - Often others have same issue
   - Stack Overflow has solutions

4. **Check browser console**
   - Right-click → Inspect → Console
   - Look for red error messages
   - Copy and search

5. **Try in different browser**
   - Test in Chrome, Firefox, Safari
   - Issues may be browser-specific

6. **Start fresh if needed**
   ```bash
   # Backup your resume data first!
   rm -rf node_modules
   rm package-lock.json
   npm install
   npm start
   ```

---

## Prevention Tips

1. **Keep everything updated**
   ```bash
   npm update
   node --version
   npm --version
   ```

2. **Use version control**
   ```bash
   git add .
   git commit -m "meaningful message"
   ```

3. **Test regularly**
   - Use different browsers
   - Test on mobile
   - Test export features

4. **Back up your data**
   - Export resumes as JSON
   - Save backups offline
   - Use multiple storage methods

5. **Follow best practices**
   - Use recommended settings
   - Keep code clean
   - Document changes

---

## Still Having Issues?

### Debug Checklist

✓ Restart development server  
✓ Clear browser cache  
✓ Check console for errors  
✓ Read error message carefully  
✓ Google the error message  
✓ Check documentation files  
✓ Try different browser  
✓ Reinstall node_modules  
✓ Check internet connection  
✓ Restart computer  

### Information to Provide When Asking for Help

- Node.js version: `node --version`
- npm version: `npm --version`
- Operating system: Windows/Mac/Linux
- Browser and version
- Exact error message
- Steps to reproduce
- Screenshot if applicable

---

**Remember: Most issues have simple solutions. Take a moment to read error messages carefully and check the documentation first!** 

For more information, see README.md, SETUP.md, or ARCHITECTURE.md
