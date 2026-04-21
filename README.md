# Charlie - CaringPays Care Advisor Widget

Charlie is a production-ready, embeddable AI chatbot widget designed to help users navigate state-funded caregiving programs.

## Features

- **AI-Powered Conversations**: Uses Google Gemini 2.0 Flash for empathetic and accurate responses.
- **Secure Backend Proxy**: Protects API keys and sensitive logic.
- **Firebase Integration**: Persistent sessions, lead capture, and audit logging.
- **HIPAA Compliant Design**: Data minimization, access control, and audit trails.
- **Embeddable Iframe**: Easy to integrate into any website.

## Setup

1. **Environment Variables**:
   Copy `.env.example` to `.env` and fill in the required values:
   - `GEMINI_API_KEY`: Your Google Gemini API Key.
   - Firebase configuration (optional but recommended for persistence).

2. **Install Dependencies**:
   ```bash
   npm install
   ```

3. **Run Development Server**:
   ```bash
   npm run dev
   ```

4. **Build for Production**:
   ```bash
   npm run build
   ```

## Embedding the Widget

To embed Charlie on your website, add the following iframe code:

```html
<iframe 
  src="https://your-deployment-url.com" 
  style="position: fixed; bottom: 20px; right: 20px; width: 450px; height: 700px; border: none; z-index: 9999;"
  allow="clipboard-write"
></iframe>
```

## Architecture

- **Frontend**: React + Vite + Tailwind CSS + Framer Motion.
- **Backend**: Node.js + Express.
- **AI**: Google Gemini API via `@google/genai`.
- **Database**: Firebase Firestore.
- **Auth**: Firebase Anonymous Auth.

## HIPAA Compliance

Charlie follows strict guidelines for handling PHI:
- No storage of SSN or DOB.
- Strict Firestore security rules.
- Comprehensive audit logging in `auditLogs` collection.
- Encrypted transmission (HTTPS).
