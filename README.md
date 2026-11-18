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

