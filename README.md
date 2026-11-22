## Module 3: Responsive Layout System
Kiara McRae | GIT 414

# Beyond the Rent

Kiara L. McRae | GIT 414 | Final Production Website Capstone

## Website and repository

- [Published website](https://pythonprincessux.github.io/git414-beyond-the-rent/)
- [Repository](https://github.com/pythonprincessux/git414-beyond-the-rent)

Beyond the Rent helps first-time renters organize questions about rental
charges, move-in payments, utilities, and written terms before a property visit.

## Final page scope

- Home: introduces the guide and links to rental-cost topics and the checklist.
- Fees: organizes rental-cost questions and reminders to confirm written terms.
- Checklist: provides four native checkbox controls with clear instructions.

The original six-page proposal was reduced to three implemented pages.
Cost Comparison, Glossary, and Resources were deferred. The original
planning package is retained as historical evidence.

## Project structure

- index.html: Home page.
- fees.html: rental-cost questions.
- checklist.html: property visit checklist.
- css/styles.css: shared layered stylesheet.
- assets/: website graphics and Module 6–7 evidence screenshots.
- evidence/: Module 5 accessibility screenshots.
- docs/: planning documents and final release report.

## Documentation

- [Original capstone planning package](docs/capstone-planning-package.pdf)
- [CSS system planning review](docs/css-system-planning-review.pdf)
- [Scope and release plan](docs/final-scope-release-plan.pdf)
- [Final release report and technical defense](docs/final-release-report.pdf)

The final report documents implementation decisions, testing, remediation,
remaining limitations, and meaningful AI assistance.

## Final CSS implementation decisions

These implemented values make the earlier CSS planning decisions specific:

- Background: #FFFAF3.
- Surface: #FFFFFF.
- Text: #242B32.
- Brand and primary buttons: #763820.
- Button hover: #542716.
- Default border: #A79D91.
- Highlight: #F3E7D8.
- Checked-item highlight: #E8F1E9.
- Keyboard focus: #005FCC.
- Body font: Arial, Helvetica, sans-serif.
- Heading font: Georgia, "Times New Roman", serif.
- Body size: 1rem with 1.6 line height.
- Main heading: clamp(2rem, 1.5rem + 2.5vw, 3.5rem).
- Paragraph reading measure: 65ch.
- Main container maximum: 72rem.

The site uses shared CSS layers, tokens, reusable components, responsive
grids, a planning-card container query, visible focus, and print styles.
Core reading, navigation, and checkbox interaction require no JavaScript.

## Module 7 release summary

### Validation and metadata

Home and Checklist were checked with the HTML validator during the release
sprint. Module 6 includes HTML validation evidence for all three pages.

The CSS validator reported three findings involving container-query syntax
and two warnings concerning static checking of CSS variables. These findings
are documented. This is not described as an error-free CSS validation pass.

Published Home source inspection confirmed its title, description,
canonical URL, Open Graph tags, and WebPage JSON-LD.

The Schema.org Validator detected one WebPage with zero errors and warnings
during Module 6 testing.

### Links and interaction

I manually checked primary navigation across all three pages and at least
five Home content/action links. Tested destinations worked.

Keyboard checks covered Tab, Shift+Tab, Enter, visible focus, skip-link
navigation, and Space to toggle checklist controls.

### Responsive and browser checks

Home was checked at 375px, 768px, and 1280px widths and 200% browser zoom.

I also tested the published site in Safari 26.6.2. All three pages,
navigation links, checklist controls, narrow-window layout, and 200% zoom
worked without observed problems.

Firefox and actual mobile devices were not tested.

### Performance

The recorded Lighthouse mobile diagnostic used Slow 4G throttling:

- Performance: 91.
- First Contentful Paint: 1.4 seconds.
- Largest Contentful Paint: 1.4 seconds.
- Total Blocking Time: 0 milliseconds.
- Cumulative Layout Shift: 0.
- Speed Index: 9.8 seconds.

Speed Index remains an unresolved finding. Its cause was not established,
and no measured improvement is claimed.

### Release evidence

- [Home HTML validation](assets/m7-html-home.png)
- [Checklist HTML validation](assets/m7-html-checklist.png)
- [CSS validator findings](assets/m7-css.png)
- [Home at 375px](assets/m7-home-narrow-375.png)
- [Home at 768px](assets/m7-home-medium-768.png)
- [Home at 1280px](assets/m7-home-wide-1280.png)
- [Home at 200% zoom](assets/m7-home-zoom-200.png)
- [Keyboard link focus](assets/m7-keyboard-link-focus.png)
- [Keyboard checkbox focus](assets/m7-keyboard-checkbox-focus.png)
- [Lighthouse performance](assets/m7-lighthouse-performance.png)
- [Lighthouse metrics](assets/m7-lighthouse-metrics.png)
- [Lighthouse diagnostics](assets/m7-lighthouse-diagnostics.png)
- [Published metadata source](assets/m7-metadata-source.png)
- [Safari visual check](assets/m7-safari-check.png)
- [Safari version](assets/m7-safari-version.png)

### Known limitations

- Checklist selections are temporary.
- The original 320px acceptance criterion is not demonstrated by the
  saved release screenshots.
- Broader screen-reader and actual mobile-device testing remain incomplete.
- CSS validator findings and the Speed Index concern remain documented.
- Platform-specific social preview rendering has not been verified.
- Accessibility spot checks do not establish complete WCAG conformance.
- Metadata and structured data do not guarantee rankings or rich results.

## AI disclosure

I used ChatGPT to help organize documentation  and troubleshoot HTML/CSS.

I reviewed suggested changes against the visible site, applied selected
edits, performed browser checks, and collected evidence myself.

## Historical module documentation

The sections below preserve earlier development notes. The release summary
and final report above describe the final testing scope and known limitations.

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


## Module 4: Media and Typography Optimization

Kiara McRae | GIT 414

Repository: https://github.com/pythonprincessux/git414-beyond-the-rent

### Asset Inventory

- Graphic: assets/rental-costs.svg
- Source: I made the SVG code incorporated into this project.
- Permission notes: No stock images or external icon libraries were used.
  No third-party license was provided with the code.
- Purpose: Summarize recurring charges, move-in payments, and utility
  responsibilities.
- Format and dimensions: SVG, 480 × 240.
- Body fonts: Arial, Helvetica, sans-serif.
- Heading fonts: Georgia, "Times New Roman", serif.
- Fonts come from the visitor's device.

- No audio, video, animation, or embeds are used.
- Evidence screenshots are documentation included in my evidence folder for submission purposes only.

### Image Decisions

The SVG scales without needing separate raster image sizes, so srcset
and sizes are not needed. Its simple composition works across widths
without cropping or a picture element.

The graphic displays at a maximum width of 30rem and shrinks to fit
smaller containers. It contains vector shapes and text, with no embedded
photographs. No separate compression comparison was performed.

### Accessibility

The informative graphic uses this alt text:
"Rental cost topics: recurring charges, move-in payments, and utility
responsibilities."

Related text is also available on the page. I checked the image's
accessibility information in Chrome DevTools.

Captions, transcripts, and iframe titles are not applicable because
this capstone has no audio, video, or embeds.

### Typography

- Body text: 1rem, line height 1.6.
- Main heading: fluid sizing from 2rem to 3.5rem using clamp().
- Section headings: fluid sizing from 1.5rem to 2rem using clamp().
- Card headings: 1.25rem.
- Heading line height: 1.2.
- Paragraph line length: maximum 65ch.
- Shared tokens control spacing and typography.


### Layout Stability

The image has explicit width and height attributes and a 2:1 CSS
aspect ratio to reserve space while it loads.

### Testing

I checked the page in Chrome at:
- 375px, 768px, and 1280px widths.
- 200% browser zoom.
- Slow 4G with caching disabled.

I also checked SVG loading, dimensions, and alt text.
Screenshots are stored directly in evidence/.

During my testing, I found missing spacing, border, radius, and container
tokens. I restored them after collecting the evidence. I did not
repeat the full checks afterward, so the screenshots and audit
document the version before that final fix.

### Recorded Lighthouse Results

- Performance: 98.
- Accessibility: 100.
- Best Practices: 100.
- SEO: 100.
- First Contentful Paint: 1.9 seconds.
- Largest Contentful Paint: 2.0 seconds.
- Total Blocking Time: 0 milliseconds.
- Cumulative Layout Shift: 0.
- Speed Index: 2.5 seconds.

### AI Disclosure

For this week's deliverable, I used ChatGPT to help compare options, draft my checklists and troubleshoot my syntax around why my spacing was so tight on my page. 

I applied the changes and collected the browser evidence myself.
The final token restoration was not fully retested. I realized the spacing was too tight after I collected all of my screenshots but it has been fixed! 


Beyond the Rent
Module 5: Accessibility Conformance and Inclusive Quality
Kiara McRae
November 18, 2026

Repository:
https://github.com/pythonprincessux/git414-beyond-the-rent


## TEST SCOPE

I tested three capstone pages:

1. Home (index.html)
   Tested the shared navigation, planning card, links, and checklist.

2. Fees (fees.html)
   Tested rental information, headings, the informative SVG, and card links.

3. Checklist (checklist.html)
   Tested checkbox labels, instructions, keyboard operation, focus, and checked states.


## AUTOMATED RESULTS

Chrome Lighthouse Accessibility scores:

Home: 100
Fees: 100
Checklist: 100

The original Home page also scored 100. The changes improved usability and page organization rather than raising the automated score.


## MANUAL TESTING

I tested the following in Chrome on macOS:

- Tab and Shift+Tab navigation.
- Enter to activate links.
- Space to toggle checkboxes.
- Visible focus and logical focus order.
- Ability to move out of controls without a keyboard trap.
- Skip-link navigation to the main content.
- Navigation between all three pages.
- Correct current-page indication.
- Responsive behavior at 375 CSS pixels.
- Readability and controls at 200% browser zoom.
- Increased text spacing without clipping or overlapping.
- Landmarks, headings, link purposes, and native HTML.
- Image alternatives and checklist instructions.

I also retested the new Fees and Checklist pages at 200% zoom and with increased text spacing. No problems were observed.

Text-spacing settings:
Line height: 1.5
Letter spacing: 0.12em
Word spacing: 0.16em
Paragraph bottom margin: 2em


## FINDINGS AND REMEDIATION

These findings include usability improvements and passing checks.

1. Limited page scope

Evidence: The original source contained one page with three sections.

Impact: It did not provide the required three-page test scope.

Priority: High for assignment scope.

Change: Added dedicated Fees and Checklist pages using the existing CSS.

Retest: All three pages loaded successfully and were tested.


2. General card-link wording

Evidence: Links included “Prepare your questions” and “Plan your visit.”

Impact: Their checklist destination was less clear when scanning links.

Priority: Medium.

Change: Updated the link labels to explicitly mention the checklist.

Retest: Each link opened checklist.html successfully.


3. Strikethrough on checked text

Evidence: m5-before-checked.png shows lines crossing checked labels.

Impact: Users may still need to read the completed questions.

Priority: Medium usability improvement.

Change: Removed strikethrough while retaining the checkmark, highlight, and bold text.

Retest: Text remained readable and checkboxes still toggled.
Evidence: m5-after-checked.png.


4. Links needed updating for separate pages

Evidence: Navigation and action links originally used same-page fragments.

Impact: Leaving them unchanged would prevent the intended navigation to the new pages.

Priority: Medium.

Change: Updated navigation, buttons, and card links to the appropriate HTML pages.

Retest: Navigation and checklist links worked as expected.


5. Separate page identities

Evidence: The new pages were initially copied from Home.

Impact: Keeping the copied title, heading, and current-page state would make page identity confusing.

Priority: Medium.

Change: Added unique document titles, one main heading per page, appropriate subheadings, and the correct aria-current state.

Retest: Page identities and current navigation states were checked. All three final Lighthouse Accessibility scores were 100.


6. Checkbox naming and grouping

Evidence: m5-accessibility-tree.png.

Impact: Incorrect names could make checklist controls difficult to understand with assistive technology.

Priority: Medium verification.

Disposition: Retained native checkbox inputs wrapped in labels, with fieldset and legend grouping. No naming fix was needed.

Retest: The sampled checkbox exposed its expected role, full label, and focusable state.


## CONTRAST RESULTS

Chrome DevTools reported:

Brown link text on white: 8.91:1
White button text on normal brown: 8.91:1
White button text on darker hover brown: 12.5:1

The sampled text combinations passed the displayed AA and AAA contrast checks.

This was a sample, not a measurement of every color and state.


## FORMS, MEDIA, AND MOTION

The checklist uses native checkbox inputs inside labels.

A fieldset and legend identify the group. aria-describedby connects the group to its instructions.

The checklist does not submit information. Required fields, submission errors, and submit buttons are not applicable.

Selections reset on reload in the tested browser. The page explains that selections are not saved.

The rental-cost SVG is informative and has descriptive alt text. Its width and height reserve space.


## ACCESSIBILITY-TREE SAMPLE

I sampled the first checklist checkbox in Chrome DevTools.

The tree showed:

Group: Questions to bring
Role: checkbox
Name: Request a list of recurring monthly charges.
Focusable: true

This screenshot was captured on index.html before the dedicated checklist page was added. The same native labeling structure was retained.



## EVIDENCE

All screenshots are stored in evidence/.

Baseline:
- m5-before-lighthouse.png
- m5-before-focus-check.png
- m5-before-home-hover.png
- m5-before-checked.png

Manual testing:
- m5-accessibility-tree.png
- m5-after-checked.png
- m5-text-spacing.png
- m5-zoom-200.png
- m5-contrast-link.png
- m5-contrast-button-2.png
- m5-contrast-button.png

Final pages and automated testing:
- m5-after-fees.png
- m5-after-checklist.png
- m5-after-lighthouse-home.png
- m5-after-lighthouse-fees.png
- m5-after-lighthouse-checklist.png

Some screenshots show the original single-page version. Final page screenshots and Lighthouse results show the three-page version.


## CONFORMANCE SUMMARY AND LIMITATIONS

The tested pages appeared usable during the documented keyboard, responsive, zoom, text-spacing, and semantic checks.

Changes clarified link destinations, improved checked-text readability, and established three connected pages with appropriate page identities.

Visible focus and native checkbox labeling were already present and were retained.


Testing was limited to Chrome on macOS, responsive emulation, manual checks, Lighthouse, and one accessibility-tree sample.

Before final release:
- Repeat testing on the published website.
- Test other browsers and actual mobile devices.
- Perform a broader screen-reader review.
- Check all meaningful color states.
- Review any future forms, tables, media, or motion.


REFERENCES

WCAG 2.2:
https://www.w3.org/TR/WCAG22/

WAI Easy Checks:
https://www.w3.org/WAI/test-evaluate/easy-checks/

Chrome Lighthouse Accessibility:
https://developer.chrome.com/docs/lighthouse/accessibility/

### AI disclosure

For this week's deliverable, I used ChatGPT to help organize the audit, suggest checks, explain HTML and CSS changes.

I considered suggested link labels, checked-state styling, page structure, and testing instructions. I applied the selected changes, performed the browser tests, checked the results, and collected the evidence myself as shown in the evidence folder screenshots.



## Module 6: Discoverability and Structured Content Package

Kiara McRae

Repository: https://github.com/pythonprincessux/git414-beyond-the-rent

Published site: https://pythonprincessux.github.io/git414-beyond-the-rent/

### Metadata inventory

#### Home: index.html
- Purpose: Introduce the housing guide and rental-cost topics.
- User task: Identify questions to ask before choosing a rental and open the visit checklist.
- Title: Beyond the Rent | Housing Guide
- Description: Beyond the Rent helps renters organize questions about housing costs and prepare for property visits.
- Primary heading: Look beyond the advertised rent.
- Canonical: https://pythonprincessux.github.io/git414-beyond-the-rent/
- Supporting links: “Fees” opens fees.html; “Use the visit checklist” opens checklist.html.
- Visible content: Monthly charges, move-in expenses, rental terms, and property visit preparation.

#### Fees: fees.html
- Purpose: Explains the rental-cost topics to discuss with a property contact.
- User task: Helps prepare questions about recurring charges, move-in payments, and written terms.
- Title: Rental Fees and Questions | Beyond the Rent
- Description: Organizes the questions about recurring rental charges, move-in expenses, utility responsibilities, and written rental terms.
- Primary heading: Questions to organize your search
- Canonical: https://pythonprincessux.github.io/git414-beyond-the-rent/fees.html
- Supporting links: “Prepare your monthly-charge checklist” and “Review the move-in checklist” both open checklist.html.
- Visible content: Monthly charges, move-in expenses, written information, and a reminder to confirm details.

#### Checklist: checklist.html
- Purpose: Provide questions to bring to a property visit.
- User task: Review and check questions about monthly charges, move-in payments, utilities, and written confirmation.
- Title: Property Visit Checklist | Beyond the Rent
- Description: Prepare for a property visit with questions about recurring charges, move-in payments, utilities, and written terms.
- Primary heading: Property visit checklist
- Canonical: https://pythonprincessux.github.io/git414-beyond-the-rent/checklist.html
- Supporting links: “Home” opens index.html; “Fees” opens fees.html.
- Visible content: Four labeled checkboxes and instructions explaining that selections are not saved.

### Headings, links, and accessibility

Each page has a primary h1. Section and card headings organize supporting content. Navigation and content links use HTML anchors with real href values. Each page identifies its current navigation item with aria-current="page".

This work builds on Module 5 improvements to checklist link wording, checked-text readability, keyboard focus, and separate page navigation. Earlier evidence is still in my evidence folder in this repo.

### Canonical, robots, and sitemap decisions

Canonical links apply now because the site is published. Each page identifies its own preferred public URL. The Home canonical uses the directory URL rather than the equivalent index.html address.

No restrictive robots meta tag was added because these pages are intended to be public. No project-level robots.txt was added. A robots.txt file must be served from the host root, not this GitHub Pages project subdirectory. 

An XML sitemap is deferred for this small, three-page site because all important pages are linked through navigation. If the site grows, I would create a sitemap containing the preferred canonical URLs and submit it through Search Console. 

### Home social metadata

- og:title: Beyond the Rent | Housing Guide
- og:description: Organize questions about monthly charges, move-in expenses, and rental terms before choosing a place to live.
- og:url: https://pythonprincessux.github.io/git414-beyond-the-rent/
- og:type: website
- og:image: https://pythonprincessux.github.io/git414-beyond-the-rent/assets/beyond-the-rent-social.png
- og:image:alt: Beyond the Rent: Look beyond the advertised rent. Monthly charges, move-in expenses, and property visit checklist.

I created the preview image in Canva using the site's colors and visible topics. 

### Structured data

Home includes a JSON-LD WebPage object inside the head. It describes the page name, public URL, description, and English language.

WebPage fits this general housing guide. I did not add rental listings, prices, ratings, or other details that are absent from the visible content.

The Schema.org Validator fetched the published Home page and detected one WebPage with 0 errors and 0 warnings. This validates the detected structured data.

### Image discoverability

#### assets/rental-costs.svg
- Used on: Home and Fees.
- Dimensions in HTML: 480 × 240.
- Alt text: Rental cost topics: recurring charges, move-in payments, and utility responsibilities.
- Context: Appears near rental-cost headings, explanatory text, and topic cards.
- Relevance: Reinforces the rental-cost topics discussed on the page.
- Filename: Describes the subject without keyword stuffing.

#### assets/beyond-the-rent-social.png
- Used for: Home social previews.
- Design target: 1200 × 630 pixels.
- Text alternative: Supplied through og:image:alt.
- Context: Represents the Home page through its name, tagline, and rental-cost topics.
- Relevance: Uses content already represented on the site.
- Filename: Identifies the site and the image's social-preview purpose.

Validation screenshots are supporting documentation, not content images used in the website interface.

### Validation evidence

- assets/m6-schema-validation.png: Published Home WebPage validation showing 0 errors and 0 warnings.
- assets/m6-html-home.png: W3C Nu HTML Checker result for Home.
- assets/m6-html-fees.png: W3C Nu HTML Checker result for Fees.
- assets/m6-html-checklist.png: W3C Nu HTML Checker result for Checklist.
- assets/m6-page-source.png: Published Home source inspection.

Source inspection checks the title, description, canonical URL, Open Graph tags, and JSON-LD inside the head. The saved validator results document the checks performed. HTML syntax validation does not establish search indexing, ranking, or identical social previews.

### Unsupported claims I will not make

1. These metadata changes guarantee first-place search rankings or increased traffic. I have no ranking or traffic evidence supporting that claim.
2. Valid WebPage JSON-LD guarantees a Google rich result. Schema validation does not prove eligibility or guarantee display.
3. Every social platform will show the exact same preview. Platforms can interpret, crop, and cache preview information differently.

### Sources

- Schema.org WebPage definition:
  https://schema.org/WebPage
- Schema.org Validator:
  https://validator.schema.org/
- Open Graph protocol:
  https://ogp.me/
- Google Search Central, robots.txt introduction:
  https://developers.google.com/search/docs/crawling-indexing/robots/intro
- Google Search Central, sitemap guidance:
  https://developers.google.com/search/docs/crawling-indexing/sitemaps/overview
- Google Search Central, structured-data guidelines:
  https://developers.google.com/search/docs/appearance/structured-data/sd-policies
- W3C Nu HTML Checker:
  https://validator.w3.org/nu/

### AI disclosure

For this week's deliverable, I used ChatGPT to help draft alternatives, organize my inventories, and explain my documentation. I changed the visible page content, applied the edits, created the social image in Canva, and performed the browser validation checks.

The implemented changes include page-specific canonical URLs, Home social metadata, a social preview image, and Home WebPage JSON-LD. Existing unique titles and descriptions were kept from the previous weeks. Placeholder URLs from earlier practice were all replaced with the published GitHub Pages address.