# Implementation Checklist

Use this checklist when developing a new skill from idea to production.

## Pre-Development Phase

### Planning
- [ ] Skill idea fully documented in SKILL_IDEAS.md
- [ ] Success criteria defined and agreed upon
- [ ] Complexity and priority assessed
- [ ] Stakeholder alignment (if applicable)
- [ ] Resource allocation confirmed

### Design
- [ ] Created skill spec document (copy of SKILL_TEMPLATE.md)
- [ ] Use cases documented with examples
- [ ] Input/output specifications finalized
- [ ] Architecture design reviewed
- [ ] Dependencies identified and available
- [ ] Edge cases and failure modes documented

---

## Development Phase

### Core Implementation
- [ ] Project structure created
- [ ] Core algorithm implemented
- [ ] Error handling in place
- [ ] Logging configured
- [ ] Dependencies verified to work
- [ ] Code follows team standards

### Testing
- [ ] Unit tests written and passing
- [ ] Integration tests created
- [ ] Edge cases tested
- [ ] Error handling tested
- [ ] Performance benchmarked
- [ ] Test coverage >= 80%

### Documentation
- [ ] Docstrings written for all functions
- [ ] README created with usage examples
- [ ] Example scripts provided
- [ ] Configuration options documented
- [ ] Known limitations clearly stated
- [ ] FAQ section added if relevant

### Quality Assurance
- [ ] Code reviewed by team member
- [ ] All test cases passing
- [ ] No critical warnings/linting issues
- [ ] Performance meets targets
- [ ] Security review completed (if applicable)
- [ ] Accessibility considerations addressed

---

## Pre-Release Phase

### Integration
- [ ] Skill integrates with existing systems
- [ ] Dependencies documented
- [ ] Configuration management in place
- [ ] Monitoring/alerting setup
- [ ] Backward compatibility checked

### Documentation & Training
- [ ] User documentation complete
- [ ] API documentation generated
- [ ] Release notes drafted
- [ ] Internal team walkthrough scheduled
- [ ] Support documentation prepared

### Release Preparation
- [ ] Version number assigned
- [ ] CHANGELOG updated
- [ ] Release branch created
- [ ] All tests passing on release branch
- [ ] Build artifacts generated

---

## Release Phase

### Deployment
- [ ] Deployed to staging environment
- [ ] Staging testing completed
- [ ] Performance validated in staging
- [ ] Deployed to production (with gradual rollout if applicable)
- [ ] Production health checks passing

### Monitoring
- [ ] Real-time monitoring active
- [ ] Alerts configured
- [ ] Error tracking setup
- [ ] Usage metrics tracked
- [ ] First 24 hours monitored closely

---

## Post-Release Phase

### Support & Validation
- [ ] User feedback collected
- [ ] Bug reports tracked and triaged
- [ ] Performance metrics analyzed
- [ ] Usage patterns studied
- [ ] Critical issues addressed within SLA

### Documentation Updates
- [ ] Based on user feedback, docs updated
- [ ] Known issues documented
- [ ] Troubleshooting guide added
- [ ] FAQ updated with real questions
- [ ] Examples refined based on usage

### Optimization
- [ ] Performance optimization opportunities identified
- [ ] User experience improvements suggested
- [ ] Feature requests compiled
- [ ] Roadmap updated
- [ ] Version 1.1 planning started (if applicable)

---

## Maintenance Phase

### Ongoing
- [ ] Regular security reviews scheduled
- [ ] Dependency updates monitored
- [ ] Performance metrics tracked
- [ ] User satisfaction monitored
- [ ] Support resources available

### Improvements
- [ ] Bug fixes deployed promptly
- [ ] Minor improvements released regularly
- [ ] Major improvements planned for next version
- [ ] User feedback incorporated
- [ ] Community contributions encouraged (if open source)

---

## Files to Create/Update

### New Skill Directory Structure
```
skills/[category]/[skill-name]/
├── README.md              # Main documentation
├── SKILL.md              # Use SKILL_TEMPLATE.md as base
├── requirements.txt      # Python dependencies (if applicable)
├── setup.py             # Installation script (if applicable)
├── src/
│   └── [skill_name].py   # Main implementation
├── tests/
│   ├── test_*.py        # Test files
│   └── fixtures/        # Test data
├── examples/
│   ├── example_1.py     # Usage examples
│   └── example_2.py
└── docs/
    ├── API.md           # API documentation
    ├── TROUBLESHOOTING.md
    └── FAQ.md
```

### Repository Updates
- [ ] SKILL_IDEAS.md updated (move skill status to "Complete", add link)
- [ ] Root README.md updated if needed
- [ ] CONTRIBUTING.md updated with new patterns discovered
- [ ] Version numbers bumped
- [ ] CHANGELOG updated

---

## Sign-Off

### Readiness Criteria
- [ ] All development checklist items complete
- [ ] All tests passing
- [ ] Documentation reviewed and approved
- [ ] Security review approved
- [ ] Performance targets met
- [ ] Stakeholder sign-off obtained

### Final Review
- [ ] Tech lead approval
- [ ] Product owner approval (if applicable)
- [ ] Documentation manager approval (if applicable)

### Release Authority
- **Reviewed by**: [Name]
- **Approved by**: [Name]
- **Released by**: [Name]
- **Release Date**: YYYY-MM-DD
- **Version**: X.Y.Z

---

## Rollback Plan

If critical issues are discovered post-release:

1. **Immediate Actions**:
   - [ ] Issue severity assessed
   - [ ] Rollback decision made
   - [ ] Stakeholders notified

2. **Rollback Execution**:
   - [ ] Previous version deployed
   - [ ] Health checks run
   - [ ] Users notified of rollback
   - [ ] RCA initiated

3. **Post-Rollback**:
   - [ ] Root cause analysis completed
   - [ ] Fix implemented and tested thoroughly
   - [ ] Re-release plan created
   - [ ] Post-mortem scheduled

---

## Tips for Success

### Best Practices
1. **Start with the spec**: Don't write code until the design is solid
2. **Test early and often**: Catch issues before they reach users
3. **Document as you go**: Don't leave it to the end
4. **Get feedback early**: Share prototypes with potential users
5. **Plan for monitoring**: Ship observability, not just features
6. **Keep it simple**: Complex skills are hard to maintain
7. **Make it composable**: Design skills to work with other skills

### Common Pitfalls to Avoid
- ❌ Skipping the design phase
- ❌ Inadequate error handling
- ❌ Insufficient testing
- ❌ Documentation left until the end
- ❌ No monitoring/alerting setup
- ❌ Over-engineering for future use cases
- ❌ Tight coupling to other systems
- ❌ No rollback plan

---

## Questions & Support

- **Design questions**: Open an issue in the repo
- **Implementation guidance**: See docs/SKILL_DESIGN.md
- **Review process**: Ask team lead for code review slot
- **Release process**: Consult DevOps/Release manager

---

**Last Updated**: 2026-03-12
