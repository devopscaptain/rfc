# AWS EC2 Compliance RFC - Name-Based Environment Detection

## Overview
This RFC defines compliance requirements for EC2 instances based on intelligent name-based environment detection only.

## Environment-Specific Requirements

### Development Environment
**Detection Criteria:**
- Instance names containing: dev, development, sandbox
- Instance ID containing: dev (if no Name tag)

**Required Tags:**
- Environment: development
- Owner: ashish
- Project: development-project
- CostCenter: dev-ops
- Purpose: poc
- Country: india

**Monitoring Requirements:**
- CPUUtilization alarm (threshold: 90%)
- Evaluation period: 10 minutes (cost optimization)

### Production Environment
**Detection Criteria:**
- Instance names containing: prod, production, live
- Instance ID containing: prod (if no Name tag)

**Required Tags:**
- Environment: production
- Owner: ashish
- Application: production-app
- CostCenter: prod-ops
- BusinessUnit: engineering
- Purpose: poc
- Country: india

**Monitoring Requirements:**
- CPUUtilization alarm (threshold: 80%)
- StatusCheckFailed alarm
- NetworkIn alarm (threshold: 1GB)
- Evaluation period: 5 minutes (high availability)

### Testing Environment
**Detection Criteria:**
- Instance names containing: test, staging, qa
- Instance ID containing: test (if no Name tag)

**Required Tags:**
- Environment: testing
- Owner: ashish
- TestSuite: automated-tests
- CostCenter: qa-ops
- Purpose: poc
- Country: india

**Monitoring Requirements:**
- CPUUtilization alarm (threshold: 85%)
- StatusCheckFailed alarm
- Evaluation period: 5 minutes

## Default Behavior
- If no environment indicators found in name or instance ID: **defaults to development**
- Instance type is NOT considered for environment detection
- Only name-based intelligent detection is used

## Compliance Actions
1. **Name-Only Detection**: AI analyzes instance name and ID only
2. **Smart Tagging**: Environment-specific tags applied automatically
3. **Monitoring Setup**: Appropriate alarms created based on environment
4. **Notification**: Detailed email with emojis sent for all actions
5. **Verification**: Post-remediation compliance check

## Cost Optimization
- Development: Minimal monitoring to reduce costs
- Production: Full monitoring for reliability
- Testing: Balanced approach for quality assurance
