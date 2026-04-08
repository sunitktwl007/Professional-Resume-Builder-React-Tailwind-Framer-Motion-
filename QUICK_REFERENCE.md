# 📚 Quick Reference Guide

A quick lookup guide for the Professional Resume Builder.

## File Structure Quick Reference

```
├─ 📄 README.md              - Main documentation
├─ 🚀 SETUP.md              - Installation guide
├─ 🏗️ ARCHITECTURE.md       - Technical architecture
├─ ✨ FEATURES.md           - Complete feature guide
├─ 💡 QUICK_REFERENCE.md    - This file
├─ 📦 package.json          - Dependencies
├─ 🎨 tailwind.config.js    - Tailwind config
├─ 📍 postcss.config.js     - PostCSS config
├─ .gitignore              - Git ignore rules
└─ src/
   ├─ App.jsx              - Main component
   ├─ index.js             - Entry point
   ├─ index.css            - Global styles
   ├─ components/          - React components
   ├─ templates/           - Resume templates
   ├─ context/             - State management
   ├─ hooks/               - Custom hooks
   └─ utils/               - Helper functions
```

## Installation Quick Start

```bash
# 1. Navigate to project
cd "path/to/Professional CV maker ( resume )"

# 2. Install dependencies
npm install

# 3. Start development server
npm start

# 4. Open browser
http://localhost:3000
```

## Component Quick Reference

### Key Components

| Component | Purpose | Location |
|-----------|---------|----------|
| `App.jsx` | Main layout | `src/` |
| `Header` | Top navigation | `src/components/Header.jsx` |
| `ResumeEditor` | Form editor | `src/components/ResumeEditor.jsx` |
| `TemplateSelector` | Template UI | `src/components/TemplateSelector.jsx` |
| `ResumePreview` | Live preview | `src/components/TemplateSelector.jsx` |

### Form Components

```
Forms.jsx
├─ PersonalInfoForm
├─ ObjectiveSummaryForm
├─ EducationForm
├─ ExperienceForm
├─ SkillsForm
├─ ProjectsForm
└─ FormInput, FormTextarea, FormCard

AdditionalForms.jsx
├─ CertificationsForm
├─ AchievementsForm
├─ LanguagesForm
└─ ReferencesForm
```

### Template Components

```
TemplateCollection.jsx
├─ ModernTemplate (Modern)
├─ MinimalTemplate (Minimal)
├─ CreativeTemplate (Creative)
└─ ProfessionalTemplate (Professional)

AdditionalTemplates.jsx
├─ ElegantTemplate (Elegant)
├─ CorporateTemplate (Corporate)
├─ ModernDarkTemplate (ModernDark)
└─ ClassicTemplate (Classic)

MoreTemplates.jsx
├─ GradientTemplate (Gradient)
├─ MinimalistTemplate (Minimalist)
├─ AccentTemplate (Accent)
└─ GeometricTemplate (Geometric)
```

## State Management

### ResumeContext

```javascript
// Access context
const {
  resumes,              // Array of all resumes
  currentResumeId,      // Current resume ID
  currentResume,        // Current resume data
  isDarkMode,           // Theme
  createNewResume,
  updateResumeData,
  updateTemplate,
  deleteResume,
  renameResume,
  exportResume,
  importResume,
  duplicateResume
} = useResume();

// Update resume data
updateResumeData('personal', { fullName: 'John' });

// Update template
updateTemplate('modern');
```

## Hooks Quick Reference

### useFormInput
```javascript
const [value, bind, setValue, reset] = useFormInput('default');
// Returns: [currentValue, bindProps, setter, resetter]
```

### useFormValidation
```javascript
const {
  values,
  errors,
  touched,
  handleChange,
  handleBlur,
  handleSubmit,
  reset
} = useFormValidation(initialState, onSubmit);
```

### useLocalStorage
```javascript
const [stored, setStored] = useLocalStorage('key', initialValue);
```

## Utility Functions

### Export & Import
```javascript
importResume(file)      // Import JSON file
exportResume(id)        // Export resume as JSON
exportAsPDF(name)       // Export as PDF
```

### Validation
```javascript
validateEmail(email)    // Check email format
validatePhone(phone)    // Check phone format
validateURL(url)        // Check URL format
```

### Formatting
```javascript
formatDate(date)        // Format date
getInitials(name)       // Get name initials
imageToBase64(file)     // Convert image to base64
```

### Other
```javascript
debounce(func, delay)                    // Debounce function
reorderArray(arr, from, to)              // Reorder array
smoothScroll(elementId)                  // Smooth scroll
downloadJSON(data, filename)             // Download JSON
```

## Common Tasks

### Add New Form Field

1. Add to schema (ResumeContext.jsx)
2. Create FormInput component (Forms.jsx)
3. Connect to form handler
4. Add to template rendering

### Create New Template

1. Create component in `templates/`
2. Export from `templates/index.js`
3. Add to ALL_TEMPLATES
4. Add to TEMPLATE_LIST

### Modify Styling

1. Edit `tailwind.config.js` for theme
2. Use utility classes in components
3. Update `index.css` for global styles
4. Use Tailwind dark mode prefix

### Add Validation

1. Create validation function in `utils/helpers.js`
2. Call in form onChange handler
3. Show error message from errors state
4. Highlight invalid field

## Keyboard Shortcuts

| Key | Action |
|-----|--------|
| `Tab` | Next field |
| `Shift+Tab` | Previous field |
| `Enter` | Form submit |
| `Escape` | Close modal |

## npm Commands

```bash
npm start              # Development server
npm run build          # Production build
npm test               # Run tests
npm run eject          # Eject configuration
npm install <pkg>     # Install package
npm uninstall <pkg>   # Remove package
npm update            # Update packages
npm audit             # Check vulnerabilities
```

## Git Commands

```bash
git init              # Initialize repo
git add .             # Stage all changes
git commit -m "msg"   # Commit changes
git push              # Push to remote
git pull              # Pull from remote
git branch            # List branches
git checkout -b name  # Create branch
```

## Browser DevTools

### Check Data
```javascript
// In console:
localStorage.getItem('resumes')
JSON.parse(localStorage.getItem('resumes'))
```

### Monitor Theme
```javascript
document.documentElement.getAttribute('data-theme')
document.documentElement.classList
```

### Clear Everything
```javascript
localStorage.clear()
sessionStorage.clear()
location.reload()
```

## Tailwind Classes Quick Reference

### Colors
```
bg-blue-500  text-gray-900  border-red-400
bg-white     text-white     bg-opacity-50
dark:bg-gray-800    dark:text-white
```

### Layout
```
flex  grid  w-full  h-screen  p-4  m-2
gap-4  space-y-2  justify-between  items-center
```

### Responsive
```
hidden  md:flex  lg:grid  xl:block
w-full  md:w-1/2  lg:w-1/3  xl:w-1/4
```

### Effects
```
rounded-lg  shadow-lg  hover:shadow-xl
transition  opacity-50  blur-sm  scale-110
```

## Debugging Tips

### Issue: Resume not showing
- Check console for errors
- Verify localStorage has data
- Reload page
- Check if template exists

### Issue: PDF export not working
- Enable JavaScript
- Check popup blocker
- Try different browser
- Verify DOM element #resume-preview exists

### Issue: Styles not applying
- Clear cache (Ctrl+Shift+Delete)
- Hard reload (Ctrl+F5)
- Restart dev server
- Check dark mode setting

### Issue: Form not updating
- Check console for errors
- Verify context is connected
- Ensure correct field names
- Check onChange handler

## Performance Tips

- Use React DevTools for debugging
- Monitor in Performance tab
- Check Network tab for slow loads
- Use Chrome Lighthouse
- Test on real devices

## Resources

- [React Docs](https://react.dev)
- [Tailwind CSS](https://tailwindcss.com)
- [Framer Motion](https://www.framer.com/motion)
- [MDN Web Docs](https://developer.mozilla.org)
- [Stack Overflow](https://stackoverflow.com)

## Important Files

| File | Purpose |
|------|---------|
| `package.json` | Dependencies & scripts |
| `src/index.js` | React entry point |
| `src/App.jsx` | Main component |
| `tailwind.config.js` | Theme configuration |
| `src/context/ResumeContext.jsx` | Global state |
| `public/index.html` | HTML template |

## Contact & Support

- **GitHub**: Create an issue
- **Email**: Contact author
- **Documentation**: See README.md, ARCHITECTURE.md, FEATURES.md
- **Questions**: Check Q&A sections

---

**Last Updated**: January 2024

For detailed information, see:
- 📄 README.md - Main documentation
- 🚀 SETUP.md - Installation guide
- 🏗️ ARCHITECTURE.md - Technical details
- ✨ FEATURES.md - Feature documentation
