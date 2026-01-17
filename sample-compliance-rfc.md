# AWS EC2 Enhanced Compliance RFC - Fixed Format

## Overview
This RFC defines comprehensive compliance requirements for EC2 instances with proper tag format.

## Environment-Specific Requirements

### Development Environment
**Detection Criteria:**
- Instance names containing: dev, development, sandbox

**Required Tags:**
Environment = development
Owner = dev-team@company.com
Project = development-project
CostCenter = DEV-2024
Purpose = development-testing
Country = usa

**Monitoring Requirements:**
- CPUUtilization alarm (threshold: 90%)
- Evaluation period: 10 minutes

### Production Environment
**Detection Criteria:**
- Instance names containing: prod, production, live

**Required Tags:**
Environment = production
Owner = platform-team@company.com
Application = production-app
CostCenter = PROD-2024
BusinessUnit = engineering
Purpose = production-workload
Country = usa

**Monitoring Requirements:**
- CPUUtilization alarm (threshold: 80%)
- Evaluation period: 5 minutes

### Testing Environment
**Detection Criteria:**
- Instance names containing: test, staging, qa

**Required Tags:**
Environment = testing
Owner = qa-team@company.com
TestSuite = automated-tests
CostCenter = QA-2024
Purpose = quality-assurance
Country = usa

**Monitoring Requirements:**
- CPUUtilization alarm (threshold: 85%)
- Evaluation period: 5 minutes

## Enhanced Features
- 5-stage notification system
- Two-pass AI analysis (structure + values)
- Graceful fallback if Bedrock unavailable
- Enhanced retry policies (2 attempts, 1-hour max age)
- Comprehensive error handling

## Compliance Actions
1. **Stage 1**: Launch detection notification
2. **Stage 2**: RFC requirements analysis
3. **Stage 3**: Auto-remediation completion
4. **Stage 4**: Already compliant (if applicable)
5. **Stage 5**: RFC update processing (bulk operations)