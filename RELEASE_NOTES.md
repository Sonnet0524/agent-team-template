# Release Notes

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

---

## [1.1.0] - 2026-03-08

### 🎉 Major Update - Production Ready

This release validates the PM Agent Template through real-world project deployment.

### ✨ New Features

#### Parallel Agent Launch Pattern
- **Verified Method**: Parallel execution of multiple agents using `opencode run --agent`
- **Task File Mechanism**: Structured task files in `tasks/` directory
- **Report File Mechanism**: Standardized reports in `reports/` directory
- **Passive Monitoring**: PM Agent waits for reports instead of polling

**Impact**:
- Development cycle reduced from 6 weeks to 3 days (93% faster)
- PM Agent workload reduced by 80%
- Test coverage increased to 91.7% (target: 80%)

#### Permission Configuration Best Practices
- Added permission configuration guide in `opencode.json`
- Non-interactive mode requires `edit: "allow"`
- Interactive mode supports `edit: "ask"`

### 📚 Documentation

#### New Experience Documents
- [Parallel Agent Launch Experience](agents/pm/experiences/parallel-agent-launch-20260308.md)
  - Non-interactive mode permission configuration
  - Task file + report file mechanism
  - Complete examples and best practices

- [v1.1 Development Experience](agents/pm/experiences/v1.1-development-20260308.md)
  - Full development cycle management
  - Problem discovery and resolution
  - Multi-repository collaboration

#### New Archive Section
- [Knowledge-Assistant Experience Archive](archive/knowledge-assistant-experiences/)
  - Real-world project implementation
  - Validated work patterns
  - Performance metrics and results

### 🔧 Improvements

#### README Enhancements
- Added v1.1.0 new features section
- Included real-world performance data
- Added quick reference for best practices
- Updated version to 1.1.0

#### opencode.json Updates
- Added permission configuration for PM Agent
- Added permission guide with examples
- Documented interactive vs non-interactive modes

### 📊 Validated Work Patterns

#### Pattern 1: Task File Driven
```
tasks/ → Agent reads → Agent executes → reports/ → PM reads
```

#### Pattern 2: Parallel Execution
```bash
# Independent tasks can run in parallel
opencode run --agent core "task1..." &
opencode run --agent ai "task2..." &
opencode run --agent integration "task3..." &
```

#### Pattern 3: Passive Reception
- ❌ No active polling
- ✅ Wait for agent reports
- ✅ Check reports on user inquiry

### 🎯 Project Validation

**Validated Project**: [Knowledge Assistant](https://github.com/Sonnet0524/knowledge-assistant)

**Results**:
| Metric | Target | Actual | Status |
|--------|--------|--------|--------|
| Development Cycle | 6 weeks | 3 days | ✅ 93% faster |
| Test Coverage | >80% | 91.7% | ✅ Exceeded |
| Integration Tests | Pass | 269/269 | ✅ 100% |
| PM Workload | High | Low | ✅ 80% reduced |

### 🔄 Changed

- Updated version from 1.0.0 to 1.1.0
- Changed status from "Template Ready" to "Production Ready"
- Enhanced experience documentation structure
- Improved permission configuration guidance

---

## [1.0.0] - 2026-03-08

### 🎊 Initial Release

First official release of PM Agent Template.

### ✨ Features

#### Core Architecture
- PM Agent as central coordinator
- Team templates for different scenarios
- Three-level documentation system
- Quality gate mechanism

#### Team Templates
- Core Team - Data processing
- AI Team - AI/ML capabilities
- Test Team - Quality assurance
- Integration Team - System integration
- Research Team - Research projects

#### Documentation System
- Level 0: CATCH_UP.md (required, <50 lines)
- Level 1: ESSENTIALS.md, WORKFLOW.md (<100 lines)
- Level 2: guides/, experiences/, archive/

#### Skills Framework
- Git workflow
- Code review process
- Quality gate decision support

### 📁 Project Structure
- agents/ - Agent definitions and templates
- framework/ - Skills and memory management
- status/ - Status tracking
- archive/ - Experience library
- tasks/ - Task files (dynamic)
- reports/ - Report files (dynamic)
- logs/ - Log files (dynamic)

---

## Version Summary

| Version | Date | Status | Key Feature |
|---------|------|--------|-------------|
| 1.1.0 | 2026-03-08 | Production Ready | Parallel Agent + Validated Patterns |
| 1.0.0 | 2026-03-08 | Template Ready | Initial Release |

---

**Maintainer**: PM Agent Framework  
**Repository**: [AgentTeam-Template](https://github.com/Sonnet0524/AgentTeam-Template)
