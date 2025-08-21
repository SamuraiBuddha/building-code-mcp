# Building Code MCP Server
> AI-powered building code compliance for expert witnesses and construction professionals

## 🎯 Project Overview

The Building Code MCP Server provides seamless access to building codes, standards, and local amendments through the Model Context Protocol (MCP). Designed specifically for construction litigation expert witnesses, architects, engineers, and compliance professionals who need instant, accurate code references.

## 💼 Business Model

### Target Market
- **Primary**: Expert witnesses in construction litigation (TAM: ~5,000 professionals @ $300-500/hr)
- **Secondary**: Architecture & Engineering firms (TAM: ~100,000 firms)
- **Tertiary**: General contractors & code consultants

### Pricing Strategy
- **Initial Setup**: $500-750 (includes configuration, training, 10 domain MCPs)
- **Monthly Retainer**: $300 (includes 1 hour support)
- **Overflow Support**: $175/hour
- **Emergency/Weekend**: $250/hour

### Value Proposition
"Save 20 hours per case on code research and compliance verification"

## 📋 Product Requirements Document (PRD)

### Core Features

#### 1. Code Search & Retrieval
- **ICC Codes**: IBC, IRC, IFC, IEBC, IECC via official API
- **NFPA Standards**: Free access to 300+ standards
- **Local Amendments**: Jurisdiction-specific modifications
- **Historical Versions**: Access to previous code editions

#### 2. Expert Witness Tools
- **Citation Formatter**: Generate court-ready code citations
- **Timeline Analysis**: Track code changes over project duration
- **Violation Finder**: Cross-reference drawings against applicable codes
- **Precedent Search**: Find similar cases and rulings

#### 3. Integration Capabilities
- **Claude Desktop**: Native MCP integration
- **Document Analysis**: Parse PDFs, CAD files, specifications
- **Report Generation**: Automated expert witness reports
- **BCL Export**: Training data for Building Code Language

### User Personas

#### 1. Expert Witness (Primary)
**Profile**: 60-75 years old, 30+ years experience, charges $300-500/hour
**Pain Points**: 
- Manually searching through multiple code books
- Tracking code versions and amendments
- Formatting citations for legal documents
**Needs**: 
- Quick code verification
- Historical code access
- Court-ready documentation

#### 2. Architect/Engineer
**Profile**: 35-55 years old, project-focused, deadline-driven
**Pain Points**:
- Code compliance during design
- Coordination between disciplines
- Keeping up with code changes
**Needs**:
- Real-time code checking
- Integration with CAD tools
- Multi-jurisdiction support

## 🔄 User Experience Flows

### Flow 1: Expert Witness Case Analysis
```
1. Upload case documents (depositions, drawings, specs)
2. AI extracts project timeline and key details
3. System identifies applicable codes for time/location
4. Search for potential violations
5. Generate preliminary report with citations
6. Export to legal document format
```

### Flow 2: Code Verification
```
1. Enter code query (e.g., "IBC 2018 egress width")
2. System searches ICC API, NFPA, local amendments
3. Returns consolidated results with official citations
4. Highlights changes from previous versions
5. Provides interpretation guidance
```

### Flow 3: Historical Analysis
```
1. Set project construction date range
2. Identify all applicable codes during that period
3. Track code changes that occurred
4. Flag retroactive requirements
5. Generate timeline report
```

## 🏗️ Technical Architecture

### Data Sources
1. **ICC Code Connect API** (Primary)
   - Official source
   - JSON responses
   - Real-time updates
   
2. **NFPA Free Access** (Secondary)
   - Web scraping
   - Public domain
   - 300+ standards

3. **Municipal Databases** (Tertiary)
   - Local amendments
   - Jurisdiction-specific
   - Quarterly updates

### MCP Server Structure
```
building-code-mcp/
├── src/
│   ├── tools/           # MCP tool implementations
│   ├── scrapers/         # NFPA and municipal scrapers
│   ├── formatters/       # Citation and report formatters
│   ├── cache/           # Local code cache
│   └── bcl-export/      # BCL training data export
├── docs/
│   ├── PRD.md
│   ├── API.md
│   └── SETUP.md
└── tests/
    ├── integration/
    └── unit/
```

## 🚀 Development Roadmap

### Phase 1: MVP (Week 1-2)
- [ ] ICC API integration
- [ ] NFPA scraper
- [ ] Basic MCP server
- [ ] Citation formatter

### Phase 2: Beta (Week 3-4)
- [ ] Cache layer
- [ ] Jurisdiction mapping
- [ ] Expert witness tools
- [ ] Testing with target users

### Phase 3: Launch (Month 2)
- [ ] Multi-jurisdiction support
- [ ] Report generation
- [ ] BCL export functionality
- [ ] Customer onboarding

### Phase 4: Scale (Month 3+)
- [ ] CAD integration
- [ ] AI violation detection
- [ ] Precedent database
- [ ] Enterprise features

## 🔒 Security & Compliance

- **API Key Management**: Secure vault storage
- **Data Privacy**: No storage of client case data
- **Access Control**: Role-based permissions
- **Audit Logging**: Complete activity tracking
- **Compliance**: Attorney-client privilege considerations

## 📊 Success Metrics

### Business KPIs
- Customer Acquisition Cost (CAC) < $500
- Monthly Recurring Revenue (MRR) growth > 20%
- Customer Lifetime Value (CLV) > $10,000
- Net Promoter Score (NPS) > 70

### Product Metrics
- Query response time < 2 seconds
- Code accuracy > 99.9%
- Uptime > 99.5%
- User time saved > 15 hours/case

## 🤝 Contributing

We follow GitHub Flow:
1. Create feature branch from `main`
2. Make changes and commit
3. Open Pull Request
4. Code review and testing
5. Merge to `main`

See [CONTRIBUTING.md](./CONTRIBUTING.md) for details.

## 📝 License

MIT License - See [LICENSE](./LICENSE) for details.

## 🆘 Support

- **Documentation**: [docs/](./docs/)
- **Issues**: [GitHub Issues](https://github.com/SamuraiBuddha/building-code-mcp/issues)
- **Email**: support@ehrigbim.com

---

**Built with ❤️ for the construction industry by Ehrig BIM & IT Consultation, Inc.**