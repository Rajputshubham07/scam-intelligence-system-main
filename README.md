# 🛡️ ScamShield - AI Honeypot Intelligence Platform

> An intelligent, autonomous system that engages scammers in conversation, extracts threat intelligence, and generates real-time risk assessments.

[![Live Demo](https://img.shields.io/badge/demo-live-success)](https://scam-intelligence-system.onrender.com/)
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.3-blue)](https://www.typescriptlang.org/)

## 🌐 Live Demo

**🚀 Try it now:** [https://scam-intelligence-system.onrender.com/](https://scam-intelligence-system-main.onrender.com/)

**API Health:** [https://scam-intelligence-system.onrender.com/health](https://scam-intelligence-system.onrender.com/health)

**Metrics:** [https://scam-intelligence-system.onrender.com/api/v1/metrics](https://scam-intelligence-system.onrender.com/api/v1/metrics)

## ✨ Key Features

### 🤖 AI-Powered Analysis
- **Claude AI Integration** - Natural persona responses that stay in character
- **OpenAI GPT-4** - Advanced scam pattern detection and reasoning
- **Hybrid Analysis** - Combines AI with rule-based detection for reliability

### 🎭 Intelligent Personas
- **Margaret Thompson** (68) - Retired teacher, trusting, low tech-savvy
- **David Chen** (45) - Small business owner, moderate awareness
- **Sarah Williams** (72) - Widow, highly vulnerable, seeks companionship
- Dynamic persona selection based on scam type

### 📊 Real-Time Detection
- **8 Signal Types**: Urgency, Financial Request, Impersonation, Threat, Authority Claim, Social Engineering, Time Pressure, Too Good To Be True
- **Entity Extraction**: Phone numbers, URLs, emails, payment IDs, bank accounts, organizations
- **Risk Scoring**: 0-100 scale with color-coded severity levels
- **Scam Classification**: Phishing, Romance, Tech Support, IRS, Lottery, Investment, and more

### 💻 Terminal-Inspired UI
- **Live Scammer Console** - Type messages as a scammer to test the system
- **12 Preset Scenarios** - One-click testing with realistic scam messages
- **Animated Risk Meter** - Real-time visual threat assessment
- **Signal Feed** - Live detection of scam tactics
- **Entity Chips** - Extracted intelligence displayed as colored badges
- **State Timeline** - Track conversation progression
- **Export Functionality** - Download complete conversation data as JSON

### 🔐 Production-Ready
- API key authentication
- Rate limiting (100 requests per 15 minutes)
- Structured JSON logging
- PostgreSQL support
- Docker deployment
- Health monitoring

## 🎯 Demo Presets

Test the system instantly with 12 realistic scam scenarios:

1. 🏛️ **IRS** - Tax fraud with arrest threats
2. 🏦 **BANK** - Account compromise urgency
3. 💻 **TECH** - Microsoft support scam
4. 💌 **ROMANCE** - Nigerian prince variant
5. ₿ **CRYPTO** - Bitcoin investment fraud
6. 🎰 **LOTTERY** - Prize claim scam
7. 👵 **GRANDPARENT** - Emergency bail money
8. 📦 **AMAZON** - Fake purchase alert
9. 📱 **SOCIAL** - Facebook account threat
10. 💰 **REFUND** - IRS tax refund phishing
11. 💼 **JOB** - Work-from-home fee scam
12. ❤️ **CHARITY** - Fake donation request

## 🚀 Quick Start

### Option 1: Use the Live Demo
Visit [https://scam-intelligence-system.onrender.com/](https://scam-intelligence-system.onrender.com/) and start testing immediately!

### Option 2: Run Locally

```bash
# Clone the repository
git clone https://github.com/Shivang1109/scam-intelligence-system.git
cd scam-intelligence-system

# Install dependencies
npm install

# Build the project
npm run build

# Start the server
node simple-server.js
```

Visit `http://localhost:3000` to access the UI.

### Option 3: Docker Deployment

```bash
# Build and run with Docker
docker build -t scamshield .
docker run -p 3000:3000 scamshield
```

## 📖 API Usage

### Start a Conversation

```bash
curl -X POST https://scam-intelligence-system.onrender.com/api/v1/conversations \
  -H "Content-Type: application/json" \
  -H "X-API-Key: test-api-key-12345" \
  -d '{
    "initialMessage": "URGENT! Your account has been compromised!"
  }'
```

### Send a Message

```bash
curl -X POST https://scam-intelligence-system.onrender.com/api/v1/conversations/{id}/messages \
  -H "Content-Type: application/json" \
  -H "X-API-Key: test-api-key-12345" \
  -d '{
    "message": "Click here to verify: secure-bank-verify.com"
  }'
```

### Get Conversation Details

```bash
curl https://scam-intelligence-system.onrender.com/api/v1/conversations/{id} \
  -H "X-API-Key: test-api-key-12345"
```

### Instant Analysis (No Conversation)

```bash
curl -X POST https://scam-intelligence-system.onrender.com/api/v1/analyze \
  -H "Content-Type: application/json" \
  -H "X-API-Key: test-api-key-12345" \
  -d '{
    "message": "Your social security has been suspended. Call 1-800-555-0192 immediately!"
  }'
```

## 🏗️ Architecture

```
┌─────────────────────────────────────────────────────────┐
│                    Frontend (UI)                        │
│  Terminal Console | Risk Meter | Signal Feed | Entities │
└────────────────────────┬────────────────────────────────┘
                         │
┌────────────────────────▼────────────────────────────────┐
│                  Express API Server                      │
│  Authentication | Rate Limiting | CORS | Logging        │
└────────────────────────┬────────────────────────────────┘
                         │
┌────────────────────────▼────────────────────────────────┐
│                 Agent Controller                         │
│  Manages multiple conversation agents                    │
└────────────────────────┬────────────────────────────────┘
                         │
        ┌────────────────┼────────────────┐
        │                │                │
┌───────▼──────┐  ┌──────▼──────┐  ┌─────▼──────┐
│   Agent 1    │  │   Agent 2   │  │  Agent N   │
│  (Margaret)  │  │   (David)   │  │  (Sarah)   │
└───────┬──────┘  └──────┬──────┘  └─────┬──────┘
        │                │                │
        └────────────────┼────────────────┘
                         │
        ┌────────────────┼────────────────┐
        │                │                │
┌───────▼──────┐  ┌──────▼──────┐  ┌─────▼──────┐
│ NLP Extractor│  │ HybridAnalyzer│ │ RiskScorer │
│ (Entities)   │  │ (AI + Rules)  │ │ (0-100)    │
└──────────────┘  └───────────────┘ └────────────┘
                         │
        ┌────────────────┼────────────────┐
        │                │                │
┌───────▼──────┐  ┌──────▼──────┐  ┌─────▼──────┐
│   Claude AI  │  │  OpenAI GPT │  │ PostgreSQL │
│  (Responses) │  │  (Analysis) │  │ (Storage)  │
└──────────────┘  └─────────────┘  └────────────┘
```

## 📊 System Metrics

The system tracks comprehensive metrics:

- **847 scams analyzed** (demo data)
- **$2.3M protected** (estimated value)
- **5 scam types** with detailed breakdowns
- **Real-time signal detection** across 8 categories
- **Uptime monitoring** and health checks

Access metrics: `GET /api/v1/metrics`

## 🧪 Testing

```bash
# Run all tests
npm test

# Run with coverage
npm run test:coverage

# Run specific test suite
npm test -- Agent.test

# Run integration tests
npm test -- integration
```

## 🔧 Configuration

### Environment Variables

Create a `.env` file (see `.env.example`):

```bash
# Application
NODE_ENV=production
PORT=3000
LOG_LEVEL=info

# Database (optional)
DB_HOST=localhost
DB_PORT=5432
DB_NAME=scam_intelligence
DB_USER=scam_user
DB_PASSWORD=your-password

# API Keys (optional - for AI features)
OPENAI_API_KEY=your-openai-key
ANTHROPIC_API_KEY=your-anthropic-key

# API Configuration
API_KEY_SECRET=your-secret-key
TEST_API_KEY=test-api-key-12345
```

## 📁 Project Structure

```
scam-intelligence-system/
├── public/              # Frontend UI
│   ├── index.html      # Main UI page
│   ├── app.js          # Frontend logic
│   └── styles.css      # Styling
├── src/                # Backend source code
│   ├── agents/         # Conversation agents
│   ├── ai/             # AI integrations (Claude, OpenAI)
│   ├── api/            # REST API routes
│   ├── nlp/            # NLP and entity extraction
│   ├── scoring/        # Risk scoring
│   ├── reporting/      # Report generation
│   ├── persistence/    # Data storage
│   └── types/          # TypeScript definitions
├── scripts/            # Database scripts
├── simple-server.js    # Combined server (API + UI)
├── copy-public.js      # Build script
├── Dockerfile          # Docker configuration
├── render.yaml         # Render deployment config
└── package.json        # Dependencies
```

## 🎨 UI Features

### Real-Time Visualization
- **Animated Risk Meter**: SVG circle that fills based on risk score (0-100)
- **Color-Coded Levels**: Green (low), Yellow (medium), Orange (high), Red (critical)
- **Signal Badges**: Live detection with confidence percentages
- **Entity Chips**: Extracted data displayed with icons and colors

### Interactive Elements
- **One-Click Presets**: Auto-send realistic scam messages
- **Duration Timer**: Track conversation length
- **State Timeline**: Visual progression through conversation states
- **Export Button**: Download complete conversation as JSON

### Critical Risk Alert
When risk score hits 80+, the system triggers a dramatic visual alert:
- Pulsing red border animation
- Glowing shadow effect
- 3-second attention-grabbing display

## 🚢 Deployment

### Render (Current)
The system is deployed on Render with automatic deployments from GitHub.

**Build Command:** `npm ci && npm run build`  
**Start Command:** `node simple-server.js`

### Docker
```bash
docker build -t scamshield .
docker run -p 3000:3000 --env-file .env scamshield
```

### Manual
```bash
npm run build
node simple-server.js
```

## 🔒 Security

- **API Key Authentication**: All endpoints require valid API keys
- **Rate Limiting**: 100 requests per 15 minutes per IP
- **CORS Protection**: Configurable origin restrictions
- **Input Validation**: Sanitized user inputs
- **Structured Logging**: Audit trail for all operations

## 📈 Performance

- **Response Time**: < 500ms for instant analysis
- **Concurrent Conversations**: Supports multiple simultaneous agents
- **Scalability**: Horizontal scaling with load balancer
- **Caching**: In-memory caching for frequent queries
- **Database**: PostgreSQL for production persistence

## 🤝 Contributing

Contributions are welcome! Please:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

Built with:
- **TypeScript** - Type-safe development
- **Express.js** - Web framework
- **Claude AI** - Natural language generation
- **OpenAI GPT-4** - Advanced analysis
- **PostgreSQL** - Data persistence
- **Jest** - Testing framework
- **Docker** - Containerization

## 📞 Contact

**GitHub**: [RajputShubham07/scam-intelligence-system](https://github.com/Rajputshubham07/scam-intelligence-system-main)

**Live Demo**: [https://scam-intelligence-system.onrender.com/](https://scam-intelligence-system.onrender.com/)

---

**⚠️ Disclaimer**: This system is designed for research and educational purposes. Always follow applicable laws and regulations when deploying scam detection systems.

**🎯 Built for hackathons, ready for production.**
