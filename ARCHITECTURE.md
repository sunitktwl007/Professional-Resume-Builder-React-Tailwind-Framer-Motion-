# 🏗️ Architecture Documentation

## Overview

This document provides a comprehensive overview of the Professional Resume Builder application architecture, design patterns, and component relationships.

## 🎯 Application Architecture

### High-Level Architecture

```
┌─────────────────────────────────────────────────────────┐
│                    React Application                    │
├─────────────────────────────────────────────────────────┤
│                      Header Component                   │
├─────────────────────────────────────────────────────────┤
│  Template Selector │  Resume Editor  │  Resume Preview  │
├─────────────────────────────────────────────────────────┤
│                  ResumeContext (State)                  │
├─────────────────────────────────────────────────────────┤
│  LocalStorage API │ PDF Export │ JSON Import/Export    │
└─────────────────────────────────────────────────────────┘
```

## 📁 Directory Structure

```
src/
├── components/              # React UI Components
│   ├── Header.jsx           # App header with controls
│   ├── Forms.jsx            # Main form components
│   ├── AdditionalForms.jsx  # Additional section forms
│   ├── ResumeEditor.jsx     # Editor container
│   ├── TemplateSelector.jsx # Template UI & Preview
│   └── index.js             # Exports
│
├── templates/               # Resume Templates
│   ├── TemplateCollection.jsx   # Modern, Minimal, Creative, Professional
│   ├── AdditionalTemplates.jsx  # Elegant, Corporate, ModernDark, Classic
│   ├── MoreTemplates.jsx        # Gradient, Minimalist, Accent, Geometric
│   └── index.js                 # Template management & export
│
├── context/                 # Global State Management
│   └── ResumeContext.jsx    # Resume data provider
│
├── hooks/                   # Custom React Hooks
│   └── useForm.js           # Form handling hooks
│
├── utils/                   # Utility Functions
│   └── helpers.js           # Export, validation, formatting
│
├── styles/
│   └── (styles in components with Tailwind)
│
├── App.jsx                  # Main application component
├── index.js                 # React entry point
└── index.css                # Global styles
```

## 🔄 Data Flow

### State Management with ResumeContext

```
User Action
    ↓
Component Event Handler
    ↓
updateResumeData() / updateTemplate()
    ↓
ResumeContext Updates State
    ↓
Components Re-render with New Data
    ↓
LocalStorage Auto-saves
    ↓
Preview Updates Instantly
```

### Component Data Flow

```
ResumeEditor
├─ PersonalInfoForm → updateResumeData('personal')
├─ ObjectiveSummaryForm → updateResumeData('objective'/'summary')
├─ EducationForm → updateResumeData('education')
├─ ExperienceForm → updateResumeData('experience')
├─ SkillsForm → updateResumeData('skills')
├─ ProjectsForm → updateResumeData('projects')
├─ CertificationsForm → updateResumeData('certifications')
├─ AchievementsForm → updateResumeData('achievements')
├─ LanguagesForm → updateResumeData('languages')
└─ ReferencesForm → updateResumeData('references')
         ↓
    ResumeContext
         ↓
    LivePreview Updates
```

## 🧩 Component Hierarchy

```
App
├── Header
│   ├── Resume Tabs
│   ├── Theme Toggle
│   └── Download Menu
├── Main Layout
│   ├── TemplateSelector (Left Sidebar)
│   │   └── Template Grid
│   ├── ResumeEditor (Center)
│   │   ├── PersonalInfoForm
│   │   ├── ObjectiveSummaryForm
│   │   ├── ExperienceForm
│   │   ├── EducationForm
│   │   ├── SkillsForm
│   │   ├── ProjectsForm
│   │   ├── CertificationsForm
│   │   ├── AchievementsForm
│   │   ├── LanguagesForm
│   │   └── ReferencesForm
│   └── ResumePreview (Right Sidebar)
│       └── Selected Template
└── Watermark
```

## 🔐 State Management Details

### ResumeContext Structure

```javascript
{
  resumes: [
    {
      id: 'uuid',
      name: 'My Resume',
      template: 'modern',
      data: {
        personal: { ... },
        objective: '',
        summary: '',
        education: [],
        experience: [],
        skills: [],
        projects: [],
        certifications: [],
        achievements: [],
        languages: [],
        references: []
      },
      createdAt: '2024-01-01...',
      updatedAt: '2024-01-01...'
    }
  ],
  currentResumeId: 'uuid',
  isDarkMode: boolean,
  
  // Methods
  createNewResume(),
  updateResumeData(),
  updateTemplate(),
  deleteResume(),
  renameResume(),
  exportResume(),
  importResume(),
  duplicateResume()
}
```

## 📊 Resume Data Schema

```javascript
{
  personal: {
    fullName: '',
    photo: null,              // Base64 image
    email: '',
    phone: '',
    address: '',
    city: '',
    state: '',
    country: '',
    zipCode: '',
    website: '',
    linkedin: '',
    github: ''
  },
  objective: '',
  summary: '',
  education: [
    {
      id: timestamp,
      institution: '',
      degree: '',
      field: '',
      startDate: 'YYYY-MM',
      endDate: 'YYYY-MM',
      description: ''
    }
  ],
  experience: [
    {
      id: timestamp,
      position: '',
      company: '',
      startDate: 'YYYY-MM',
      endDate: 'YYYY-MM',
      description: '',
      currentlyWorking: false
    }
  ],
  skills: [
    {
      id: timestamp,
      name: '',
      level: 1-5
    }
  ],
  projects: [
    {
      id: timestamp,
      title: '',
      description: '',
      technologies: '',
      link: '',
      startDate: 'YYYY-MM',
      endDate: 'YYYY-MM'
    }
  ],
  certifications: [
    {
      id: timestamp,
      name: '',
      issuer: '',
      issueDate: 'YYYY-MM',
      expiryDate: 'YYYY-MM',
      credentialId: '',
      credentialUrl: ''
    }
  ],
  achievements: [
    {
      id: timestamp,
      title: '',
      description: '',
      date: 'YYYY-MM'
    }
  ],
  languages: [
    {
      id: timestamp,
      name: '',
      level: 'Basic|Intermediate|Professional|Fluent|Native'
    }
  ],
  references: [
    {
      id: timestamp,
      name: '',
      title: '',
      company: '',
      email: '',
      phone: '',
      relationship: ''
    }
  ]
}
```

## 🎨 Template System

### Template Architecture

```
Templates
├── Modern (4 Templates)
│   ├── ModernTemplate
│   ├── MinimalTemplate
│   ├── CreativeTemplate
│   └── ProfessionalTemplate
├── Classic (4 Templates)
│   ├── ElegantTemplate
│   ├── CorporateTemplate
│   ├── ModernDarkTemplate
│   └── ClassicTemplate
├── Modern Variations (4 Templates)
│   ├── GradientTemplate
│   ├── MinimalistTemplate
│   ├── AccentTemplate
│   └── GeometricTemplate
└── Template Registry
    ├── ALL_TEMPLATES
    ├── ALL_TEMPLATE_NAMES
    ├── TEMPLATE_LIST
    └── Helper Functions
```

### Template Component Structure

```jsx
const TemplateComponent = ({ data }) => {
  // data structure:
  // {
  //   personal: {...},
  //   objective: '',
  //   education: [{...}],
  //   experience: [{...}],
  //   skills: [{...}],
  //   // ... etc
  // }
  
  return (
    <motion.div>
      {/* Template HTML/JSX */}
    </motion.div>
  );
};
```

## 🔌 Hooks & Custom Logic

### useFormInput Hook
Manages single form input state:
```javascript
const [value, bind, setValue, reset] = useFormInput(initialValue);
// value: current input value
// bind: { value, onChange }
// setValue: directly set value
// reset: reset to initial
```

### useFormValidation Hook
Manages complete form validation:
```javascript
const {
  values,
  errors,
  touched,
  isSubmitting,
  handleChange,
  handleBlur,
  handleSubmit,
  reset,
  setFieldValue
} = useFormValidation(initialState, onSubmit);
```

### useLocalStorage Hook
Manages localStorage data:
```javascript
const [storedValue, setValue] = useLocalStorage(key, initialValue);
```

## 🛠️ Utility Functions

### helpers.js Functions

```javascript
// PDF Export
exportAsPDF(resumeName)
  
// Validation
validateEmail(email)
validatePhone(phone)
validateURL(url)

// Formatting
formatDate(date)
getInitials(name)

// Conversion
imageToBase64(file)

// DOM Utilities
smoothScroll(elementId)

// Data Utilities
debounce(func, delay)
reorderArray(array, startIndex, endIndex)
downloadJSON(data, filename)
```

## 🎬 Animation & Effects

### Framer Motion Usage

```jsx
// Entry Animation
<motion.div
  initial={{ opacity: 0, y: 20 }}
  animate={{ opacity: 1, y: 0 }}
/>

// Hover Effects
<motion.button
  whileHover={{ scale: 1.05 }}
  whileTap={{ scale: 0.95 }}
/>

// Layout Animation
<motion.div layout>
  {/* Content */}
</motion.div>

// Presence Animation
<AnimatePresence>
  {showContent && <motion.div ... />}
</AnimatePresence>
```

## 🎨 Styling Architecture

### Tailwind CSS Approach

```javascript
// Utility-first CSS
className="px-4 py-2 bg-blue-500 text-white rounded-lg hover:bg-blue-600 transition"

// Dark mode support
className="bg-white dark:bg-gray-800 text-gray-900 dark:text-white"

// Responsive design
className="w-full md:w-1/2 lg:w-1/3"

// Custom animations
animation: 'fadeIn 0.6s ease-in-out'
```

### Global Styles (index.css)

- Glassmorphism effects
- Neumorphism effects
- Custom scrollbars
- Selection styles
- Print styles
- Watermark animation

## 📱 Responsive Design

### Breakpoints

```
Mobile:  < 640px (sm)
Tablet:  640px - 1024px (md-lg)
Desktop: > 1024px (xl)
```

### Layout Changes

```
Mobile:
- Single column (Editor only)
- Templates as dropdown
- Summary mode for preview

Tablet:
- Two columns (Editor + Editor)
- Templates sidebar hidden
- Templates in header

Desktop:
- Three columns (Templates | Editor | Preview)
- Full interface
- All features visible
```

## 🔄 Data Pipeline

### Create Resume Flow
```
User clicks "+ New" 
  ↓
createNewResume('Name')
  ↓
Generate UUID
  ↓
Create resume object with initialResumeData
  ↓
Add to resumes array
  ↓
Save to localStorage
  ↓
Switch to new resume
  ↓
Update preview
```

### Update Resume Flow
```
User types/clicks/uploads
  ↓
Form onChange handler
  ↓
updateResumeData(section, data)
  ↓
Update ResumeContext state
  ↓
Save to localStorage
  ↓
Component re-renders
  ↓
Preview updates automatically
```

### Export Resume Flow
```
User clicks export button
  ↓
Choose format (PDF/JSON)
  ↓
If PDF: html2pdf converts to PDF
  ↓
If JSON: stringify resume data
  ↓
Create Blob & download link
  ↓
Trigger browser download
  ↓
File saved to Downloads
```

### Import Resume Flow
```
User selects JSON file
  ↓
FileReader reads file
  ↓
Parse JSON
  ↓
Generate new UUID
  ↓
Add to resumes array
  ↓
Save to localStorage
  ↓
Show notification
  ↓
Switch to imported resume
```

## 🔐 Data Persistence

### LocalStorage Strategy

```javascript
// Key: 'resumes'
// Value: JSON string of all resumes array
// Updated: On every resume data change
// Loaded: On app initialization

const saved = localStorage.getItem('resumes');
const resumes = saved ? JSON.parse(saved) : [];

// Theme persistence
const theme = localStorage.getItem('theme');
const isDarkMode = theme === 'dark';
```

## 🚀 Performance Optimizations

### Code Splitting
- Templates loaded as needed
- Components lazy loaded
- Animations GPU accelerated

### State Optimization
- Only necessary data stored
- Efficient re-renders
- Memoized components

### UI Performance
- Debounced inputs
- Smooth animations
- Optimized scrolling

## 🧪 Testing Considerations

### Unit Tests
- Validate form inputs
- Test data persistence
- Test export/import

### Integration Tests
- Resume creation flow
- Template switching
- PDF export

### E2E Tests
- Complete workflow
- Multi-resume management
- Dark mode switching

## 🔍 Debugging

### Browser DevTools
```javascript
// Access ResumeContext
localStorage.getItem('resumes')

// Check theme
document.documentElement.getAttribute('data-theme')

// Monitor animations
Performance tab in DevTools
```

### Console Logging
```javascript
console.log('Resume data:', currentResume);
console.log('All resumes:', resumes);
console.log('DOM node:', document.getElementById('resume-preview'));
```

## 📈 Scalability Considerations

### For Growth
1. Add backend API layer
2. Implement database
3. Add user authentication
4. Cloud storage for files
5. Collaboration features
6. Advanced analytics

### Code Maintainability
- Modular component structure
- Clear naming conventions
- Separation of concerns
- Comprehensive documentation
- Consistent formatting

## 🎯 Key Design Decisions

### Why ResumeContext?
- Simple for this app size
- No external dependency
- Easy to migrate to Redux later
- Sufficient for feature set

### Why LocalStorage?
- Privacy-first approach
- No server required
- Instant data access
- Easy user data backup

### Why Tailwind CSS?
- Rapid development
- Consistent styling
- Easy customization
- Dark mode support built-in

### Why Framer Motion?
- Elegant animations
- Performance optimized
- Developer friendly
- Production ready

## 🔗 Dependencies Justification

```
React 18.2         → UI library (required)
React DOM 18.2     → DOM rendering (required)
Tailwind CSS 3.3   → Styling framework
Framer Motion      → Animations
html2pdf           → PDF export
UUID               → Unique IDs
Lucide React       → Icons
React Scripts      → Build tools
```

---

This architecture provides a solid foundation for a scalable, maintainable, and performant resume builder application.
