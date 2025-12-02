<<<<<<< HEAD
# Fixly — AI Code Review

Simple, fast, and reliable AI-driven code reviews for small snippets and files.

Overview
--------
Fixly analyzes submitted code and returns clear, actionable feedback about bugs, security, performance, and style.

Key benefits
------------
- Fast reviews for pasted snippets or small files
- Structured output: problems, recommended fixes, and explanations
- Easy copy-and-paste for suggested fixes
- Clean React + Tailwind frontend and a small Express backend

Quick start (Windows PowerShell)
-------------------------------
1. Backend

```powershell
cd Backend
npm install
copy NUL .env
# Edit .env and add your Google API key
# Example .env:
# PORT=3000
# GOOGLE_API_KEY=your_google_api_key
npm start
```

2. Frontend

```powershell
cd frontend
npm install
# set VITE_BASE_URL in .env.local, e.g. VITE_BASE_URL=http://localhost:3000/ai
npm run dev
```

How to use
----------
- Open the frontend (usually http://localhost:5173).
- Paste code into the textarea and click "Review Code".
- The app sends the code to the backend endpoint and shows a structured review.

API (simple)
------------
POST /ai/get-review

Request body
```json
{ "code": "<your code here>" }
```

Response (example)
```json
{
   "bad_code": { "label": "❌ Bad Code", "language": "javascript", "code": "..." },
   "issues": { "label": "🔍 Issues", "list": ["...", "..."] },
   "recommended_fix": { "label": "✅ Recommended Fix", "language": "javascript", "code": "..." },
   "improvements": { "label": "💡 Improvements", "list": ["..."] },
   "final_note": "..."
}
```

Environment variables
---------------------
- Backend: `PORT`, `GOOGLE_API_KEY`
- Frontend: `VITE_BASE_URL` (e.g. `http://localhost:3000/ai`)

Project structure (important files)
----------------------------------
- `Backend/server.js` — server entry
- `Backend/src/app.js` — Express app
- `Backend/src/services/ai.service.js` — Google AI integration
- `frontend/src/HomePage/HomePage.jsx` — main UI
- `frontend/src/components/CodeReviewDisplay.jsx` — shows results

Notes and tips
--------------
- Make sure the backend can reach Google Generative AI and that the API key is valid.
- If you get CORS errors, confirm the backend has `cors()` enabled (it's included).
- Adjust `VITE_BASE_URL` for deployed backends.

Contributing
------------
Fork and send a PR for fixes or improvements. Keep changes small and focused.

License
-------
ISC

Author
------
Akash Katti — © 2025

---

If you'd like, I can: update the API docs with examples from your code, add a short demo gif, or generate a small deployment guide.
=======
# 🔍 Code Review AI

<img width="1866" height="937" alt="Code rev op img" src="https://github.com/user-attachments/assets/7952ad6c-2dde-4cc8-8ae7-afa74c920d1d" />



An AI-powered code review application that leverages Google's Generative AI to provide expert-level code analysis, suggestions, and improvements. Submit your code snippets and receive detailed feedback on quality, performance, security, and best practices.

## 🌟 Features

- **AI-Powered Code Review**: Uses Google Generative AI to analyze code and provide comprehensive feedback
- **Real-time Analysis**: Get instant code review results with actionable insights
- **Structured Feedback**: Receive reviews in a organized format covering:
  - Code quality issues
  - Security vulnerabilities
  - Performance optimization opportunities
  - Best practices and refactoring suggestions
  - Readability and maintainability improvements
- **User-Friendly Interface**: Clean, modern UI built with React and Tailwind CSS
- **Multi-language Support**: Works with multiple programming languages
- **Copy Code Blocks**: Easy copy-to-clipboard functionality for suggested fixes

## 📋 Tech Stack

### Backend
- **Node.js** with Express.js
- **Google Generative AI** (@google/generative-ai)
- **CORS** enabled for frontend communication
- **Environment Variables** via dotenv

### Frontend
- **React 19** with Vite
- **Tailwind CSS** for styling
- **Axios** for HTTP requests
- **Lucide React** & **React Icons** for UI elements
- **ESLint** for code quality

## 🚀 Getting Started

### Prerequisites
- Node.js (v14 or higher)
- npm or yarn
- Google API Key for Generative AI

### Backend Setup

1. Navigate to the Backend directory:
   ```bash
   cd Backend
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Create a `.env` file in the Backend directory:
   ```env
   PORT=3000
   GOOGLE_API_KEY=your_google_api_key_here
   ```

4. Start the server:
   ```bash
   npm start
   ```
   The server will run on `http://localhost:3000`

### Frontend Setup

1. Navigate to the frontend directory:
   ```bash
   cd frontend
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Create a `.env.local` file in the frontend directory:
   ```env
   VITE_BASE_URL=http://localhost:3000/ai
   ```

4. Start the development server:
   ```bash
   npm run dev
   ```
   The frontend will be available at `http://localhost:5173` (or the port shown in terminal)

## 📁 Project Structure

```
.
├── Backend/
│   ├── server.js              # Entry point
│   ├── package.json
│   └── src/
│       ├── app.js             # Express app configuration
│       ├── controller/
│       │   └── ai.controller.js    # Review endpoint logic
│       ├── routes/
│       │   └── ai.routes.js        # API routes
│       └── services/
│           ├── ai.service.js       # Google AI integration
│           └── instruction.md      # AI review guidelines
│
└── frontend/
    ├── package.json
    ├── vite.config.js
    ├── tailwind.config.js
    ├── index.html
    └── src/
        ├── main.jsx           # React entry point
        ├── App.jsx
        ├── App.css
        ├── index.css
        ├── HomePage/
        │   └── HomePage.jsx   # Main interface
        └── components/
            ├── CodeReviewDisplay.jsx  # Review results display
            └── CopyCodeBlock.jsx      # Copy functionality
```

## 🔌 API Endpoints

### POST `/ai/get-review`
Submits code for AI-powered review.

**Request:**
```json
{
  "code": "your code here"
}
```

**Response:**
```json
{
  "bad_code": {
    "label": "❌ Bad Code",
    "language": "javascript",
    "code": "problematic snippet"
  },
  "issues": {
    "label": "🔍 Issues",
    "list": ["issue 1", "issue 2"]
  },
  "recommended_fix": {
    "label": "✅ Recommended Fix",
    "language": "javascript",
    "code": "improved code"
  },
  "improvements": {
    "label": "💡 Improvements",
    "list": ["improvement 1", "improvement 2"]
  },
  "final_note": "Summary note"
}
```

## 🛠️ Available Scripts

### Backend
```bash
npm start        # Start the server
npm test         # Run tests
```

### Frontend
```bash
npm run dev      # Start development server
npm run build    # Build for production
npm run preview  # Preview production build
npm run lint     # Run ESLint
```

## 🔐 Environment Variables

### Backend
- `PORT`: Server port (default: 3000)
- `GOOGLE_API_KEY`: Google Generative AI API key (required)

### Frontend
- `VITE_BASE_URL`: Backend API base URL (default: http://localhost:3000/ai)

## 📝 How It Works

1. **User Input**: Paste your code into the textarea
2. **Submit**: Click "Review Code" to send the code to the backend
3. **AI Analysis**: The backend sends the code to Google's Generative AI with expert code review prompts
4. **Structured Response**: AI returns feedback in a structured JSON format
5. **Display**: The frontend displays the review results with syntax highlighting and copy functionality

## 🎨 UI Features

- **Dark Theme**: Modern dark interface with gradient accents
- **Responsive Design**: Works on desktop and mobile devices
- **Loading States**: Shows "Analyzing..." feedback during processing
- **Error Handling**: Clear error messages for various failure scenarios
- **Syntax Highlighting**: Code snippets displayed with proper formatting

## 🐛 Error Handling

The application handles various error scenarios:
- Missing code input
- Backend server errors
- CORS issues
- Network timeouts
- Invalid API responses

## 📦 Dependencies

### Backend
- express@^5.1.0
- @google/generative-ai@^0.24.1
- dotenv@^17.2.3
- nodemon@^3.1.11
- cors (for CORS support)

### Frontend
- react@^19.2.0
- react-dom@^19.2.0
- vite@^7.2.4
- tailwindcss@^4.1.17
- axios@^1.13.2
- lucide-react@^0.554.0
- react-icons@^5.5.0

## 🚀 Deployment

### Backend
- Can be deployed to services like Heroku, Railway, or Vercel
- Set environment variables on the hosting platform
- Ensure PORT environment variable is configurable

### Frontend
- Build with `npm run build`
- Deploy the `dist` folder to services like Vercel, Netlify, or GitHub Pages
- Update `VITE_BASE_URL` to point to your deployed backend

## 📄 Code Review Guidelines

The AI reviewer follows these principles:
- **Code Quality**: Clean, maintainable, structured code
- **Best Practices**: Industry standards and modern approaches
- **Efficiency**: Identify bottlenecks and redundant operations
- **Security**: Check for vulnerabilities (SQL injection, XSS, CSRF, etc.)
- **Scalability**: Future-proof recommendations
- **Readability**: Clear naming, structure, and formatting

## 🤝 Contributing

Feel free to fork this repository and submit pull requests for any improvements or bug fixes.



## 👨‍💻 Author

**Akash Katti**

© 2025 All rights reserved

## 🙏 Support

If you encounter any issues or have suggestions, please open an issue in the repository.

---

**Made with ❤️ using AI and modern web technologies**
>>>>>>> c0f837ef611f2bddf32a165f12ba99def1c0d73f
#   f i x l y  
 