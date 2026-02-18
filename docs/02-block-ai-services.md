# Lab 2: Block AI Services

## Introduction
In this lab, you will use Cloudflare Secure Web Gateway (SWG) to:

- Create HTTP filtering policies
- Block unapproved AI tools
- Protect prompts sent to web-based AI apps
- Use Gateway HTTP redirects and Workers block pages for user-friendly messaging

> Reference: Cloudflare docs - `Gateway` → `HTTP policies`, `Application and content categories`, and `Custom block pages`.

## Part 1: Create HTTP Filtering Policies

1. In the Zero Trust dashboard, go to **Gateway** → **Firewall Policies** → **HTTP**.
2. Click **Create a policy**.
3. Set **Action** to **Block**.
4. In **Selector**, choose **Application** or **Domain**.
5. Use **Application** selectors to target common AI tools (e.g., *ChatGPT*, *Claude*, *Gemini*).
6. Optionally, add conditions for **User group**, **Device posture**, or **Location** for more granular control.
7. Save the policy.

## Part 2: Test Blocking Rules

1. From a WARP-enrolled device, open a browser.
2. Browse to `https://chatgpt.com`, `https://claude.ai`, or other AI tools you blocked.
3. Confirm that:
   - The site is blocked, **and**
   - The event appears in **Gateway → Logs** (filter by your device IP or user).

## Part 3: Gateway HTTP Redirects + Workers Block Pages

> Goal: Give users a clear message and optionally redirect them to an internal AI portal.

### 3.1 Create a Workers-Based Block Page (Optional)

1. In the Cloudflare dashboard, go to **Workers & Pages** → **Create application**.
2. Choose **Create Worker** and use a simple script that:
   - Returns an HTML page explaining that AI access is blocked or restricted.
   - Optionally includes a link to an approved internal AI portal.
3. Deploy the Worker and note the **Worker URL**.

### 3.2 Configure HTTP Redirect / Block Page

1. In **Gateway → Firewall Policies → HTTP**, edit your AI blocking policy or create a new one.
2. For **Action**, choose:
   - **Block with custom block page**, or
   - **Redirect** (if available for your policy type).
3. Set the **custom block page or redirect URL** to your Worker URL or internal help page.
4. Save the policy.

## Lab Verification Checklist

- HTTP policy exists targeting AI applications and/or domains.
- Access to blocked AI tools results in a block or redirect page.
- AI prompts and uploads are inspected according to your HTTP/DLP policy design.
- Events appear in **Gateway Logs** with the expected policy names and actions.
