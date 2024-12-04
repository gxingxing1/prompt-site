![](https://cdn.nlark.com/yuque/0/2024/png/50546945/1733293007783-4a0707e4-cd8a-4cf2-b4be-c7bbef03e340.png)

# 初始化项目：
npx create-next-app@latest winsurf-site

npx shadcn@latest init

# Prompt:
## Step1：
```plain
Create detailed components with these requirements:
1. Use 'use client' directive for client-side components
2. Style with Tailwind CSS utility classes for responsive design
3. Use Lucide React for icons (from lucide-react package). Do NOT use other UI libraries unless requested
4. Use stock photos from picsum.photos where appropriate, only valid URLs you know exist
5. Configure next.config.js image remotePatterns to enable stock photos from picsum.photos
6. Create root layout.tsx page that wraps necessary navigation items to all pages
7. MUST implement the navigation elements items in their rightful place i.e. Left sidebar, Top header
8. Accurately implement necessary grid layouts
9. Follow proper import practices:
   - Use @/ path aliases
   - Keep component imports organized
   - Update current src/app/page.tsx with new comprehensive code
   - Don't forget root route (page.tsx) handling
   - You MUST complete the entire prompt before stopping

Code Editor Landing Page with Dark Theme
</summary_title>

<image_analysis>

1. Navigation Elements:
- Top navbar with: Logo, Features, Use Cases, Pricing, Teams, Company, Resources, Sign In
- Footer navigation with: Company, Features, Learn, Support, Connect sections


2. Layout Components:
- Full-width header section (100vw)
- Content containers max-width: 1200px
- Editor preview section: 800px width
- Comparison grid: 2-column layout
- Feature cards grid: 3-column layout
- Testimonial cards: Horizontal scrolling layout


3. Content Sections:
- Hero section with editor preview
- Statistics/metrics display
- Product comparison table
- Testimonial carousel
- Feature highlights grid
- Call-to-action sections
- Footer with multi-column layout


4. Interactive Controls:
- Primary CTA buttons in teal (#00FFD1)
- Secondary ghost buttons with border
- Interactive code editor preview
- Carousel navigation controls
- Card hover states with subtle elevation


5. Colors:
- Primary: #00FFD1 (Teal)
- Background: #000000 (Black)
- Text: #FFFFFF (White)
- Secondary: #1A1A1A (Dark Gray)
- Accent: #333333 (Light Gray)


6. Grid/Layout Structure:
- 12-column grid system
- 24px base grid spacing
- Responsive breakpoints at 768px, 1024px, 1440px
- Card grid: 32px gap between items
</image_analysis>

<development_planning>

1. Project Structure:
```
src/
├── components/
│   ├── layout/
│   │   ├── Navbar
│   │   ├── Footer
│   │   └── Container
│   ├── features/
│   │   ├── CodeEditor
│   │   ├── ComparisonTable
│   │   └── TestimonialCarousel
│   └── shared/
├── assets/
├── styles/
├── hooks/
└── utils/
```


2. Key Features:
- Interactive code editor preview
- Product comparison matrix
- Testimonial carousel
- Feature cards grid
- Statistics display
- Responsive navigation


3. State Management:
```typescript
interface AppState {
├── editor: {
│   ├── content: string
│   ├── language: string
│   └── theme: 'dark' | 'light'
├── }
├── navigation: {
│   ├── isMenuOpen: boolean
│   └── activeSection: string
├── }
}
```


4. Routes:
```typescript
const routes = [
├── '/',
├── '/features/*',
├── '/pricing',
├── '/teams',
└── '/docs/*'
]
```


5. Component Architecture:
- Atomic design pattern
- Shared UI component library
- Container/Presenter pattern
- HOCs for layout components


6. Responsive Breakpoints:
```scss
$breakpoints: (
├── 'mobile': 320px,
├── 'tablet': 768px,
├── 'desktop': 1024px,
└── 'wide': 1440px
);
```
</development_planning>
```

## Step2 : 
```plain
Next.js route structure based on navigation menu items (excluding main route). Make sure to wrap all routes with the component:

Routes:
- /features
- /use-cases
- /pricing
- /teams
- /company
- /resources
- /sign-in
- /learn
- /support
- /connect-sections

Page Implementations:
/features:
Core Purpose: Showcase product features and capabilities
Key Components
- Feature cards with icons and descriptions
- Interactive demos
- Feature comparison table
- Call-to-action buttons
Layout Structure
- Hero section with main feature highlight
- Grid layout for feature cards
- Responsive columns (3 on desktop, 2 on tablet, 1 on mobile)

/use-cases:
Core Purpose: Demonstrate practical applications and success stories
Key Components
- Case study cards
- Industry filters
- Success metrics
- Customer testimonials
Layout Structure
- Filterable grid layout
- Detailed case study modal views
- Responsive masonry layout

/pricing:
Core Purpose: Display pricing plans and subscription options
Key Components
- Pricing plan cards
- Feature comparison table
- Plan selector
- Payment integration
Layout Structure
- Horizontal plan comparison (desktop)
- Vertical stacked plans (mobile)
- Sticky purchase button

/teams:
Core Purpose: Team collaboration and management features
Key Components
- Team creation wizard
- Member management interface
- Role permissions matrix
- Team analytics dashboard
Layout Structure
- Sidebar navigation
- Main content area
- Responsive dashboard layout

/company:
Core Purpose: Company information and about us content
Key Components
- Company timeline
- Team member profiles
- Mission/Vision statements
- Office locations map
Layout Structure
- Scrolling sections
- Grid-based team gallery
- Location-based content sections

/resources:
Core Purpose: Educational and support materials hub
Key Components
- Resource category filters
- Download

/access cards
- Search functionality
- Resource preview
Layout Structure:
- Filterable grid
- Category sidebar
- List

/sign-in:
Core Purpose: User authentication and account access
Key Components
- Login form
- Social auth options
- Password recovery
- 2FA integration
Layout Structure
- Centered card layout
- Form validation feedback
- Mobile-optimized input fields

/learn:
Core Purpose: Educational content and tutorials
Key Components
- Course catalog
- Progress tracking
- Interactive tutorials
- Knowledge assessments
Layout Structure
- Course grid layout
- Video player integration
- Progress sidebar

/support:
Core Purpose: Customer support and help center
Key Components
- Knowledge base articles
- Ticket system
- Live chat widget
- FAQs
Layout Structure
- Search-first design
- Category navigation
- Article content area

/connect-sections:
Core Purpose: Integration and API documentation
Key Components
- API documentation
- Integration guides
- Code samples
- Testing console
Layout Structure
- Split view (docs

Layouts:
MainLayout:
- Applicable routes: All except /sign-in
- Core components
  - Header with navigation
  - Footer
  - Breadcrumbs
  - Mobile menu
- Responsive behavior
  - Collapsible navigation on mobile
  - Fluid container widths
  - Dynamic spacing

AuthLayout
- Applicable routes: /sign-in
- Core components
  - Minimal header
  - Auth form container
  - Brand elements
- Responsive behavior
  - Centered card design
  - Full-screen on mobile
  - Flexible form inputs

DocsLayout
- Applicable routes: /resources, /learn, /support, /connect-sections
- Core components
  - Side navigation
  - Content area
  - Search bar
  - Table of contents
- Responsive behavior
  - Collapsible sidebar
  - Responsive typography
  - Mobile-first navigation
```

