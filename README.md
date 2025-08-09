# 🤖 AI-Powered Resume Analyzer

An intelligent resume analysis system built with React, React Router, and Puter.js that automatically evaluates candidate resumes against job requirements using AI-powered matching algorithms.

![Resume Analyzer](https://img.shields.io/badge/React-18.x-blue) ![TypeScript](https://img.shields.io/badge/TypeScript-5.x-blue) ![AI-Powered](https://img.shields.io/badge/AI-Powered-green)

## ✨ Features

### 🎯 Smart Resume Analysis
- **AI-Powered Evaluation**: Automated resume scoring based on job requirements
- **Multi-Category Assessment**: Analyzes ATS compatibility, tone & style, content quality, structure, and skills match
- **Detailed Feedback**: Provides specific tips for improvement with explanations
- **Overall Score**: Comprehensive scoring system (0-100) for quick evaluation

### 🏢 Job Management
- **Create Job Listings**: Define job requirements with titles, descriptions, locations, and required skills
- **Skills Matching**: AI matches candidate skills against job requirements
- **Multiple Applications**: Track multiple candidates per job posting

### 📊 Resume Processing
- **File Upload Support**: Upload PDF and DOC resume formats
- **Real-time Analysis**: Instant AI processing and feedback generation
- **Resume Preview**: View uploaded resumes with analysis overlay
- **Application Tracking**: Monitor submission status and scores

### 🔍 Advanced Analytics
- **ATS Optimization**: Ensures resumes are ATS-friendly
- **Keyword Analysis**: Identifies missing keywords and suggests improvements
- **Structure Assessment**: Evaluates resume formatting and organization
- **Content Quality**: Analyzes achievement descriptions and quantifiable results

## 🚀 Quick Start

### Prerequisites
- Node.js (v16 or higher)
- npm or yarn
- Modern web browser

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/your-username/ai-resume-analyzer.git
   cd ai-resume-analyzer
   ```

2. **Install dependencies**
   ```bash
   npm install
   # or
   yarn install
   ```

3. **Set up environment variables**
   ```bash
   cp .env.example .env.local
   ```

   Configure your AI service API keys:
   ```env
   REACT_APP_AI_API_KEY=your_ai_service_key
   REACT_APP_PUTER_API_KEY=your_puter_key
   ```

4. **Start the development server**
   ```bash
   npm run dev
   # or
   yarn dev
   ```

5. **Open your browser**
   Navigate to `http://localhost:5173`

## 🏗️ Project Structure

```
ai-resume-analyzer/
├── public/
│   ├── images/           # Static images and assets
│   └── resumes/         # Sample resume files
├── src/
│   ├── components/      # Reusable UI components
│   │   ├── Navbar.tsx
│   │   ├── ResumeCard.tsx
│   │   └── JobListing.tsx
│   ├── routes/          # React Router pages
│   │   ├── home.tsx
│   │   ├── jobs.tsx
│   │   └── analysis.tsx
│   ├── services/        # AI and API services
│   │   ├── aiAnalyzer.ts
│   │   └── puterService.ts
│   ├── types/           # TypeScript type definitions
│   │   └── resume.ts
│   ├── utils/           # Helper functions
│   └── constants/       # App constants and sample data
├── constants/
│   └── index.ts         # Resume and job data
└── package.json
```

## 🔧 Configuration

### AI Service Setup
The application uses AI services for resume analysis. Configure your preferred AI provider:

```typescript
// src/services/aiAnalyzer.ts
const AI_CONFIG = {
  provider: 'openai', // or 'claude', 'gemini'
  apiKey: process.env.REACT_APP_AI_API_KEY,
  model: 'gpt-4-turbo'
};
```

### Puter.js Integration
Puter.js handles file storage and management:

```typescript
// src/services/puterService.ts
import puter from 'puter';

puter.configure({
  apiKey: process.env.REACT_APP_PUTER_API_KEY
});
```

## 📝 Usage Guide

### Creating Job Listings

1. **Navigate to Jobs Section**
    - Click on "Jobs" in the navigation menu

2. **Add New Job**
   ```typescript
   const newJob = {
     title: "Senior Frontend Developer",
     description: "Looking for an experienced React developer...",
     location: "San Francisco, CA",
     requiredSkills: ["React", "TypeScript", "Node.js"]
   };
   ```

3. **Define Requirements**
    - Add specific skills and qualifications
    - Set experience level requirements
    - Include location preferences

### Uploading and Analyzing Resumes

1. **Upload Resume**
    - Drag and drop PDF/DOC files
    - Or use the file picker

2. **Select Target Job**
    - Choose which job position to analyze against
    - Multiple jobs can be selected for comparison

3. **View Analysis Results**
   ```typescript
   interface AnalysisResult {
     overallScore: number;
     ATS: { score: number; tips: Tip[] };
     toneAndStyle: { score: number; tips: Tip[] };
     content: { score: number; tips: Tip[] };
     structure: { score: number; tips: Tip[] };
     skills: { score: number; tips: Tip[] };
   }
   ```

### Understanding Scores

- **90-100**: Excellent match, ready to submit
- **80-89**: Good match, minor improvements needed
- **70-79**: Decent match, several improvements recommended
- **60-69**: Fair match, significant improvements needed
- **Below 60**: Poor match, major revisions required

## 🤖 AI Analysis Categories

### 1. ATS Compatibility (25%)
- Keyword optimization
- Standard formatting
- Section headings recognition
- File format compatibility

### 2. Content Quality (25%)
- Achievement descriptions
- Quantifiable results
- Relevance to job requirements
- Experience presentation

### 3. Skills Matching (20%)
- Technical skills alignment
- Required vs. mentioned skills
- Skill proficiency indicators
- Domain expertise

### 4. Structure & Format (15%)
- Visual hierarchy
- Consistent formatting
- Length appropriateness
- Contact information clarity

### 5. Tone & Style (15%)
- Professional language
- Active voice usage
- Confidence level
- Industry-appropriate terminology

## 🔍 API Reference

### Resume Analysis Endpoint
```typescript
POST /api/analyze-resume
{
  "resumeFile": File,
  "jobId": string,
  "analysisType": "comprehensive" | "quick"
}

Response:
{
  "success": boolean,
  "data": AnalysisResult,
  "processingTime": number
}
```

### Job Creation Endpoint
```typescript
POST /api/jobs
{
  "title": string,
  "description": string,
  "location": string,
  "requiredSkills": string[]
}
```

## 🛠️ Development

### Available Scripts

```bash
# Development
npm run dev          # Start development server
npm run build        # Build for production
npm run preview      # Preview production build

# Testing
npm run test         # Run unit tests
npm run test:e2e     # Run end-to-end tests
npm run test:coverage # Generate coverage report

# Code Quality
npm run lint         # Run ESLint
npm run type-check   # Run TypeScript checks
npm run format       # Format with Prettier
```

### Environment Variables

```env
# AI Service Configuration
REACT_APP_AI_API_KEY=your_openai_api_key
REACT_APP_AI_MODEL=gpt-4-turbo

# Puter.js Configuration  
REACT_APP_PUTER_API_KEY=your_puter_api_key

# Application Settings
REACT_APP_MAX_FILE_SIZE=10485760  # 10MB
REACT_APP_SUPPORTED_FORMATS=pdf,doc,docx
```

## 🚀 Deployment

### Vercel (Recommended)
```bash
npm install -g vercel
vercel --prod
```

### Netlify
```bash
npm run build
# Upload dist/ folder to Netlify
```

### Docker
```dockerfile
FROM node:18-alpine
WORKDIR /app
COPY package*.json ./
RUN npm ci --only=production
COPY . .
RUN npm run build
EXPOSE 3000
CMD ["npm", "run", "preview"]
```

## 🤝 Contributing

We welcome contributions! Please see our [Contributing Guide](CONTRIBUTING.md) for details.

### Development Workflow
1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

### Code Standards
- Use TypeScript for all new code
- Follow ESLint configuration
- Write tests for new features
- Update documentation as needed

## 📊 Performance

- **Analysis Speed**: ~3-5 seconds per resume
- **File Size Limit**: 10MB per upload
- **Concurrent Processing**: Up to 5 resumes simultaneously
- **Supported Formats**: PDF, DOC, DOCX

## 🔐 Security & Privacy

- All uploaded files are processed securely
- No resume content is stored permanently
- AI analysis happens in isolated environments
- GDPR compliant data handling

## 📋 Roadmap

- [ ] **Bulk Analysis**: Process multiple resumes simultaneously
- [ ] **Advanced Filters**: Filter candidates by score ranges
- [ ] **Integration APIs**: Connect with ATS systems
- [ ] **Mobile App**: React Native mobile application
- [ ] **Team Collaboration**: Multi-user workspace features
- [ ] **Custom Templates**: Resume template suggestions
- [ ] **Interview Scheduling**: Integrated calendar system

## 🐛 Troubleshooting

### Common Issues

**Resume not uploading:**
- Check file size (max 10MB)
- Ensure file format is supported (PDF, DOC, DOCX)
- Verify network connection

**AI analysis failing:**
- Confirm API key is configured correctly
- Check AI service rate limits
- Ensure resume contains readable text

**Low analysis scores:**
- Review specific feedback provided
- Check keyword alignment with job requirements
- Ensure standard resume formatting

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 👨‍💻 Author

**M-tech-cmd**
- GitHub: [@your-username](https://github.com/M-tech-cmd)
- LinkedIn: [Your Profile](https://linkedin.com/in/your-profile)
- Email: kimaniemma20@gmail.com

## 🙏 Acknowledgments

- OpenAI for AI analysis capabilities
- Puter.js team for file management solutions
- React community for excellent documentation
- All contributors who helped improve this project

---

**⭐ If you find this project helpful, please consider giving it a star on GitHub!**