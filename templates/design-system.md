# Design System

## Metadata

- **Project ID:**
- **Artifact version:**
- **Status:** DRAFT / REVIEW_REQUIRED / APPROVED
- **Reference inputs:**
- **Assumptions:**

## 1. Visual personality

Describe the visible characteristics using concrete rules.

- **Overall character:**
- **Information density:** Low / Medium / High
- **Primary visual emphasis:** Typography / Data / Photography / Illustration / Mixed
- **Contrast behavior:**
- **Whitespace behavior:**
- **Motion or transition guidance, if relevant:**

## 2. Slide geometry

- **Slide ratio and dimensions:**
- **Safe margins:** Top / Right / Bottom / Left
- **Primary grid:**
- **Columns:**
- **Gutter:**
- **Baseline or spacing unit:**
- **Alignment anchors:**

## 3. Typography

| Role | Font | Fallback | Size | Weight | Line spacing | Case | Notes |
|---|---|---|---:|---|---|---|---|
| Display title |  |  |  |  |  |  |  |
| Action title |  |  |  |  |  |  |  |
| Section label |  |  |  |  |  |  |  |
| Body |  |  |  |  |  |  |  |
| Metric |  |  |  |  |  |  |  |
| Caption |  |  |  |  |  |  |  |
| Chart label |  |  |  |  |  |  |  |
| Footnote/source |  |  |  |  |  |  |  |
| Chinese variant |  |  |  |  |  |  |  |

### Typography rules

- Maximum title lines:
- Body-copy limits:
- Number formatting:
- Punctuation style:
- Emphasis method:
- Prohibited treatments:

## 4. Color system

| Token | HEX/RGB | Role | Usage rule | Contrast note |
|---|---|---|---|---|
| background.primary |  |  |  |  |
| background.secondary |  |  |  |  |
| text.primary |  |  |  |  |
| text.secondary |  |  |  |  |
| accent.primary |  |  |  |  |
| accent.secondary |  |  |  |  |
| semantic.positive |  |  |  |  |
| semantic.negative |  |  |  |  |
| semantic.warning |  |  |  |  |
| neutral.rule |  |  |  |  |

### Chart palette

| Series role | Color | Rule |
|---|---|---|
| Primary focus |  |  |
| Comparison |  |  |
| Historical |  |  |
| Forecast |  |  |
| Other / context |  |  |

## 5. Spacing and shape tokens

- **Spacing scale:**
- **Corner radii:**
- **Line weights:**
- **Borders:**
- **Shadows:**
- **Transparency:**
- **Container padding:**

## 6. Layout family library

Repeat this block for every approved family.

### Layout family: [name]

- **Purpose:**
- **Best for:**
- **Do not use for:**
- **Grid structure:**
- **Content limits:**
- **Image or chart area:**
- **Visual balance:**
- **Title placement:**
- **Source-note placement:**
- **Responsive or bilingual behavior:**
- **Reference slides:**

## 7. Images and illustration

- **Photography style:**
- **Crop behavior:**
- **Subject positioning and negative space:**
- **Color grading:**
- **Background treatment:**
- **Illustration style:**
- **Prohibited clichés or styles:**

## 8. Icons and diagrams

- **Icon family:**
- **Stroke or fill:**
- **Default size:**
- **Color behavior:**
- **Connector style:**
- **Arrow treatment:**
- **Hierarchy and grouping:**

## 9. Charts and tables

- **Axis treatment:**
- **Gridlines:**
- **Legend treatment:**
- **Data labels:**
- **Highlight behavior:**
- **Forecast treatment:**
- **Table header and row rules:**
- **Source-note format:**

## 10. Bilingual rules

- **Language hierarchy:**
- **Font pairing:**
- **Relative type sizes:**
- **Line-break behavior:**
- **Translation expansion allowance:**
- **Punctuation and numeral conventions:**

## 11. Anti-patterns

- 

## 12. Builder tokens

```yaml
slide:
  ratio: "16:9"
  margin_top: null
  margin_right: null
  margin_bottom: null
  margin_left: null

typography:
  action_title:
    font: null
    size_pt: null
    weight: null
  body:
    font: null
    size_pt: null

colors:
  background_primary: null
  text_primary: null
  accent_primary: null

spacing:
  unit: null
```

## 13. Builder checklist

- [ ] Slide dimensions confirmed
- [ ] Fonts available or fallbacks approved
- [ ] Color tokens defined
- [ ] Layout families defined
- [ ] Chart rules defined
- [ ] Image treatment defined
- [ ] Bilingual behavior defined
- [ ] Source-note style defined
- [ ] Exceptions and uncertainties recorded
