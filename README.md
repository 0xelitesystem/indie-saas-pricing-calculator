# indie-saas-pricing-calculator

![Indie SaaS Pricing Calculator screenshot](screenshot.png)

**Live demo:** https://0xelitesystem.github.io/indie-saas-pricing-calculator/

Side-by-side pricing math for indie SaaS founders deciding between BYOK, bundled, and hybrid pricing. Real margins, real churn-adjusted LTV, real breakeven user counts. Browser-only.

For general information only. This is not financial, tax or legal advice. Check the numbers with a qualified professional before you rely on them.

## What it does

You're shipping a SaaS that uses an LLM or other paid API. You can charge customers in three ways:

- **BYOK** (bring your own key): customer pays the API provider directly, you charge a thin platform fee.
- **Bundled**: you charge a higher subscription that includes API costs; you eat the variance.
- **Hybrid**: small base subscription, customer pays API directly on top.

The tool calculates, per-model: gross margin, COGS per user, net per user, churn-adjusted LTV, LTV/CAC ratio, and the number of customers you need to hit $50K MRR.

## Inputs

| Input | What it's for |
|---|---|
| API cost / user / month | The variable cost of LLM or other API usage |
| Infrastructure cost / user / month | Hosting, bandwidth, storage |
| Payment processor fee (%) | Stripe default 2.9% + 30¢ ignored for simplicity |
| BYOK price | What you'd charge for the thin platform layer |
| Bundled price | All-in subscription that absorbs API |
| Hybrid base price | Lower base for users who bring their own key |
| Monthly churn rate (%) | Drives LTV math |
| CAC | Paid + organic blended |

## Outputs

Per pricing model:

- **Gross margin** (green ≥80%, amber 60-79%, red <60%)
- **Revenue / user / month**
- **COGS / user / month**
- **Net / user / month**
- **Churn-adjusted LTV** = net / churn rate
- **LTV/CAC ratio** (green ≥3x, amber 1.5-3x, red <1.5x)
- **Users needed for $50K MRR**

Plus a verdict block that names the winner per dimension and flags margins under 50% or LTV/CAC under 1.5x.

## Use

[https://0xelitesystem.github.io/indie-saas-pricing-calculator/](https://0xelitesystem.github.io/indie-saas-pricing-calculator/)

Or open `index.html` locally; everything runs in the browser.

1. Enter your API cost, infrastructure cost, and payment fee per user, or click **Load example: $50K MRR target**.
2. Enter your BYOK, bundled, and hybrid prices, monthly churn, and CAC.
3. Click **Calculate**.
4. Compare margin, LTV, LTV/CAC, and users needed per model, then read the verdict block. **Reset** clears the form.

## Why this exists

Founders building on paid APIs have to choose between BYOK, bundled, and hybrid pricing, and the margin and LTV math differs for each. This tool puts the three models side by side. It is one HTML file with inline CSS and JavaScript: no account, no tracking, no analytics, no external scripts or fonts, and it works offline. MIT licensed, so you can fork it, self-host it, or read every line.

## Privacy

Everything runs in your browser. The numbers you enter are never sent anywhere and are not saved; reload the page and they reset. The only thing written to storage is your light or dark theme choice, saved in localStorage under the key `theme`. No analytics, no cookies, no network requests.

## Run locally

```bash
git clone https://github.com/0xelitesystem/indie-saas-pricing-calculator
cd indie-saas-pricing-calculator
```

Then open `index.html` in any modern browser. Or serve the folder with `python -m http.server 8000` and visit http://localhost:8000.

## Build

No build step. The whole tool is one `index.html` with no dependencies, so there is nothing to install or compile.

## What this tool does NOT do

- No taxes, no shared overhead (salary, tools, marketing), no cohort modeling. It's per-user math.
- No live API price data; you enter the rate.
- No live churn data; you enter your assumption.
- No connection to your billing provider; this is a planning calculator, not analytics.
- No storage. Reload the page and everything resets.

## What's not included

- No localStorage except the light or dark theme choice, no cookies, no tracking.
- No third-party scripts.
- No paywall.

## Pairs with

- [breakeven-runway-calculator](https://github.com/0xelitesystem/breakeven-runway-calculator): plug the net-per-user number from this tool into the runway calculator to project breakeven date.
- [indie-saas-financial-baseline](https://github.com/0xelitesystem/indie-saas-financial-baseline): the markdown reference on indie SaaS money discipline that this calculator implements one section of.
- [prompt-cost-calculator](https://github.com/0xelitesystem/prompt-cost-calculator): use this to figure out the per-user API cost input.

## More

Part of a catalog of single-file browser tools and plain-language references, all MIT licensed and dependency-free: [0xelitesystem.github.io](https://0xelitesystem.github.io/). Built by [elitesystem.ai](https://elitesystem.ai).

## License

MIT.
