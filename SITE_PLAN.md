## Her Cloud Website Plan

### High-level goals
- **Inform**: What the club is, who it's for, how to join
- **Promote**: Upcoming events, announcements, and YouTube video highlights
- **Engage**: Clear calls-to-action (join, attend events, subscribe)
- **Capture**: Email signup form for newsletter/mailing list
- **Track**: Analytics for user behavior, signup sources, and website performance
- **Sustain**: Simple, low-maintenance updates by student officers

### Current tech stack (from this repo)
- **Platform**: GitHub Pages
- **Static site generator**: Jekyll (Minima theme)
- **Templating**: Liquid (`_layouts`, `_includes`)
- **Styling**: Sass via Minima (`_sass/minima/*`, `assets/css/style.scss`)
- **Content**: Markdown pages + posts (`_posts`)
- **Analytics**: Google Analytics include exists
- **Build**: Native GitHub Pages Jekyll build

### Gaps vs. goals
- **Content types**: No structured types for events, announcements, or videos
- **Calendaring**: No events calendar or past events archive
- **Homepage**: Lacks mission, how to join, and "next event" highlights
- **Email capture**: No signup form or email list integration
- **Analytics**: Basic GA exists but no custom event tracking for signups/sources
- **Editing**: No CMS/editor workflow for non-technical officers
- **Branding**: Navigation and look-and-feel need tailoring beyond Minima defaults

### Recommendation: keep Jekyll and enhance
- **Why**: Zero backend, free hosting, simple PR-based edits, native support on GitHub Pages
- **Add structured content**:
  - Collections: `events`, `announcements`, `videos`
  - Taxonomies: tags for event types (workshop, talk); categories if needed
- **Plugins** (GitHub Pages compatible or via Actions):
  - `jekyll-seo-tag`, `jekyll-sitemap`, `jekyll-feed`, `jekyll-archives` (optional)
  - If extra plugins are needed beyond the allowlist, build via GitHub Actions
- **Editing options for officers**:
  - GitHub UI + PR templates for events/announcements
  - Optional Decap CMS (Netlify CMS successor) stored in repo; build via Actions
- **Integrations**:
  - YouTube embeds for a playlist/highlights
  - Google Calendar embed or ICS; or native `events` collection with upcoming filter
  - Contact form via Formspree (or mailto)
  - Email signup form with Google Workspace integration
  - Enhanced analytics with custom event tracking

### Information architecture (pages/sections)
- **Home**: Mission, next event card, latest announcement, "Join" CTA, YouTube highlight, email signup
- **Events**: Upcoming events list; past events archive
- **Announcements**: Reverse-chron list with categories
- **Videos**: Featured playlist + recent uploads
- **About**: Mission, officers, faculty advisor, FAQ
- **Join Us**: How to join, meeting cadence, socials, email signup form, Discord invite
- **Resources** (optional): Slides, guides, starter projects, external links
- **Contact**: Email form or mailto; socials
- **Global**: Footer with socials, email, GitHub, email signup; site search (optional)

### Data model (Jekyll collections)
- **`events/` documents**:
  - Front matter: `title`, `start_datetime`, `end_datetime` (optional), `location`, `rsvp_url`, `tags`, `description`
- **`announcements/` documents**:
  - Front matter: `title`, `date`, `category`, `summary`
- **`videos/` documents**:
  - Front matter: `title`, `youtube_id`, `date`, `playlist`, `summary`
- **Includes**: Helper includes for event cards, announcement teasers, video embeds

### Visual/brand and UX
- Keep Minima, but customize:
  - Club branding (logo/colors) in `custom-variables.scss` and `custom-styles.scss`
  - Clear CTAs and event cards
  - Mobile-first layout, readable typography, dark mode (Minima skins exist)
- Accessibility: High contrast, alt text, semantic headings, focus states

### Email signup & Google Workspace integration
- **Email collection options**:
  - **Google Forms**: Simple form → Google Sheets → Google Groups/Workspace
  - **Formspree + Zapier**: Formspree form → Zapier → Google Workspace/Groups
  - **Mailchimp**: Dedicated email marketing platform with Google Workspace sync
  - **Custom solution**: Jekyll form → Netlify Functions → Google Workspace API
- **Recommended approach**: Google Forms → Google Groups (simplest, no API keys needed)
- **Form placement**: Homepage hero, footer, dedicated signup page, event pages
- **Data collected**: Email, name (optional), graduation year, interests/topics

### Analytics & tracking recommendations
- **Google Analytics 4** (already configured):
  - Enhanced ecommerce events for signup tracking
  - Custom events: `email_signup`, `event_rsvp`, `video_play`
  - Source tracking: UTM parameters, referrer analysis
  - Conversion funnels: visitor → signup → event attendance
- **Additional tracking**:
  - **Google Tag Manager**: Easier event management without code changes
  - **Hotjar/Microsoft Clarity**: Heatmaps, session recordings (free tiers available)
  - **Google Search Console**: Search performance, indexing issues
- **Key metrics to track**:
  - Signup conversion rate by page/source
  - Event RSVP rates
  - Video engagement (watch time, completion)
  - Traffic sources (social, search, direct)
  - Geographic data for local outreach
- **No database needed**: All data stored in Google Analytics, Google Sheets, and email platform

### SEO/analytics/performance
- `jekyll-seo-tag`, sitemap, Open Graph tags
- GA4 via existing include + custom event tracking
- Verify favicons & manifest metadata
- Optimize images (webp where possible), lazy loading

### Maintenance & workflow
- Content PR templates for events/announcements
- Optional Decap CMS for non-technical editing
- GitHub Actions build if using non-allowlisted plugins or CMS previews
- Short contributor docs for officers (how to add events/announcements)

### Theme considerations with new features
- **Keep Minima theme**: Still the best choice because:
  - **Form integration**: Minima's clean structure easily accommodates signup forms
  - **Analytics compatibility**: Works seamlessly with GA4 and GTM
  - **Performance**: Lightweight, fast loading for better conversion rates
  - **Mobile-first**: Essential for student users
  - **Customization**: Easy to add custom signup components and tracking
- **Enhancements needed**:
  - Custom signup form components (`_includes/signup-form.html`)
  - Analytics event tracking snippets (`_includes/analytics-events.html`)
  - Enhanced footer with signup CTA
  - Custom CSS for form styling and conversion optimization
- **Alternative themes considered**: Not recommended because:
  - **Academic themes**: Too formal for student club
  - **Corporate themes**: Overkill for simple brochure site
  - **Custom themes**: Unnecessary complexity for GitHub Pages

### Phased plan
- **Phase 1**: IA, collections, pages, styling polish; embed YouTube and events
- **Phase 2**: Email signup forms, enhanced analytics, CMS/editor workflow
- **Phase 3**: Advanced tracking, A/B testing, calendar integration
- **Phase 4**: Enhancements (archives, resources, richer components)

## Phase 1: Foundation & Core Content Structure

### Issues We're Tackling:
1. **No structured content types** - Currently only blog posts exist, but we need events, announcements, and videos
2. **Missing core pages** - No dedicated events, announcements, or videos pages
3. **Poor homepage experience** - Lacks mission statement, next event highlights, clear CTAs
4. **No event calendar/archive** - Can't showcase upcoming events or past activities
5. **Basic branding** - Still using default Minima styling without club identity
6. **No YouTube integration** - Can't showcase club videos effectively

### Phase 1 Deliverables:

#### 1. **Jekyll Collections Setup**
- Create `_events/` collection for structured event data
- Create `_announcements/` collection for club updates
- Create `_videos/` collection for YouTube content
- Configure `_config.yml` with collection settings

#### 2. **Core Pages Creation**
- **Enhanced Homepage** (`index.md`):
  - Hero section with mission statement
  - "Next Event" card (upcoming event)
  - Latest announcement teaser
  - "Join Us" CTA button
  - Featured YouTube video
- **Events Page** (`events.md`):
  - Upcoming events list
  - Past events archive
- **Announcements Page** (`announcements.md`):
  - Reverse-chronological list
  - Category filtering
- **Videos Page** (`videos.md`):
  - Featured playlist
  - Recent uploads grid

#### 3. **Navigation & Layout Updates**
- Update `_includes/nav-items.html` with new pages
- Create custom layouts for events/announcements if needed
- Update `_includes/header.html` for better navigation

#### 4. **Content Structure**
- Add sample events (2-3 upcoming, 2-3 past)
- Add sample announcements (3-4 recent)
- Add sample videos (3-4 YouTube embeds)
- Create helper includes for event cards, announcement teasers

#### 5. **Basic Styling & Branding**
- Update `_sass/minima/custom-variables.scss` with club colors
- Enhance `_sass/minima/custom-styles.scss` for:
  - Event card styling
  - CTA button styling
  - YouTube embed styling
  - Homepage hero section

#### 6. **YouTube Integration**
- Create `_includes/youtube-embed.html` for consistent video embeds
- Add YouTube playlist integration
- Responsive video containers

### Technical Implementation Order:
1. Configure collections in `_config.yml`
2. Create collection directories and sample content
3. Build core pages (home, events, announcements, videos)
4. Create helper includes for reusable components
5. Update navigation and layouts
6. Apply custom styling and branding
7. Test responsive design and functionality

### Success Criteria:
- ✅ Homepage showcases mission, next event, latest announcement
- ✅ Events page displays upcoming/past events clearly
- ✅ Announcements page shows recent updates
- ✅ Videos page embeds YouTube content properly
- ✅ Navigation includes all new pages
- ✅ Mobile-responsive design maintained
- ✅ Club branding applied (colors, logo, styling)


