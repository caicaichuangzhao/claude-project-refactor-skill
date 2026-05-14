# Claude Code Skill: Project Refactor

A Claude Code skill for comprehensive project refactoring and migration management.

## Overview

This skill provides a structured approach to refactoring projects, tracking architecture changes, API routes, frontend interfaces, and optimization goals throughout the refactoring process.

## Features

- **Architecture Tracking**: Document and monitor system structure changes
- **API Route Management**: Track API modifications and backward compatibility
- **Frontend Interface Audit**: Catalog UI components and their dependencies
- **Progress Monitoring**: Visual tracking of refactoring milestones
- **Risk Assessment**: Identify potential breaking changes before implementation

## Core Principles

1. **Track Before Change**: Document current state before making modifications
2. **Incremental Migration**: Break refactoring into manageable phases
3. **Backward Compatibility**: Maintain service during transition
4. **Rollback Planning**: Always have a plan to undo changes

## Skill Structure

```
claude-project-refactor-skill/
├── SKILL.md                        # Main entry point
├── references/
│   ├── checklist.md                # Refactoring checklist
│   ├── templates.md                # Document templates
│   └── analysis-guide.md           # Code analysis guidelines
```

## Usage

This skill automatically activates when you mention refactoring keywords:
- "refactor"
- "migrate"
- "rewrite"
- "upgrade project"
- "重构项目"
- "代码重构"
- "continue refactor"

## Typical Refactoring Workflow

### Phase 1: Assessment
1. Analyze current architecture
2. Identify technical debt
3. Document API contracts
4. Catalog frontend dependencies

### Phase 2: Planning
1. Define target architecture
2. Create migration phases
3. Plan data migration strategy
4. Set up feature flags for gradual rollout

### Phase 3: Execution
1. Set up parallel systems if needed
2. Migrate data layer first
3. Update API layer
4. Refactor frontend incrementally

### Phase 4: Validation
1. Run integration tests
2. Performance benchmarking
3. User acceptance testing
4. Monitor for regressions

## Example: E-commerce Platform Refactor

**From**: Express + EJS + SQLite
**To**: Next.js + Prisma + PostgreSQL

**Tracking Areas**:
- Database schema migration
- API endpoint mapping
- Template to component conversion
- Authentication flow changes
- Payment integration updates

## Key Documents Generated

1. **Architecture Diagram**: Before/After comparison
2. **API Mapping Sheet**: Old routes → New routes
3. **Component Inventory**: List of UI elements to migrate
4. **Risk Assessment**: Potential breaking changes
5. **Rollback Plan**: Emergency procedures

## Installation

Place this skill in your Claude Code skills directory:
- Windows: `%USERPROFILE%/.claude/skills/project-refactor/`
- macOS/Linux: `~/.claude/skills/project-refactor/`

## Integration with Other Skills

Works well with:
- **no-hardcode**: Ensures refactored code uses real data
- **enterprise-dev-plan**: Applies architectural best practices

## License

MIT

---

*Part of the Claude Code skills system*
