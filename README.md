# Hive_Studio

**Hive_Studio** is a web application designed for creators to upload, manage, and organize their videos and other content. Built with **React**, **Vite**, and **TypeScript**, it incorporates a custom routing system similar to the one used in **Hive_Watch**, offering advanced route persistence and a smooth user experience.

---

## Features

### 1. **Content Management**
- Upload videos and other media content directly to the server.
- Manage uploaded content with features like bulk deletion and metadata editing.
- Organize content into categories or playlists for streamlined accessibility.

### 2. **Custom Routing System**
- Utilizes a custom router for dynamic and nested routing, inspired by **Hive_Watch**:
  - **Route Persistence**: Routes remain in the DOM even when hidden, allowing for fast toggling and seamless transitions.
  - **Prefetching**: Allows specific routes to be pre-rendered for improved performance.
  - **Dynamic Actions**: Routes can trigger actions (e.g., data fetching) on navigation.
- Might switch to react-router-dom for better community support and more features.

### 3. **Responsive Design**
- Optimized for a wide range of devices, ensuring creators can manage their content on desktops, tablets, or smartphones.

---

## Technology Stack

### Frontend Framework
- **React**: Powers the component-based architecture.
- **Vite**: Provides fast development and build processes.

### State Management
- **Redux**: Manages application state and enables efficient data flow across components.

### Routing
- **Custom Router**:
  - Supports route persistence and dynamic actions.
  - Includes wildcard routes for handling 404 errors gracefully.

---

## Deployment

### Hosting
- Designed to be hosted on platforms like AWS Amplify, Vercel, or Netlify for global accessibility.

### Build Process
1. Install dependencies:
   ```bash
   npm install
   ```
2. Build the application:
   ```bash
   npm run build
   ```
3. Deploy the `dist` folder to your hosting provider.

---

## Key Code Example: Custom Router Integration

### Main.tsx
```tsx
import { AppRouterProvider } from "./AppRouter/components/Provider.tsx";

createRoot(document.getElementById("hvd-studio-app")!).render(
  <StrictMode>
    <Provider store={store}>
      <AppRouterProvider>
        <App />
      </AppRouterProvider>
    </Provider>
  </StrictMode>
);
```

### App.tsx
```tsx
export default function App() {
  return (
    <div className="page-manager">
      <AppRouter persist>
        <Route
          element={<Upload />}
          path="/upload"
          action={() => dispatch(fetchUploadSettings())}
          prefetch
        />
        <Route
          element={<ManageContent />}
          path="/manage"
          action={() => dispatch(fetchUserContent())}
          prefetch
        />
        <Route
          element={<Analytics />}
          path="/analytics"
          prefetch
        />
        {/* Wildcard Route */}
        <Route path="*" element={<NotFound />} />
      </AppRouter>
    </div>
  );
}
```

---

## Future Enhancements

1. **Enhanced Content Editing**
   - Add support for batch updates, such as changing titles or descriptions for multiple videos at once.

2. **Advanced Analytics**
   - Provide creators with detailed insights into their content’s performance, including views, watch time, and engagement metrics.

3. **Improved Upload Workflow**
   - Implement real-time progress tracking and error handling during uploads.

4. **Integrations**
   - Add third-party integrations, such as social media sharing or external video hosting platforms.

---

## Getting Started

### Prerequisites
- **Node.js 18+**
- A running instance of **Hive_Server** for handling uploads.

### Installation
1. Clone the repository:
   ```bash
   git clone https://github.com/HiveOrg89/Hive_Studio.git
   cd Hive_Studio
   ```
2. Install dependencies:
   ```bash
   npm install
   ```
3. Start the development server:
   ```bash
   npm run dev
   ```