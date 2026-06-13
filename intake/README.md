# Claim Document Intake — Quick Start

Convert claim files to Markdown so they can be reviewed by the Auto Claims Next-Action Routing Operator.

---

## How to use

1. Open `intake.html` in any web browser (Chrome, Edge, or Firefox).
2. Drag and drop one or more claim files onto the drop zone — or click **Choose Files**.
3. Click **Convert to Markdown**.
4. When conversion completes, click **Copy to Clipboard**.
5. Open your **Auto Claims Next-Action Routing Operator** Claude Project.
6. Paste the Markdown into the chat and ask for a routing recommendation.

---

## Accepted file types

| File type | Formats |
|---|---|
| Claim notes / reports | PDF, DOCX, TXT |
| Repair estimates | PDF, XLSX |
| Police reports | PDF, DOCX |
| Emails | EML |
| Spreadsheets / logs | XLSX |
| Presentations | PPTX |

---

## Requirements

- A modern web browser — Chrome 90+, Edge 90+, or Firefox 90+
- Internet access on first use (conversion libraries load from public CDNs)
- No installation, no Python, no command line required

---

## Limitations

| Situation | What happens |
|---|---|
| Scanned or image-only PDF | Little or no text is extracted. Output will say so. |
| Password-protected file | Cannot be converted. Remove the password first. |
| HTML-only email body | Partial extraction. Plain-text emails work fully. |
| PPTX charts or images | Not included. Slide text only. |

**Privacy:** All conversion runs inside your browser. No files are sent to any server or external service.

---

## Suggested instruction for the routing operator

After pasting the converted Markdown into your Claude Project, add:

```
Review the attached claim materials and produce a routing packet.
```

The operator will extract claim facts, identify gaps, and return a complete next-action routing recommendation.
