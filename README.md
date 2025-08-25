# YouKnowMCP

**Feed your AI Model with your handcrafted knowlege bits**

A curated knowledge search system for your handcrafted personal digital brain

YouKnowMCP is designed for **carefully curated, human-refined knowledge** rather than raw data aggregation. Transform your thoughtfully structured markdown (or other) knowledge files into a searchable, intelligent MCP (Model Context Protocol) server that respects the deliberate curation you’ve invested in your knowledge.

Unlike traditional note-taking tools that mix raw capture with processed information, or AI systems that aggregate vast amounts of unvetted data, YouKnowMCP is built for **quality over quantity** - serving your personally distilled, verified, and structured insights to be used with your preferred AI model.

The knowlege (KnowFiles) are mostly plug-and-play, and you can curate your information, be that book summaries, personal recipes, life events or whatever you want to record and make it available in a friendly way to your LLM. So, instead of uploading your whole book library, you only make available the information bits (KnowBits) of your content that you created using your preferred way (AI summary, personal notes, etc) to any of your LLM, be in your phone, desktop or other systems.

## 🎯 Core Philosophy

- **Handcrafted knowledge**: Build your KnowFiles for curated insights, not automated content aggregation
- **Human-refined data**: Each knowledge item represents deliberate synthesis and understanding
- **Separation of concerns**: Knowledge curation happens elsewhere, YouKnowMCP handles intelligent retrieval
- **Domain isolation**: Each knowledge area maintains its own conceptual boundaries and expertise
- **API-first**: Access your curated knowledge through any interface via MCP protocol
- **Multilingual support**: Handle knowledge in multiple languages within the same domain via keyword matching (manually created).

## 🔍 Quality-Focused Approach

**Not for:**

- Automatic web scraping or content aggregation
- Raw note dumps or unprocessed research
- AI-generated content without human verification

**Designed for:**

- Knowledge you’ve personally verified and synthesized
- Insights extracted from trusted sources and filtered through your expertise
- Structured understanding that reflects real learning and comprehension
- Cross-referenced concepts that you’ve deliberately connected

## 🏗️ Architecture Overview

```
Knowledge Files "KnowFiles" (.md) → Domain Parser → Unified Database → MCP Server → Any Client
```

### Knowledge Organization

**Knowfiles** (your `.md` files) contain **Knowbits** (individual knowledge items) organized by **domains**:

```
your_knowledge/
├── classical_music/
│   ├── greatest_componists.md
│   ├── my_favorite_book_quotes.md
│   ├── my_favorite_pieces.md
│   ├── my_own_collection.md
│   ├── my_music_diary.md
│   └── key_figures.md
├── japanese_crafts/
│   ├── pottery.md
│   ├── my_favorite_techniques.md
│   └── tea.md
├── great_civilizations/
│   ├── china.md
│   ├── egypt.md
│   ├── pre-colombian.md
│   ├── a_favorite_book_summary.md
│   ├── another_favorite_book_summary.md
│   ├── personal_notes.md
    └── roman.md
```

* The files don't need to follow this folder structure, they can all be connected simply by using the domain configuration as below.


### Domain Configuration

Each domain is defined in `config/domains.yaml`:

```yaml
classical_music:
  name: "European classical music"
  keywords: ["barroque", "romantic", "modern"]
  concepts: ["chamber music", "orchestra"]
  search_hints: ["Chamber music pieces, two violas, Bach"]
  
japanese_crafts:
  name: "Japanese Crafts"
  keywords: ["joinery", "temple", "tea hut"]
  concepts: ["joinery types", "traditional woods", "wood shaving"]
  search_hints: ["Joinery for buddhist temple roofs"]
```

## 🔍 Smart Search Capabilities

### Domain-Aware Queries

- **Auto-detection**: “What cultures have built pyramids?” → searches `great_civilizations` domain
- **Explicit targeting**: Search specific domains when you know the context
- **Cross-domain search**: When concepts might span multiple areas

### Entity Normalization via your own keywords

- **Multilingual entities**: “Ryoba” = “Ryoba Saw” = “両刃鋸”
- **Technical synonyms**: “double-edged saw” = “nokogiri”
- **Domain-specific context**: “classical music” means different things in classical music and  vs great civilizations

### Intelligent Results

- **Concept expansion**: Search for “great compositors” finds all related historical figures
- **Relationship awareness**: Understands connections between concepts within domains
- **Provenance tracking**: Know which knowledge file contributed each result

## 🚀 Getting Started (TBD)

### 1. Install YouKnowMCP

```bash
git clone https://github.com/yourusername/youknowmcp
cd youknowmcp
pip install -e .
```

### 2. Prepare Your Knowledge Files (KnowFile)

Create markdown files with domain headers:

```markdown
---
domain: your_domain_name
languages: [english, japanese]
---
# Your Knowledge File

## Overview
Domain description and scope

## Key Concepts
- Main concept 1
- Main concept 2

## Resources
- Source materials and references

## Notes (KeyBits)

### 2024-01-15 - Quote
**Category:** Technical Parameters
**Content:** Your carefully curated knowledge item
**Tags:** tag1, tag2, tag3
```

### 3. Configure Your Domains

Create `config/domains.yaml`:

```yaml
domains:
  your_domain:
    name: "Your Domain Name"
    keywords: ["key", "terms", "for", "detection"]
    concepts: ["important concepts", "main ideas"]
    search_hints: ["When to search this domain"]
    languages: ["english"]
```

### 4. Parse and Serve (TBD)

```bash
# Parse your knowledge files
youknowmcp parse --input ./your_knowledge/ --config ./config/domains.yaml

# Start MCP server
youknowmcp serve --port 8000

# Test the connection
youknowmcp test-query "your search term"
```

### 5. Connect via MCP (TBD)

Add to your MCP client configuration:

```json
{
  "mcpServers": {
    "youknowmcp": {
      "command": "youknowmcp",
      "args": ["serve"],
      "env": {}
    }
  }
}
```

## 🎯 Use Cases

### Personal Knowledge Management

- **Research synthesis**: Distilled insights from academic papers and books
- **Technical expertise**: Curated procedures, best practices, and hard-won knowledge
- **Historical research**: Primary sources analysis and chronological understanding

### Professional Knowledge Bases

- **Domain expertise**: Legal precedents, medical protocols, engineering standards
- **Project wisdom**: Lessons learned, architectural decisions, troubleshooting guides
- **Training materials**: Structured knowledge for team development

### Multilingual Documentation

- **Cultural knowledge**: Traditional practices with native terminology preserved
- **Technical specifications**: International standards with regional variations
- **Historical sources**: Primary documents in original languages with expert translations

## 🛠️ Technical Features (TBD)

### Database Design

- **SQLite-first**: Simple deployment, easy backup, portable knowledge base 
- **Full-text search**: Advanced querying with FTS5 for fast, relevant results
- **Relationship tracking**: Entities, aliases, and conceptual cross-references
- **Migration path**: Scale to PostgreSQL when your knowledge base grows

### MCP Integration

- **Standard protocol**: Works with Claude and other MCP-compatible clients
- **Rich metadata**: Categories, tags, source attribution, language detection
- **Flexible queries**: Simple text search to complex domain-specific analysis

### Extensibility

- **Custom parsers**: Handle different markdown formats and knowledge structures
- **Domain plugins**: Add specialized processing for specific expertise areas
- **Export capabilities**: Generate reports, summaries, or structured datasets

##  Contributing

YouKnowMCP is designed for people who value **thoughtful knowledge curation** over information hoarding:

- **Quality examples**: Share well-structured knowledge formats and curation methodologies
- **Parser contributions**: Support different markdown (or other text-file) structures while preserving human organization
- **Domain templates**: Example configurations for common areas of expertise
- **Curation tools**: Better ways to structure, verify, and cross-reference knowledge
- **Search enhancements**: Improved entity recognition, semantic understanding, relationship detection

### Contributing Guidelines

- Respect human curation and expertise
- Enhance search quality over search quantity
- Support thoughtful knowledge organization
- Maintain domain boundaries and conceptual clarity

## 📋 Roadmap (TBD)

- ✅ Project architecture and design
- 🔄 Core parsing and domain detection system
- 🔄 SQLite database with full-text search implementation
- 🔄 Basic MCP server with domain-aware queries
- ⏳ Entity normalization and multilingual alias handling
- ⏳ Advanced search with concept expansion
- ⏳ Vector embeddings for semantic search capabilities
- ⏳ Web interface for knowledge exploration and validation
- ⏳ Import/export tools for popular knowledge management formats

## 📖 Documentation (TBD)

- [Knowledge File Format Guide](docs/knowledge-format.md)
- [Domain Configuration Reference](docs/domain-config.md)
- [MCP Integration Examples](docs/mcp-examples.md)
- [Advanced Search Techniques](docs/search-guide.md)

## 📄 License

MIT License - see <LICENSE> for details.

## Acknowledgments

Built for those that seek **quality curation beats quantity aggregation**, and believe that human expertise deserves intelligent, respectful search database.

-----

**YouKnowMCP**: Feed your AI with your hand-crafted knowlege bits
