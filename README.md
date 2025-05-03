# Sport Wales Project Template (SWPT)

Welcome to the Sport Wales Project Template - a comprehensive foundation for building React applications that align with Sport Wales' design system and development standards. This template combines Vite, React, Tailwind CSS, and our custom component library to help you build consistent, high-quality applications.

## Getting Started

### Prerequisites
Before you begin, ensure you have the following installed:
- Node.js (version 18 or higher)
- npm (comes with Node.js)
- Git for version control
- A code editor (we recommend VS Code)

### Setting Up Your Project Repository

First, clone the SWPT repository to your local machine:

```bash
git clone https://github.com/Sport-Wales/sport-wales-project-template
```

When you clone the SWPT, you'll need to disconnect it from the template repository and connect it to your new project repository. This process ensures your project starts with a clean Git history while maintaining all the template files to start your new project. Here's how to do it:

1. First, navigate to your project directory that holds your project files. In your terminal, PowerShell or Command Prompt:

```bash
cd "C:\Users\YourUsername\Path\To\Your\Project-Name\sport-wales-project-template"
```

2. Remove the existing remote repository connections by executing the following commands:
```bash
# Remove remote repository references
Remove-Item -Path ".git/refs/remotes/origin" -Recurse -Force
Remove-Item -Path ".git/logs/refs/remotes/origin" -Recurse -Force
git remote remove origin
```

3. You now need to go to github and create a new repository for your project. Once you have done that, add your new repository as the origin:
```bash
# Replace the URL with your project's repository URL
git remote add origin https://github.com/Sport-Wales/Your-Project-Name.git
```

4. Verify the new remote connection:
```bash
git remote -v
```

This should show your new repository URL as both fetch and push destinations.

### Creating Your Project

1. If you havent cloned the SWPT template in to your porject folder, do so now:
```bash
git clone https://github.com/Sport-Wales/sport-wales-project-template
cd your-project-name
```

2. Update project configuration:
   - Open `package.json` and update:
     ```json
     {
       "name": "your-project-name",
       "version": "0.0.1",
       // Keep other configurations as is
     }
     ```
   - Update the title in `index.html`
   - Initialise a new repository:
     ```bash
     git init
     ```

3. Install dependencies:
```bash
npm install
```

4. Start development:
```bash
npm run dev
```

## Project Architecture

### Directory Structure
```
your-project/
├── public/                    # Static assets
│   ├── sport_wales_logo_white.png
│   ├── sw_favicon.ico
│   └── vite.svg
├── src/
│   ├── components/           # React components
│   │   ├── component_library/  # Reusable UI components
│   │   ├── main/              # Core components
│   │   └── ui/                # Basic UI elements
│   ├── pages/                # Page components
│   ├── assets/               # Project assets
│   ├── data/                 # Data files
│   ├── styles/               # CSS styles
│   │   ├── index.css          # Main styles
│   │   └── custom/            # Custom styles
│   ├── utils/                # Utility functions
│   ├── App.jsx              # Main application
│   └── main.jsx             # Entry point
└── [Configuration Files]     # Various config files
```

### Key Features

#### 1. Styling System
The template uses a combination of Tailwind CSS and custom Sport Wales styles:
- Sport Wales brand colors (configured in `tailwind.config.js`)
- Custom components with consistent styling
- Responsive design utilities
- CSS variables for brand consistency

#### 2. Component Library
Located in `src/components/component_library/`:
- Pre-built components following Sport Wales design guidelines
- Form components with validation
- Layout components
- Interactive elements

#### 3. Bilingual Support
Built-in support for English and Welsh:
- Route-based language switching
- Language toggle component
- Structured content organisation

#### 4. Development Tools
- Hot Module Replacement with Vite
- ESLint configuration for code quality
- PostCSS for advanced CSS features
- Tailwind CSS for utility-first styling

## Customisation Guide

### Adding New Features

1. Page Components:
```jsx
// src/pages/YourNewPage.jsx
import React from 'react';
import { Layout } from '../components/Layout';

export function YourNewPage() {
  return (
    <Layout>
      <div className="sw-container">
        {/* Your content here */}
      </div>
    </Layout>
  );
}
```

2. Add the route in `App.jsx`:
```jsx
<Route path="/your-path" element={<YourNewPage />} />
```

## Understanding the Style System

### Base Styling Architecture

Our styling system combines Tailwind CSS with Sport Wales' custom design system. Think of it as a layered approach:

1. **Tailwind Base Layer**: The foundation
2. **Sport Wales Custom Variables**: Our brand-specific values
3. **Component-Specific Styles**: Pre-built, consistent components
4. **Utility Classes**: Quick style modifications

### How Our Style System Works

#### CSS Variables and Brand Colors

In `src/styles/index.css`, we define our brand-specific CSS variables:

```css
:root {
  /* Primary Brand Colors */
  --color-sw-red: #E32434;
  --color-sw-yellow: #F6B207;
  --color-sw-blue: #164B64;
  --color-sw-green: #299D91;

  /* Typography */
  --font-primary: 'Objektiv MK1', 'Montserrat', Arial, sans-serif;
  --font-size-body: 16px;
  --line-height-normal: 110%;
}
```

These variables are then integrated with Tailwind in `tailwind.config.js`:

```javascript
export default {
  theme: {
    extend: {
      colors: {
        'sw-red': '#E32434',
        'sw-blue': '#164B64',
        // other colors...
      },
      fontSize: {
        'body': '20px',
        'hero': '95px',
      }
    }
  }
}
```

#### Using the Style System

1. **Basic Component Styling**:
```jsx
// Using Sport Wales utility classes
<button className="sw-button-primary">
  Click Me
</button>

// Same button with additional Tailwind utilities
<button className="sw-button-primary mt-4 hover:opacity-80">
  Click Me
</button>
```

2. **Layout Components**:
```jsx
// Sport Wales container with Tailwind spacing
<div className="sw-container py-8">
  <div className="sw-card">
    Content here
  </div>
</div>
```

3. **Text Styling**:
```jsx
// Combining Sport Wales and Tailwind classes
<h1 className="sw-heading-primary text-sw-blue mb-6">
  Main Heading
</h1>
```

#### Custom Components and Overrides

Our `@layer components` defines Sport Wales-specific components:

```css
@layer components {
  .sw-button {
    height: var(--button-height);
    padding: var(--button-padding);
    border-radius: var(--border-radius-button);
    @apply font-semibold transition-all duration-300;
  }

  .sw-card {
    @apply rounded-lg bg-white p-6 shadow-md;
  }
}
```

#### Responsive Design

Our components are mobile-first and use Tailwind's responsive prefixes:

```jsx
<div className="sw-container">
  <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
    {/* Content */}
  </div>
</div>
```

#### Form Components

Form elements use our custom styles with Tailwind utility classes:

```jsx
<form className="space-y-6">
  <div>
    <label className="sw-label">Input Label</label>
    <input 
      className="sw-input w-full focus:ring-sw-blue" 
      type="text"
    />
  </div>
</form>
```

### Common Style Patterns

Here are some frequently used style combinations:

1. **Card Layouts**:
```jsx
<div className="sw-card hover:shadow-lg transition-shadow">
  <h3 className="sw-heading-secondary">Card Title</h3>
  <p className="text-gray-600">Card content</p>
</div>
```

2. **Button Variations**:
```jsx
// Primary button
<button className="sw-button-primary">Primary Action</button>

// Secondary button with icon
<button className="sw-button-secondary inline-flex items-center">
  <span>Secondary Action</span>
  <ArrowRight className="ml-2 h-4 w-4" />
</button>
```

3. **Status Indicators**:
```jsx
<div className="sw-notice">
  <p className="text-sw-blue font-medium">Important Notice</p>
</div>
```

### Styling Guidelines



1. Using Sport Wales classes:
```jsx
// Preferred approach using our utility classes
<button className="sw-button sw-button-primary">
  Click Me
</button>

// Custom styling when needed
<div className="sw-card custom-class">
  Content
</div>
```

2. Adding custom styles:
```css
/* src/styles/custom/styles.css */
.custom-class {
  /* Your styles here */
}
```

## Deployment Options

### Netlify Deployment

1. Configure `netlify.toml`:
```toml
[build]
  command = "npm run build"
  publish = "dist"

[[redirects]]
  from = "/*"
  to = "/index.html"
  status = 200
```

2. Deploy:
   - Connect your GitHub repository to Netlify, or
   - Use Netlify CLI:
     ```bash
     npm install -g netlify-cli
     netlify deploy
     ```

### Railway Deployment

1. Configure `railway.toml`:
```toml
[build]
builder = "nixpacks"
buildCommand = "npm run build"

[deploy]
startCommand = "npm start"
healthcheckPath = "/"
```

2. Use Railway's GitHub integration or CLI for deployment.

### Docker Deployment

The template includes a production-ready Dockerfile:
```dockerfile
FROM node:18-alpine
WORKDIR /app
COPY package*.json ./
COPY . .
RUN npm ci
RUN npm run build
EXPOSE $PORT
CMD ["npm", "start"]
```

Build and run:
```bash
docker build -t your-project-name .
docker run -p 3000:3000 your-project-name
```

## Development Workflow

1. Start development:
```bash
npm run dev
```

2. Build for production:
```bash
npm run build
```

3. Preview production build:
```bash
npm run preview
```

## Environment Variables

Create a `.env` file for environment variables:
```env
VITE_API_URL=your-api-url
VITE_OTHER_VAR=other-value
```

Remember: All variables must be prefixed with `VITE_`

## Best Practices

1. Component Organization:
   - Place reusable components in `component_library`
   - Keep page-specific components in `pages`
   - Use the Layout component for consistent page structure

2. State Management:
   - Use React hooks for local state
   - Consider context for shared state
   - Keep state as close to where it's used as possible

3. Styling:
   - Use Sport Wales utility classes when available
   - Follow the component styling guidelines
   - Maintain responsive design principles

4. Performance:
   - Lazy load routes and heavy components
   - Optimize images and assets
   - Use appropriate caching strategies

## Support and Resources

- **Documentation**: Full Sport Wales design system documentation is available in the main repository
- **Support**: Contact the Sport Wales development team at [team-email]
- **Issues**: Raise issues in the GitHub repository
- **Updates**: Check the changelog for template updates

## License and Attribution

This project template is proprietary to Sport Wales. All rights reserved.

## Important Notes

- Always prefix environment variables with `VITE_`
- Use `npm run dev` for development
- The production build is in the `dist` directory
- Keep the Sport Wales design system documentation handy
- Follow the established coding standards and patterns

Need help? Contact the development team or raise an issue in the repository.
