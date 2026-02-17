# Cloudflare Zero Trust Workshop - AI Security

Hands-on lab workshop: Deploy Cloudflare Zero Trust to protect employees from unauthorized external AI services.

## Module Request
**Network Access (ZTNA)**  
**Secure Web Gateway (SWG)**  
**Data Loss Prevention (DLP)**

## What You'll Build

**Lab 1:** Setup Zero Trust environment and connect devices  
**Lab 2:** Configure Gateway policies to block AI services  
**Lab 3:** Implement Data Loss Prevention (DLP) for AI tools  
**Lab 4:** Setup monitoring, alerts and analytics  
**Lab 5:** Create approved AI access with isolation

## Workshop Modules

| Module | Lab | Duration |
|--------|-----|----------|
| 1 | [Zero Trust Setup](./docs/01-zerotrust-setup.md) | 20 min |
| 2 | [Block AI Services](./docs/02-block-ai-services.md) | 30 min |
| 3 | [Data Loss Prevention](./docs/03-dlp-policies.md) | 30 min |
| 4 | [Monitoring & Analytics](./docs/04-monitoring.md) | 20 min |
| 5 | [Approved AI Access](./docs/05-approved-access.md) | 30 min |

**Total:** 2 hours 10 minutes

## Objectives

By the end of this workshop, you will:
- ✅ Deploy Cloudflare Zero Trust with WARP client
- ✅ Block access to unauthorized AI services (ChatGPT, Claude, Gemini, etc.)
- ✅ Prevent sensitive data uploads to public AI tools
- ✅ Configure identity-based access controls
- ✅ Implement device posture checks
- ✅ Create allowlist for approved AI services
- ✅ Setup DLP policies to detect sensitive information
- ✅ Monitor and analyze AI service usage
- ✅ Configure alerts for policy violations
- ✅ Use Browser Isolation for approved AI tools

## Requirements

- Computer with web browser (Chrome, Firefox, Safari, or Edge)
- Internet connection
- Free Cloudflare account
- Email address for identity verification
- Mobile device for 2FA (optional but recommended)

## Architecture Overview

```
┌─────────────────┐
│   Employees     │
│  (Any Device)   │
└────────┬────────┘
         │
         ├─── WARP Client
         │
┌────────▼────────────────────────┐
│   Cloudflare Zero Trust         │
│                                 │
│  ┌───────────────────────────┐ │
│  │  Identity Verification    │ │
│  │  - Email / SSO            │ │
│  │  - Device Posture         │ │
│  └───────────────────────────┘ │
│                                 │
│  ┌───────────────────────────┐ │
│  │  Gateway Policies (SWG)   │ │
│  │  - Block AI Services      │ │
│  │  - DLP Scanning           │ │
│  │  - Allow Approved Tools   │ │
│  └───────────────────────────┘ │
│                                 │
│  ┌───────────────────────────┐ │
│  │  Analytics & Logging      │ │
│  └───────────────────────────┘ │
└─────────────────────────────────┘
         │
         ├─── ✅ Approved AI (Isolated)
         └─── ❌ Blocked AI Services
```

## Quick Start

1. Start with [Module 1: Zero Trust Setup](./docs/01-zerotrust-setup.md)
2. Continue to [Module 2: Block AI Services](./docs/02-block-ai-services.md)
3. Complete [Module 3: Data Loss Prevention](./docs/03-dlp-policies.md)
4. Setup [Module 4: Monitoring & Analytics](./docs/04-monitoring.md)
5. Finish with [Module 5: Approved AI Access](./docs/05-approved-access.md)
6. Test blocking by accessing restricted AI services
7. Review logs and verify policies are working

## AI Services Blocked by Default

### Chat AI Services
- `chat.openai.com` - ChatGPT
- `claude.ai` - Anthropic Claude
- `gemini.google.com` - Google Gemini
- `perplexity.ai` - Perplexity AI
- `character.ai` - Character AI
- `poe.com` - Poe
- `you.com` - You.com

### Code AI Assistants
- `github.com/features/copilot` - GitHub Copilot
- `copilot.microsoft.com` - Microsoft Copilot
- `codeium.com` - Codeium
- `tabnine.com` - Tabnine
- `cursor.sh` - Cursor

### Image Generation AI
- `midjourney.com` - Midjourney
- `leonardo.ai` - Leonardo AI
- `playground.ai` - Playground AI
- `getimg.ai` - GetImg AI

### Writing AI Tools
- `jasper.ai` - Jasper
- `copy.ai` - Copy.ai
- `writesonic.com` - Writesonic
- `rytr.me` - Rytr

## What You'll Learn

### Module 1: Zero Trust Setup (20 min)
- Create Cloudflare Zero Trust account
- Configure organization settings
- Deploy WARP client on your device
- Connect device to Zero Trust
- Verify connectivity

### Module 2: Block AI Services (30 min)
- Create HTTP filtering policies
- Configure application-based blocking
- Setup domain-based blocking
- Test blocking rules
- View blocked requests in logs

### Module 3: Data Loss Prevention (30 min)
- Create DLP profiles
- Configure sensitive data patterns
- Apply DLP to AI services
- Test DLP detection
- Review DLP violations

### Module 4: Monitoring & Analytics (20 min)
- Access Gateway Analytics
- Create custom dashboards
- Setup email alerts
- Configure webhook notifications
- Export logs to SIEM

### Module 5: Approved AI Access (30 min)
- Create allow policies for approved AI
- Configure Browser Isolation
- Setup identity-based access
- Implement time-based restrictions
- Test isolated AI access

## Lab Files Structure

```
cloudflare-ai-security-workshop/
├── README.md                           # This file
├── QUICK-REFERENCE.md                  # Commands and shortcuts
├── docs/
│   ├── 01-zerotrust-setup.md          # Lab 1: Setup guide
│   ├── 02-block-ai-services.md        # Lab 2: Block AI policies
│   ├── 03-dlp-policies.md             # Lab 3: DLP configuration
│   ├── 04-monitoring.md               # Lab 4: Analytics setup
│   └── 05-approved-access.md          # Lab 5: Approved AI access
├── configs/
│   ├── gateway-policies.json          # Sample Gateway policies
│   ├── dlp-profiles.json              # DLP profile templates
│   └── warp-config.xml                # WARP deployment config
└── scripts/
    ├── deploy-policies.sh             # Automated policy deployment
    └── test-blocking.sh               # Test AI blocking rules
```

## Testing Your Setup

After completing the labs, test your configuration:

1. **Test AI Blocking**
   - Try accessing `chat.openai.com`
   - Try accessing `claude.ai`
   - Verify you see block page

2. **Test DLP**
   - Attempt to upload fake credit card number
   - Attempt to paste API key format
   - Check DLP logs for detections

3. **Test Approved Access**
   - Access approved AI tool
   - Verify isolation is active
   - Test copy/paste restrictions

## Troubleshooting

### WARP Client Won't Connect
```bash
# Check WARP status
warp-cli status

# Re-register device
warp-cli registration delete
warp-cli registration new

# Reconnect
warp-cli connect
```

### Policies Not Blocking
- Check policy precedence (lower number = higher priority)
- Verify device is connected to WARP
- Check if user is in exclusion group
- Review Gateway logs for policy matches

### Can't Access Approved AI
- Verify allow policy has precedence 0
- Check user email is in allowed group
- Confirm identity is verified
- Test from incognito/private window

## Resources

### Documentation
- [Quick Reference Guide](./QUICK-REFERENCE.md)
- [Cloudflare Zero Trust Dashboard](https://one.dash.cloudflare.com)
- [Zero Trust Documentation](https://developers.cloudflare.com/cloudflare-one/)
- [Gateway Policies Guide](https://developers.cloudflare.com/cloudflare-one/policies/filtering/)
- [WARP Client Deployment](https://developers.cloudflare.com/cloudflare-one/connections/connect-devices/warp/)

### Tools
- [Policy Testing Tool](https://developers.cloudflare.com/cloudflare-one/policies/filtering/test-gateway-policy/)
- [WARP Diagnostics](https://developers.cloudflare.com/cloudflare-one/connections/connect-devices/warp/troubleshooting/)
- [Gateway Logs](https://developers.cloudflare.com/cloudflare-one/analytics/logs/)

### Support
- [Cloudflare Community](https://community.cloudflare.com/)
- [Support Portal](https://support.cloudflare.com/)
- [Status Page](https://www.cloudflarestatus.com/)

## Best Practices

### 1. Start with Audit Mode
Deploy policies in audit-only mode first:
- Set action to `audit` for 2 weeks
- Review logs to understand usage patterns
- Identify false positives
- Switch to `block` after validation

### 2. Communicate Changes
- Send org-wide email about new AI policy
- Provide list of approved alternatives
- Create process for access requests
- Schedule training sessions

### 3. Regular Reviews
- Weekly: Review blocked attempts
- Monthly: Assess approved AI usage
- Quarterly: Update AI service list
- Annually: Audit security policy

### 4. Exception Process
```
Request → Manager Approval → Security Review → 
Access Granted → Monitor Usage → Quarterly Review
```

## Advanced Topics

### Integration with SIEM
- Export logs to Splunk/ELK
- Create correlation rules
- Setup automated alerting
- Build security dashboards

### API Automation
- Deploy policies via Terraform
- Automated testing scripts
- Bulk user management
- Dynamic policy updates

### Compliance Reporting
- Generate monthly reports
- Track policy violations
- Audit access logs
- Document exception approvals

## Contributing

Found an issue or want to improve the workshop?

1. Fork the repository
2. Create feature branch (`git checkout -b feature/improvement`)
3. Commit your changes (`git commit -m 'Add improvement'`)
4. Push to branch (`git push origin feature/improvement`)
5. Open Pull Request

## License

This workshop is licensed under the MIT License - see [LICENSE](LICENSE) file for details.

## Acknowledgments

- Cloudflare Zero Trust Team
- Security Community Contributors
- Workshop Participants and Feedback

---

**Ready to start?** Begin with [Module 1: Zero Trust Setup](./docs/01-zerotrust-setup.md)

⭐ If this workshop helped you, please give it a star!
