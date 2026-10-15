# SAP Article Generator - Integration Guide

## Overview

This is a **self-contained** Claude skill that generates professional SAP technical articles with embedded images. It includes built-in image downloading capabilities and doesn't require any external skills.

## Features

✅ **Self-contained**: All image fetching built-in  
✅ **Web research**: Automatic fact-checking via web_search  
✅ **Image downloading**: Built-in scripts to fetch images from the web  
✅ **Professional formatting**: SAP-specific styling and layouts  
✅ **Multiple formats**: Screenshots, diagrams, flowcharts  
✅ **Complete articles**: 2000-4000 words with 2-3+ embedded images

## Installation

### Option 1: Upload to Claude Desktop/Code

1. **Compress the skill folder:**
   ```bash
   cd /path/to/sap-article-generator-v2
   zip -r sap-article-generator.zip .
   ```

2. **Upload to Claude:**
   - Claude Desktop: Place in your skills directory
   - Claude Code: Upload via skills management

### Option 2: Manual Setup

1. Create the skill directory structure:
   ```
   sap-article-generator/
   ├── SKILL.md
   ├── INTEGRATION_GUIDE.md
   ├── requirements.txt
   ├── scripts/
   │   ├── fetch_image.py
   │   └── fetch_images_batch.py
   └── references/
       ├── article-standards.md
       └── sap-terminology.md
   ```

2. Copy all files to your Claude skills directory

3. Restart Claude to load the skill

## Usage

### Quick Start

Simply ask Claude:
```
"Create an SAP article about [topic]"
"Write a guide on configuring SAP sales order types"
"Generate documentation for SAP MM procurement process"
```

### What Happens Automatically

When you request an SAP article, Claude will:

1. ✅ Read the docx skill documentation
2. ✅ Research the topic with 2-3+ web searches
3. ✅ Search for relevant images
4. ✅ Download images to /tmp/sap_article/temp_images/
5. ✅ Create a professional Word document
6. ✅ Embed images with captions
7. ✅ Format with SAP styling
8. ✅ Include references section
9. ✅ Save to /workspace/

### Example Requests

**Configuration Guides:**
- "Create an article on SAP sales order type configuration"
- "Write a guide for setting up material master in MM"
- "Document the FI-CO integration setup process"

**Conceptual Articles:**
- "Explain SAP SD pricing procedure architecture"
- "Create an article on SAP archiving concepts"
- "Write about S/4HANA embedded analytics"

**Troubleshooting Guides:**
- "Create a troubleshooting guide for SAP IDocs"
- "Write about common SAP data archiving issues"
- "Document solutions for SAP OData API problems"

## What Gets Generated

Each article includes:

### 1. Title Page
- Professional title in SAP blue
- Subtitle and scope
- Date and version

### 2. Table of Contents
- Auto-generated from headings
- Hierarchical structure

### 3. Content Sections
- Introduction and business context
- Step-by-step instructions
- Configuration screens
- Technical details
- Best practices
- Troubleshooting tips

### 4. Embedded Images (2-3+)
- Transaction screenshots
- Process flow diagrams
- Architecture diagrams
- Configuration examples
- All with figure captions

### 5. Professional Formatting
- SAP blue headings (#0070AD)
- Transaction codes in monospace
- Professional tables
- Proper spacing and alignment

### 6. References Section
- Web sources cited
- URLs and access dates
- Numbered references

## File Locations

**Article Output:**
```
/workspace/SAP_[Topic]_Guide.docx
```

**Temporary Images:**
```
/tmp/sap_article/temp_images/
```

**Downloaded Images:**
Images are automatically downloaded during article generation and embedded directly into the Word document.

## Dependencies

The skill requires these Python packages:
- `requests` - For downloading images
- `Pillow` - For image processing

These are automatically installed when needed with:
```bash
pip install requests Pillow --break-system-packages
```

## Troubleshooting

### Images Not Downloading

**Problem:** Images fail to download  
**Solution:** 
- Check that URLs are direct image links
- Some sites block automated downloads - try different sources
- Verify network connectivity

### Images Not Embedding

**Problem:** Images don't appear in Word document  
**Solution:**
- Verify images exist in /tmp/sap_article/temp_images/
- Check that docx skill was read first
- Ensure proper image paths in document creation

### Dependencies Missing

**Problem:** Python packages not found  
**Solution:**
```bash
pip install requests Pillow --break-system-packages
```

### No Images in Article

**Problem:** Article generated without images  
**Solution:**
- This is a critical issue - articles MUST have images
- Ensure web_search returned image results
- Try more specific image search queries
- Use alternative image sources

## Best Practices

### For Best Results

1. **Be specific** in your request:
   - ✅ "Create an article on SAP VOV8 transaction for sales order types"
   - ❌ "Tell me about SAP SD"

2. **Specify the type** if you have a preference:
   - "Create a configuration guide for..."
   - "Write a conceptual article about..."
   - "Generate a troubleshooting guide for..."

3. **Mention images** if you want specific ones:
   - "Include screenshots of transaction VOV8"
   - "Add a process flow diagram"

### For SAP Consultants

This skill is perfect for:
- Creating client documentation
- Building knowledge base articles
- Training materials
- Configuration guides
- Troubleshooting documents
- Technical handover documentation

## Skill Workflow (Technical)

For developers/admins who want to understand the process:

```
User Request → SAP Article Generator Skill
    ↓
1. Read docx SKILL.md
    ↓
2. Research topic (web_search 2-3x)
    ↓
3. Search for images (web_search)
    ↓
4. Download images (scripts/fetch_images_batch.py)
    ↓
5. Create Word document with docx
    ↓
6. Embed downloaded images
    ↓
7. Format with SAP styling
    ↓
8. Save to /workspace/
    ↓
9. Provide computer:// link to user
```

## Advanced Usage

### Custom Image Sources

You can specify image sources:
```
"Create an SAP article on MM procurement, 
use images from SAP Help Portal if possible"
```

### Specific Formatting

You can request specific styling:
```
"Create an SAP article with extra emphasis on screenshots,
include at least 5 images"
```

### Target Audience

You can specify the audience level:
```
"Create a beginner-friendly SAP article on..."
"Write an advanced technical article for..."
```

## Version History

### Version 2.0 (Current)
- ✅ Self-contained with built-in image fetching
- ✅ No external skill dependencies
- ✅ Streamlined workflow
- ✅ Better error handling
- ✅ Clearer documentation

### Version 1.0
- ❌ Required separate image-fetcher skill
- ❌ More complex integration

## Support

For issues or questions:
1. Check this integration guide
2. Review the SKILL.md for detailed workflow
3. Verify all dependencies are installed
4. Check that Claude has web_search access

## License

MIT License - Free to use and modify

---

**Ready to use!** Just ask Claude to create an SAP article and watch it work its magic! 🚀
