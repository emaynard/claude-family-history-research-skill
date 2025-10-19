# Family History Research Planning Skill for Claude

A family history and genealogy research tool in Claude's skill format.

## Overview

This skill provides Claude with specialized knowledge and workflows for family history and genealogy research following the Genealogical Proof Standard (GPS) and Evidence Explained citation methodology.

## Skill Structure

```
genealogy-research-skill/
├── SKILL.md                              # Main skill file (loaded when skill triggers)
├── references/                           # Reference documentation (loaded as needed)
│   ├── citation-templates.md            # Citation formats for 14+ source types
│   ├── evidence-evaluation.md           # Conflict resolution frameworks
│   ├── gps-guidelines.md                # Genealogical Proof Standard details
│   └── research-strategies.md           # Advanced research methodologies
└── assets/                               # Templates for output documents
    └── templates/
        ├── research-plan-template.md    # Research project planning
        ├── citation-template.md         # Citation library entry
        ├── evidence-analysis-template.md # Evidence analysis report
        └── research-log-template.md     # Research session documentation
```

## What This Skill Does

### 1. Research Planning
Guides users through creating structured family history research plans with:
- Specific research questions
- Source identification
- Search strategies
- GPS framework integration
- Timeline and milestones

### 2. Citation Creation
Generates properly formatted genealogical citations for:
- Census records
- Vital records (birth, marriage, death)
- Church records
- Land and probate records
- Military records
- Immigration records
- Newspapers
- Online databases
- Published books and manuscripts

### 3. Evidence Analysis
Systematically analyzes conflicting genealogical evidence:
- Individual source evaluation
- Reliability assessment
- Conflict identification
- Resolution frameworks
- Preponderance of evidence analysis
- GPS compliance checking
- Proof argument construction

### 4. Research Documentation
Creates professional research logs documenting:
- Sources searched (positive and negative results)
- Search strategies
- Findings and discoveries
- Evidence quality assessment
- Next steps

## When Claude Uses This Skill

Claude automatically loads this skill when users:
- Ask about family history or genealogy research
- Mention family history or ancestry
- Need help with genealogical citations
- Have conflicting information from multiple sources
- Ask about research planning or strategies
- Reference census records, vital records, or historical documents
- Need help analyzing evidence quality

## Key Features

### Professional Standards
- Built on Genealogical Proof Standard (GPS)
- Evidence Explained citation methodology
- Board for Certification of Genealogists (BCG) standards

### Progressive Disclosure
- Core instructions in SKILL.md (~4k words)
- Detailed reference material loaded as needed
- Templates available for document creation

### Comprehensive Coverage
- 14+ citation templates
- Detailed conflict resolution frameworks
- Advanced research strategies
- Complete GPS guidelines

## How to Use This Skill

### As a User
Simply ask Claude for help with family history research:
- "Help me plan research on my great-grandfather"
- "Create a citation for this census record"
- "I have conflicting birth dates - help me figure out which is right"
- "How do I systematically research this ancestor?"

Claude will load the skill automatically and guide you through the appropriate workflow.

### As Claude
When family history or genealogy research is detected:
1. Load SKILL.md for procedural guidance
2. Load specific reference files as needed:
   - `references/citation-templates.md` for citation help
   - `references/evidence-evaluation.md` for conflict resolution
   - `references/gps-guidelines.md` for GPS compliance
   - `references/research-strategies.md` for advanced techniques
3. Use templates from `assets/templates/` to create output documents
4. Follow workflows systematically
5. Apply professional standards throughout

## Conversion from BMAD Method

This skill was converted from a BMAD Method genealogy assistant module that included:
- 3 specialized agents (Research Coordinator, Source Analyst, Evidence Evaluator)
- 4 workflows (research planning, citation generation, evidence analysis, research logging)
- Professional genealogical standards
- Template-based document generation

### Key Differences from BMAD

**BMAD Structure:**
- Multiple agent files with personas and menus
- Separate workflow files (YAML config + instructions + checklists)
- Template variable substitution
- Extensive step-by-step XML-tagged instructions

**Claude Skill Structure:**
- Single SKILL.md with procedural knowledge
- Reference files for detailed information
- Template files in assets
- Concise, focused guidance

### What Was Preserved
- All professional genealogical knowledge
- GPS framework and requirements
- Evidence Explained citation standards
- Conflict resolution methodologies
- Research strategies
- Template structures

### What Was Adapted
- Agent personas converted to procedural workflows
- Multi-file workflows consolidated
- XML-tagged instructions converted to markdown
- Variable placeholders preserved in templates
- Checklist validation integrated into workflows

## Professional Standards Compliance

This skill ensures research follows:

### Genealogical Proof Standard (GPS)
- Reasonably exhaustive research
- Complete and accurate citations
- Analysis and correlation
- Conflict resolution
- Soundly reasoned conclusions

### Evidence Explained
- Proper citation format
- Original vs. derivative distinction
- Complete source documentation

### BCG Standards
- Professional genealogical methodology
- Ethical research practices
- Peer-reviewable work

## Output Documents

Claude can create four types of genealogy documents using this skill:

1. **Research Plans** - Strategic planning documents
2. **Citations** - Properly formatted source citations
3. **Evidence Analysis Reports** - Systematic conflict resolution
4. **Research Logs** - Session documentation

All outputs follow professional genealogical standards and are ready for:
- Personal research management
- Professional genealogy work
- Publication
- Sharing with other researchers
- GPS compliance review

## Version

**Version:** 1.0
**Created:** October 2025
**Source:** BMAD Method genealogy-assistant module
**Converted by:** Claude with skill-creator guidance

## License

This skill was created from a genealogy research project. Please respect professional genealogical standards and properly attribute sources when using the workflows and methodologies contained herein.

## Support

For questions about:
- **Genealogy methodology**: Refer to professional resources (BCG, NGS, Evidence Explained)
- **Skill usage**: Ask Claude for help - the skill is designed to guide you
- **Professional standards**: See references/ files for detailed guidelines

---

**Ready to start your family history research? Just ask Claude!**
