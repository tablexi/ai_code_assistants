# Goal Tracker Application Setup - TODO List

## Minimal React Native with Expo Frontend Setup (Hello, World)

### 1. Initialize the Project
- [ ] Install Expo CLI globally: `npm install -g expo-cli`
- [ ] Create a new Expo project: `expo init goal-tracker-frontend`
  - Select the blank TypeScript template
- [ ] Navigate to the project directory: `cd goal-tracker-frontend`

### 2. Basic Project Structure
- [ ] Set up simple folder structure
  ```
  /src
    /screens
  ```
- [ ] Create a basic App.tsx file that renders "Hello, World"

### 3. Install Essential Dependencies
- [ ] Install Expo development dependencies: `expo install expo-status-bar`
- [ ] Install Base UI library (React Native Paper): `npm install react-native-paper`

### 4. Create Hello World Component
- [ ] Create a simple HomeScreen component in `/src/screens/HomeScreen.tsx` that displays "Hello, World"
- [ ] Add basic styling to make the text centered and visually appealing

### 5. Configure App Entry Point
- [ ] Modify App.tsx to import and render the HomeScreen component
- [ ] Set up Paper provider for basic styling (optional but helpful for consistency)

### 6. Test the Application
- [ ] Run the app in development mode: `expo start`
- [ ] Test the web version: Press `w` in the Expo CLI
- [ ] Test on iOS simulator (if available): Press `i` in the Expo CLI
- [ ] Verify "Hello, World" appears on screen with proper styling

## Notes
- This setup includes only the bare minimum to get "Hello, World" running
- We've removed navigation setup as it's not needed for a single screen
- We've simplified the folder structure to include only what's needed now
- Additional dependencies and structure will be added as needed when implementing features
