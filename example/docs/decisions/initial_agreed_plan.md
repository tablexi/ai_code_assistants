# Goal Tracker Application Architecture Decision

## 1. Summary

We've decided to build a cross-platform goal tracking application using React Native with Expo for the frontend (enabling code sharing between web and iOS), FastAPI for the backend (to leverage Python for future data processing needs), and Supabase for authentication and database services. The application will be deployed to Fly.io for hosting the backend services.

## 2. Detailed Architecture Plan

### Frontend Architecture
- **Framework**: React Native with Expo
  - Enables code sharing between web and iOS platforms
  - Provides native iOS experience while maintaining single codebase
  - Expo's managed workflow simplifies deployment and updates
- **State Management**: Redux or Context API
- **UI Component Library**: React Native Paper or Native Base
- **Web Deployment**: Vercel (for the web version)
- **iOS Deployment**: App Store via Expo build services

### Backend Architecture
- **Framework**: FastAPI (Python)
  - High-performance asynchronous API framework
  - Built-in validation and documentation
  - Supports Python data science libraries for future expansion
- **Deployment**: Fly.io
  - Globally distributed applications
  - Simple deployment model
  - Cost-effective for small to medium applications

### Database & Authentication
- **Provider**: Supabase
  - PostgreSQL database with built-in authentication
  - Row-level security for data protection
  - Real-time capabilities
  - Built-in user management and authentication

### API Architecture
- RESTful API design
- JWT token authentication
- Rate limiting for security
- Versioned endpoints

### Data Model
- Users
- Goals (with name, start date, frequency, status)
- Progress tracking entries
- Notifications/reminders

## 3. Key Architecture Choices

| Component | Selected Choice | Aligns with Initial Recommendation? | Reasoning |
|-----------|----------------|-----------------------------------|-----------|
| Frontend Framework | React Native + Expo | ✅ Yes | Maximizes code sharing between platforms while providing native experience |
| Backend Framework | FastAPI (Python) | ❌ No | Differs from Node.js recommendation to better support future data processing needs and leverage Python ecosystem |
| Database | Supabase (PostgreSQL) | ❌ No | Chosen over MongoDB for relational data model and integrated authentication/authorization features |
| Authentication | Supabase Auth | ❌ No | Integrated solution reduces development overhead compared to custom OAuth implementation |
| Backend Hosting | Fly.io | ❌ No | Selected over Heroku for better pricing model and global distribution capabilities |
| Frontend Web Hosting | Vercel | ✅ Yes | Excellent integration with React applications |

### Notes on Divergence from Initial Recommendations

1. **FastAPI over Node.js**: While Node.js would provide JavaScript across the full stack, FastAPI was chosen for its performance characteristics and to support anticipated future data analysis requirements that would benefit from Python's data science ecosystem.

2. **Supabase over MongoDB Atlas**: Selected for its combination of relational PostgreSQL database with built-in authentication and row-level security, which simplifies development and provides a more integrated solution for this application's needs.

3. **Fly.io over Heroku**: Chosen for its more favorable pricing model and built-in global distribution capabilities, which will improve application responsiveness for users across different regions.
