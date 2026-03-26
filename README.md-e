# Honduran Law MCP Server

**The honduras.justia.com alternative for the AI age.**

[![npm version](https://badge.fury.io/js/@ansvar%2Fhonduran-law-mcp.svg)](https://www.npmjs.com/package/@ansvar/honduran-law-mcp)
[![MCP Registry](https://img.shields.io/badge/MCP-Registry-blue)](https://registry.modelcontextprotocol.io)
[![License](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![GitHub stars](https://img.shields.io/github/stars/Ansvar-Systems/Honduran-law-mcp?style=social)](https://github.com/Ansvar-Systems/Honduran-law-mcp)
[![CI](https://github.com/Ansvar-Systems/Honduran-law-mcp/actions/workflows/ci.yml/badge.svg)](https://github.com/Ansvar-Systems/Honduran-law-mcp/actions/workflows/ci.yml)
[![Provisions](https://img.shields.io/badge/provisions-54-blue)]()

Query **200 Honduran statutes** -- from the Código Penal and Código de Trabajo to the Ley de Transparencia, Ley de Propiedad Intelectual, and more -- directly from Claude, Cursor, or any MCP-compatible client.

If you're building legal tech, compliance tools, or doing Honduran legal research, this is your verified reference database.

Built by [Ansvar Systems](https://ansvar.eu) -- Stockholm, Sweden

---

## Why This Exists

Honduran legal research means navigating the Congreso Nacional portal, cross-referencing Gaceta Oficial publications, and manually tracing amendments through multiple sources. Whether you're:

- A **lawyer** validating citations in a brief or contract before Honduran courts
- A **compliance officer** checking obligations under the Ley de Protección de Datos Personales or labor regulations
- A **legal tech developer** building tools for the Central American market
- A **researcher** tracing legislative history across Honduran statutes

...you shouldn't need dozens of browser tabs and manual PDF cross-referencing. Ask Claude. Get the exact provision. With context.

This MCP server makes Honduran law **searchable, cross-referenceable, and AI-readable**.

---

## Quick Start

### Use Remotely (No Install Needed)

> Connect directly to the hosted version -- zero dependencies, nothing to install.

**Endpoint:** `https://honduran-law-mcp.vercel.app/mcp`

| Client | How to Connect |
|--------|---------------|
| **Claude.ai** | Settings > Connectors > Add Integration > paste URL |
| **Claude Code** | `claude mcp add honduran-law --transport http https://honduran-law-mcp.vercel.app/mcp` |
| **Claude Desktop** | Add to config (see below) |
| **GitHub Copilot** | Add to VS Code settings (see below) |

**Claude Desktop** -- add to `claude_desktop_config.json`:

```json
{
  "mcpServers": {
    "honduran-law": {
      "type": "url",
      "url": "https://honduran-law-mcp.vercel.app/mcp"
    }
  }
}
```

**GitHub Copilot** -- add to VS Code `settings.json`:

```json
{
  "github.copilot.chat.mcp.servers": {
    "honduran-law": {
      "type": "http",
      "url": "https://honduran-law-mcp.vercel.app/mcp"
    }
  }
}
```

### Use Locally (npm)

```bash
npx @ansvar/honduran-law-mcp
```

**Claude Desktop** -- add to `claude_desktop_config.json`:

**macOS:** `~/Library/Application Support/Claude/claude_desktop_config.json`
**Windows:** `%APPDATA%\Claude\claude_desktop_config.json`

```json
{
  "mcpServers": {
    "honduran-law": {
      "command": "npx",
      "args": ["-y", "@ansvar/honduran-law-mcp"]
    }
  }
}
```

**Cursor / VS Code:**

```json
{
  "mcp.servers": {
    "honduran-law": {
      "command": "npx",
      "args": ["-y", "@ansvar/honduran-law-mcp"]
    }
  }
}
```

---

## Example Queries

Once connected, just ask naturally (Spanish examples):

- *"¿Qué dice el Código Penal sobre el delito de estafa?"*
- *"¿El Código de Trabajo sigue vigente? ¿Ha sido reformado recientemente?"*
- *"Busca disposiciones sobre protección de datos personales en la legislación hondureña"*
- *"¿Cuáles son los requisitos del Código de Comercio para constituir una sociedad anónima?"*
- *"¿Qué establece la Ley de Transparencia sobre acceso a la información pública?"*
- *"Valida la cita 'Decreto No. 131-1982' (Constitución de la República)"*
- *"¿Cuáles son las obligaciones del empleador según el Código de Trabajo hondureño?"*
- *"Construye un argumento legal sobre responsabilidad civil extracontractual en Honduras"*
- *"¿Qué dispone la Ley de Propiedad Intelectual sobre derechos de autor?"*

---

## What's Included

| Category | Count | Details |
|----------|-------|---------|
| **Statutes** | 200 statutes | Honduran legislation from official sources |
| **Provisions** | 54 sections | Full-text searchable with FTS5 |
| **Database Size** | ~0.3 MB | Optimized SQLite, portable |
| **Freshness Checks** | Automated | Drift detection against source |

**Verified data only** -- every citation is validated against official sources (honduras.justia.com). Zero LLM-generated content.

---

## See It In Action

### Why This Works

**Verbatim Source Text (No LLM Processing):**
- All statute text is ingested from [honduras.justia.com](https://honduras.justia.com) and official Honduran government sources
- Provisions are returned **unchanged** from SQLite FTS5 database rows
- Zero LLM summarization or paraphrasing -- the database contains regulation text, not AI interpretations

**Smart Context Management:**
- Search returns ranked provisions with BM25 scoring (safe for context)
- Provision retrieval gives exact text by statute identifier + chapter/section
- Cross-references help navigate without loading everything at once

**Technical Architecture:**
```
honduras.justia.com --> Parse --> SQLite --> FTS5 snippet() --> MCP response
                          ^                        ^
                   Provision parser         Verbatim database query
```

### Traditional Research vs. This MCP

| Traditional Approach | This MCP Server |
|---------------------|-----------------|
| Search Justia by statute name | Search by plain Spanish: *"protección datos personales"* |
| Navigate multi-chapter statutes manually | Get the exact provision with context |
| Manual cross-referencing between laws | `build_legal_stance` aggregates across sources |
| "¿Está vigente esta ley?" → check manually | `check_currency` tool → answer in seconds |
| Find international basis → dig through OAS treaties | `get_eu_basis` → linked international instruments |
| No API, no integration | MCP protocol → AI-native |

**Traditional:** Search Congreso Nacional portal → Download PDF → Ctrl+F → Cross-reference with Gaceta Oficial → Repeat

**This MCP:** *"¿Qué dice el Código de Trabajo sobre despido injustificado y cuál es la indemnización?"* → Done.

---

## Available Tools (13)

### Core Legal Research Tools (8)

| Tool | Description |
|------|-------------|
| `search_legislation` | FTS5 full-text search across 54 provisions with BM25 ranking. Supports quoted phrases, boolean operators, prefix wildcards |
| `get_provision` | Retrieve specific provision by statute identifier + chapter/section |
| `check_currency` | Check if a statute is in force, amended, or repealed |
| `validate_citation` | Validate citation against database -- zero-hallucination check |
| `build_legal_stance` | Aggregate citations from multiple statutes for a legal topic |
| `format_citation` | Format citations per Honduran conventions |
| `list_sources` | List all available statutes with metadata and coverage scope |
| `about` | Server info, capabilities, dataset statistics, and coverage summary |

### International Law Integration Tools (5)

| Tool | Description |
|------|-------------|
| `get_eu_basis` | Get international instruments (OAS, IACHR, ILO conventions) that a Honduran statute aligns with |
| `get_honduran_implementations` | Find Honduran laws aligning with a specific international instrument |
| `search_eu_implementations` | Search international documents with Honduran implementation counts |
| `get_provision_eu_basis` | Get international law references for a specific provision |
| `validate_eu_compliance` | Check alignment status of Honduran statutes against international standards |

---

## International Law Alignment

Honduras is not an EU member state, but Honduran law intersects with several international frameworks:

- **IACHR (Inter-American Court of Human Rights)** -- Honduras is subject to the American Convention on Human Rights; key decisions shape constitutional and criminal law
- **ILO Conventions** -- Honduras has ratified core ILO conventions on labor rights; the Código de Trabajo reflects these obligations
- **OAS frameworks** -- Honduras participates in Organization of American States conventions on anti-corruption, cybercrime, and organized crime
- **CAFTA-DR** -- The Central America Free Trade Agreement shapes commercial and intellectual property law
- **Basel/FATF** -- Anti-money laundering and financial crime statutes align with FATF recommendations

The international alignment tools allow you to explore these relationships -- checking which Honduran provisions correspond to treaty obligations, and vice versa.

> **Note:** International cross-references reflect alignment and treaty relationships. Honduras adopts its own legislative approach, and these tools help identify where Honduran and international law address similar domains.

---

## Data Sources & Freshness

All content is sourced from authoritative Honduran legal databases:

- **[honduras.justia.com](https://honduras.justia.com)** -- Comprehensive Honduran statute database
- **[Congreso Nacional de Honduras](https://www.congreso.gob.hn)** -- Official legislative portal
- **[Gaceta Oficial](https://www.gaceta.hn)** -- Official gazette for promulgated legislation

### Data Provenance

| Field | Value |
|-------|-------|
| **Primary source** | honduras.justia.com |
| **Retrieval method** | Structured ingestion from official sources |
| **Language** | Spanish |
| **Coverage** | 200 Honduran statutes |
| **Database size** | ~0.3 MB |

**Verified data only** -- every citation is validated against official sources. Zero LLM-generated content.

---

## Security

This project uses multiple layers of automated security scanning:

| Scanner | What It Does | Schedule |
|---------|-------------|----------|
| **CodeQL** | Static analysis for security vulnerabilities | Weekly + PRs |
| **Semgrep** | SAST scanning (OWASP top 10, secrets, TypeScript) | Every push |
| **Gitleaks** | Secret detection across git history | Every push |
| **Trivy** | CVE scanning on filesystem and npm dependencies | Daily |
| **Docker Security** | Container image scanning + SBOM generation | Daily |
| **Socket.dev** | Supply chain attack detection | PRs |
| **OSSF Scorecard** | OpenSSF best practices scoring | Weekly |
| **Dependabot** | Automated dependency updates | Weekly |

See [SECURITY.md](SECURITY.md) for the full policy and vulnerability reporting.

---

## Important Disclaimers

### Legal Advice

> **THIS TOOL IS NOT LEGAL ADVICE**
>
> Statute text is sourced from official Honduran legal databases. However:
> - This is a **research tool**, not a substitute for professional legal counsel
> - **Court case coverage is not included** -- do not rely solely on this for case law research
> - **Verify critical citations** against primary sources for court filings
> - **International cross-references** reflect alignment relationships, not formal transposition
> - **Departmental and municipal legislation is not included** -- this covers national statutes only

**Before using professionally, read:** [DISCLAIMER.md](DISCLAIMER.md) | [SECURITY.md](SECURITY.md)

### Client Confidentiality

Queries go through the Claude API. For privileged or confidential matters, use on-premise deployment.

### Professional Responsibility

Members of the **Colegio de Abogados de Honduras** should ensure any AI-assisted research complies with professional ethics rules on competence and verification of sources before relying on output in client matters or court filings.

---

## Development

### Setup

```bash
git clone https://github.com/Ansvar-Systems/Honduran-law-mcp
cd Honduran-law-mcp
npm install
npm run build
npm test
```

### Running Locally

```bash
npm run dev                                       # Start MCP server
npx @anthropic/mcp-inspector node dist/index.js   # Test with MCP Inspector
```

### Data Management

```bash
npm run ingest           # Ingest statutes from source
npm run build:db         # Rebuild SQLite database
npm run drift:detect     # Run drift detection against anchors
npm run check-updates    # Check for source updates
npm run census           # Generate coverage census
```

### Performance

- **Search Speed:** <100ms for most FTS5 queries
- **Database Size:** ~0.3 MB (efficient, portable)
- **Reliability:** 100% ingestion success rate

---

## Related Projects: Complete Compliance Suite

This server is part of **Ansvar's Compliance Suite** -- MCP servers that work together for end-to-end compliance coverage:

### [@ansvar/eu-regulations-mcp](https://github.com/Ansvar-Systems/EU_compliance_MCP)
**Query 49 EU regulations directly from Claude** -- GDPR, AI Act, DORA, NIS2, MiFID II, eIDAS, and more. Full regulatory text with article-level search. `npx @ansvar/eu-regulations-mcp`

### [@ansvar/nicaraguan-law-mcp](https://github.com/Ansvar-Systems/Nicaraguan-law-mcp)
**Query 1,730 Nicaraguan statutes directly from Claude** -- Central American legal research companion. `npx @ansvar/nicaraguan-law-mcp`

### [@ansvar/us-regulations-mcp](https://github.com/Ansvar-Systems/US_Compliance_MCP)
**Query US federal and state compliance laws** -- HIPAA, CCPA, SOX, GLBA, FERPA, and more. `npx @ansvar/us-regulations-mcp`

### [@ansvar/security-controls-mcp](https://github.com/Ansvar-Systems/security-controls-mcp)
**Query 261 security frameworks** -- ISO 27001, NIST CSF, SOC 2, CIS Controls, SCF, and more. `npx @ansvar/security-controls-mcp`

**70+ national law MCPs** covering Brazil, Canada, Colombia, Cuba, Denmark, France, Germany, Guyana, Ireland, Netherlands, Nicaragua, Norway, Panama, El Salvador, Sweden, UK, Venezuela, and more.

---

## Contributing

Contributions welcome! See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

Priority areas:
- Provision parsing expansion (current database has early-stage parsing)
- Court case law coverage
- Gaceta Oficial amendment tracking
- International treaty cross-reference mapping

---

## Roadmap

- [x] Core statute database with FTS5 search
- [x] Initial corpus ingestion (200 statutes)
- [x] International law alignment tools
- [x] Vercel Streamable HTTP deployment
- [x] npm package publication
- [ ] Full provision parsing expansion
- [ ] Court case law coverage
- [ ] Gaceta Oficial automated amendment tracking
- [ ] Historical statute versions
- [ ] Departmental regulatory coverage

---

## Citation

If you use this MCP server in academic research:

```bibtex
@software{honduran_law_mcp_2026,
  author = {Ansvar Systems AB},
  title = {Honduran Law MCP Server: AI-Powered Legal Research Tool},
  year = {2026},
  url = {https://github.com/Ansvar-Systems/Honduran-law-mcp},
  note = {200 Honduran statutes with full-text search and international law alignment}
}
```

---

## License

Apache License 2.0. See [LICENSE](./LICENSE) for details.

### Data Licenses

- **Statutes & Legislation:** Honduran Government (public domain via official sources)
- **International Metadata:** OAS/IACHR public domain

---

## About Ansvar Systems

We build AI-accelerated compliance and legal research tools for the global market. This MCP server is part of our Latin American legal coverage expansion -- because navigating 200 statutes across a fragmented portal ecosystem shouldn't require a law degree.

**[ansvar.eu](https://ansvar.eu)** -- Stockholm, Sweden

---

<p align="center">
  <sub>Built with care in Stockholm, Sweden</sub>
</p>
