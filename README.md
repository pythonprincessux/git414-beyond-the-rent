## Module 3: Responsive Layout System
Kiara McRae | GIT 414

### Building on Module 2
For this week, I decided to update the extends of my existing CSS architecture rather than replacing
it. The reset, base, layout, components, utilities, states, overrides,
and print layers remain in place. Existing tokens, navigation, cards,
checklist controls, keyboard focus, and print styles are retained.

### Responsive Foundation
The centered container uses a flow that has logical inline sizing, automatic inline
margins, flexible side gutters, and a maximum size of 72rem. Hero and
section spacing use clamp(2rem, 5vw, 4rem).

Additional logical properties include border-block-start,
border-block-end, min-inline-size, inset-block-start, and
inset-inline-start.

### Two Meaningful Grid Layouts
1. The housing-information card grid uses two of my favorites:
   repeat(auto-fit, minmax(min(100%, 18rem), 1fr)).
   Cards wrap according to the available space while preserving readable
   widths and allowing a single card to fit a narrow container.

2. The hero uses one flexible column by default. At 60rem, it
   uses minmax(0, 3fr) and minmax(18rem, 2fr) to place the introduction
   beside the rental-planning card.

These layouts support the site's tasks of reviewing rental costs
and preparing questions for a property visit, making it easier for the user/viewer. 

### Content-Based Breakpoint
The hero on the site provides a 60rem breakpoint provides room for the long main heading
and the planning card to share a row. Below that threshold, stacking
preserves the space for text and controls.

My testing included widths immediately below and above the threshold:
944px and 976px. This breakpoint concerns the hero content; the
housing-card grid determines its column count independently.

### Container-Query Component
The rental-planning card sits inside `.resource-shell`, which declares
the named inline-size container `planning`.

The card has a stacked default layout. When its container reaches
36rem, the query places its text beside its action link using
minmax(0, 1fr) and fit-content(12rem).

The component responds to its own available space. It may therefore
use a horizontal arrangement in a full-width stacked hero and return
to a vertical arrangement in a narrower hero column.

### Subgrid Alternative
Subgrid is not necessary for the current content. Housing cards use
the same component structure, a shared gap, and a flexible column
layout. Automatic block-start margin on each card link places it
toward the bottom of the card.

Using this alternative provides the consistent spacing and link placement without requiring
shared internal row tracks. Subgrid can also be reconsidered if future
cards need headings and descriptions aligned across shared rows.

### Preference and Fallback Strategy
The prefers-contrast: more query darkens component borders, increases
their width to 2px, and increases focus outlines to 4px.

If container queries are unsupported, the planning card retains its
stacked default. Its text and link remain available. This fallback
path is documented; unsupported-browser behavior has not been
separately verified.

Print extensions keep the hero and planning card in a simple block
layout and preserve readable dark text on a white background.

### Testing Evidence
I completed all of the manual checks and testing in Chrome using the local Live Server page.
The Module 3 evidence records these conditions:

- Narrow viewport: 375px.
- Medium viewport: 768px.
- Wide viewport: 1280px.
- Browser zoom: 200%.
- Keyboard navigation and visible focus.
- Increased-contrast preference emulation.

Evidence files:
- evidence/module3/narrow-375.png
- evidence/module3/medium-768.png
- evidence/module3/wide-1280.png
- evidence/module3/zoom-200.png
- evidence/module3/keyboard-focus.png
- evidence/module3/contrast-more.png

The contrast screenshot shows prefers-contrast: more selected,
the active CSS rule, and the checklist's darker, thicker border.

All of these checks apply to the current demonstration page in Chrome.

### AI Disclosure
For this week's assignment, I used ChatGPT to explain syntax, suggest edge cases, and help troubleshoot through the styles css layout concerns. I verified all browser behavior and completed all testing and the evidence myself.