# Test Issues for PR Extensions

This file documents the intentional issues created in this repository for testing GitHub Pull Request extensions.

## Issues Created

### 1. Documentation Typos (README.md)
**Type:** Spelling errors  
**Location:** Line 38-40  
**Description:**
- "Follow" misspelled as "Folow"
- "installed" misspelled as "instaled"

**Why this is useful for testing:**
- Tests spell-checking and linting extensions
- Tests code review comments on documentation changes
- Simple to fix, good for testing basic PR workflows

### 2. Missing Dependency Installation (test-pr-workflow.yaml)
**Type:** Logical error  
**Location:** Lines 21-28  
**Description:**
- Workflow tries to run `npm test` and `npm run build` without first running `npm install`
- This will fail at runtime because dependencies are not installed

**Why this is useful for testing:**
- Tests workflow validation extensions
- Tests CI/CD failure detection
- Realistic scenario that requires understanding of the workflow logic

### 3. YAML Syntax Errors (broken-workflow.yaml)
**Type:** Syntax error  
**Location:** Lines 17 and 20  
**Description:**
- Line 17: Comment and `run` command on separate lines without proper YAML structure
- Line 20: Incorrect indentation (extra spaces before `run:`)

**Why this is useful for testing:**
- Tests YAML linting extensions
- Tests syntax validation
- Will be caught by GitHub Actions workflow validation
- Common mistake that PR extensions should catch

### 4. Missing Workflow Permissions (test-pr-workflow.yaml & broken-workflow.yaml)
**Type:** Security issue  
**Location:** Both workflow files  
**Description:**
- Workflows do not limit the permissions of the GITHUB_TOKEN
- Should add explicit permissions block with minimal required permissions (e.g., `contents: read`)

**Why this is useful for testing:**
- Tests security scanning and CodeQL integration
- Tests GitHub Actions security best practices validation
- Important security consideration for PR reviews

## How to Use These Issues

These issues are intentional and can be used to test:
1. **PR Review Extensions** - Test automated code review comments
2. **Linting Tools** - Test YAML and markdown linters
3. **CI/CD Integration** - Test workflow validation and execution
4. **Spell Checkers** - Test documentation quality checks
5. **Diff Views** - Test code change visualization

## Expected Fixes

To fix these issues:
1. Fix typos: "Folow" → "Follow", "instaled" → "installed"
2. Add `npm install` step before running tests/build in test-pr-workflow.yaml
3. Fix YAML syntax in broken-workflow.yaml (proper indentation and structure)
4. Add explicit permissions blocks to both workflow files for security best practices
