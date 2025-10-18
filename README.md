# 🎯 Lead Score API

> FastAPI wrapper around a LangChain lead-scoring chain using GPT-3.5-turbo for intelligent prospect qualification

---

## 📋 Overview

A production-ready API service that provides intelligent lead scoring capabilities using LangChain and OpenAI's GPT-3.5-turbo. This service analyzes enriched prospect data to classify leads as **Hot**, **Warm**, or **Cold** with detailed reasoning and personalization recommendations.

**Built for:** Sales teams, marketing automation platforms, and CRM systems that need AI-powered lead qualification at scale.

---

## ✨ Key Features

- 🎯 **AI-Powered Lead Scoring** - Uses GPT-3.5-turbo to analyze prospect fit
- 🔥 **Hot/Warm/Cold Classification** - Clear, actionable lead temperature ratings
- 💡 **Personalization Recommendations** - AI suggests angles for outreach
- 📊 **Confidence Scoring** - Provides 0-100 confidence score for each classification
- ⚡ **Fast & Scalable** - FastAPI for high-performance REST endpoints
- 🔗 **LangChain Integration** - Leverages LangChain for robust AI workflows
- 📝 **Detailed Reasoning** - Returns explanation for each score

---

## 🏗️ Architecture

```
┌─────────────┐
│   Client    │
│ Application │
└──────┬──────┘
       │
       │ POST /score
       ▼
┌─────────────────┐
│   FastAPI       │
│   Server        │
└────────┬────────┘
         │
         │ LangChain
         ▼
┌─────────────────┐
│  GPT-3.5-turbo  │
│  (OpenAI API)   │
└─────────────────┘
```

---

## 🚀 Tech Stack

- **Framework:** FastAPI (Python)
- **AI Framework:** LangChain
- **LLM:** OpenAI GPT-3.5-turbo
- **Language:** Python 3.11+
- **API Style:** RESTful

---

## 📡 API Endpoints

### `POST /score`

Scores a prospect based on enriched data.

**Request Body:**
```json
{
  "prospect_data": {
    "name": "John Smith",
    "title": "Facility Manager",
    "company": "Acme Corp",
    "industry": "Manufacturing",
    "company_size": "500-1000",
    "location": "Chicago, IL",
    "email_status": "verified",
    "confidence_score": 85,
    "tech_stack": ["Salesforce", "AWS"],
    "linkedin_profile": "https://linkedin.com/in/johnsmith"
  },
  "icp_criteria": {
    "target_industries": ["Manufacturing", "Logistics"],
    "target_titles": ["Facility Manager", "Operations Director"],
    "min_company_size": 250
  }
}
```

**Response:**
```json
{
  "score": "hot",
  "confidence": 92,
  "reasoning": "Perfect ICP match: Facility Manager at mid-size manufacturing company with verified email and strong tech stack.",
  "personalization_suggestions": [
    "Reference their Salesforce implementation",
    "Mention AWS infrastructure optimization",
    "Lead with manufacturing facility modernization case study"
  ],
  "recommended_action": "immediate_outreach",
  "estimated_conversion_probability": 0.68
}
```

**Lead Temperature Definitions:**
- 🔥 **Hot** (80-100): Perfect ICP match, verified contact info, high engagement potential
- 🌡️ **Warm** (50-79): Good fit, some missing data, moderate engagement potential
- ❄️ **Cold** (0-49): Poor fit, low-quality data, or low engagement potential

---

## 🎯 Use Cases

### 1. **CRM Integration**
Automatically score leads as they enter your CRM system and route to appropriate sales reps.

### 2. **Marketing Automation**
Trigger different nurture sequences based on lead temperature.

### 3. **Sales Prioritization**
Help SDRs focus on hot leads first with AI-powered prioritization.

### 4. **Data Enrichment Pipeline**
Score leads after enrichment to determine outreach strategy.

### 5. **Campaign Optimization**
Analyze which lead sources produce the hottest prospects.

---

## 🧠 Scoring Logic

The AI considers multiple factors:

**Firmographic Match:**
- Industry alignment with ICP
- Company size within target range
- Geographic location

**Contact Quality:**
- Email verification status
- Phone number availability
- LinkedIn profile completeness

**Engagement Signals:**
- Tech stack compatibility
- Company growth indicators
- Recent funding rounds

**Data Completeness:**
- Overall enrichment confidence score
- Number of validated data points

---

## 🔧 Configuration

The API uses environment variables for configuration:

```bash
OPENAI_API_KEY=sk-...
MODEL_NAME=gpt-3.5-turbo
TEMPERATURE=0.3
MAX_TOKENS=500
```

---

## 📊 Performance

- **Average Response Time:** ~800ms per lead
- **Throughput:** ~75 leads/minute (single instance)
- **Cost:** ~$0.001 per lead scored (GPT-3.5-turbo)
- **Accuracy:** 87% agreement with human sales qualification (based on internal testing)

---

## 🔗 Integration with CARISM SDR

This API is a core component of the **CARISM SDR System**, where it:
1. Scores prospects after enrichment
2. Determines outreach priority
3. Influences email personalization strategy
4. Triggers different nurture sequences based on temperature

---

## 🛠️ Local Development

```bash
# Install dependencies
pip install -r requirements.txt

# Set environment variables
export OPENAI_API_KEY=your_key_here

# Run the server
uvicorn main:app --reload

# Test the endpoint
curl -X POST http://localhost:8000/score \
  -H "Content-Type: application/json" \
  -d @sample_prospect.json
```

---

## 📝 Error Handling

The API includes comprehensive error handling:

- **Invalid Input:** Returns 400 with validation errors
- **OpenAI API Issues:** Returns 503 with retry-after header
- **Rate Limiting:** Returns 429 with rate limit info
- **Server Errors:** Returns 500 with error ID for tracking

---

## 🔐 Security Features

- ✅ API key authentication
- ✅ Rate limiting per client
- ✅ Input validation and sanitization
- ✅ CORS configuration
- ✅ Request logging for audit

---

## 🚀 Deployment

Designed for easy deployment to:
- AWS Lambda (with Mangum adapter)
- Docker containers
- Kubernetes
- Serverless platforms (Vercel, Railway)

---

## 🤝 Part of CARISM Suite

This API is part of the comprehensive **CARISM Sales Intelligence Platform**:

- 🎯 **CARISM SDR** - Automated prospecting and outreach
- 🧠 **CARISM Intelligence Hub** - Lead enrichment and profiling
- 📊 **CARISM Analytics** - Performance tracking and optimization

---

## 📫 Questions or Issues?

For support or inquiries:
- 📧 Email: alessandro@carism.it
- 📧 Email: alex@carismusa.com
- 💼 LinkedIn: [Alessandro De Luca](https://www.linkedin.com/in/aldeluca)

---

## 📄 License

Proprietary - © 2025 Alessandro De Luca | BizzBrain.AI

---

<div align="center">

**Built with 🧠 by [BizzBrain.AI](https://bizzbrain.ai)**

*Making AI-powered sales intelligence accessible and practical*

</div>
