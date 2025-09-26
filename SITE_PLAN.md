## Her Cloud Website Plan

### High-level goals
- **Inform**: What the club is, who it’s for, how to join
- **Promote**: Upcoming events, announcements, and YouTube video highlights
- **Engage**: Clear calls-to-action (join, attend events, subscribe)
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
- **Homepage**: Lacks mission, how to join, and “next event” highlights
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

### Information architecture (pages/sections)
- **Home**: Mission, next event card, latest announcement, “Join” CTA, YouTube highlight
- **Events**: Upcoming events list; past events archive
- **Announcements**: Reverse-chron list with categories
- **Videos**: Featured playlist + recent uploads
- **About**: Mission, officers, faculty advisor, FAQ
- **Join Us**: How to join, meeting cadence, socials, mailing list/Discord invite
- **Resources** (optional): Slides, guides, starter projects, external links
- **Contact**: Email form or mailto; socials
- **Global**: Footer with socials, email, GitHub; site search (optional)

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

### SEO/analytics/performance
- `jekyll-seo-tag`, sitemap, Open Graph tags
- GA4 via existing include
- Verify favicons & manifest metadata
- Optimize images (webp where possible), lazy loading

### Maintenance & workflow
- Content PR templates for events/announcements
- Optional Decap CMS for non-technical editing
- GitHub Actions build if using non-allowlisted plugins or CMS previews
- Short contributor docs for officers (how to add events/announcements)

### Phased plan
- **Phase 1**: IA, collections, pages, styling polish; embed YouTube and events
- **Phase 2**: CMS/editor workflow; search; calendar integration
- **Phase 3**: Enhancements (archives, resources, richer components)


