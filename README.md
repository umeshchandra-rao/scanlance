# Scanlance - AI-Powered Resume Analysis Platform

A sophisticated web application that leverages artificial intelligence to analyze, optimize, and enhance resumes for job seekers. Built with modern web technologies and advanced AI capabilities.

## 🚀 Features

### Core Functionality
- **Multi-format Resume Parsing** - Support for PDF, DOCX, and TXT files
- **AI-Powered Analysis** - Google Gemini integration for intelligent resume evaluation
- **Job Matching** - Compare resumes against specific job descriptions
- **Comprehensive Scoring** - Technical skills, experience, education, formatting, and soft skills analysis
- **Improvement Recommendations** - Actionable suggestions for resume enhancement

### User Experience
- **Step-by-Step Workflow** - Guided analysis process with intuitive navigation
- **Real-time Progress** - Live updates during analysis with progress indicators
- **Interactive Results** - Detailed breakdown with expandable sections
- **Responsive Design** - Optimized for desktop, tablet, and mobile devices
- **Dark Mode Support** - Modern UI with theme switching
- **Smooth Animations** - Framer Motion powered transitions and micro-interactions

### Technical Features
- **Rate Limiting** - Redis-based (optional) with graceful fallback for API protection
- **Error Handling** - Comprehensive error boundaries and user-friendly error messages
- **File Processing** - Advanced text extraction with multiple fallback methods
- **Type Safety** - Full TypeScript implementation with strict typing
- **Performance Optimized** - Next.js 14 with optimized builds and caching

## 🛠 Prerequisites

- **Node.js** v18+ (Latest LTS recommended)
- **pnpm** (preferred) or npm/yarn
- **Redis** (optional, for rate limiting - graceful fallback without it)

## 🚀 Quick Start

1. **Clone the repository**
   ```bash
   git clone https://github.com/umeshchandra-rao/scanlance.git
   cd scanlance
   ```

2. **Install dependencies**
   ```bash
   pnpm install
   # or
   npm install
   ```

3. **Environment Setup**
   
   Create a `.env.local` file in the root directory:
   ```env
   # Required
   GEMINI_API_KEY=your_google_gemini_api_key_here
   
   # Optional but recommended
   REDIS_URL=redis://localhost:6379
   RESEND_API_KEY=your_resend_api_key_for_email
   NEXT_PUBLIC_APP_URL=http://localhost:3000
   ```

4. **Start development server**
   ```bash
   pnpm dev
   ```
   
   Open [http://localhost:3000](http://localhost:3000) in your browser.

## 🔧 Environment Variables

| Variable | Required | Description | Default |
|----------|----------|-------------|---------|
| `GEMINI_API_KEY` | ✅ | Google Gemini API key for AI analysis | - |
| `REDIS_URL` | ❌ | Redis connection string for rate limiting | - |
| `RESEND_API_KEY` | ❌ | Resend API key for email functionality | - |
| `NEXT_PUBLIC_APP_URL` | ❌ | Public URL of your application | `http://localhost:3000` |

## 📁 Project Architecture

```
scanlance/
├── app/                          # Next.js 14 App Router
│   ├── globals.css              # Global styles and Tailwind imports
│   ├── layout.tsx               # Root layout with providers
│   ├── page.tsx                 # Landing page
│   ├── actions.ts               # Server actions for form handling
│   ├── analyzer/                # Resume analysis feature
│   │   ├── page.tsx            # Main analyzer page
│   │   ├── layout.tsx          # Analyzer-specific layout
│   │   ├── AnalyzerClientPage.tsx # Main analyzer client component
│   │   ├── components/         # Analysis UI components
│   │   │   ├── StepProgress.tsx
│   │   │   ├── JobDetailsForm.tsx
│   │   │   ├── ResumeUploader.tsx
│   │   │   ├── AnalysisProgress.tsx
│   │   │   └── ResultsDisplay.tsx
│   │   ├── hooks/              # Custom hooks for analyzer
│   │   │   ├── useFileHandling.ts
│   │   │   ├── useAnalysis.ts
│   │   │   └── useStepNavigation.ts
│   │   ├── animations.ts       # Framer Motion configurations
│   │   ├── constants.ts        # Analyzer constants
│   │   └── utils.ts           # Analyzer utilities
│   └── api/                    # API routes
│       ├── analyze/           # Resume analysis endpoint
│       └── send-feedback/     # Feedback submission endpoint
├── components/                 # Shared React components
│   ├── error-boundary.tsx     # Error handling
│   ├── file-uploader.tsx      # File upload component
│   ├── footer.tsx             # Site footer
│   ├── navbar.tsx             # Navigation bar
│   ├── hero-section.tsx       # Landing page hero
│   ├── features-section.tsx   # Features showcase
│   ├── how-it-works.tsx       # Process explanation
│   ├── testimonials-section.tsx # User testimonials
│   ├── faq-section.tsx        # FAQ component
│   ├── theme-provider.tsx     # Dark mode provider
│   ├── resume-analysis-result.tsx # Results display
│   ├── pdf-viewer-basic.tsx   # PDF viewer
│   ├── pdf-fallback-viewer.tsx # PDF fallback
│   └── ui/                    # shadcn/ui components
│       ├── button.tsx
│       ├── card.tsx
│       ├── dialog.tsx
│       ├── form.tsx
│       ├── input.tsx
│       ├── progress.tsx
│       ├── tabs.tsx
│       └── [30+ other UI components]
├── lib/                       # Core business logic
│   ├── analyze-resume.ts      # Main analysis engine
│   ├── gemini-client.ts       # Google Gemini API client
│   ├── pdf-extractor.ts       # PDF text extraction
│   ├── docx-extractor.ts      # DOCX text extraction
│   ├── text-extractor-utils.ts # Text processing utilities
│   ├── rate-limiter.ts        # Redis-based rate limiting
│   ├── error-handler.ts       # Error handling utilities
│   ├── validation-schemas.ts  # Zod validation schemas
│   ├── env-validation.ts      # Environment validation
│   ├── types.ts              # TypeScript type definitions
│   ├── utils.ts              # General utilities
│   ├── prompt-templates.ts   # AI prompt templates
│   ├── education-analyzer.ts # Education analysis (AI module)
│   ├── skill-taxonomy.ts     # Skill categorization (AI module)
│   ├── domain-specific-ner.ts # Named entity recognition (AI module)
│   ├── improved-resume-section-detector.ts # Section detection (AI module)
│   └── resume-template-generator.ts # Template generation (AI module)
├── hooks/                     # Global custom hooks
│   ├── use-mobile.tsx        # Mobile detection
│   └── use-toast.ts          # Toast notifications
├── public/                    # Static assets
│   ├── placeholder-*.png     # Placeholder images
│   └── [other static files]
├── styles/
│   └── globals.css           # Additional global styles
├── __tests__/                # Test configuration
│   └── jest-dom.d.ts        # Jest DOM types
├── coverage/                 # Test coverage reports
├── jest.config.js           # Jest configuration
├── jest.setup.js           # Jest setup
├── next.config.mjs         # Next.js configuration
├── tailwind.config.ts      # Tailwind CSS configuration
├── tsconfig.json           # TypeScript configuration
└── package.json           # Dependencies and scripts
```

## 🎯 How It Works

1. **Job Description Input** - Users provide details about the target job position
2. **Resume Upload** - Support for PDF, DOCX, and TXT file formats
3. **Text Extraction** - Advanced parsing with multiple fallback methods
4. **AI Analysis** - Google Gemini processes the content with sophisticated prompts
5. **Comprehensive Scoring** - Evaluation across multiple dimensions:
   - Technical Skills (frameworks, languages, tools)
   - Professional Experience (relevance, progression, achievements)
   - Educational Background (degrees, certifications, relevance)
   - Document Formatting (structure, readability, ATS compatibility)
   - Soft Skills (leadership, communication, teamwork indicators)
6. **Actionable Recommendations** - Specific improvement suggestions
7. **Results Visualization** - Interactive dashboard with detailed breakdowns

## 🧰 Available Scripts

| Command | Description |
|---------|-------------|
| `pnpm dev` | Start development server with hot reload |
| `pnpm build` | Create optimized production build |
| `pnpm start` | Start production server |
| `pnpm lint` | Run ESLint for code quality checks |
| `pnpm lint:fix` | Auto-fix linting issues |
| `pnpm test` | Run test suite (Jest) |
| `pnpm test:watch` | Run tests in watch mode |
| `pnpm test:coverage` | Generate test coverage report |
| `pnpm type-check` | Run TypeScript type checking |

## Dependencies

- Next.js 14
- React 18
- Tailwind CSS
- shadcn/ui
- Redis (ioredis)
- Google Gemini API, OpenAI API
- PDF/DOCX processing libraries

## Contributing

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## Getting Help

- For issues, use [GitHub Issues](https://github.com/umeshchandra-rao/scanlance/issues)
- For questions, open a discussion or contact the maintainer

## 📚 API Documentation

### Analyze Resume Endpoint

**POST** `/api/analyze`

Analyzes a resume against a job description and returns comprehensive scoring.

#### Request Body
```json
{
  "jobDescription": "string (required) - Target job position details",
  "resumeText": "string (required) - Extracted resume content",
  "filename": "string (optional) - Original file name for context"
}
```

#### Response Format
```json
{
  "success": true,
  "data": {
    "overallScore": "number (0-100)",
    "scores": {
      "technicalSkills": "number (0-100)",
      "experience": "number (0-100)",
      "education": "number (0-100)",
      "formatting": "number (0-100)",
      "softSkills": "number (0-100)"
    },
    "recommendations": [
      {
        "category": "string",
        "priority": "high|medium|low",
        "suggestion": "string",
        "impact": "string"
      }
    ],
    "strengths": ["string array"],
    "weaknesses": ["string array"],
    "extractedSkills": ["string array"],
    "missingSkills": ["string array"],
    "experienceLevel": "entry|junior|mid|senior|executive"
  }
}
```

### Send Feedback Endpoint

**POST** `/api/send-feedback`

Collects user feedback for continuous improvement.

#### Request Body
```json
{
  "rating": "number (1-5)",
  "feedback": "string",
  "category": "analysis|ui|performance|other"
}
```

## � Configuration

### Advanced Settings

#### Rate Limiting Configuration
```typescript
// lib/rate-limiter.ts customization
export const rateLimiterConfig = {
  windowMs: 15 * 60 * 1000, // 15 minutes
  max: 100, // requests per window
  skipSuccessfulRequests: true,
  enableRedis: process.env.REDIS_URL ? true : false
};
```

#### AI Model Parameters
```typescript
// lib/gemini-client.ts configuration
const modelConfig = {
  model: 'gemini-1.5-pro',
  temperature: 0.3, // Lower for more consistent results
  maxOutputTokens: 8192,
  topP: 0.8,
  topK: 40
};
```

#### File Processing Limits
```typescript
// File size and type constraints
const FILE_CONSTRAINTS = {
  maxSize: 10 * 1024 * 1024, // 10MB
  allowedTypes: ['.pdf', '.docx', '.txt'],
  maxPages: 50, // PDF page limit
  timeout: 30000 // Processing timeout (ms)
};
```

## 🧪 Testing

### Running Tests
```bash
# Run all tests
pnpm test

# Run with coverage
pnpm test:coverage

# Run specific test file
pnpm test components/file-uploader.test.tsx

# Watch mode for development
pnpm test:watch
```

### Test Coverage
Current test coverage focuses on:
- ✅ Core utility functions
- ✅ Text extraction logic
- ✅ Validation schemas

### Adding New Tests
```typescript
// Example test structure
import { render, screen } from '@testing-library/react';
import { analyzeResume } from '@/lib/analyze-resume';

describe('Resume Analysis', () => {
  it('should return valid analysis results', async () => {
    const result = await analyzeResume({
      jobDescription: 'Software Engineer',
      resumeText: 'Experienced developer...'
    });
    
    expect(result.overallScore).toBeGreaterThan(0);
    expect(result.scores).toHaveProperty('technicalSkills');
  });
});
```

## 🐛 Troubleshooting

### Common Issues

#### Build Errors
```bash
# Clear cache and reinstall
rm -rf node_modules pnpm-lock.yaml
pnpm install

# TypeScript issues
pnpm type-check
```

#### API Rate Limiting
- **Issue**: "Too many requests" error
- **Solution**: Implement Redis or increase rate limits
- **Config**: Check `REDIS_URL` environment variable

#### File Upload Failures
- **Issue**: Large files not processing
- **Solution**: Check file size limits and server memory
- **Debug**: Enable verbose logging with `DEBUG=true`

#### AI Analysis Errors
- **Issue**: Gemini API errors
- **Solution**: Verify API key and quota
- **Fallback**: Implement retry logic with exponential backoff

### Debug Mode
```bash
# Enable detailed logging
DEBUG=true pnpm dev

# Check environment variables
pnpm run env-check
```

### Performance Optimization

#### Client-Side
- Implement file chunking for large uploads
- Add progress indicators for long operations
- Use React.memo for expensive components

#### Server-Side
- Enable Redis caching for repeated analyses
- Implement request queuing for high traffic
- Add CDN for static assets

## 🤝 Contributing

### Development Workflow

1. **Fork & Clone**
   ```bash
   git clone https://github.com/yourusername/scanlance.git
   cd scanlance
   ```

2. **Setup Development Environment**
   ```bash
   pnpm install
   cp .env.example .env.local
   # Add your API keys
   ```

3. **Create Feature Branch**
   ```bash
   git checkout -b feature/your-feature-name
   ```

4. **Development Guidelines**
   - Follow TypeScript strict mode
   - Add tests for new features
   - Update documentation
   - Run lint and type checks before commit

5. **Commit Standards**
   ```bash
   # Use conventional commits
   git commit -m "feat: add new analysis metric"
   git commit -m "fix: resolve PDF parsing issue"
   git commit -m "docs: update API documentation"
   ```

### Code Style
- **ESLint**: Configured with Next.js recommended rules
- **Prettier**: Auto-formatting on save
- **TypeScript**: Strict mode enabled
- **Components**: Use functional components with hooks
- **Styling**: Tailwind CSS with consistent spacing

### Pull Request Process
1. Ensure all tests pass
2. Update README if needed
3. Add screenshots for UI changes
4. Request review from maintainers

## 📄 License

MIT License - see [LICENSE](LICENSE) file for details.

---

<div align="center">
  <p>Built with ❤️ by the ScanLance team</p>
  <p>
    <a href="https://github.com/yourusername/scanlance/issues">Report Bug</a> •
    <a href="https://github.com/yourusername/scanlance/discussions">Discussions</a> •
    <a href="https://twitter.com/scanlance">Twitter</a>
  </p>
</div> License. See LICENSE file for details.
