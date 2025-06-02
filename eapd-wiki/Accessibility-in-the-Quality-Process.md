# Accessibility Tools
The Quality team is expected to utilize these accessibility tools as part of their review process

### Screen Readers
- Windows: Built in app, [Narrator](https://support.microsoft.com/en-us/windows/complete-guide-to-narrator-e4397a0d-ef4f-b386-d8ae-c172f109bdb1)
- MAC: Built in app, [VoiceOver](https://www.apple.com/voiceover/info/guide/_1121.html)
- Any: Commonly accepted tool, [NVDA (NonVisual Desktop Access)](https://www.nvaccess.org/)
### Cypress-Axe
- Our Cypress tests have [cypress-axe](https://github.com/component-driven/cypress-axe) built within them for automated accessibility testing. These tests are run on every single page to ensure no accessibility issues get checked in. 
- A11y Standards that are checked are:
  - [WCAG 2.1](https://www.w3.org/TR/WCAG21/)
  - [WCAG 2.0](https://www.w3.org/TR/WCAG20/)
  - [Section 508](https://www.section508.gov/)
- For more information regarding cypress-axe and A11y testing, please refer to this [article!](https://medium.com/geekculture/accessibility-test-automation-with-axe-4-cypress-8994b358e730)
### WAVE Evaluation Tool 
- [WAVE](https://wave.webaim.org/extension/) is an accessibility tool that can be used to evaluate accessibility on a page!
- How to use it (Chrome Extension):
  - Navigate to the page you'd like to evaluate and click on the WAVE extension in you Google Chrome extensions. It's that simple.

# Accessibility Notes

## Navigations with Screen Reader + Tab

### Mac Voiceover:
|   | Firefox | Chrome | Edge | Safari |
|---|---|---|---|---|
| Main Navigation Bar | Firefox starts tab at top navigation. User can easily tab through account submenu and log out easily. Tabbing over the drop down menu option whites out the word. [1] | Chrome immediately starts at the eAPD navigation, so user has to tab backwards to get to account information. User can easily tab through account submenu and log out easily. Tabbing over the drop down menu option whites out the word. [1] | Like Chrome, Edge immediately starts at the eAPD navigation, so user has to tab backwards to get to account information. User can easily tab through account submenu and log out easily. Tabbing over the drop down menu option whites out the word. [1] | Like Chrome, Safari immediately starts at the eAPD navigation, so user has to tab backwards to get to account information. Tab will immediately skip the submenu. |
| eAPD Navigation | Tab will start at `Skip to Main` link. User has to tab through upper navigation to get to eAPD navigation. Voiceover picks up title and will consistently say how many list items under the link. | Tab will immediately select the first navigation link in an eAPD. Voiceover will sometimes skip to the next link title or not say the link title. This can be corrected navigating back and forth with `Tab` and `Tab+Shift` can reset Voiceover. | Like Chrome, tab will immediately select the first navigation link in the eAPD. Voiceover picks up title and is consistent through eAPD navigation. | Like Chrome, tab will immediately select the first navigation link in the eAPD. When tabbing through eAPD navigation, tab skips over all sub navigation items to the next navigation. |

### Window's Narrator:
|   | Firefox | Chrome | Edge |
|---|---|---|---|
| Main Navigation Bar | Firefox starts tab at top navigation. User can easily tab through account submenu and log out easily. Tabbing over the drop down menu option whites out the word. [1] | Chrome immediately starts at the eAPD navigation, so user has to tab backwards to get to account information. User can easily tab through account submenu and log out easily. Tabbing over the drop down menu option whites out the word. [1] | Like Chrome, Edge immediately starts at the eAPD navigation, so user has to tab backwards to get to account information. User can easily tab through account submenu and log out easily. Tabbing over the drop down menu option whites out the word. [1] |
| eAPD Navigation | Tab will start at `Skip to Main` link. User has to tab through upper navigation to get to eAPD navigation. Voiceover picks up title and will consistently say how many list items under the link. | Tab will immediately select the first navigation link in an eAPD. Voiceover will sometimes skip to the next link title or not say the link title. This can be corrected navigating back and forth with `Tab` and `Tab+Shift` can reset Voiceover. | Like Chrome, tab will immediately select the first navigation link in the eAPD. Voiceover picks up title and is consistent through eAPD navigation. |

[1] 
<img width="376" alt="Screen Shot 2022-09-14 at 1 21 28 PM" src="https://user-images.githubusercontent.com/44708048/190238103-f516e543-b415-4dd1-9c0b-2eec2b7f0971.png">

## Known Screen Reader Bugs (Chrome + VoiceOver)
When using the Chrome browser, Voiceover, the default screen reader for Mac, does not always work on subforms. When tabbing through existing subforms, such as Key Personnel and Program Management, it will read out the first input value when tabbing on to edit. When edit is selected it will usually start to automatically read a different part of the subform and not say the correct value as the user tabs through the inputs.

To mitigate this, the user can tab back out of the subform and re-tab in and the voiceover should pick up all correct input values.

Voiceover might also not indicate that there is text in a rich text area (for example: Other Funding Description or Activity Details). If this happens, the user can prompt the screen reader by utilizing the up and down arrow keys.

On the page for Assurances and Compliance, Voice over will repeat ‘No no no no’ with no current way to pause or stop.

## Known Screen Reader Bugs (Chrome + Narrator)
Tabbing into a rich text area (TinyMCE text boxes) doesn't read the text content out loud.

