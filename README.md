# Recruit CRM - Vue.js Dashboard Application

A modern, responsive candidate recruitment dashboard built with Vue.js 3, Bootstrap 5, and Bootstrap Icons.

## 🚀 Features

### **Layout & Navigation**
- **Left Sidebar**: Collapsible navigation with smooth animations
- **Top Header**: Search functionality, notifications, messaging, and user profile
- **Responsive Design**: Mobile-friendly layout with adaptive components

### **Dashboard Components**
- **Welcome Section**: Personalized greeting with user profile
- **Statistics Cards**: Key metrics with trend indicators
- **Recent Activities**: Timeline view of user activities
- **Quick Actions**: Common tasks and shortcuts
- **Job Applications Table**: Comprehensive job tracking with filters

### **UI/UX Features**
- Modern card-based design with shadows and hover effects
- Color-coded status indicators and badges
- Smooth transitions and animations
- Professional color scheme and typography
- Interactive elements with hover states

## 🛠️ Technology Stack

- **Frontend Framework**: Vue.js 3
- **UI Framework**: Bootstrap 5.3.7
- **Icons**: Bootstrap Icons 1.13.1
- **Build Tool**: Vue CLI
- **Styling**: CSS3 with custom animations

## 📁 Project Structure

```
candidate-dashboard/
├── public/
│   ├── index.html
│   └── favicon.ico
├── src/
│   ├── components/
│   │   ├── SidebarPanel.vue      # Left navigation sidebar
│   │   └── TopbarPanel.vue       # Top header with search & user
│   ├── views/
│   │   └── DashboardComponent.vue # Main dashboard content
│   ├── assets/
│   ├── App.vue                   # Main application component
│   └── main.js                   # Application entry point
├── package.json
├── vue.config.js
└── README.md
```

## 🚀 Getting Started

### Prerequisites
- Node.js (v14 or higher)
- npm or yarn package manager

### Installation

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd candidate-dashboard
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Run development server**
   ```bash
   npm run serve
   ```

4. **Build for production**
   ```bash
   npm run build
   ```

5. **Lint and fix files**
   ```bash
   npm run lint
   ```

## 🎯 Component Details

### **SidebarPanel.vue**
- Collapsible left sidebar (70px → 250px)
- Navigation menu with icons and labels
- User profile section at bottom
- Smooth width transitions
- Mobile-responsive overlay mode

### **TopbarPanel.vue**
- Search bar with filter button
- Email notifications with badge counters
- Messaging system with unread indicators
- User profile dropdown menu
- Quick action buttons

### **DashboardComponent.vue**
- Welcome section with user info
- 4 statistics cards (Jobs, Completed, In Progress, Rating)
- Recent activities timeline
- Quick actions panel
- Job applications data table

## 🎨 Design Features

- **Color Scheme**: Professional blues and grays
- **Typography**: Clean, readable fonts
- **Spacing**: Consistent padding and margins
- **Shadows**: Subtle depth with box-shadows
- **Animations**: Smooth hover effects and transitions
- **Responsive**: Mobile-first design approach

## 📱 Responsive Design

- **Desktop**: Full sidebar and header layout
- **Tablet**: Adaptive grid layouts
- **Mobile**: Collapsible sidebar, stacked components
- **Breakpoints**: Bootstrap 5 responsive utilities

## 🔧 Customization

### **Colors**
Modify CSS variables in component styles for brand colors:
```css
:root {
  --primary-color: #0d6efd;
  --secondary-color: #6c757d;
  --success-color: #198754;
  --warning-color: #ffc107;
  --danger-color: #dc3545;
}
```

### **Layout**
Adjust sidebar widths and transitions in `SidebarPanel.vue`:
```css
.sidebar {
  width: 70px; /* Collapsed width */
}

.sidebar.open {
  width: 250px; /* Expanded width */
}
```

## 🚀 Deployment

### **Build for Production**
```bash
npm run build
```

### **Deploy to Static Hosting**
- Netlify
- Vercel
- GitHub Pages
- AWS S3

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## 📄 License

This project is licensed under the MIT License.

## 🆘 Support

For support and questions:
- Create an issue in the repository
- Contact the development team
- Check the documentation

---

**Built with ❤️ using Vue.js and Bootstrap**
