# 📄 Professional Resume Builder

A stunning, modern, and fully-featured Resume/CV builder web application built with React, Framer Motion, and Tailwind CSS.

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![React](https://img.shields.io/badge/react-18.2-61dafb.svg)
![Tailwind CSS](https://img.shields.io/badge/tailwind_css-3.3-38b2ac.svg)

## ✨ Features

### Core Features
- ✅ **Complete Resume Sections**
  - Personal Information with photo upload
  - Professional Objective / Summary
  - Education
  - Professional Experience
  - Skills with proficiency levels
  - Projects
  - Certifications
  - Achievements
  - Languages
  - References

- ✅ **Live Preview**
  - Real-time resume preview while editing
  - Instant template switching
  - Responsive design preview

- ✅ **Multiple Templates** (12+ Professional Styles)
  - Modern
  - Minimal
  - Creative
  - Professional
  - Elegant
  - Corporate
  - Modern Dark
  - Classic
  - Gradient
  - Minimalist
  - Accent
  - Geometric

- ✅ **Multi-Tasking**
  - Create and manage multiple resumes
  - Easy switching between resumes
  - Rename, duplicate, and delete resumes

### Export & Import
- 📄 **Download as PDF** - Professional PDF export
- 📋 **Export as JSON** - Save resume data to JSON
- 📥 **Import Resume** - Load previous resume data
- 💾 **Auto-save** - LocalStorage auto-save functionality

### UI/UX Features
- 🌓 **Dark Mode & Light Mode** - Theme toggle
- 🎨 **Modern Design**
  - Glassmorphism effects
  - Smooth animations & transitions
  - Responsive layout (mobile, tablet, desktop)
  - Professional color schemes

- ✨ **Animations & Effects**
  - Page transitions
  - Hover animations
  - Micro-interactions
  - Animated watermark footer

### User Experience
- 🖼️ **Profile Picture Upload** - Drag-and-drop or click to upload
- ✔️ **Form Validation** - Real-time input validation
- 📱 **Responsive Design** - Works on all devices
- 💡 **Intuitive Interface** - Easy-to-use forms
- 🔄 **Real-time Updates** - Instant preview updates

### Special Features
- 🎯 **Animated Watermark** - "Designed by Sunit Katuwal (BSc CSIT)"
- 🎨 **Custom Animations** - Fade, slide, and glow effects
- 💼 **Professional Quality** - Production-ready code
- 🗂️ **Organized Structure** - Modular and scalable codebase

## 🚀 Quick Start

### Prerequisites
- Node.js (v14 or higher)
- npm or yarn

### Installation

1. **Clone or navigate to the project:**
   ```bash
   cd "path/to/Professional CV maker (resume)"
   ```

2. **Install dependencies:**
   ```bash
   npm install
   ```

3. **Start the development server:**
   ```bash
   npm start
   ```

4. **Open in browser:**
   - The app will automatically open at `http://localhost:3000`

### Build for Production
```bash
npm run build
```

## 📁 Project Structure

```
project-root/
├── public/
│   ├── index.html
│
├── src/
│   ├── components/
│   │   ├── Header.jsx              # Header with resume management
│   │   ├── Forms.jsx               # Main form components
│   │   ├── AdditionalForms.jsx     # Additional section forms
│   │   ├── ResumeEditor.jsx        # Main editor component
│   │   └── TemplateSelector.jsx    # Template selector & preview
│   │
│   ├── templates/
│   │   ├── TemplateCollection.jsx  # Templates 1-4
│   │   ├── AdditionalTemplates.jsx # Templates 5-8
│   │   ├── MoreTemplates.jsx       # Templates 9-12
│   │   └── index.js                # Template management
│   │
│   ├── context/
│   │   └── ResumeContext.jsx       # Global state management
│   │
│   ├── hooks/
│   │   └── useForm.js              # Custom form hooks
│   │
│   ├── utils/
│   │   └── helpers.js              # Utility functions
│   │
│   ├── styles/
│   │
│   ├── App.jsx                     # Main app component
│   ├── index.js                    # React entry point
│   └── index.css                   # Global styles
│
├── package.json
├── tailwind.config.js
├── postcss.config.js
├── .gitignore
└── README.md
```

## 🎨 Template Categories

### Professional Templates
- **Modern** - Clean, contemporary design
- **Professional** - Executive-style resume
- **Corporate** - Business professional format
- **Elegant** - Luxury design with decorative elements

### Creative Templates
- **Creative** - Colorful, design-forward layout
- **Accent** - Bold color accents
- **Geometric** - Modern geometric shapes
- **Gradient** - Modern gradient effects

### Simple Templates
- **Minimal** - Simplistic, text-focused
- **Minimalist** - Ultra-clean design
- **Classic** - Traditional ATS-friendly format
- **Modern Dark** - Dark theme with a tech feel

## 🛠️ Technologies Used

### Frontend Framework
- **React 18.2** - UI library
- **React DOM** - DOM rendering

### Styling
- **Tailwind CSS 3.3** - Utility-first CSS
- **Framer Motion 10.16** - Animation library
- **Lucide React** - Icon library

### Export & Storage
- **html2pdf** - PDF export
- **jsPDF** - PDF generation
- **UUID** - Unique ID generation
- **LocalStorage API** - Data persistence

### Development
- **React Scripts** - Build tools
- **Create React App** - Project scaffolding

## 📝 Usage Guide

### Creating a Resume

1. **Start with Personal Information**
   - Upload profile photo
   - Enter basic details (name, email, phone, etc.)
   - Add professional links

2. **Fill in Sections**
   - Click on any section to expand/collapse
   - Add items using the "+ Add" buttons
   - Fill in required information
   - Add descriptions and details

3. **Choose Template**
   - Browse templates in the left sidebar
   - Click to switch templates instantly
   - See live preview on the right

4. **Export Resume**
   - Click Download button in header
   - Choose PDF or JSON format
   - Save to your device

### Managing Multiple Resumes

- **Create New** - Click "+ New" in the header
- **Switch** - Click resume tabs at the top
- **Rename** - Use the menu option
- **Duplicate** - Clone existing resume
- **Delete** - Remove unwanted resume

### Theme & Settings

- **Dark Mode** - Toggle moon icon in header
- **Auto-save** - Automatically saves to browser storage
- **Responsive** - Adapts to your screen size

## 🎯 Features Breakdown

### Form Validation
- Email format validation
- Phone number validation
- URL validation
- Real-time error checking

### Data Persistence
- Auto-save to localStorage
- Export/import functionality
- Multiple resume support
- Chrome DevTools inspection available

### Responsive Design
- **Desktop** (1200px+) - Three-column layout with preview
- **Tablet** (768px-1199px) - Two-column layout
- **Mobile** (below 768px) - Single column optimized

### Animations
- Page fade-in animations
- Smooth section expansions
- Hover effects on buttons
- Template switching transitions
- Watermark pulse animation

## 📊 Resume Sections

Each resume includes:
- **Personal** - Name, photo, contact details
- **Summary** - Objective and professional summary
- **Experience** - Work history with descriptions
- **Education** - Degrees and institutions
- **Skills** - Technical and soft skills with levels
- **Projects** - Portfolio projects with links
- **Certifications** - Professional certifications
- **Achievements** - Notable accomplishments
- **Languages** - Language proficiency levels
- **References** - Professional references

## 🔐 Data Storage

All resume data is stored locally in your browser:
- **localStorage** - Persists between sessions
- **No server upload** - Your data stays private
- **Export capability** - Easy data backup
- **Import support** - Restore from backup

## 🎨 Customization

### Adding New Templates
Edit `src/templates/index.js` and add your template component:

```jsx
// Add to templates file
export const CustomTemplate = ({ data }) => {
  // Your template component
};

// Add to export
export const ALL_TEMPLATES = {
  ...existing,
  custom: CustomTemplate,
};
```

### Changing Colors
Modify `tailwind.config.js`:
```js
theme: {
  extend: {
    colors: {
      primary: '#your-color',
    },
  },
}
```

### Modifying Sections
Edit form components in `src/components/`:
- Add/remove fields
- Change validation rules
- Update styling

## 📱 Browser Support

- ✅ Chrome/Edge (latest)
- ✅ Firefox (latest)
- ✅ Safari (latest)
- ⚠️ IE not supported

## ⚙️ Performance Optimizations

- Code splitting loaded components
- Memoized component rendering
- Efficient state management
- Optimized animations (GPU accelerated)
- LocalStorage for instant data loading

## 🐛 Troubleshooting

### Resume not saving
- Check if localStorage is enabled
- Clear cache and try again
- Check browser storage quota

### PDF export not working
- Ensure JavaScript is enabled
- Check popup blocker settings
- Try different PDF settings

### Templates not loading
- Refresh the page
- Check network connection
- Verify all files are present

## 🔒 Privacy & Security

- All data stored locally
- No data sent to servers
- No tracking or analytics
- Safe to use with sensitive info
- Can be used offline

## 📄 License

MIT License - See LICENSE file for details

## 👤 Creator

**Designed by Sunit Katuwal (BSc CSIT)**
- Professional Resume Builder
- Created with ❤️

## 🙏 Acknowledgments

- React team for the amazing framework
- Tailwind CSS team for utility CSS
- Framer Motion for smooth animations
- All contributors and users

## 📞 Support

For issues, suggestions, or feedback:
- Check the GitHub issues
- Review documentation
- Test in different browsers

## 🚀 Future Enhancements

- [ ] Cloud sync functionality
- [ ] More template options
- [ ] Collaboration features
- [ ] Mobile app version
- [ ] AI-powered content suggestions
- [ ] LinkedIn integration
- [ ] Video preview

## 💡 Tips for Best Results

1. **Professional Photo** - Use a high-quality headshot
2. **Clear Content** - Be concise and specific
3. **Consistent Formatting** - Use consistent date formats
4. **Proofread** - Check for spelling/grammar
5. **Keep Updated** - Maintain current resume version
6. **Export Regularly** - Backup your data frequently

---

**Happy Resume Building! 🎉**

*Make your resume shine with ResumeMaker - The Professional Resume Builder*
