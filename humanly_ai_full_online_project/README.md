HUMANLY AI — ONLINE AI REWRITER (Cloudflare Pages + Workers AI)

This project includes:
- Responsive frontend in public/index.html
- Server-side AI endpoint in functions/api/humanize.js
- Wrangler config with a Workers AI binding
- No API key is exposed in browser JavaScript

Important cost note:
Cloudflare Workers AI currently documents a free allocation of 10,000 Neurons/day; requests can fail after that allocation is used on the Free plan. Verify current terms and the model's availability before launch:
https://developers.cloudflare.com/workers-ai/platform/pricing/
Static Pages assets are free under the documented Pages plan, while API calls are subject to Workers/AI limits:
https://developers.cloudflare.com/pages/functions/pricing/

DEPLOYMENT (recommended path: Cloudflare Pages + Git)
1. Create/sign into Cloudflare: https://dash.cloudflare.com/
2. Create a GitHub repository and upload these project files, preserving the folder structure.
3. In Cloudflare dashboard, go to Workers & Pages → Create → Pages → Connect to Git and select the repository.
4. Build settings: Framework preset = None; Build command = leave blank; Build output directory = public.
5. The included wrangler.toml declares the AI binding. If Cloudflare dashboard requests an AI binding separately, add binding named AI under Settings → Functions → Workers AI (dashboard wording can change).
6. Deploy. Your public site URL will be shown by Cloudflare.
7. Test with a short paragraph. If /api/humanize returns an error, inspect the Pages deployment logs and confirm the AI binding is configured.

ALTERNATIVE: Wrangler CLI
Install Node.js, then install Wrangler (`npm install -D wrangler`), authenticate (`npx wrangler login`) and deploy using the current Cloudflare Pages deployment workflow. Cloudflare changes CLI details over time, so follow the official Pages docs:
https://developers.cloudflare.com/pages/get-started/
https://developers.cloudflare.com/workers-ai/get-started/workers-wrangler/

NOTES
- A free-tier AI service is not unlimited. If you want truly no recurring provider charges, a self-hosted model needs a machine/server to run it.
- This app has a 12,000-character input limit per request to reduce timeouts and abuse.
- The app does not promise that text will evade AI detectors. Review generated output for accuracy and your own voice.
- For public launch, consider adding rate limiting / abuse protection before sharing widely.
