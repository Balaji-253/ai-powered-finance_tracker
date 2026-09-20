# AI-Powered Finance Tracker

<div align="center">

![Node.js](https://img.shields.io/badge/Node.js-18%2B-339933?style=for-the-badge&logo=nodedotjs)
![React](https://img.shields.io/badge/React-18-61DAFB?style=for-the-badge&logo=react)
![MongoDB](https://img.shields.io/badge/MongoDB-Atlas-47A248?style=for-the-badge&logo=mongodb)
![OpenAI](https://img.shields.io/badge/OpenAI-Insights-412991?style=for-the-badge&logo=openai)

</div>

A modern full-stack personal finance application designed to help users track spending, manage budgets, understand financial behavior, and generate AI-driven insights. The platform combines a React + Vite frontend with an Express + MongoDB backend and supports authentication, analytics, transaction management, and intelligent recommendations.

## Overview

The application helps individuals:

- Track income and expense transactions in real time
- Categorize and search transactions efficiently
- Set monthly and category-specific budgets
- Monitor financial health through dashboard summaries
- Analyze spending patterns using AI-powered insights
- Generate downloadable monthly reports
- Maintain account profile and security settings

## Key Features

### User Management
- Secure signup and login with JWT authentication
- Protected routes for authenticated users only
- Profile update and password change flows
- Account stats and summary endpoints

### Transaction Management
- Create, update, delete, and list transactions
- Search, filter, and sort by date/category/payment method
- Track recurring financial activity and spending patterns

### Budget Management
- Monthly budget limits
- Category-level budget constraints
- Budget progress visualization
- Cross-check spending against target allocations

### Financial Intelligence
- AI-generated insights using OpenAI integration
- Heuristic fallback when AI is unavailable
- Expense prediction and spend trend analysis

### Reporting & Analytics
- Dashboard summaries and charts
- Monthly financial overview
- PDF report generation for export
- Visual insights for spending by category and time period

## Tech Stack

### Frontend
- React 18
- Vite
- Redux Toolkit
- React Router
- Tailwind CSS
- Recharts
- Axios

### Backend
- Node.js
- Express.js
- MongoDB with Mongoose
- JWT for authentication
- Helmet + rate limiting for security
- OpenAI API integration
- PDF generation with PDFKit

## Architecture

```mermaid
flowchart LR
    User[User] --> Frontend[React + Vite Frontend]
    Frontend --> API[Express REST API]
    API --> Auth[JWT Authentication]
    API --> DB[(MongoDB Atlas / Local MongoDB)]
    API --> AI[OpenAI Insights]
    Frontend --> Reports[Reports + PDF Export]
    Frontend --> Dashboard[Analytics Dashboard]
```

## Project Structure

```text
Finance-Tracker/
├── client/
│   ├── src/
│   ├── index.html
│   ├── package.json
│   ├── vite.config.js
│   ├── tailwind.config.js
│   └── postcss.config.cjs
├── server/
│   ├── app.js
│   ├── server.js
│   ├── .env.example
│   ├── package.json
│   ├── config/
│   ├── controllers/
│   ├── middleware/
│   ├── models/
│   ├── routes/
│   ├── services/
│   └── utils/
├── README.md
├── .gitignore
└── .env.example
```

## Prerequisites

Before running the project, make sure you have:

- Node.js 18+ installed
- npm or yarn installed
- MongoDB Atlas cluster or a local MongoDB instance
- OpenAI API key (optional for AI-generated insights)

## Environment Setup

Create the backend environment file from the template:

```bash
cd server
copy .env.example .env
```

Then update the values in `server/.env`:

```env
NODE_ENV=development
PORT=5000

MONGODB_URI=mongodb+srv://your_user:your_password@cluster0.xxxxx.mongodb.net/ai-finance-tracker?retryWrites=true&w=majority
MONGODB_DNS_SERVERS=1.1.1.1,8.8.8.8

JWT_SECRET=your_super_secure_jwt_secret
JWT_EXPIRE=7d

OPENAI_API_KEY=your_openai_api_key
OPENAI_MODEL=gpt-4o-mini

FRONTEND_URL=http://localhost:5173
```

### MongoDB Atlas Notes

If your environment has issues resolving MongoDB SRV records, add: 

```env
MONGODB_DNS_SERVERS=1.1.1.1,8.8.8.8
```

Also verify that your Atlas cluster allows access from the current machine IP address under Network Access.

## Installation

Install dependencies for both frontend and backend:

```bash
cd client
npm install

cd ../server
npm install
```

## Running the Application

### Start the backend

```bash
cd server
npm run dev
```

The backend runs on:

```text
http://localhost:5000
```

### Start the frontend

Open a second terminal:

```bash
cd client
npm run dev
```

The frontend runs on:

```text
http://localhost:5173
```

## Available Scripts

### Backend

```bash
npm run dev
npm start
npm test
```

### Frontend

```bash
npm run dev
npm run build
npm run preview
npm run lint
```

## API Highlights

The backend exposes REST endpoints grouped by feature:

- Authentication: `/api/auth/*`
- Transactions: `/api/transactions/*`
- Budgets: `/api/budget/*`
- AI insights: `/api/ai/*`
- Dashboard: `/api/dashboard/*`
- Reports: `/api/reports/*`

## Security Considerations

- Store secrets only in environment variables, never in source code
- Keep `.env` out of version control
- Enable MongoDB Atlas IP whitelisting for deployment environments
- Use strong JWT secrets and rotate API keys regularly
- Validate user input before persisting data

## Production Deployment

For deployment, consider:

- Hosting the backend on a secure Node.js server or container platform
- Using a managed MongoDB service such as MongoDB Atlas
- Serving the frontend via Vite preview, static hosting, or a CDN
- Configuring environment variables in the deployment platform
- Setting `FRONTEND_URL` and CORS rules to match the deployed domain

### Recommended deployment checklist

1. Add deployment domain to MongoDB Atlas Network Access
2. Set production environment variables securely
3. Configure `FRONTEND_URL` to the deployed frontend origin
4. Enable HTTPS for both frontend and backend
5. Use a production-grade JWT secret and rotate API keys regularly
6. Run build verification before deployment

```bash
cd client
npm run build
```

## License

This project is distributed under the ISC license unless otherwise stated.

## Contributing

Contributions are welcome. To contribute:

1. Fork the repository
2. Create a feature branch
3. Implement your change with clear, focused commits
4. Run relevant checks for frontend/backend changes
5. Open a pull request with a descriptive summary and screenshots when relevant

### Contribution guidelines

- Keep changes scoped and easy to review
- Prefer small, well-documented PRs
- Update docs if behavior changes
- Validate environment variables and deployment assumptions

## Support

For setup questions or troubleshooting:

- Confirm MongoDB connection credentials and Atlas network access
- Verify `.env` values are correctly loaded
- Check both backend and frontend logs during startup

---

Built for personal finance visibility, budgeting discipline, and AI-powered decision support.
