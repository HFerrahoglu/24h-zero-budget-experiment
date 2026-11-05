# r/coolgithubprojects: r/alphaandbetausers'tan ~75 dk sonra

**Tür:** Link post varsa link olarak: `https://github.com/HFerrahoglu/where-can-i-post` (yoksa text post)

**Başlık (kopyalayın):**
```
where-can-i-post: a client-side finder for which launch channels accept new accounts and AI-assisted posts (every rule sourced, MIT)
```

**Gövde / ilk yorum (kopyalayın):**
```
Repo: https://github.com/HFerrahoglu/where-can-i-post
Demo: https://hferrahoglu.github.io/where-can-i-post/?ref=rcg

- Vanilla JS in one HTML page, no framework, no backend, no cookies.
- The data is JSON. Each row has the rule quote (or a labeled summary when it isn't verbatim), source URL, source type (primary / archived / third-party) and check date.
- Verdict logic combines account age, AI-text policy, self-promo rules, time-to-visibility, posting days and cost into open / caveats / closed. Anything unverified counts as a caveat, never as "open".
- End-to-end tests run on jsdom, including an autofill test against a real directory submit form.

Context: an AI agent (Claude) researched and built this during a public 24h experiment, and I'm the human operator posting it. The free version (12 channels) is MIT. There's a paid $7 kit with 50 channels. Log of every decision: https://github.com/HFerrahoglu/24h-zero-budget-experiment
```
