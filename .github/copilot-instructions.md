# For Allah - Islamic Content Hub

**CRITICAL**: Always reference these instructions first and fallback to search or bash commands only when you encounter unexpected information that does not match the info here.

For Allah is a static HTML Islamic content website featuring interactive educational content about Islamic wisdom, Quranic verses, and prophetic traditions. The site consists of 4 standalone HTML pages with embedded JavaScript for interactivity.

## Working Effectively

### Repository Structure
- **NO BUILD PROCESS REQUIRED** - This is pure static HTML
- Files are ready to serve as-is from any web server
- 4 main HTML files: `index.html` (homepage), `Water.html` (interactive parable), `ibraheem.html` (Prophet story), `promises-of-allah.html` (searchable promises)
- Uses Tailwind CSS and Google Fonts via CDN (external dependencies)
- All JavaScript is embedded inline - no separate JS files

### Essential Commands (Validated)
- **Serve the website locally**: `python3 -m http.server 8000` - takes 2 seconds to start. NEVER CANCEL.
- **Validate HTML**: `html5validator *.html` - takes 2 seconds. NEVER CANCEL.
  - **NOTE**: Shows 3 validation warnings for modern CSS properties (`backdrop-filter`, `background-clip: text`) and one stray tag - these are non-critical and expected.
- **Install HTML validator**: `pip install html5validator` - takes 30 seconds. NEVER CANCEL.

### Timing Expectations
- **Web server startup**: 2 seconds
- **Page loading**: < 1 second per page
- **HTML validation**: 2 seconds for all files
- **pip install html5validator**: 30 seconds

## Validation Requirements

### Manual Testing Scenarios
**ALWAYS** test these complete user scenarios after making changes:

#### Scenario 1: Homepage Navigation
1. Start web server: `python3 -m http.server 8000`
2. Navigate to `http://localhost:8000/`
3. Verify all 3 content cards display properly
4. Click each "Explore", "Experience", and "Learn" link
5. Verify navigation to respective pages works

#### Scenario 2: Interactive Water Parable (Water.html)
1. Navigate to Water.html
2. **Test slider functionality**: Drag the time slider from 0 to 100
   - At 0-32: Should show "Flourishing (نشوونما)" with green plants
   - At 33-66: Should show "Decline (زوال)" with wilted plants  
   - At 67-100: Should show "Dispersal (انتشار)" with brown scattered plants
3. **Test button navigation**: Click each of the 4 soul journey buttons
   - Verify content switches between stages: Descent, Union, Evaporation, Return
   - Verify active button highlighting works
   - Default stage 1 (Descent) should be active on page load

#### Scenario 3: Search Functionality (promises-of-allah.html)
1. Navigate to promises-of-allah.html
2. **Test search**: Type "patience" in search box and press Enter
   - Should filter to show only "7. For Patience (Sabr)" section
3. **Test search**: Type "paradise" and press Enter
   - Should show only "1. The Promise of Paradise (Jannah)" section
4. **Test search**: Clear search box and press Enter
   - Should show all 14 promises sections again
5. **Test scroll-to-top**: Scroll down, click the up arrow button
   - Should smoothly scroll back to top
   - Button appears when scrolled >300px, hidden when at top

### Browser Testing
- **Use browser tools for interactive testing** - Python server + Playwright/browser automation
- All pages work correctly despite CDN blocking warnings (expected in sandboxed environments)
- Interactive JavaScript features all function properly

## Technical Details

### Dependencies
- **External**: Tailwind CSS (CDN), Google Fonts (CDN) - both optional for functionality
- **Python**: Built-in `http.server` module for local serving
- **Validation**: `html5validator` Python package

### File Information
- **Total files**: 4 HTML pages, 1 GitHub workflow
- **Size**: index.html (149 lines), Water.html (252 lines), ibraheem.html (227 lines), promises-of-allah.html (361 lines)
- **No separate CSS, JS, or config files** - everything is self-contained

### GitHub Actions
- **Deployment**: `.github/workflows/static.yml` deploys to GitHub Pages automatically
- **No CI/CD testing** - manual validation required

## Common Tasks

### Adding New Content
- Edit HTML files directly - no compilation step needed
- Always validate HTML after changes: `html5validator filename.html`
- Test interactivity with browser tools if adding JavaScript

### Debugging Issues
- **Interactive features not working**: Check browser console for JavaScript errors
- **Styling issues**: Verify Tailwind CSS classes and inline styles
- **Search not filtering**: Check JavaScript event listeners in promises-of-allah.html

### Pre-commit Validation
**ALWAYS** run these commands before pushing changes:
1. `html5validator *.html` - Fix any NEW critical errors (ignore the 3 known warnings)
2. Start local server and manually test affected interactive features
3. Verify all navigation links work correctly

## Project Context

### Purpose
Educational Islamic content website featuring:
- Interactive Quranic parable visualization (Water.html)
- Searchable collection of divine promises with Hadith references
- Traditional Islamic wisdom and stories

### Technology Choices
- **Pure HTML**: Maximum compatibility and simplicity
- **Inline JavaScript**: Self-contained, no build dependencies
- **CDN resources**: Reduces local file complexity
- **Static hosting**: Perfect for GitHub Pages deployment

### Frequently Referenced Files
```
/home/runner/work/ForAllah/ForAllah/
├── index.html              # Homepage with navigation cards
├── Water.html              # Interactive parable with sliders/buttons  
├── ibraheem.html           # Static content about Prophet
├── promises-of-allah.html  # Searchable promises with JavaScript
└── .github/
    └── workflows/
        └── static.yml      # GitHub Pages deployment
```

This is a complete, working Islamic educational website requiring no build process - just serve and use.