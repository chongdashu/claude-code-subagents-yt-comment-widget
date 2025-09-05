Create a FOCUSED Product Requirements Document (PRD) for an open-source, self-hosted web application that transforms YouTube videos into embeddable social proof widgets.

CRITICAL CONSTRAINTS - READ FIRST:
- Maximum 400 lines for entire PRD
- Focus on WHAT needs to be built and WHY, not HOW to implement
- NO code examples, TypeScript interfaces, or technical implementations
- NO specific API endpoints, URLs, or request/response formats
- NO UI mockups with pixel dimensions (conceptual descriptions only)
- NO database schemas, cache keys, or environment variables
- NO sprint planning, timelines, or week-by-week breakdowns
- NO error code tables or detailed technical specifications

REMEMBER: Other agents in the design phase will handle:
- ui-designer: Creates actual mockups and component hierarchies
- youtube-api-expert: Defines YouTube API integration specifics
- chatgpt-expert: Handles OpenAI integration details
- shadcn-expert: Selects UI components and design systems
- system-architect: Designs technical implementation
- Your role: Define requirements and business logic ONLY

User Journey:
1. Developer clones the repository and deploys their own instance
2. Developer adds their YouTube API and OpenAI API keys to environment variables
3. Developer visits their instance (e.g., localhost:3000 or their-domain.vercel.app)
4. Developer enters a YouTube URL to generate a widget
5. App generates an embed code pointing to developer's instance
6. Developer embeds the iframe on their website
7. End users see the widget (no API keys needed on their part)

The app should:
Core Functionality

Video Data Extraction: Accept a YouTube URL and retrieve essential metadata via YouTube Data API v3:

Title, description, channel name
View count, like count, comment count
Thumbnail URL, publish date
Video duration
ALWAYS check latest API documentation before implementation


Social Proof Visualization: Design a visually compelling component displaying:

Formatted view count (e.g., "2.3M views")
Like/comment ratios with visual indicators
Engagement rate calculation
Trust badges based on metrics thresholds


Sentiment Analysis:

Fetch the top 20-50 most relevant comments (optimize for API quotas)
Send comments batch to OpenAI API (GPT-3.5-turbo for cost efficiency)
Generate an overall sentiment score (1-5 stars)
Provide a brief AI-generated summary of audience reception (2-3 sentences)
Include confidence score for the analysis


Comment Carousel:

Display 5 highly positive comments in a rotating carousel
Filter for comments with high like counts and positive sentiment
Include commenter names and timestamps
Add verified badge for channel owner responses


Widget Embedding (Self-Hosted Model):

Open-source application that developers self-host
Developers provide their own YouTube & OpenAI API keys
Generate embeddable iframe code pointing to their instance
Widget generator UI at main app (localhost:3000 or their domain)
Embed endpoint at /embed?v=[videoId] serves the widget
Support multiple widgets per page
Customizable size via URL params (?size=small|medium|large)
Widget is a static render (no API keys in client code)



Technical Constraints & Considerations

Self-hosted architecture (developers run their own instance)
Environment variables for API keys (YOUTUBE_API_KEY, OPENAI_API_KEY)
Use YouTube API quotas efficiently (1 unit per video, 1 unit per comment fetch)
Cache video data for 24 hours, sentiment analysis for 7 days
Handle videos with comments disabled gracefully
Implement fallbacks for private/deleted videos
Limit initial comment fetch to 20-50 for cost optimization
Documentation-first approach: Check latest API specs before implementation

Key Requirements to Document (High-Level Only)

Core functionality requirements (what the system must do)
User acceptance criteria (how we know it works)
Performance targets (< 2 second load time)
Business constraints (API quotas, cost considerations)
Success metrics (adoption, performance, quality)

Deployment & Documentation

README with clear setup instructions
.env.template with required API keys
One-click deploy button for Vercel
Docker support (optional, post-MVP)
Example embed code generator
Troubleshooting guide for common issues

Out of Scope (to avoid over-engineering)

Real-time comment updates
Multi-language sentiment analysis (MVP in English only)
Historical tracking of metrics
User authentication system
Comment moderation features
Widget customization UI (use URL parameters instead)
Analytics tracking for widget usage

Please structure the PRD with these FOCUSED sections:
1. Executive Summary (100-150 words): Problem, solution, value proposition
2. User Stories (5-10 stories): User needs with acceptance criteria
3. Functional Requirements (Bullet points): WHAT the system does, not HOW
4. Technical Approach (50-100 words): High-level tech stack only
5. Success Metrics (5-8 metrics): Measurable outcomes
6. Risks & Assumptions (Brief list): Key dependencies and risks

SKIP THESE (other agents will handle):
- Detailed technical architecture → system-architect
- API implementation details → api experts
- UI component specifications → ui-designer
- Implementation timelines → orchestrator
- Code examples or interfaces → implementation agents

IMPORTANT ARCHITECTURE NOTE: This is a self-hosted, open-source application where developers deploy their own instances and use their own API keys. See docs/notes.md for detailed architecture rationale. Focus on making it easy for developers to deploy and customize their own instance.

FINAL REMINDER - OUTPUT VALIDATION:
✓ If your PRD exceeds 400 lines, you're over-engineering
✓ If you're writing code or API URLs, stop - that's for implementation
✓ If you're creating ASCII mockups, stop - that's for ui-designer
✓ If you're defining cache strategies, stop - that's for system-architect
✓ Focus on business requirements and user needs ONLY"