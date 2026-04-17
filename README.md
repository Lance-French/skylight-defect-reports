# Skylight Defect Reports

QA defect reports, screenshots, and video walkthroughs for the [Skylight](https://ourskylight.com) web application, documented as part of a QA Engineer assessment. Testing was performed from the perspective of a primary parent setting up and managing a household of four children (ages 4, 8, 12, and 16).

For the companion Playwright automation scripts, see [skylight-automation](https://github.com/Lance-French/skylight-automation).

## Defect Summary

| ID | Title | Severity | Type |
|----|-------|----------|------|
| 001 | Activation code prompt persists on already activated device | Major | Functional, UI/UX |
| 002 | Calendar filter toggles clipped off screen | Minor | UI/UX |
| 003 | Household email text input cut off | Minor | UI/UX |
| 004 | Blank white space below content on calendar sync pages | Minor | UI/UX |
| 005 | Linked calendar selection does not save during profile creation | Major | Functional |

## Key Findings

Defects 002, 003, and 004 share a common root cause: CSS layout properties (`flex: 1` and `overflow: clip`) applied at the component level cause content to render incorrectly across multiple pages. Addressing this at the shared component level could resolve all three defects with a single fix.

Defect 005 was discovered during automated testing with Playwright. The automation script correctly selected a linked calendar during profile creation, but the selection did not persist after saving. Manual testing confirmed the same behavior, reinforcing the value of automation as a discovery tool alongside regression coverage.

## Repo Structure

```
skylight-defect-reports/
├── README.md
└── defects/
    ├── 001/    # Activation code modal won't dismiss
    ├── 002/    # Filter toggles clipped
    ├── 003/    # Email input text cut off
    ├── 004/    # White space on sync pages
    └── 005/    # Linked calendar not saving
```

Each defect folder contains a PDF report with full reproduction steps, screenshots showing the defect, and a video walkthrough demonstrating the issue.

## Report Format

Each defect report follows a consistent structure: environment details (browser, platform, test environment), severity and frequency classification, user impact analysis written from a real-world family use case perspective, numbered reproduction steps, expected vs. actual results, and additional notes including DevTools investigation where applicable.

## Tools Used

Testing was performed in production across Chrome and Firefox on the Skylight web application. Screenshots were captured with browser-native tools and annotated to highlight defect areas. Video walkthroughs were recorded to provide full reproduction context. Browser DevTools were used for root cause investigation on layout-related defects (002, 003, 004).

## Author

**Lance French** — QA Engineer
