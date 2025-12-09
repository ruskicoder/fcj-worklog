# Hugo Front Matter Format Reference

## Critical Configuration for Worklog Pages

This document defines the EXACT format that must be used for all worklog page front matter to ensure correct ordering and navigation in Hugo.

## Standard Worklog Front Matter Template

### English Version (_index.md)

```yaml
---
title: "Week X Worklog"
date: "YYYY-MM-DD"
weight: X
chapter: false
pre: " <b> 1.X. </b> "
---
```

### Vietnamese Version (_index.vi.md)

```yaml
---
title: "Worklog Tuần X"
date: "YYYY-MM-DD"
weight: X
chapter: false
pre: " <b> 1.X. </b> "
---
```

## Weight Parameter Rules

**CRITICAL:** The `weight` parameter MUST match the week number exactly.

| Week Folder | Weight Value | English Title | Vietnamese Title |
|-------------|--------------|---------------|------------------|
| 1.1-Week1   | weight: 1    | Week 1 Worklog | Worklog Tuần 1  |
| 1.2-Week2   | weight: 2    | Week 2 Worklog | Worklog Tuần 2  |
| 1.3-Week3   | weight: 3    | Week 3 Worklog | Worklog Tuần 3  |
| 1.4-Week4   | weight: 4    | Week 4 Worklog | Worklog Tuần 4  |
| 1.5-Week5   | weight: 5    | Week 5 Worklog | Worklog Tuần 5  |
| 1.6-Week6   | weight: 6    | Week 6 Worklog | Worklog Tuần 6  |
| 1.7-Week7   | weight: 7    | Week 7 Worklog | Worklog Tuần 7  |
| 1.8-Week8   | weight: 8    | Week 8 Worklog | Worklog Tuần 8  |
| 1.9-Week9   | weight: 9    | Week 9 Worklog | Worklog Tuần 9  |
| 1.10-Week10 | weight: 10   | Week 10 Worklog | Worklog Tuần 10 |
| 1.11-Week11 | weight: 11   | Week 11 Worklog | Worklog Tuần 11 |
| 1.12-Week12 | weight: 12   | Week 12 Worklog | Worklog Tuần 12 |

## Why Weight Matters

Hugo uses the `weight` parameter to determine page ordering in navigation menus. If multiple pages have the same weight, Hugo falls back to alphabetical sorting by folder name, which causes:

- ❌ Week 1.1 to appear after Week 1.9 (alphabetically "1.1" > "1.9")
- ❌ Week 1.10, 1.11, 1.12 to appear after Week 1.9 but before Week 1.2

By assigning unique sequential weights (1, 2, 3, ..., 12), we ensure correct chronological ordering.

## Complete Examples

### Week 1 English (_index.md)
```yaml
---
title: "Week 1 Worklog"
date: "2025-09-08"
weight: 1
chapter: false
pre: " <b> 1.1. </b> "
---
```

### Week 1 Vietnamese (_index.vi.md)
```yaml
---
title: "Worklog Tuần 1"
date: "2025-09-08"
weight: 1
chapter: false
pre: " <b> 1.1. </b> "
---
```

### Week 10 English (_index.md)
```yaml
---
title: "Week 10 Worklog"
date: "2025-11-10"
weight: 10
chapter: false
pre: " <b> 1.10. </b> "
---
```

### Week 10 Vietnamese (_index.vi.md)
```yaml
---
title: "Worklog Tuần 10"
date: "2025-11-10"
weight: 10
chapter: false
pre: " <b> 1.10. </b> "
---
```

## Field Descriptions

| Field | Purpose | Format | Notes |
|-------|---------|--------|-------|
| title | Page title in navigation | String | Use "Week X Worklog" (EN) or "Worklog Tuần X" (VI) |
| date | Page date metadata | "YYYY-MM-DD" | Use actual week start date |
| weight | Ordering priority | Integer | MUST match week number (1-12) |
| chapter | Chapter page flag | Boolean | Always `false` for worklog pages |
| pre | Prefix in navigation | String | Format: `" <b> 1.X. </b> "` with spaces |

## Validation Checklist

When updating worklog front matter:
- [ ] Weight value matches week number
- [ ] Both English and Vietnamese files have identical weight
- [ ] Date format is YYYY-MM-DD
- [ ] Title follows naming convention
- [ ] Pre value matches folder numbering (1.X.)
- [ ] Chapter is set to false
- [ ] No extra spaces or formatting issues

## Testing

After updating front matter, verify ordering:
```bash
hugo server
```

Navigate to the Worklog section and confirm weeks appear in order: 1 → 2 → 3 → ... → 12

## Reference Implementation

See `content/1-Worklog/1.1-Week1/_index.md` and `content/1-Worklog/1.1-Week1/_index.vi.md` for the reference implementation of correct front matter formatting.
