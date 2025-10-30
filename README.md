10.31.25: profile screen mockup share

10.29.25: artist curation by request

10.27.25: screen: waitlist bottom modal

10.26.25: screen: log in or sign up

10.24.25: screen: list, list-detail page

# Product Requirements Document (PRD)
## curated by - Personal Link Collection

**Version:** 2.0 (Updated)  
**Date:** October 24, 2025  
**Status:** Prototype Phase

---

## Product Vision

A minimalist, single-page web app for curating and sharing your favorite links. Present your discoveries in a clean, elegant format - like a digital bookshelf others can browse.

---

## Core Purpose

- Collect links you discover online
- Share your curated collection with others
- Present everything in a beautiful, scannable format

---

## User Roles

- **Public Viewer**: Anyone who visits your curated.me page
- **Admin/Curator**: The owner who adds/manages links (you)

---

## Key Features

### Public View (Main Page)

- Clean list of curated links
- Each entry displays:
  - **Favicon**: Automatically fetched from the link
  - **Source Label**: Clean brand name (e.g., "Spotify", "YouTube") extracted from domain
  - **Page Title**: Fetched automatically from the link
  - **Date Added**: In MM.DD.YY format
- Header shows: "Curated by [username]"
- Links are listed chronologically (newest first)
- Footer displays: © 2025 Curated by Inc. | Seoul, KR. [current time]

### Admin Panel (Hidden)

- **Access**: Type "zzz" anywhere on main page to reveal admin panel
- **Add New Link**:
  - URL input field
  - Automatically fetches page title, favicon, and metadata
  - Option to edit/rewrite the title before saving
  - Submit button
- **Manage Existing Links**:
  - View all links with delete option
  - Each link shows same info as public view
- **Settings**:
  - Edit username/display name (e.g., "sunho.works")
- **Exit**: Button to close admin panel and return to public view

---

## Design Principles

- **Minimal & Modern**: Clean like Claude or OpenAI interfaces
- **Breathing Room**: Generous white space, comfortable line height
- **Subtle Interactions**: Gentle hover effects, smooth transitions
- **Typography-focused**: Let the content shine
- **Visual Hierarchy**: Favicon + source label + title + date flow naturally

---

## Design Reference

Based on Figma design with:
- Light background (#fafafa or similar)
- Clean sans-serif typography
- Left-aligned content in centered container
- Favicon icons adding color/visual interest
- Subtle gray for secondary text (source labels, dates)

---

## Technical Approach

### Phase 1 (Prototype - Current)

- **Tech Stack**: Single HTML file with React (via CDN)
- **Storage**: Browser localStorage
- **Metadata Fetching**: Fetch page title, favicon, and domain info from URLs
- **No Backend**: Everything runs client-side
- **Deployment**: Simple - just open HTML file or host on GitHub Pages

### Phase 2 (Future)

- **Backend**: Supabase for database and authentication
- **Multi-user**: Different users can have their own curated.me pages
- **URL Structure**: curated.me/username
- **Rate Limiting**: One link per day feature
- **Authentication**: Proper login for admin access

---

## Data Structure

### Link Entry
```javascript
{
  id: "unique-identifier",
  url: "https://example.com/page",
  title: "Page Title (editable)",
  domain: "Example", // Clean brand name
  favicon: "https://example.com/favicon.ico",
  dateAdded: "2025-10-23T12:00:00.000Z"
}
```

### Settings
```javascript
{
  username: "sunho.works" // Display name
}
```

---

## What's OUT of Scope (For Now)

- ~~Star ratings~~ (removed from original plan)
- No user authentication (Phase 1)
- No social sharing buttons
- No search or filtering
- No categories or tags
- No link preview images (only favicons)
- No editing links after creation (only delete/re-add)
- No one-link-per-day limitation (adding in Phase 2)

---

## User Flows

### Visitor Flow
1. Visit curated.me page
2. Browse list of links
3. Click any link to visit (opens in new tab)

### Admin Flow
1. Visit curated.me page
2. Type "zzz" to enter admin mode
3. Add new link:
   - Paste URL
   - Wait for auto-fetch of metadata
   - Optionally edit title
   - Submit
4. Manage links (delete if needed)
5. Edit username in settings
6. Close admin panel to return to public view

---

## Success Criteria

- Link metadata (title, favicon, domain) fetches reliably
- Admin panel is hidden but easily accessible
- Public view looks exactly like Figma design
- Smooth, fast interactions
- Data persists between sessions (localStorage)

---

## Future Considerations

- Migration path to Supabase
- Custom domain support (user.curated.me)
- Export/import functionality
- Analytics (view counts)
- RSS feed of your links
- Dark mode support
- Mobile responsive design optimization

---

## Development Roadmap

### Phase 1: Prototype (Current)
- [ ] Build main page with link list display
- [ ] Implement admin panel with "zzz" trigger
- [ ] Add link form with metadata fetching
- [ ] Delete functionality
- [ ] Username/settings editor
- [ ] localStorage persistence

### Phase 2: Backend Integration
- [ ] Set up Supabase project
- [ ] Migrate from localStorage to Supabase
- [ ] Add user authentication
- [ ] Multi-user support
- [ ] One-link-per-day rate limiting

### Phase 3: Polish & Features
- [ ] Custom domains
- [ ] Analytics
- [ ] Export/import
- [ ] Mobile optimization
- [ ] Dark mode

---

## Questions & Decisions Log

**Q: Should we use star ratings?**  
A: Removed. Keeping it simple - just curated links without ratings.

**Q: Where should the add form be?**  
A: Hidden admin panel, accessed by typing "zzz"

**Q: Favicons - yes or no?**  
A: Yes! Adds visual interest and context.

**Q: How to handle the brand name label?**  
A: Fetch and display clean brand name (e.g., "Spotify" not "spotify.com")

**Q: Single HTML or proper React setup?**  
A: Single HTML with React CDN for prototype, easy migration later.

---

## Contact & Contribution

For questions or contributions, please open an issue on GitHub.

**Project maintained by:** sunho.works
