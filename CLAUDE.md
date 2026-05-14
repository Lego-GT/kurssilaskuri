# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview
This is a Finnish high school course planner ("Koululukkari") for LOPS 2021 curriculum. The tool helps students select courses to reach the required 150 points for graduation. It features a clean, modern interface with soft colors that complement the background image, using elegant typography (Playfair Display and Montserrat) and saves user selections to localStorage.

## Code Structure
The project consists of a single HTML file (`koululukkari.html`) that contains:
- HTML structure with embedded CSS and JavaScript
- Course data defined in the `subjects` array
- State management using localStorage (key: 'lops_retro_v1')
- Core functions: `renderGrid()`, `updateExtra()`, `save()`, `updateStats()`, `resetData()`
- Event handlers for course selection and extra points input

## Common Development Commands
As this is a static HTML/CSS/JS project:
- **View**: Open `koululukkari.html` in any web browser
- **Development**: Edit the file directly with any text editor
- **Testing**: Manual verification in browser - check:
  - Course selection toggles active state correctly
  - Point calculations update properly
  - LocalStorage persistence works
  - Reset function clears all data
  - Responsive design works at different screen sizes
  - UI interactions (hover effects, animations) function correctly
  - Clickable squares display point values (not course IDs) and are sized according to point values (1pt=w1, 2pt=w2, 3pt=w3)
- **Debugging**: Use browser developer tools to:
  - Inspect elements and styles
  - Debug JavaScript in console
  - Check localStorage state under Application tab
  - Monitor network requests (though this app runs entirely client-side)

## Key Implementation Details
1. **Course Data Structure**: Each subject has an array of courses with:
   - `i`: course identifier
   - `p`: point value (displayed in clickable squares and used for sizing)
   - `t`: type (req/opt/loc)
   - `a`: optional flag for ABI courses

2. **State Management**: 
   - Course selections stored in localStorage as `{courseId: boolean}` pairs
   - Extra points stored separately as `extra` property
   - State object structure: `{ extra: number, [subject-id]: boolean, ... }`

3. **Design System**:
   - Color palette: Soft, modern colors with blue primary (#4a6fa5) and accent colors for course types
   - Typography: Playfair Display for headings, Montserrat for body text
   - Layout: Card-based design with glassmorphism effects (blur + transparency)
   - Interactions: Hover effects, click animations, and subtle transitions
   - Responsiveness: Mobile-friendly layouts that adapt to different screen sizes
   - Sizing: Course boxes sized by point value (w1=34px for 1pt, w2=54px for 2pt, w3=74px for 3pt)

4. **Core Logic**:
   - Point calculation sums selected course points + extra points
   - Remaining points calculated as max(0, 150 - total)
   - Render function rebuilds entire grid on each state change
   - Event delegation through individual course box onclick handlers
   - Clickable squares display course point values (`course.p`) and use width classes `w${course.p}`

## Maintenance Notes
- All code is contained in one file for simplicity
- To modify course data, edit the `subjects` array
- To change styling, modify CSS variables or rules in the :root section
- To add features, consider the existing function structure and patterns
- Current implementation balances readability with functionality
- The design uses CSS variables for easy theming and modernization