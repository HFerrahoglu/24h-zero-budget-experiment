# r/SideProject: hedef ≤18:30 TR (10:30 ET)

**Tür:** Text post · **Flair:** (Görev 2.2'de zorunlu bir flair varsa en uygun olanı seçin. Yoksa boş bırakın.)

**Başlık (kopyalayın):**
```
We checked 50 launch channels for brand-new accounts with AI-assisted posts. On a zero-budget, 24-hour launch, 26 were closed and only 1 had no blocking rule
```

**Gövde (kopyalayın):**
```
Some context first: I'm the human operator in a public experiment. An AI agent (Claude) gets 24 hours, $0 and no audience to find a real problem, build something and try to sell it. I only handle the steps that need a person, like creating accounts and posting. The agent drafted this post and I'm publishing it.

The first wall it hit was distribution, not code. Here's what it found for a brand-new account with AI-assisted text (every rule is linked to its source in the tool):

- Hacker News: "Please don't put generated text in HN posts." Show HN is also temporarily restricted for new accounts.
- Product Hunt: new accounts wait one week before they can post a product.
- r/webdev, r/SaaS, r/Entrepreneur, r/InternetIsBeautiful: AI-written posts aren't allowed (per a third-party rules tracker). r/SaaS also wants a 60-day-old account.
- Stack Overflow: generative-AI content is banned.
- Free directory queues: Uneed assigns a date at least 50 days out, Firsto says about 180 days, OpenHunts showed "~60 weeks", and Open-Launch's free launches are booked into 2027.

Out of 50 channels, for "new account + AI-assisted text + needs eyes within 24h + $0": 26 closed, 23 possible with caveats, and 1 with no blocking rule we could find.

So the agent turned the research into a small tool. You pick your account age, whether AI touched your text, how fast you need visibility and your budget. It sorts channels into open / caveats / closed and shows the rule, the source, and whether the source is the platform's own page or a third-party tracker.

To be clear, it's not an AI wrapper. The tool makes no AI or API calls. It's a sourced dataset plus plain JavaScript that runs in your browser. The only AI part is who built it, and that's said up front.

Free, no sign-up: https://hferrahoglu.github.io/where-can-i-post/?ref=rsp

The free version covers 12 major channels. There's also a $7 one-time kit with all 50, plus a launch profile with character counters, an autofill bookmarklet for submit forms (it never auto-submits) and a tracker. That's how we're testing whether anyone would actually pay for this. You don't need it to use anything in this post.

Caveats: rules change, and some rows rely on third-party trackers (each row is labeled). If you spot something wrong, comment and I'll fix it today.

Full log of every decision the agent made: https://github.com/HFerrahoglu/24h-zero-budget-experiment
```
