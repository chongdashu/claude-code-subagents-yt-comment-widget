# YouTube Social Proof Widget - Product Requirements Document

## Executive Summary

YouTube creators and businesses struggle to showcase the positive reception and engagement their video content receives, missing opportunities to build trust with potential viewers and customers. This open-source, self-hosted application transforms YouTube videos into embeddable social proof widgets that display engagement metrics, sentiment analysis, and curated positive comments. By providing developers with a deployable solution they control, the application enables businesses to leverage their YouTube content as powerful social proof on their websites, increasing conversion rates and building credibility. The self-hosted architecture ensures data privacy, customization flexibility, and cost control while eliminating vendor lock-in.

## User Stories

### Developer Stories

**Story 1: Repository Setup**
As a developer, I want to quickly deploy my own instance of the application so that I can start generating widgets for my organization.
Acceptance Criteria: Given a cloned repository, When I follow setup instructions and add API keys, Then the application runs locally within 5 minutes.

**Story 2: Widget Generation**
As a developer, I want to generate widget embed codes for YouTube videos so that I can add social proof to my website.
Acceptance Criteria: Given a valid YouTube URL, When I submit it to my instance, Then I receive an embeddable iframe code within 2 seconds.

**Story 3: Widget Customization**
As a developer, I want to customize widget appearance through URL parameters so that widgets match my website design.
Acceptance Criteria: Given embed code with size parameters, When I embed the widget, Then it displays at the specified dimensions.

### End User Stories

**Story 4: Widget Viewing**
As a website visitor, I want to see authentic social proof from YouTube so that I can trust the content creator.
Acceptance Criteria: Given an embedded widget, When I view it, Then I see engagement metrics and positive comments without leaving the page.

**Story 5: Comment Discovery**
As a website visitor, I want to read real viewer comments so that I understand audience reception.
Acceptance Criteria: Given a widget with comment carousel, When I interact with it, Then I can cycle through curated positive comments.

### Business Stories

**Story 6: Trust Building**
As a business owner, I want to display YouTube engagement metrics so that potential customers see social validation.
Acceptance Criteria: Given embedded widgets on product pages, When visitors see high engagement numbers, Then conversion rates improve.

**Story 7: Content Leverage**
As a content creator, I want to repurpose my YouTube success as website social proof so that I maximize content value.
Acceptance Criteria: Given successful YouTube videos, When I generate widgets, Then I can showcase engagement across my web properties.

## Functional Requirements

### Core Widget Functionality

- **Video Data Extraction**
  - Accept YouTube video URLs in standard and shortened formats
  - Validate URL format and video availability
  - Extract video metadata including title, channel, thumbnail
  - Retrieve engagement metrics: views, likes, comments
  - Calculate engagement rate from available metrics
  - Handle edge cases: private videos, deleted content, disabled metrics

- **Sentiment Analysis Engine**
  - Fetch relevant comments from video (20-50 most engaged)
  - Process comments through AI for sentiment scoring
  - Generate overall sentiment rating (1-5 star system)
  - Create audience reception summary (2-3 sentences)
  - Calculate confidence score for analysis accuracy
  - Filter and identify highly positive comments for display

- **Social Proof Visualization**
  - Display formatted view count with appropriate units
  - Show engagement metrics with visual indicators
  - Present sentiment score as star rating
  - Include AI-generated audience summary
  - Feature comment carousel with top positive feedback
  - Apply trust badges based on metric thresholds

- **Widget Embedding System**
  - Generate unique embed codes for each video
  - Support responsive sizing through URL parameters
  - Enable multiple widgets per webpage
  - Provide static widget rendering (no client-side API calls)
  - Include fallback display for error states
  - Support custom styling parameters

### Developer Experience

- **Instance Deployment**
  - One-command local development setup
  - Environment variable configuration for API keys
  - Clear setup documentation with prerequisites
  - Deployment templates for common platforms
  - Health check endpoint for verification

- **Widget Management Interface**
  - Simple URL input for video submission
  - Real-time widget preview
  - Copy-to-clipboard embed code generation
  - Widget customization options preview
  - Recent widgets history

### Data Management

- **Caching Strategy**
  - Store video metadata for reuse
  - Cache sentiment analysis results
  - Minimize redundant API calls
  - Implement cache invalidation rules
  - Provide manual refresh option

- **Error Handling**
  - Graceful degradation for API failures
  - User-friendly error messages
  - Fallback content for edge cases
  - Retry logic for temporary failures
  - Clear troubleshooting guidance

### Performance Requirements

- Widget load time under 2 seconds
- Smooth comment carousel transitions
- Responsive design for all screen sizes
- Optimized asset delivery
- Minimal JavaScript payload

## Technical Approach

The application uses a modern web stack with Next.js and TypeScript for type safety and developer experience. Server-side rendering ensures fast widget delivery while API routes handle data fetching and processing. The self-hosted architecture gives developers full control over their instance, using their own YouTube Data API and OpenAI API keys. Caching layers minimize API usage and costs. The widget endpoint serves pre-rendered content, eliminating client-side API dependencies. Docker and Vercel deployment options provide flexibility for different hosting preferences.

## Success Metrics

1. **Adoption Rate**: Number of GitHub stars and forks within first 6 months
2. **Deployment Success**: 90% of developers successfully deploy within 30 minutes
3. **Widget Performance**: Average load time under 2 seconds for 95% of widgets
4. **API Efficiency**: Average API cost per widget under $0.02
5. **User Engagement**: 30% of website visitors interact with embedded widgets
6. **Developer Satisfaction**: 4+ star average rating in user feedback
7. **Widget Reliability**: 99.5% uptime for generated widgets
8. **Conversion Impact**: 15% improvement in conversion rates for pages with widgets

## Risks & Assumptions

### Risks
- YouTube API quota limitations may restrict high-volume usage
- Changes to YouTube API could break functionality
- OpenAI API costs might increase unexpectedly
- Comment quality varies significantly across videos
- Self-hosting requires technical knowledge from users

### Assumptions
- Developers have basic deployment knowledge
- YouTube videos have sufficient comments for analysis
- English language comments provide adequate sentiment data
- API keys can be obtained without significant barriers
- Positive comments correlate with conversion improvement

### Dependencies
- YouTube Data API v3 availability and stability
- OpenAI API or alternative AI service accessibility
- Modern browser support for iframe embedding
- Stable hosting environment for self-hosted instances
- Sufficient server resources for caching layer

## Out of Scope

The following features are explicitly excluded from initial release:
- Real-time comment updates after widget generation
- Multi-language sentiment analysis beyond English
- Historical metrics tracking and analytics
- User authentication and account management
- Comment moderation or filtering interface
- Visual widget customization UI
- Widget analytics and tracking
- A/B testing capabilities
- White-label branding options
- Automated widget updates
- Mobile application
- Browser extension
- WordPress plugin
- API for third-party integrations
- Batch processing multiple videos
- Scheduled widget generation
- Custom AI model training
- Video transcript analysis
- Competitor comparison features

---

*This PRD defines the requirements for an open-source, self-hosted YouTube social proof widget application. Implementation details are intentionally excluded and will be determined during technical design phases.*