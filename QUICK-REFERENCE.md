# Quick Reference Guide

## Useful Links
- [One Dash (Zero Trust Console)](https://one.dash.cloudflare.com)
- [Gateway Logs](https://one.dash.cloudflare.com/?to=/:account/zero-trust/analytics/gateway)
- [Help/Debug Tools](https://help.teams.cloudflare.com)

## CLI Commands
### WARP (warp-cli)
- `warp-cli status`: Check connection
- `warp-cli connect`: Connect to ZT
- `warp-cli disconnect`: Disconnect ZT
- `warp-cli settings`: Show local settings

## Common Policy Patterns
### HTTP Block (Selector: Application)
- **Application** `in` `ChatGPT`, `Claude`, `Gemini`
- **Action**: `Block`

### HTTP Isolate (Selector: Application)
- **Application** `in` `ApprovedAI`
- **Action**: `Isolate`
