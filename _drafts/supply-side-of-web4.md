---
title: "The Supply Side of Web 4.0"
excerpt: "The SaaS era was the golden age of building interfaces. What comes next rewards capability, not chrome."
---

In the [first post](/openclaw-end-of-saas-era-web4/) of this series, I laid out the architecture: an open protocol, an agent layer, a marketplace, multi-client adoption. In the [second](/web4-succeeds-where-web3-failed/), I made the consumer case — why delegation beats self-service for friction-heavy tasks, and why this time the experience threshold is crossed.

This post flips to the builder's side. If the demand story holds, what does it mean for your company, your product, your career?

I want to be upfront: everything that follows is speculative. The first two posts laid out an architecture and a demand case. This one reasons through the builder implications *if* those arguments hold. They might not. The shift might play out very differently from what I'm imagining, or it might stall entirely. I'd rather think through the possibilities honestly than pretend to certainty I don't have.

The key question from the builder's chair: how much of self-service is *tolerated* rather than *valued*?

I covered the [full circle](/openclaw-end-of-saas-era-web4/) — human intermediaries to self-service to AI intermediaries — in the first post. Self-service originally won not just on cost but because it was less conflicted: no commissions, you saw the raw options. But in the pursuit of growth, self-service has reintroduced many of the same problems through different mechanisms — promoted placements on comparison sites, dark patterns in checkout flows, hidden referral fees shaping which options surface, algorithmic curation that isn't neutral. And the economic model has degraded too: subscriptions get more expensive year over year, products add features nobody asked for to justify the increases, and services actively downgrade their existing tiers to create new premium ones — Amazon Prime retrofitting ads into a paid service and charging extra to remove them is the pattern in its purest form. The "less conflicted" advantage that made self-service win has substantially eroded, while the labour stayed with you. AI intermediaries bring the convenience back, and the trust problem with it — but the honest comparison isn't against the pristine self-service of 2005. It's against the degraded self-service of today, where you do all the work *and* get manipulated. That lowers the bar considerably.

The circle only closes, though, for tasks where self-service is endured, not enjoyed.

Think about what you actually do when you interact with most software. You compare insurance quotes — not because comparing is fun, but because you need coverage. You file expenses — not because the interface is rewarding, but because you want to get reimbursed. You research flights across six tabs, navigate government paperwork, set up utilities in a new city, dispute a charge with your bank. The [second post](/web4-succeeds-where-web3-failed/) described this from the consumer's side. From the builder's side, the uncomfortable question is: how many of your users are there because they want to be, and how many are there because they have to be?

I think the tolerated category is very big. Insurance, travel, expense reporting, government services, price comparison, scheduling, routine financial tasks, HR workflows, procurement — the list of software people *endure* to reach an outcome dwarfs the list of software people *choose* to use. And the delegation model is a direct substitute for endurance.

Some of these sectors are heavily regulated, and agent-mediated transactions in insurance, finance, or healthcare will require more controlled integrations than booking a restaurant — full forensics on why a service was selected, audit trails, compliance infrastructure. That shapes the timeline, not the direction. And the addressable market fragments by trust model too — not everyone will hand their data to a US platform. I'll develop both of these threads in a later post.

## Why Would Providers Join?

The consumer demand story is one half of the equation. A platform with no services is a search engine with no websites. The thesis depends on providers participating — many of whom get commoditised in the process. So why would they?

I think the answer is a prisoner's dilemma, not a willing embrace — though this depends on the consumer habit actually forming. As the [second post](/web4-succeeds-where-web3-failed/) argued, the demand is latent, not proven. Providers wouldn't need to join a platform nobody uses. But they don't need the habit to have fully formed — just the *risk* that it might.

Hotels didn't choose Booking.com. They joined for incremental bookings — a new channel, low risk. Then consumer behaviour shifted. Travellers started searching on Booking.com first, comparing across properties, expecting the same cancellation policies and review transparency everywhere. By the time hotels realised their direct bookings were declining, opting out meant invisibility. The platform had become the default discovery layer.

The pattern repeats. Businesses didn't choose to depend on Google — they had to be where consumers looked. Developers didn't love the App Store's 30% cut, but that's where the users were. First movers get distribution advantage; once critical mass forms, holdouts are punished.

But the pattern doesn't hold everywhere, and the base rate for platforms achieving this kind of coercive supply-side dynamic is low. Most platforms never get there. Enterprise software was never fully intermediated by a discovery platform. Professional services resisted aggregation for decades. The prisoner's dilemma requires a discovery choke point — consumer attention consolidating on a small number of interfaces.

And here's the tension: MCP is an open protocol. There's no proprietary gatekeeper baked into the architecture. As I argued in the [first post](/openclaw-end-of-saas-era-web4/), though, an open protocol doesn't prevent concentration at the discovery layer. HTTP is open; Google still controls most of search. If consumer attention migrates to a small number of agent interfaces — Claude, ChatGPT, perhaps a handful of others — those interfaces become the choke point, and the prisoner's dilemma kicks in. If that attention migration doesn't happen, neither does the supply-side pressure. The whole argument is conditional on the consumer habit forming, which is far from guaranteed — and historically, most bets on this kind of consolidation have been wrong.

But there's a positive case too, and I think it's underplayed. MCP Apps mean providers aren't fully commoditised — they control their presentation, their brand, their UX within the agent's interface. A provider on an agent platform is a website rendered in a browser they don't control. That's exactly what the web already is, and providers have lived with that for decades.

The analogy goes further than presentation. Just as some users type a URL directly and others click the first Google result, some users will say "book me a flight" and let the agent choose, while others will say "book me a flight on Lufthansa" or configure their agent to always prefer certain providers. The discovery layer matters for users who don't specify — but it's not the only path to the provider. That's closer to the open web than to a walled garden.

The agent also sends qualified, high-intent traffic — no idle browsing, no bouncing. And providers shed the cost of building and maintaining a full consumer-facing application. Their "interface" becomes a display template. For many companies, that's a genuine saving.

The honest breakdown: companies with real capability behind the UI benefit — they get distribution at lower cost. Companies whose only value *was* the UI get destroyed. Companies in the middle join reluctantly because the alternative is worse. That's the pattern I see from Booking.com, Google, and the App Store — though it played out differently in enterprise software and professional services, where discovery never consolidated the same way.

## Three Forces Killing the SaaS Playbook

I touched on this in the first post, but it's worth a closer look. These pressures apply regardless of whether Web 4.0 materialises.

- **Post-ZIRP economics** → The funding environment that enabled "grow at all costs" SaaS is gone. Higher interest rates compress multiples, raise the profitability bar, and make the traditional playbook — raise money, build a UI, sell subscriptions, grow — harder to execute. The era of funding SaaS companies on the promise of eventually finding margins is over.
- **LLM commoditisation** → General-purpose models now do much of what SaaS products charged subscriptions for: summarisation, analysis, comparison, natural language queries on structured data. The value of wrapping these capabilities in a dedicated product with a monthly price tag erodes when the user's general-purpose agent does the same thing with broader context.
- **Agentic coding** → This is the one builders feel most viscerally. Solopreneurs using AI coding tools build in a weekend what previously required a funded team. Competition explodes. Moats that relied on "we built it first and it's polished" weaken when anyone can build a polished version in days. Product shelf life shortens.

These three forces are independent. They don't need the platform thesis to be right. They're already reshaping what gets built, what gets funded, and how long it lasts.

## The Disruption Framework in Depth

In the first post, I sketched three categories: dies, commoditised, untouched. Here's the richer picture.

- **Dies** → Products that are essentially a presentation layer over data or services that exist elsewhere, with minimal proprietary logic behind the UI. The value is making something accessible or comparable — and an agent does that natively.

  Price comparison aggregators that pull public pricing into a grid. Simple booking intermediaries that wrap someone else's inventory in a nicer interface. Form-filling tools that walk you through a public government form. Dashboard-only analytics that visualise data you already own. Thin job board aggregators that scrape listings from elsewhere.

  These products exist because the alternative — doing it manually — is worse. An agent *is* a better alternative.

- **Gets commoditised** → Products with real underlying capability — proprietary data, workflow logic, network effects — but whose interface premium erodes. The product persists as infrastructure the agent calls into, but the UI becomes less relevant and revenue may compress.

  Some examples: CRM systems like Salesforce, where the data, workflows, and permissions persist but users increasingly interact through the agent layer. Job boards with proprietary inventory and employer networks — the matching UI erodes but the network and employer-side tools remain. Expense management with approval chains and accounting integrations. Project management tools where the workflow engine persists as infrastructure.

  Commodity creative production falls here too — template-based marketing assets, stock photo replacement, social media content at scale. The output is functional rather than craft.

  The *administrative* uses of productivity tools also land here. Formatting a report in Google Docs, generating a summary spreadsheet from raw data, setting up a Miro board from a template. You're using the tool as a means to an end, and the agent handles the mechanical parts.

- **Untouched** → Tasks where the interaction fidelity exceeds what text and voice can express, or where the quality and control threshold makes delegation unacceptable. This isn't about being "creative" — it's about the gap between what you can describe in conversation and what you need to do with your hands and eyes.

  Professional design tools like Figma and Photoshop, where spatial and visual micro-decisions can't be art-directed through a chat interface at the fidelity a brand requires. Music production in Ableton or Logic, where the authoring surface *is* the creative process. Productivity tools *as authoring environments* — writing in Google Docs, thinking visually on a Miro board, building a model in Excel where the cells are the thinking. Portfolio management, where control over financial decisions is the point.

Some products straddle categories depending on how they're used — productivity tools are the clearest case. The same app is untouched when you're thinking on the canvas and commoditised when you're doing mechanical work to get a task done. The categories describe *uses*, not products. These lists aren't complete — they're meant to illustrate the principle, not define the boundary.

This framework maps onto the [internet bifurcation](/openclaw-end-of-saas-era-web4/) from the first post. Products in the transactional kill zone — booking, comparing, scheduling, filing — are where "dies" and "commoditised" concentrate. Content and control-as-value products sit in the safe zone. If you're building, the first question is which territory your product lives in.

**There's also an adaptation path worth naming.** SaaS incumbents aren't standing still. Salesforce is building Agentforce. Microsoft has Copilot. These embedded agents have a genuine advantage: native access to the product's internal data, custom fields, workflows, and context that a general agent accessing the same product via MCP would only partially see.

I think the most interesting trajectory here is from "commoditised" toward something closer to "untouched" — incumbents that evolve into specialised agents, plugged into the general platform via MCP or something similar. A general-purpose model can't and won't handle everything. Complex CRM workflows, deep financial modelling, sophisticated supply chain logic — these may be better served by specialised agents that the general agent orchestrates rather than replaces.

Whether that's what actually happens, or whether the general agent gets good enough to handle most of it directly, I genuinely don't know. But it's a credible path, and it means "commoditised" isn't necessarily a permanent destination.

**The shallow AI trap is a different story.** I see three layers of vulnerability in the current wave of "AI-powered" SaaS:

- **Most exposed** → Features that wrap general LLM capabilities — "ask your data in natural language," "AI-powered summaries." If the general agent gets broad data access, it does this natively with broader context, and an agent that queries *across* your tools outperforms a chatbot trapped inside one product. But this depends on users granting that access, which is far from automatic.
- **Moderately exposed** → AI features that use proprietary data for interface-level tasks — smart filtering, auto-categorisation, predictive UI. If agents bypass the interface entirely, the investment in a "smart interface" is wasted. Though there's a counter-case here: a product's embedded AI has full access to its internal data, and for complex single-domain tasks, it may remain superior to a general agent that only sees what the MCP server exposes. The question is whether users care enough about that edge to stay inside the product's interface.
- **Least exposed** → AI features that create genuinely new capabilities — medical imaging analysis, fraud detection on proprietary transaction graphs, structural engineering simulations. Here the AI *is* the product. These become infrastructure the agent *invokes* rather than replaces. Products with deep domain AI and proprietary data are in a fundamentally different category.

There's an irony I keep coming back to. As I noted in the [first post](/openclaw-end-of-saas-era-web4/), companies adding shallow LLM features may be training their users to prefer delegation — to type natural language instead of clicking buttons, to expect conversational interaction instead of navigating menus. If that habit transfers to a general agent, it makes those same in-product features unnecessary.

That's a big "if," though. Users might just as easily develop a preference for *in-context* AI — the assistant that already has their data — rather than a general agent that needs to be granted access. I think the general agent wins for cross-tool tasks, but the outcome for single-product workflows is genuinely open.

## What to Build Instead

If the interface premium erodes, where does durable value live?

- **Proprietary raw data** → Unique datasets that literally don't exist elsewhere — sensor networks, transaction records, genomic databases, satellite imagery. The agent needs to access these, and the provider charges for it.

  But there's a squeeze even here. A firm like Gartner charges tens of thousands a year for market research, and their value is partly raw data (survey results, vendor assessments) and partly synthesised analysis (trend reports, analyst interpretation). An LLM can approximate the synthesis from public sources. The safe zone is truly unique *raw* data that can't be approximated — not the interpretation layer built on top of it.

- **Real-world execution** → Booking a flight, processing a payment, shipping a package, dispatching a technician. These require infrastructure the agent doesn't own. The physical world is a moat.

- **Domain logic** → Complex calculations, compliance rules, risk models. The agent can invoke these but not replicate them — yet. This boundary shifts as models improve, which means it's safe for now, not safe forever. The honest framing: domain logic is a time-bounded advantage whose clock is ticking.

- **Certified trust** → Medical diagnosis tools, legal compliance checkers, financial audit systems. Users need *certified* outputs, not LLM approximations. This is the most durable safe zone because it's regulatory, not technical. Regulations don't move at the speed of model improvement.

One category I think is underappreciated: capabilities that expand who gets to use a service. As I argued in the [second post](/web4-succeeds-where-web3-failed/), the delegation model doesn't just help existing users — it makes services accessible to people currently excluded by complex interfaces. Building for that accessibility layer through the agent is a durable value source, not a feature.

The mental model shift: **don't build interfaces, build capabilities.** The MCP app model is essentially this — you're not building a full application, you're building a service an agent invokes. Smaller surface area, lower development cost, but accessed at the exact moment of commercial intent.

## The Solopreneur Wave

AI coding tools are enabling a wave of solopreneurs building products that previously required funded teams. This looks like a SaaS renaissance. I think it's actually two overlapping waves that will diverge.

- **The last SaaS hurrah** → Solopreneurs building traditional SaaS products — comparison tools, dashboards, aggregators — faster and cheaper than ever. But if *everyone* can build a SaaS product in a weekend, competition explodes, niches fill instantly, and the moat — UI polish — is exactly the thing agents commoditise.
- **The first Web 4.0 ecosystem** → Solopreneurs building MCP skills, niche domain tools, agent infrastructure — things that *serve* the new platform rather than compete with it. Building an MCP skill is closer to building an API than building an app. The economics favour small teams.

The challenge is that most solopreneurs can't easily tell which wave they're riding. But there are litmus tests that I think are useful, even if they're not binary:

- **Does your product's value survive if the user never sees your UI?** If yes, you're building capability. If no, you're building something the agent eventually bypasses.
- **Would an agent invoke your product, or replace it?** An MCP skill that provides flight pricing data serves the agent. A comparison website that displays flight pricing competes with it.
- **Does your moat strengthen or weaken as agents improve?** Proprietary data and physical-world infrastructure get more valuable as more agents need access. UI polish and curation get less valuable as agents bypass them.

Even "last hurrah" products may generate real revenue for years — the transition won't be instant. At solopreneur cost structures, a three-to-five-year revenue window is a perfectly good business. It's just not a venture-scale one.

## The Developer Transition

Here's where I think the picture gets uncomfortable, especially for those of us who build software for a living.

The transition itself is a massive employment programme for developers. Building MCP servers, designing tool schemas, constructing trust infrastructure, migrating services from UI-first to API-first — agents aren't close to doing this autonomously. The scope of work is very large. In the near term, developer demand may actually *increase*.

But there's something different about this transition: the productivity multiplier arrives simultaneously. When the web arrived, humans had to build all the web software. When mobile arrived, humans had to build all the mobile apps. This time, agentic coding tools dramatically amplify what each developer can produce. The new platform gets built by fewer people than any prior transition required.

I think of it as three reinforcing dynamics:

1. **The barrier to building drops.** Solopreneurs build what previously required funded teams. More software gets built, but by fewer professional developers.
2. **The longevity of what gets built drops.** If anyone can ship a product in a weekend, competition explodes, niches fill instantly, and most products have short shelf lives.
3. **Infrastructure gets built by fewer, more productive engineers.** The Web 4.0 buildout doesn't require the same headcount as prior platform buildouts.

This suggests a three-phase timeline. A **transition boom** — where we are now, possibly more demand, not less. A **plateau** — infrastructure matures, patterns stabilise, new SaaS products stop being built at the old rate. And a possible **contraction** — similar or more software to build, but dramatically fewer people needed to build it, with shorter commercial lifespans.

Now, I should be honest about what I'm not sure of here. Historically, every productivity improvement in software development — higher-level languages, frameworks, cloud infrastructure, open source — has been accompanied by a massive expansion in what gets built. The productivity gains got absorbed by growing demand. This is the [Jevons paradox](https://en.wikipedia.org/wiki/Jevons_paradox) applied to software: make it cheaper to build, and people build more of it, and the net effect on employment is neutral or positive. That pattern has held for decades.

I think this time *might* be different, for two reasons. First, the productivity leap appears to be qualitatively larger than prior transitions — though the magnitude is genuinely uncertain and varies enormously by category of work. Second, the demand expansion depends on new markets opening up, and if the agent layer handles much of what those new markets would need, the demand for *custom software* may not expand the way it did before.

But I want to be clear: I'm arguing against a pattern that has held through every prior transition. I might be wrong. The contraction phase might never come. New categories of software we can't yet imagine might absorb the productivity gains entirely, the way mobile created an entire economy that didn't exist before.

What I'm more confident about: even in the optimistic scenario, the *type* of developer work shifts substantially. The reframing matters — it's not necessarily "fewer developers" but "different work, different skills, different relationship to the tools."

I think developers are safe *because of* the transition, not *despite* it — and that safety is time-bounded by the transition's duration. The same pattern as travel agents training customers to use Expedia. But the duration is genuinely uncertain, and the historical pattern of induced demand is a real counterargument I can't dismiss.

## The Capital Picture

VC capital will flow into Web 4.0 infrastructure because capital needs deployment. That's a mechanism, not validation. When capital searches for a narrative, it tends to create the conditions for that narrative to become real — the same thing happened with mobile, and also with Web 3. Capital flowing doesn't prove the thesis is correct.

What's investable: vertical agents (the "Uber for LLM-mediated travel booking"), infrastructure plays (payments, trust, identity for the agent ecosystem), picks-and-shovels (developer tools for building MCP apps), and content aggregators (bundled access to data sources for LLM consumption).

But there's a deeper tension: the transition that VC money accelerates may ultimately reshape the VC model itself. The traditional software VC playbook — fund a team to build a SaaS product, scale on recurring revenue, exit at a revenue multiple — depends on software being expensive to build, defensible through UX, and monetised through subscriptions. If all three legs weaken simultaneously, the model's foundations erode.

I think the industry bifurcates. **Infrastructure-scale capital still works** — foundation models, compute, trust and payments systems require billions and offer venture-scale returns. **Small and niche thrives** — micro-funds backing solopreneurs building MCP skills and vertical tools, lower check sizes, faster cycles. **The middle hollows out** — the classic Series A-B SaaS fund is most at risk, because its deal flow is the category being disrupted.

What partially fills the gap: incumbent defensive capital. Google, Salesforce, enterprise SaaS companies — the ones fighting hardest against irrelevance fund ecosystem development to control the transition or stay relevant through it. Different incentives than growth-seeking VC, but it keeps the ecosystem capitalised.

## Platform Economics and Provider Incentives

The platform's leverage is discovery and attention, not protocol lock-in. That distinction is less comforting than it sounds.

MCP is open. Providers can technically be accessed directly. There's no distribution lock-in to justify App Store-level commissions. But as I noted in the [first post](/openclaw-end-of-saas-era-web4/), MCP today is like HTTP without DNS and without search engines — the protocol works, but the discovery infrastructure doesn't exist yet.

Whoever builds that discovery layer — the thing that maps user intent to relevant services — captures the economics. Discovery has winner-take-most dynamics. HTTP being open didn't prevent Google from monopolising search. MCP being open doesn't prevent a discovery monopoly. It just moves the bottleneck up the stack.

The value proposition to providers is bundled services (identity, payments, trust infrastructure), the threat of invisibility as consumer attention migrates to chat-based interfaces, and legal liability infrastructure (biometric confirmation, audit trails, dispute resolution) that makes delegated transactions legally sound. The *protocol* is open; the *platform services* built on top of it probably won't be.

Monetisation sits on a spectrum of plausibility. **Discovery and promoted placement** is most likely — this is Google's proven model, and when the agent selects between competing services for a given intent, whoever controls that selection controls the business model. **Subscription bundling** is plausible — "Claude Pro: $50/month, includes access to 200+ premium data sources" is the Spotify model applied to services. **Transaction commissions** are more speculative — the open protocol limits platform leverage compared to the App Store's walled garden.

**From the provider's chair, the question is: what are the levers I can pull to be discovered?** The answer looks more familiar than you might expect. Quality-of-service rankings (TrustPilot, G2, or platform-native ratings), paid placement that's clearly labelled as such, direct user preference ("always use Lufthansa"), and brand strength that makes users name you explicitly. These are the same dynamics as the web today.

Sponsored results would need to be transparent — and there's a plausible freemium model where lower-tier users see promoted results while paid users don't. None of this is novel.

The [convenience/conflict trade-off](/openclaw-end-of-saas-era-web4/) I introduced in the first post applies here too, but from the builder's side: the platform's incentive to monetise discovery is real, and smaller providers who can't pay for placement may struggle for visibility. How that tension resolves — through regulation, competition between agent platforms, or user demand for unbiased results — is an open question I'll return to in a later post.

**Inference costs** are the near-term constraint worth naming. Agent interactions are currently more expensive per transaction than serving web pages — multiple tool calls, reasoning, context management. But inference costs are falling rapidly, driven by model efficiency improvements, open-source commoditisation pressure (DeepSeek and others), and the shift from capability arms races to efficiency optimisation.

The trend lines are steep — costs per token have dropped by orders of magnitude in two years and show no sign of levelling off. I think this is a near-term constraint, not a structural barrier, but I'm making a bet on continued cost reduction that could prove wrong.

## What Comes Next

If any of this is directionally right, the builders who thrive are the ones who provide things the agent can't do on its own. Proprietary data. Physical-world execution. Certified trust. Specialised agents with deep domain logic. Capabilities, not chrome.

The SaaS era was the golden age of building interfaces. Founders built companies around the insight that a better UI could make people pay a subscription. If the pressures I've described in this post play out, that model gets squeezed from multiple directions simultaneously. What comes next rewards capability over interface.

But I want to close with honest uncertainty. I've spent this post reasoning through a scenario, not predicting a future. The consumer delegation habit might not form. The general agent might stay a power-user tool, not a mass-market shift. Incumbents might successfully embed AI in ways that strengthen rather than erode their positions. The whole thing might be a pattern I'm seeing because I'm looking for one.

I've tried to flag the conditional assumptions throughout — the "ifs" matter as much as the conclusions. The cost of thinking through this and being wrong is low. The cost of not thinking through it and being right is higher. That asymmetry is what motivates the series, not confidence in the outcome.

*[Previously](/openclaw-end-of-saas-era-web4/): the architecture and the platform thesis. [And](/web4-succeeds-where-web3-failed/): the consumer demand story. Next: who controls Web 4.0 — and does it matter?*
