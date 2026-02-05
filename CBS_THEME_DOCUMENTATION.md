# CBS Faculty Website Theme Documentation

This document describes the Columbia Business School (CBS) faculty website theme implementation for academic personal websites.

## Overview

The CBS theme features a clean, professional design with:
- Blue hero banner for the homepage
- Light gray headers for content pages
- Minimal navigation
- Clean typography with Columbia blue accents
- Responsive design for mobile devices

## Color Palette

- **Columbia Blue**: `#0078AB` - Primary brand color used for hero banner, links, and accents
- **Light Gray**: `#F1F4F7` - Background for content page headers
- **Content Black**: `#333333` - Main text color
- **Pure Black**: `#000000` - Specific elements (email, office, author names)
- **White**: `#FFFFFF` - Hero banner text

## Site Structure

### Pages

1. **Homepage** (`index.md`)
   - Layout: `home`
   - Blue hero banner with faculty name and navigation
   - Two-column bio section: headshot (left) + content (right)
   - Includes: affiliation, CV link, contact info, research overview, education

2. **Research** (`research.md`)
   - Layout: `work`
   - Light gray header with breadcrumb and navigation
   - Three sections: Publications, Working Papers, Work in Progress
   - Simplified publication format (title, authors, venue, optional note)

3. **Teaching** (`teaching.md`)
   - Layout: `default`
   - Light gray header with breadcrumb and navigation
   - Course listings with h3 headers and descriptions

4. **Public Goods** (`publicgoods.md`)
   - Layout: `default`
   - Light gray header with breadcrumb and navigation
   - Sections: Discussion, Data, Blog links

### Layouts

1. **home.html** - Homepage layout
   ```html
   - Blue hero banner (.hero-banner)
   - Faculty name in large white text (54px)
   - Navigation: Home | Research | Teaching | Public Goods
   - Bio section (.bio-section) with two columns
   ```

2. **work.html** - Research page layout
   ```html
   - Light gray content header (.content-header)
   - Clickable breadcrumb (faculty name)
   - Navigation with "Research" marked as active
   - Publication listings with simplified format
   ```

3. **default.html** - Generic content page layout
   ```html
   - Light gray content header (.content-header)
   - Clickable breadcrumb (faculty name)
   - Navigation for all pages
   - Content wrapped in .research-content for consistent styling
   ```

### Components

**Navigation**
- Format: `Home | Research | Teaching | Public Goods`
- Separators: Vertical bars (|)
- CV removed from navigation (embedded in homepage instead)
- Active page styling: Bold with blue underline on content pages

**Breadcrumb**
- Format: `Faculty Name ›`
- Clickable link returns to homepage
- Only appears on content pages (not homepage)

**Hero Banner** (Homepage only)
- Background: Columbia Blue (#0078AB)
- Faculty name: 54px bold white text
- Full-width design with max-width 1200px content area
- Padding: 60px vertical, 40px horizontal

**Content Header** (Content pages)
- Background: Light Gray (#F1F4F7)
- Bottom border: 1px solid darker gray
- Padding: 20px vertical, 40px horizontal
- Contains breadcrumb (left) and navigation (right)

**Bio Section** (Homepage)
- Max-width: 1200px
- Two columns with 60px gap
- Headshot: 300px fixed width
- Bio content: Flexible width
- Affiliation: Pure black (#000000), 16px
- CV link: Columbia blue
- Contact info: Pure black with blue links
- Content: 16px with 1.7 line-height

**Publication Format** (Research page)
- Title: Clickable link to PDF, black text, blue on hover
- Authors: Pure black (#000000), comma-separated
- Venue: Italic, 16px
- Note: Italic, darker black, displays on new line
- Spacing: 18px between publications
- Line height: 1.5

## Typography

- **Font Family**: 'Helvetica Neue', Arial, sans-serif
- **Faculty Name**: 54px bold (36px on mobile)
- **Page Headings (h1)**: 32px bold
- **Section Headings (h2)**: 28px bold, 50px top margin, 30px bottom margin
- **Subsection Headings (h3)**: 18px, 5px top and bottom margins
- **Body Text**: 16px with 1.7 line-height
- **Links**: Columbia blue, no underline, underline on hover

## Styling Details

### Homepage Specific
- Hero banner stretches full width
- Bio section has 60px top and bottom margins
- Headshot max-width: 300px
- Contact info has 20px top margin, 30px bottom margin
- "Welcome" heading (h2): 28px bold, 30px top margin

### Research Page Specific
- "Publications" heading (h1): 32px bold, 40px bottom margin
- "Working Papers" and "Work in Progress" (h2): 28px bold
- Publication title links: Black text, blue on hover
- Authors in pure black (#000000)
- Venue in italics
- Notes in italics on separate line
- 18px spacing between publications

### Teaching and Public Goods Pages
- Wrapped in `.research-content` for consistency
- h3 headers for course names/section titles
- Links in Columbia blue
- Lists with 20px left padding, 8px item spacing

## Responsive Design

Mobile breakpoint: 800px

### Mobile Adjustments
- Hero banner: 40px padding, flex-direction: column
- Faculty name: 36px (reduced from 54px)
- Navigation: Flex-wrap enabled, 15px gaps
- Bio section: Stacks vertically, 20px padding, 30px gap
- Headshot: Max-width 250px
- Content header: 15px padding, stacked layout

## Files Structure

```
homepage/
├── _layouts/
│   ├── home.html         # Homepage with blue hero banner
│   ├── work.html         # Research page with light gray header
│   └── default.html      # Other content pages with light gray header
├── _includes/
│   ├── head.html         # HTML head section
│   └── foot.html         # Footer section
├── _sass/
│   └── _cbs.scss         # All CBS theme styles
├── assets/
│   └── css/
│       └── main.scss     # Imports _cbs.scss
├── index.md              # Homepage content
├── research.md           # Research publications (YAML-based)
├── teaching.md           # Teaching information
├── publicgoods.md        # Public goods content
├── 404.md                # Error page
├── README.md             # Repository documentation
└── LICENSE.md            # License information
```

## Implementation Notes

1. **CV Link**: Embedded in homepage bio section, not in navigation
2. **Author Names**: Not linked, displayed as plain text in pure black
3. **No Abstracts**: Publications show only title, authors, venue, and optional note
4. **No Numbering**: Publications are not numbered
5. **Breadcrumb Navigation**: Faculty name is clickable and returns to homepage
6. **Active State**: Research page shows active styling (bold + blue underline) in navigation
7. **Pure Black Elements**: Email, office address, and author names use #000000 instead of #333333
8. **Consistent Spacing**: Tight spacing (18px between publications) for cleaner look

## Research Page YAML Structure

Publications use YAML front matter with three sections:

```yaml
pubs:
  - title: "Paper Title"
    pdf: "URL to PDF"
    authors: "Author 1, Author 2, Author 3"
    venue: "Journal Name, Volume, Pages (Date)"
    note: "Optional award or note"  # Optional, displays in italics

items:  # Working Papers
  - title: "Working Paper Title"
    pdf: "URL to PDF"
    authors: "Author 1, Author 2"
    venue: "Optional status (e.g., 'Under Review')"
    note: "Optional note"

progress:  # Work in Progress
  - title: "Project Title"
    authors: "Author 1, Author 2"
    note: "Optional description"
```

## Key Design Principles

1. **Simplicity**: Clean, minimal design without clutter
2. **Consistency**: Same navigation and header across all pages
3. **Readability**: Generous line-height (1.7) and spacing
4. **Professionalism**: Columbia blue used sparingly for brand consistency
5. **Accessibility**: Good color contrast, clickable areas, responsive design
6. **Academic Focus**: Content-first design that highlights research and teaching

## Color Usage Guidelines

- **Columbia Blue (#0078AB)**: Links, hero banner, active states, hover colors
- **Light Gray (#F1F4F7)**: Content page headers only
- **Pure Black (#000000)**: Contact info (email, office), author names in publications, affiliation text
- **Content Black (#333333)**: All other text content
- **White (#FFFFFF)**: Hero banner text only

## CSS Architecture

All CBS theme styles are contained in `_sass/_cbs.scss`, which includes:

1. **Color Variables**: Defined at the top for easy customization
2. **Hero Banner**: Full-width blue banner for homepage
3. **Content Header**: Light gray header for content pages
4. **Bio Section**: Two-column layout with photo and content
5. **Research Content**: Styles for publications, headings, and text
6. **Responsive Breakpoints**: Mobile-friendly adjustments at 800px

## Building and Testing

**Requirements:**
- Ruby 3.4+
- Jekyll 4.4.0+
- Bundler

**Local Development:**
```bash
bundle install
bundle exec jekyll serve --port 4001
```

**Production Build:**
```bash
bundle exec jekyll build
```

## Browser Support

- Modern browsers (Chrome, Firefox, Safari, Edge)
- Mobile browsers (iOS Safari, Chrome Mobile)
- Responsive design tested at 320px, 768px, 1024px, 1440px

---

*Last Updated: February 5, 2026*
*Theme based on Columbia Business School faculty website standards*
