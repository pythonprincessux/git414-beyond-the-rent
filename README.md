# Beyond the Rent: CSS Architecture Package

**Author:** Kiara McRae  
**Course:** GIT 414  
**Project:** Housing information guide

## Purpose and Scope

For this week's assignment, I built an architecture package that establishes the first reusable CSS system for my site, Beyond the Rent. The demonstration that I built to start with includes the navigation, housing information cards, a call-to-action link, an informational callout, and a property visit checklist. Just some basics to provide knowledge and guidance throughout the renter journey and their process.

The site uses only uses html and css. The native checkboxes support checklist interaction without JavaScript. Selections are not stored by the site. This is an architecture demonstration, so this was intentional so the site's functionality could be understood. 

## Files

- `index.html`: is the semantic demonstration page.
- `css/styles.css`: is the layered stylesheet to provide the layout and neutral colors.
- `evidence/`: are my screenshots from the browser testing I conducted in devtools.
- `README.md`: has the in detail layout of the page's architecture, refactoring, testing, and my AI disclosure notes.

## CSS Organization and Cascade Strategy

The declared layer order I selected is:

`reset, base, layout, components, utilities, states, overrides, print`

Reset takes care of the box sizing and default margins. Base defines the shared tokens and document styles. Layout controls the containers, spacing, wrapping, and the responsive grid. Components define the reusable interface patterns I have. Utilities give small adjustments, and states define all of the interaction and selection feedback.

The overrides layer is being saved for any documented exceptions I may come across and is currently and intentionally empty. Print rules appear last so printed output can replace screen presentation.

Normal declarations in layers that come later take priority over normal declarations in earlier layers. Most selectors will typically use classes, with limited descendant selectors for the component elements. There are currently no ID selectors or `!important` declarations to be made for this week's assignment.

## Custom Properties and Token Decisions

- **Color:** I used purpose based tokens to define backgrounds, text, brand, borders, highlights, completion feedback, and focus.
- **Typography:** System fonts do not use any external font requests. Arial supports body text, Georgia distinguishes headings, and the main title uses a fluid size for easy readability and scanning for the viewer/user.
- **Spacing:** Here, I am using four shared spacing values control gaps, padding, and section separation to avoid cramped and overcluttering for the viewer/user. 
- **Shape:** I chose the shared border width and radius tokens keep all of the component edges consistent.
- **Sizing:** A 72rem container limit controls page width, while a 65ch utility is limiting to the paragraph length. 
- **Focus:** A blue focus outline uses shared width and offset tokens to navigate the site page with keyboard access only. (Tab button, space bar, arrows, and enter keys).
- **Component scope:** `.card` defines the `--card-padding` and `--card-background` locally, allowing the later card variations without changing any of the global tokens.

## Components, Utilities, and States

The five component patterns used on the site are the navigation, button-style links, cards, callouts, and checklist controls. The header, footer, and skip link also have repeatable and shared styles.

The three utilities are:

- `.u-measure`: limits the text width.
- `.u-uppercase`: styles any short introductory labels.
- `.u-text-center`: centers the footer text at the bottom of the page.

States include link and button hover, keyboard focus through `:focus-visible`, current-page navigation through `aria-current="page"`, and checked checklist items. Checked items keep the native checkbox indicator and receive bold, crossed-out text to give the same idea of actually crossing off a list for the viewer/user.

Naming uses readable component classes such as `.card` and `.callout`, a component element name for `.checklist__item`, and a `u-` prefix for the utilities.

## Refactoring Evidence

The earlier draft that I submitted included a comparison table, resource list, secondary button variation, and their supporting styles. The revised package takes out those demonstration sections to focus on the five core patterns as decribed above this week.

The shared header and footer padding and backgrounds are now grouped into one rule. Hero and section spacing will also share one rule. The smaller spacing scale replaces the earlier collection of spacing values.

The card pattern keeps one reusable class applied to the three articles. Card specific properties keep the future variations within the component instead of requiring multiple, separate copies of the complete card rule.

The earlier and revised versions are kept in my GitHub repository history for comparison. This refactor reduces the scope and shared declarations.

## Browser Checks

I completed all of my testing manually in Chrome using the local Live Server page and launching devtools.

### Wide Layout and Recorded Limitation

Chrome’s responsive toolbar showed 1280px, while devtools measured the card grid at 682px with two 329px columns. Two cards appeared on the first row and the third was wrapped below. However, there was still no overflow as all the content displayed on the page without appearing cropped or having to scroll horizontally. 

The discrepancy between the selected viewport and measured layout is unresolved as of now, this will be something I work to correct over the remainder of the course. A three column layout at an actual 1280px layout viewport was not confirmed. I will have to do additional testing here before final release.

Evidence: `evidence/wide-1280.png`

### Narrow Layout

I tested this page by using the 375px responsive setting for card stacking, navigation wrapping, readability, and the horizontal overflow.

Evidence: `evidence/narrow-375.png`

### Keyboard and Checklist

When completing my keyboard testing, I covered the Tab navigation, visible focus, and Space bar activation of native checkboxes. The checked state was reviewed for its bold and crossed-out text treatment. Everything worked as expected.

Evidence: `evidence/keyboard-focus.png`

### Print

I tested the chrome print preview as well.  The preview generated two pages, removed the site navigation and the call-to-action button, and displayed content with dark text on a white background. Cards changed to a single column layout as expected.

Print rules also discourage the breaks inside individual checklist items.

Evidence: `evidence/print-preview.png`

These checks cover this demo page in when using the chrome browser. Other browsers and the completed capstone pages will still need their own testing.

## AI Disclosure

I used ChatGPT to suggest the organization, token names, and the refactoring options. 

I considered an initial larger version and a simplified version. I selected the smaller version, which removed the comparison table, resource list, secondary button variation, and related styles while retaining the required core patterns.

I applied my code in VS Code and completed all of the browser checks myself and verified browser behavior. AI also assisted with interpreting screenshot I tried to troublehsoot regarding the cards not stacking on top of each other, but instead displaying the top two and then wrapping the third. I recorded the unresolved viewport discrepancy instead of reporting it as a successful three column test.