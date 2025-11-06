# Version 1.0.6: Metadata Structure Refinement & Improved Research Controls

This release simplifies the skill definition by moving version and update information from the YAML frontmatter into the document body, making maintenance easier while maintaining version tracking. It also reinforces research planning as a mandatory prerequisite before conducting any searches.

## What's New

### Reinforced Research Planning Requirements

**Explicit prohibition against unsolicited internet searches**
- Added clear directive that the skill will NOT perform unsolicited web searches or research activities
- Users must explicitly request internet research within the context of an approved research plan
- Emphasizes that research planning and strategy development must come FIRST
- Users receive structured guidance to clarify objectives before any searches begin

**Benefits of this approach:**
- Ensures genealogy research follows professional methodologies
- Prevents scattered, unfocused search activities
- Guarantees proper documentation and planning before record research
- Aligns with Genealogical Proof Standard (GPS) requirements
- Helps users develop systematic research strategies

### Metadata Restructuring

**Improved SKILL.md Structure**
- Moved `Version` field from YAML frontmatter to document body
- Moved `Last Updated` field from YAML frontmatter to document body
- YAML frontmatter now contains only essential skill metadata (name and description)

**Benefits of this change:**
- Reduces git friction when updating version information
- Version and timestamp are still visible to users in the document
- Cleaner YAML frontmatter for Claude's skill parsing
- Easier maintenance of version history without editing frontmatter
- Better separation between machine-readable and human-readable metadata

## Why This Matters

### Professional Research Methodology

Genealogy is not about finding *any* records—it's about conducting *systematic, documented research* that answers specific questions following professional standards. This release emphasizes that critical distinction:

- **Planning first**: Forces researchers to clarify their objectives before investing effort
- **Prevents "record chasing"**: Users won't conduct random searches in hopes of finding relevant records
- **Ensures GPS compliance**: The Genealogical Proof Standard requires "reasonably exhaustive research," which means strategic planning, not scattered searching
- **Builds stronger proofs**: Systematic research with documented methodology leads to more defensible conclusions

### Better Maintainability

Previously, version bumps required updating both:
1. YAML frontmatter (for Claude's skill system)
2. Body text (for users viewing the document)

Now version information is consistently maintained in the document body while the frontmatter remains stable.

### Cleaner Version Control

By keeping YAML metadata minimal and stable:
- Fewer changes to frontmatter during updates
- Version history focuses on actual content changes
- More meaningful git commits

## Structure After Update

```yaml
---
name: family-history-planning
description: Provides assistance with planning family history and genealogy research projects.
---

# Family History Research Planning Skill

**Version:** 1.0.6
**Last Updated:** November 5, 2025

[Rest of documentation...]
```

## Installation

### Quick Start

1. Download the latest release: `genealogy-research-skill-v1.0.6.zip`
2. Extract the ZIP file
3. **Claude.ai users**: Enable Skills in Settings > Capabilities, then upload the skill folder
4. **Claude Code users**: Move the `genealogy-research-skill` folder to `~/.claude/skills/`
5. Start using: Just ask Claude about family history research!

### Full Instructions

See the [README.md](https://github.com/emaynard/claude-family-history-research-skill/blob/main/README.md#installation) for complete installation instructions.

## What This Skill Does

The Family History Research Planning Skill provides Claude with specialized knowledge for:
- **Research Planning** - Create structured research plans following GPS standards
- **Citation Creation** - Generate properly formatted genealogical citations for 14+ source types
- **Evidence Analysis** - Systematically analyze and resolve conflicting genealogical evidence
- **Research Documentation** - Create professional research logs and documentation

## Changelog

### Version 1.0.6 Changes
- **Reinforced research planning requirements**: Explicit prohibition against unsolicited internet searches
- Users must work through research planning workflow before any searches or research activities
- Added clear guidance that users must explicitly request internet research within approved plans
- Moved version and last updated information from YAML frontmatter to document body
- Improved metadata structure for better maintainability
- Streamlined YAML frontmatter for cleaner skill parsing

### Related Changes from Previous Releases
See the [full changelog](https://github.com/emaynard/claude-family-history-research-skill/blob/main/CHANGELOG.md) for complete version history.

## Professional Standards

All documentation continues to support:
- **Genealogical Proof Standard (GPS)** - Reasonably exhaustive research documented
- **Evidence Explained** - Complete and accurate citations
- **Board for Certification of Genealogists (BCG)** - Professional methodology

## Support

- **Issues**: Report bugs or request features in [GitHub Issues](https://github.com/emaynard/claude-family-history-research-skill/issues)
- **Documentation**: See [README.md](https://github.com/emaynard/claude-family-history-research-skill/blob/main/README.md)
- **Professional Standards**: Refer to GPS, Evidence Explained, and BCG resources
- **Responsible AI**: Learn more at [CRAIGEN.org](https://craigen.org)

---

**Full Changelog**: https://github.com/emaynard/claude-family-history-research-skill/compare/v1.0.5...v1.0.6
