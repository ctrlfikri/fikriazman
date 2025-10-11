# Nuxt 3 Portfolio

This is a modern personal portfolio project built with Nuxt 3, Vite, and Tailwind CSS. It showcases projects, skills, and provides a contact form for potential clients or employers to reach out.

## Project Structure

The project is organized as follows:

```
nuxt3-portfolio
├── assets
│   └── css
│       └── tailwind.css
├── components
│   ├── Navbar.vue
│   ├── Footer.vue
│   ├── HeroSection.vue
│   ├── ProjectCard.vue
│   └── ContactForm.vue
├── layouts
│   └── default.vue
├── pages
│   ├── index.vue
│   ├── about.vue
│   ├── projects.vue
│   └── contact.vue
├── public
│   └── favicon.ico
├── nuxt.config.ts
├── tailwind.config.js
├── package.json
└── README.md
```

## Getting Started

To get started with this project, follow these steps:

1. **Clone the repository:**
   ```bash
   git clone <repository-url>
   cd nuxt3-portfolio
   ```

2. **Install dependencies:**
   ```bash
   npm install
   ```

3. **Run the development server:**
   ```bash
   npm run dev
   ```

4. **Open your browser and navigate to:**
   ```
   http://localhost:3000
   ```

## Features

- **Responsive Design:** The portfolio is designed to be fully responsive, ensuring a great experience on both desktop and mobile devices.
- **Dynamic Project Cards:** Projects are displayed dynamically using reusable components.
- **Contact Form:** A simple contact form that integrates with Formspree for handling submissions.
- **Tailwind CSS:** Utilizes Tailwind CSS for styling, allowing for rapid UI development.

## Customization

You can customize the portfolio by modifying the following files:

- **components/Navbar.vue:** Update navigation links.
- **components/HeroSection.vue:** Change the introduction text and call-to-action.
- **pages/about.vue:** Add your personal information and background.
- **pages/projects.vue:** List your projects and details.
- **pages/contact.vue:** Adjust the contact form settings as needed.

## License

This project is open-source and available under the [MIT License](LICENSE).