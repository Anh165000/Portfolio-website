# Portfolio Website - Phạm Duy Anh

A modern, responsive portfolio website built with Vue 3 and Vite. Features a sleek dark mode design with smooth animations, GitHub API integration for dynamic project display, and a responsive bento grid layout.

## ✨ Features

- **Modern Dark Mode Design** - Beautiful dark theme with gradient accents and smooth transitions
- **Bento Grid Layout** - Responsive grid system (4-col → 2-col → 1-col) that adapts to all screen sizes
- **GitHub API Integration** - Dynamically fetches and displays your GitHub repositories
- **Smooth Animations** - AOS (Animate On Scroll) for elegant scroll animations
- **Responsive Navigation** - Fixed navbar with smooth anchor scrolling to sections
- **Hardware Acceleration** - Optimized CSS with GPU acceleration for 60 FPS performance
- **Mobile Friendly** - Fully responsive design with touch-friendly interactions
- **Dark/Light Mode Ready** - CSS variables for easy theme customization
- **Performance Optimized** - Minimal dependencies, fast load times, optimized animations

## 🛠️ Technologies

- **Vue 3** - Modern progressive JavaScript framework
- **Vite** - Next-generation frontend build tool
- **CSS Grid** - Advanced layout system
- **AOS (Animate On Scroll)** - Scroll animation library
- **FontAwesome Icons** - Icon library
- **Google Fonts** - Plus Jakarta Sans font
- **GitHub API** - Dynamic repository fetching

## 📦 Installation

### Prerequisites

- Node.js (v16 or higher)
- npm or yarn

### Setup

1. **Clone the repository**

```bash
git clone https://github.com/anh1650000/portfolio-website.git
cd portfolio-website
```

2. **Install dependencies**

```bash
npm install
```

3. **Start development server**

```bash
npm run dev
```

The site will be available at `http://localhost:5173`

## 📝 Usage

### Development

```bash
npm run dev      # Start development server
npm run build    # Build for production
npm run preview  # Preview production build
```

### Structure

```
src/
├── components/          # Vue components
│   ├── Navbar.vue      # Navigation with smooth scrolling
│   ├── HeroCard.vue    # Hero section with intro
│   ├── TechStack.vue   # Technology skills display
│   ├── ProjectsGrid.vue # GitHub projects showcase
│   ├── ExperienceTimeline.vue # Work experience
│   ├── ContactCard.vue # Contact information
│   ├── AcademicStats.vue # Education/credentials
│   └── ChatbotPlaceholder.vue # Chatbot widget
├── views/
│   └── Portfolio.vue    # Main portfolio page
├── assets/
│   └── portfolio.css    # Global styles and layout
└── main.js             # Vue app entry point
```

## 🎨 Customization

### Colors

Edit CSS variables in `src/assets/portfolio.css`:

```css
:root {
    --primary-color: #a78bfa; /* Purple */
    --secondary-color: #60a5fa; /* Blue */
    --accent-color: #f97316; /* Orange */
    --dark-bg: #0a0e27; /* Dark background */
    --dark-card: #111829; /* Card background */
    --text-primary: #f1f5f9; /* Primary text */
    --text-secondary: #a0a0a0; /* Secondary text */
}
```

### Hero Section

Edit `src/components/HeroCard.vue` to customize your intro and add Typed.js text variations.

### Projects

`src/components/ProjectsGrid.vue` automatically fetches from GitHub API. To change:

- Update GitHub username in the API call
- Adjust number of repositories displayed

### Contact Information

Edit `src/components/ContactCard.vue` to update:

- Email address
- Phone number
- Social media links (LinkedIn, GitHub, Twitter, etc.)

### Tech Stack

Customize `src/components/TechStack.vue` to add/remove technologies and proficiency levels.

## 📊 Component Details

### Navbar

- Fixed position with glassmorphism effect
- Smooth scroll navigation to all sections
- Responsive mobile menu
- Active state indicators

### Hero Card

- Animated intro text with Typed.js
- Personal stats display
- Gradient text effects

### Projects Grid

- Dynamic GitHub repository fetching
- Responsive grid layout
- Repository stars, forks, and language display
- Direct links to repositories

### Experience Timeline

- Chronological work experience display
- Job title, company, and duration
- Responsive timeline design

### Tech Stack

- Technology proficiency levels (percentage display)
- Categorized by skill type
- Visual progress indicators

### Contact Card

- Copy-to-clipboard email functionality
- Social media links with hover effects
- Location information
- Availability status

## 🚀 Performance

- **60 FPS Scrolling** - Hardware-accelerated animations
- **Optimized CSS** - Minimal file size with GPU acceleration
- **Lazy Loading** - Components load efficiently
- **Mobile Optimized** - Disabled heavy animations on mobile
- **Fast Build** - Vite's instant HMR (Hot Module Replacement)

### Performance Features

- `will-change` and `transform: translateZ(0)` for GPU acceleration
- Reduced `backdrop-filter` blur (8px) for better performance
- Animations run once with `AOS` configuration
- Minimal repaints and reflows

## 📱 Responsive Breakpoints

- **Desktop** (1200px+) - Full 4-column grid
- **Tablet** (768px - 1199px) - 2-column grid
- **Mobile** (below 768px) - Single column, optimized navigation

## 🔧 Build & Deployment

### Build for Production

```bash
npm run build
```

This creates an optimized `dist/` folder ready for deployment.

### Deploy to Vercel (Recommended)

```bash
npm install -g vercel
vercel
```

### Deploy to Netlify

```bash
npm run build
# Drag and drop dist/ folder to Netlify
```

### Deploy to GitHub Pages

1. Update `vite.config.js` with your repo name
2. Run `npm run build`
3. Push the `dist/` folder to `gh-pages` branch

## 🔗 Links

- **Live Demo**: https://phmdanh.id.vn
- **GitHub**: https://github.com/anh1650000/
- **LinkedIn**:

## 📄 License

This project is open source and available under the MIT License.

## 👤 About

Created by **Phạm Duy Anh** - A passionate developer interested in building modern web experiences with Vue.js and web technologies.

---
