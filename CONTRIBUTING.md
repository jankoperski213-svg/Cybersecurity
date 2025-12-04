# Contributing to Cybersecurity Portfolio

Thank you for your interest in this cybersecurity learning repository! This document provides guidelines for contributing.

## 📋 Overview

This repository documents a cybersecurity professional's journey into penetration testing and defensive security. It combines:
- Learning notes from courses & certifications
- Practical pentesting lab writeups
- Security tools & automation scripts
- Portfolio demonstration for recruitment

## 🤝 How to Contribute

### 1. **Reporting Issues**
- Found a typo or error in documentation?
- Have a suggestion for lab exercises?
- Report via GitHub Issues
- Include clear description and references

### 2. **Improving Documentation**
Have suggestions to improve existing content?

```bash
# Fork the repository
# Create a new branch
git checkout -b docs/your-improvement

# Make your changes
# Commit with clear message
git commit -m "docs: Improve [section name] documentation"

# Push and create a pull request
git push origin docs/your-improvement
```

### 3. **Adding Lab Writeups**

Want to share pentesting lab solutions?

**File structure:**
```
Projects/
├── TryHackMe-Labs/
│   └── [Machine-Name]/
│       ├── README.md          # Lab overview & goals
│       ├── walkthrough.md     # Step-by-step solution
│       └── notes.md           # Key learnings
└── HackTheBox-Writeups/
    └── [Box-Name]/
        ├── README.md
        └── writeup.md
```

**Writeup format:**
- Machine/Challenge name & difficulty
- Objective & scope
- Tools used
- Step-by-step exploitation process
- Key vulnerabilities discovered
- Lessons learned
- Defense recommendations

### 4. **Adding Tools & Scripts**

Sharing security automation scripts?

**File structure:**
```
Projects/Custom-Scripts/
├── [script-name]/
│   ├── README.md          # Usage & documentation
│   ├── script.py          # Main script
│   └── requirements.txt    # Dependencies
```

**Script documentation must include:**
- Purpose & use case
- Requirements & installation
- Usage examples
- Disclaimer about legal use

## 📝 Commit Message Guidelines

Follow this format for clarity:

```
<type>: <subject>

<body>

<footer>
```

**Types:**
- `docs:` - Documentation changes
- `feat:` - New features/labs/scripts
- `fix:` - Fixes in existing content
- `refactor:` - Content reorganization
- `test:` - Lab testing & verification

**Examples:**
```
docs: Add CompTIA Security+ domain 1 notes
feat: Add TryHackMe "Blue" writeup
fix: Correct Metasploit syntax in script
```

## 🔒 Security & Ethical Guidelines

All contributions must adhere to:

1. **Legal Use Only**
   - All labs: Authorized environments only (TryHackMe, HackTheBox, personal labs)
   - No real-world exploitation without permission
   - Document that all work is for educational purposes

2. **No Sensitive Information**
   - Never commit credentials or API keys
   - Use `.env.example` for configuration
   - Reference `.gitignore` for excluded files

3. **Responsible Disclosure**
   - Do not publish 0-day exploits
   - Follow responsible disclosure timelines
   - Respect vendor security policies

4. **Attribution**
   - Credit sources & inspirations
   - Link to original challenges/courses
   - Cite security researchers & tools

## 📚 Content Quality Standards

### Documentation
- ✅ Clear, concise writing
- ✅ Proper markdown formatting
- ✅ Code syntax highlighting
- ✅ Step-by-step explanations
- ✅ Links to resources
- ✅ Screenshots where helpful

### Code
- ✅ Commented & documented
- ✅ PEP 8 compliance (Python)
- ✅ Error handling
- ✅ Usage examples
- ✅ Legal disclaimer

### Lab Writeups
- ✅ Complete walkthrough
- ✅ Tools & commands used
- ✅ Vulnerability explanations
- ✅ Defense recommendations
- ✅ Learning takeaways

## 🔄 Pull Request Process

1. **Create a fork** and branch from `main`
2. **Make your changes** following guidelines above
3. **Test thoroughly** - verify all content works
4. **Write clear PR description**
   - What does it add/fix?
   - Why is it valuable?
   - Any security/ethical considerations?
5. **Submit PR** for review
6. **Address feedback** from maintainers
7. **Merge** once approved

## 📞 Contact & Questions

- Have questions? Check existing issues first
- Open a new issue for discussion
- Request mentor guidance if needed
- Keep discussions professional & constructive

## 📜 License & Attribution

This repository is for educational purposes. By contributing, you agree that:
- Contributions are original work
- Content follows ethical security guidelines
- Repository maintains its educational focus

## 🙏 Thank You!

Thank you for contributing to this cybersecurity learning repository! Every contribution helps build a better security community.

---

**Last Updated:** December 2024  
**Maintainer:** jankoperski213-svg
