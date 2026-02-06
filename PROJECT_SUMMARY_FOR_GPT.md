# NicorAI Website - Project Summary for Portfolio

## Project Name
**NicorAI Website** - AI-Powered Company Portfolio Platform

## Project Type
Full-Stack Web Application (Production-Ready MVP)

## Brief Description
A sophisticated, full-stack AI-powered company website that serves as both a modern portfolio platform and an interactive AI demonstration. Built with Next.js 15 and React 19 frontend, Node.js/Express backend, deployed on AWS with optimized cloud infrastructure. Features include an intelligent chat interface powered by RAG systems, dynamic content views, responsive design, and enterprise-grade security.

## Tech Stack

**Frontend:**
- Next.js 15.3.1 (React 19.0.0) with TypeScript
- Tailwind CSS 4.0 + Framer Motion
- React Markdown, Axios

**Backend:**
- Node.js/Express 5.1.0
- Zod validation, Redis caching
- N8N webhook integration, reCAPTCHA v3

**Infrastructure:**
- AWS S3 + CloudFront (Frontend)
- AWS App Runner (Backend)
- Terraform (Infrastructure as Code)
- Docker containerization

## Key Features

1. **AI-Powered Chat Interface**
   - RAG-based conversational AI with contextual responses
   - Persistent chat history with localStorage
   - Redis caching for optimized performance
   - Real-time message processing with loading states

2. **Dynamic Content Views**
   - About Us (company story, team, values)
   - What We Do (6 comprehensive AI services)
   - What We've Done (portfolio case studies)
   - Research Blog (technical articles)
   - Connect (contact form with email integration)

3. **Advanced UI/UX**
   - Smooth Framer Motion animations
   - Fully responsive mobile-first design
   - Sidebar navigation with chat history
   - Auto-refresh version checking
   - Keyboard shortcuts (ESC to close)

4. **Security & Performance**
   - Rate limiting (100 req/15min per IP)
   - reCAPTCHA v3 bot protection
   - Zod schema validation
   - Helmet.js security headers
   - Static site generation + CDN
   - Redis response caching (1-hour TTL)

## Architecture Highlights

- **Modular Design**: Separation of concerns with reusable components
- **Service Layer**: Dedicated API service for backend communication
- **Caching Strategy**: Redis integration to minimize API calls
- **Error Handling**: Structured error responses at multiple levels
- **Infrastructure as Code**: Terraform for reproducible deployments
- **Cost Optimized**: ~$17.49/month AWS infrastructure costs

## Project Structure

```
frontend/              # Next.js application
  ├── src/app/         # App router with components & services
nicorai-api-gateway/   # Express.js API
  ├── src/             # Controllers, middleware, routes, services
infra/                 # Terraform infrastructure code
```

## Technical Achievements

- ✅ Production-ready full-stack application
- ✅ Type-safe TypeScript implementation
- ✅ Enterprise-grade security implementation
- ✅ Performance optimized (static generation + CDN)
- ✅ Cost-effective cloud architecture (~$17/month)
- ✅ Scalable design (horizontal scaling ready)
- ✅ Modern development practices (IaC, CI/CD ready)

## Deployment

- **Frontend**: AWS S3 + CloudFront CDN
- **Backend**: AWS App Runner (containerized)
- **Caching**: External Redis service
- **Infrastructure**: Terraform-managed AWS resources

## Portfolio Value

Demonstrates expertise in:
- Modern React/Next.js development
- TypeScript and type safety
- RESTful API design and integration
- AWS cloud services and infrastructure
- Security best practices
- Performance optimization
- Cost-effective solution architecture
- Production-ready code quality

## Status
✅ Production-Ready MVP | Deployed on AWS | Optimized for cost and performance

---

**Use this summary when sharing the project with GPT or including it in portfolio presentations.**

