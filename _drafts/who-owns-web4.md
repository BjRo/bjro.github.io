---
title: "Who Owns Web 4.0?"
excerpt: "Three companies, three bets on where platform control lives. And a geopolitical shift that might matter more than any of them."
---

The [first post](/openclaw-end-of-saas-era-web4/) in this series laid out the architecture. The [second](/web4-succeeds-where-web3-failed/) made the consumer case. The [third](/supply-side-of-web4/) explored what the shift means for builders. Each one was implicitly asking a question I've been deferring: if this platform takes shape, who controls it?

That question matters more than usual. Prior platform transitions created gatekeepers — Microsoft for the desktop, Google for the web, Apple and Google for mobile. Each gatekeeper captured the economics of their era. An LLM platform that mediates your transactions, research, and decision-making concentrates more personal data and economic leverage than any platform before it. Who controls it isn't just a business question. It's a structural one.

And the answer is less settled than most coverage suggests.

## Google's Innovator's Dilemma

I mentioned in the [first post](/openclaw-end-of-saas-era-web4/) that Google's absence from MCP adoption looked like the innovator's dilemma playing out in real time. That's worth unpacking, because Google's strategy represents the strongest counterargument to the entire platform thesis.

Google derives roughly 75% of its revenue from advertising, overwhelmingly through search. An LLM platform that routes user intent directly to services — bypassing the search results page entirely — is an existential threat to that model. Google's response has been to embed Gemini into Search, Gmail, Docs, and the rest of its product suite. This is the rational strategy of the company with the most to lose: make AI a feature of your existing products, not a new platform that cannibalises them.

And it might work. If Google's "AI as feature layer" approach succeeds — if users prefer AI-enhanced search over delegation to an agent — then no new platform gatekeeper emerges. The current distribution and attention structure holds. Google stays dominant. This is the version of the future where my thesis is wrong, and it's credible specifically because Google has billions of users, the most popular browser, the dominant mobile OS, and an advertising model that funds aggressive integration.

But Google's resistance to MCP — building proprietary integrations rather than adopting the open protocol — is a tell. It signals that Google sees MCP-style cross-platform interoperability as a threat, not an opportunity. The company that won the web by being the best at routing user intent is betting against the next generation of intent-routing infrastructure. That's the classic innovator's dilemma: the rational move for the incumbent is the wrong move for the market.

## Three Bets on Where the Platform Lives

If Google is playing defence, three companies are playing offence — and they're making fundamentally different bets about where platform control sits.

### Apple: the device controls the agent

Apple has the structural advantage that should make this obvious: devices (iPhone, Mac, Watch, AirPods), a payments infrastructure (Apple Pay), a consumer identity system (Apple ID), a developer ecosystem (App Store), and the trust that comes from a decade of privacy positioning.

The multi-device handoff is Apple's natural strength. Earbuds handle conversation and low-stakes delegation — "remind me to cancel that subscription" or "what's the weather in Porto next week." High-stakes confirmation flows to the phone, where the screen and biometrics live — "confirm this EUR 340 booking with Face ID." The device ecosystem works together. No other company has this.

But Apple hasn't executed on the model layer. Apple Intelligence has been underwhelming by industry consensus. The privacy constraints that make Apple trusted also make cloud-based inference harder — you can't route personal data through a cloud model and maintain the privacy brand. On-device inference limits model size and capability. Apple's structural advantage is irrelevant if they can't ship a competitive agent.

The race is whether insurgents establish distribution and consumer habits before Apple catches up. Historically, Apple has been late to categories and then won them — smartphones, tablets, watches. But they've also been late and lost — social, search, maps, streaming. This could go either way, and it depends heavily on whether Apple's privacy constraints are a moat or a shackle on the model layer.

### OpenAI: hedging across two layers

The OpenClaw acquisition gives OpenAI messaging distribution — agents running in WhatsApp, Telegram, Signal, meeting users where they already are. The [Jony Ive hire](https://openai.com/sam-and-jony/) signals a purpose-built device play. ClawHub provides a marketplace. This looks like a full platform stack being assembled: model + agent + app store + distribution + device.

But Ben Evans makes a [compelling argument](https://www.ben-evans.com/benedictevans/2026/2/19/how-will-openai-compete-nkg2x) that OpenAI's stack looks ambitious and lacks the coercive power that made prior platform stacks work. No network effects. No structural lock-in. Shallow engagement — roughly 5% of ChatGPT's users pay, and 80% sent fewer than 1,000 messages in 2025. Product strategy flows from research, not user needs. Evans cites Fidji Simo: "I get a researcher pinging me saying: 'I have something pretty cool. How are you going to use it in chat?'" — the opposite of Jobs' "start with the customer experience and work backwards."

A [Wardley Map analysis](https://www.linkedin.com/pulse/ai-platform-wars-wardley-map-openai-vs-anthropic-google-mohandass-uffoc/) of the AI platform wars adds context. Enterprise market share has shifted — Anthropic from 12% to 40%, OpenAI declining from 50% to 27%. OpenAI's projected $14B in losses against Anthropic's path to profitability suggests fundamentally different strategies: OpenAI is executing a capital-intensive land-grab; Anthropic is running a protocol-and-partnerships play. The analysis draws a Palantir analogy for OpenAI's forward-deployed engineer approach — effective for enterprise penetration but expensive and hard to scale — and calls out Microsoft as a cautionary tale of distribution without differentiation.

Evans' critique sharpens why the OpenClaw distribution play matters so much. It's not just a talent acquisition — it's an attempt to manufacture the engagement depth that OpenAI currently lacks. If users interact with agents through messaging apps they already open fifty times a day, the engagement problem looks different than "log into ChatGPT and type a prompt." Whether that works is genuinely uncertain.

There's a more fundamental fragility underneath. OpenAI's strategy is the most capital-intensive of the three — projected losses of $14B, sustained by venture funding and the Microsoft relationship. If the engagement depth doesn't materialise, if the revenue model doesn't close the gap, the burn rate becomes existential. This isn't hypothetical risk-mongering — it's the arithmetic of a company spending at infrastructure scale without infrastructure-scale revenue. A bankruptcy or distress acquisition wouldn't kill the ecosystem. OpenClaw is open-source. ClawHub's marketplace patterns would persist. Consumer habits, if they'd formed, would migrate. Android would have survived Google's hypothetical failure in 2008. But it would abruptly reshape *who controls* the platform — which is exactly the question this post is about.

### Anthropic: the protocol is the platform

MCP as the HTTP for agent interaction. MCP Apps as the rendering layer. No device hardware. No messaging distribution. The bet is that the protocol layer is where value accrues, and that devices are interchangeable clients — just as browsers are interchangeable clients for the web. Claude is a client, ChatGPT is a client, VS Code is a client, and any future agent can be a client. If you control the standard they all use, you don't need to control the device.

This is the most elegant strategy and arguably the riskiest. It depends on MCP adoption continuing — which it has, impressively — but also on the protocol layer being the point of leverage rather than the client layer. HTTP is open and foundational, but the platform economics of the web didn't accrue to the protocol designers. They accrued to Google, Facebook, Amazon — companies that built the best discovery and services on top. Anthropic's bet is that the AI platform era plays out differently. It might. But the historical pattern isn't encouraging for protocol owners.

There's a paradox worth naming. Anthropic is leaner than OpenAI — closer to profitability, less dependent on a single capital partner — but still pre-profit and burning cash in a race with better-funded competitors. If Anthropic fails, though, something interesting happens: MCP doesn't die with it. The protocol is open, already adopted by competitors, already the basis for a growing ecosystem. HTTP didn't need its designers to persist. If MCP survives Anthropic — and I think it would — that's actually evidence *for* the protocol thesis. The standard becomes infrastructure that outlasts its creator. It also means the protocol bet might succeed even if the company that made it doesn't.

Notably, neither Evans nor the Wardley Map analysis covers Apple. Both focus on the model-layer competition and largely ignore the device layer. I think that omission is itself revealing — the device play is the underexplored bet in the current discourse.

## The Missing Layer: Discovery

This is the thread I've been deferring since the [first post](/openclaw-end-of-saas-era-web4/) and that the [third post](/supply-side-of-web4/) flagged explicitly: MCP today is like HTTP without DNS and without search engines. The protocol works. Finding the right service for a given intent doesn't.

Right now, if you want to use an MCP tool, you need to know it exists, install it, configure it. That's roughly where the web was in 1993 — you needed to know the URL. What made the web into a platform was the discovery layer: Yahoo, then AltaVista, then Google. What makes Web 4.0 into a platform is the equivalent layer: user expresses intent, a discovery system identifies relevant services, the right schemas get loaded dynamically.

Whoever builds this controls the platform economics. The protocol is open — anyone can build an MCP server. But which server gets invoked for a given user intent is a discovery decision, and discovery has winner-take-most dynamics. Google didn't control HTTP. Google controlled which websites you found. The same structure applies here.

This is also where the platform services stack gets built: identity (who is the user?), payments (how do transactions settle?), trust infrastructure (biometric confirmation, audit trails, dispute resolution), and legal liability (who's responsible when the agent books the wrong flight?). None of these exist yet in a standardised form for agent interactions. Whoever bundles them into a coherent platform services layer creates something providers can't easily replicate on their own — and something they'll depend on.

The [third post](/supply-side-of-web4/) explored the prisoner's dilemma: providers join because the alternative — being invisible while competitors are visible — is worse. But that dilemma only kicks in when consumer attention consolidates on a small number of agent interfaces. Whether that happens, and how quickly, is the central uncertainty.

## Multi-Agent Architecture and Platform Power

There's a competitive dynamics dimension I haven't addressed yet, and I think it matters more than it's getting credit for: multi-agent architecture.

The current framing — one general agent mediating between user and services via MCP — is a simplification. What's already emerging is a layered model: a general orchestrator that routes to specialised sub-agents. These specialised agents might be smaller, domain-trained models that handle specific verticals — a medical agent trained on clinical literature, a legal agent on case law, a financial agent calibrated for regulatory compliance.

This is a different economic tier than MCP services. An MCP server exposes an API: "here are the tools I offer, here's how to call them." A specialised sub-agent is a model trained on proprietary data that handles a category of reasoning. The distinction matters for competitive dynamics.

**Who trains the specialised models?** If the general platform trains them on licensed domain data, the platform captures another layer of value — it's not just routing to services, it's *becoming* the service for entire categories. If domain experts train and host their own specialised agents, the model looks more distributed. Both paths are plausible, and the outcome probably varies by domain. Healthcare data governance is different from travel inventory.

**Who controls the routing?** The general orchestrator deciding which specialised agent handles a given request is another form of platform power — a layer above MCP discovery. If the orchestrator routes your medical question to one specialised agent over another, that's a decision with economic consequences. The same discovery-layer dynamics apply, one level of abstraction up.

**Does this widen or narrow participation?** On one hand, multi-agent architecture could broaden the ecosystem. A domain expert who can't build an MCP server might fine-tune a specialised model on their proprietary data and make it available through the orchestration layer. On the other hand, training and hosting models requires more capital and technical sophistication than building an API endpoint. The barrier to the most valuable tier of participation might actually be *higher*.

My instinct is that multi-agent architecture reinforces platform dynamics rather than disrupting them. The orchestration layer — deciding which specialised agent to invoke, how to combine outputs from multiple sub-agents, when to escalate to more capable (and expensive) models — is a natural fit for the general platform to control. And the economics of "route to the cheapest model that can handle the task" create competitive pressure that favours whoever controls the routing.

The implication for the discovery question is direct. The platform doesn't just need to discover MCP servers for a given intent. It needs to identify the right specialised agent, the right MCP services, and orchestrate them together. More complex routing means more platform leverage.

## Technology Sovereignty

The [third post](/supply-side-of-web4/) noted that not everyone will hand their data to a US platform — the demand for delegation fragments by trust model. I said I'd come back to this. The geopolitical context has since shifted in ways that make sovereignty much more than an abstract policy concern.

### Why an LLM platform is worse than Google dependency

European policymakers have worried about dependence on US tech platforms for years. The current dependencies — Google for search, AWS for cloud infrastructure, Microsoft for productivity — each operate at a specific layer. Google sees your search queries. AWS hosts your compute. Each platform sees a slice of your digital life.

An LLM agent platform that mediates your transactions, research, and decision-making sees *all of it*. Your intent, your deliberations, your financial decisions, your health research, your professional communications — all flowing through a single entity, controlled by a single jurisdiction. This isn't another layer of dependence. It's the integration of all previous dependencies into one.

And the US has demonstrated, repeatedly, that it will weaponise technology dependencies when it serves its interests. SWIFT exclusions to punish geopolitical opponents. The Huawei ban to restrict a competitor. The CLOUD Act compelling access to data held by US companies anywhere in the world. The TikTok forced sale to control a foreign-owned platform operating on US soil. These aren't hypotheticals. They're precedent.

### The shift in European sentiment

Until recently, technology sovereignty was an abstract policy discussion — something for Brussels regulators and think-tank papers. I think the Trump administration's posture toward allies has changed that at a fundamental level.

When the US president threatens military action against Denmark — a NATO ally — over Greenland, something shifts in how Europeans think about dependence on American institutions. I notice it in conversations, in public discourse, in the tone of policy discussions that used to be technocratic and are now visceral. The sentiment I observe isn't "we should consider diversifying our technology stack." It's "we *cannot* afford to depend on a country that threatens its allies."

This isn't about whether the Greenland threat was militarily serious. It's about what it revealed about the reliability of the transatlantic relationship as a foundation for technology dependence. If the US is willing to threaten a NATO ally over territory, the assumption that US tech platforms will remain available, neutral, and governed by rule of law becomes harder to sustain. Add the broader pattern — tariff threats against EU members, transactional framing of security alliances, explicit scepticism toward multilateral institutions — and the picture is of a relationship where the terms can change unilaterally.

I want to be careful here. I'm not arguing that European tech sovereignty is easy or that the sentiment translates automatically into capability. I'm arguing that the *political will* has shifted in a way that makes sovereign alternatives more likely to be funded, politically supported, and adopted than they were even two years ago. Public opinion is a precondition for policy, and the opinion has moved decisively.

For engineers and engineering leaders in Europe, this isn't abstract. It's the question of whether the infrastructure you build on — the cloud, the models, the agent platforms — will still be available on the same terms in five years. And increasingly, the answer that comes back from the policy environment is: don't bet on it.

The risk isn't only political. The AI companies building these platforms are burning capital at historic rates, most are pre-profit, and the competitive landscape could shift abruptly through bankruptcy, distress acquisition, or strategic pivot. Building your stack on a platform whose provider might not exist in three years — or might exist under very different ownership and terms — compounds the jurisdictional risk. The sovereignty question and the capital fragility question aren't separate concerns. They reinforce each other.

### Trust-model fragmentation

The fragmentation isn't random. It follows institutional and geopolitical lines:

- **US users and businesses** are the natural early adopters of US-based agent platforms. The trust question exists, but convenience and ecosystem maturity overcome it for most.
- **European users and regulators** will increasingly demand that agent interactions involving financial, health, and personal data either run on European infrastructure or comply with European governance frameworks. This isn't hypothetical — it's the trajectory that GDPR, the Digital Markets Act, eIDAS, and PSD2 have been on for years. The political climate accelerates it.
- **Privacy-sensitive users everywhere** will prefer open-source or self-hosted agents — as I noted in the [second post](/web4-succeeds-where-web3-failed/). The demand for delegation doesn't disappear. It routes through different infrastructure.
- **China builds its own parallel ecosystem.** This is already happening with DeepSeek and others, and it doesn't depend on the Web 4.0 thesis specifically.

The realistic picture isn't sovereign platform races in every major bloc. India, Brazil, the Gulf states building their own agent platforms is speculative. What I think is more likely: US platforms dominating by default, China's parallel ecosystem serving its domestic market, and Europe as the critical swing — with regulatory infrastructure that could credibly underpin sovereign alternatives, but a track record of not building the consumer-facing platforms to use them.

### The EU's position

Europe has strong regulatory infrastructure and weak platform-building capability. That's been the pattern for two decades, and I'm not going to pretend I expect it to change overnight. Mistral is the most credible European bet on the model layer — a French company with genuine technical capability and government backing. But a model alone isn't a platform. The platform requires discovery, payments, trust infrastructure, developer ecosystem — all the layers we've been discussing.

What Europe *can* build, and where I think the real opportunity is: compliance infrastructure. The regulatory frameworks that make agent-mediated transactions legally sound in European contexts — biometric confirmation under eIDAS, payment processing under PSD2, data governance under GDPR, dispute resolution under consumer protection law. This is infrastructure that US platforms will need to integrate with, and that creates leverage. Not platform control, but regulatory moat.

The open protocol is the escape hatch. MCP being open means European alternatives don't need to convince providers to adopt a different standard — they can consume the same MCP servers that US platforms consume. The protocol is shared; the platform services layer on top can be sovereign. That's necessary but not sufficient. An open protocol without a discovery layer, without integrated payments, without trust infrastructure, is just a specification.

The question is whether European institutions fund and build those platform services before the US alternatives become the default — before the habit forms and switching costs accumulate. Given the shift in political will, I think there's a window. Windows close.

### What this means for the competitive picture

Technology sovereignty adds a dimension that pure market analysis misses. The "winner" of Web 4.0 might not be one company. It might be a fragmented landscape: US platforms serving the American market and parts of the world that accept US jurisdiction, European alternatives serving regulated and privacy-conscious contexts, China's ecosystem serving its domestic market, and open-source agents serving the long tail.

That fragmentation reduces the platform power concentration the thesis predicts — but doesn't eliminate it within each zone. The US platform winner still dominates a massive market. And the dynamics within each zone are similar: discovery concentration, platform services capture, provider prisoner's dilemma.

The sovereignty question isn't a footnote on the platform thesis. It's a structural force shaping who controls the platform and on what terms. And right now, the political wind in Europe is blowing in a direction that makes this question far more consequential than the model benchmark charts that dominate tech coverage.

## The Strongest Counterarguments

I want to close the competitive analysis by engaging honestly with the case against platform consolidation. This section draws significantly on Evans' analysis, which I think provides the most rigorous version of the sceptical case.

### The engagement problem

Evans' [data on ChatGPT usage](https://www.ben-evans.com/benedictevans/2026/2/19/how-will-openai-compete-nkg2x) is the hardest piece of evidence to dismiss: 800-900 million users, only 5% paying, 80% having sent fewer than 1,000 messages in 2025. US teens use chatbots "a few times a week or less," not daily. If hundreds of millions of people have access to the tool and most don't engage deeply, that's empirical evidence against the delegation habit forming.

My response: current chatbot usage measures a conversational search tool, not a delegation agent. The habit we're predicting — delegate a task, review curated options, confirm — doesn't exist in product form yet. Nobody has shipped a consumer agent that books flights, compares insurance, and coordinates across providers with the flow the thesis describes. Judging the delegation habit by ChatGPT engagement data is like judging the mobile app economy by WAP browser usage in 2004.

But I want to be honest: this is a promissory argument. I'm saying "the product hasn't been built yet, so the data doesn't apply." That's convenient. Evans' counter is straightforward — the tool exists, hundreds of millions have tried it, and deep engagement hasn't formed for most. If the delegation product ships and people still don't use it deeply, the thesis is wrong. That's the test.

### The widget fallacy

Evans argues that reducing complex products to simple API calls historically fails because providers resist ceding control of their user experience. Developers don't want to become "dumb API calls." This directly challenges the MCP-as-HTTP analogy.

Here I think the response is stronger. MCP Apps return rich UIs. Providers keep control of their presentation, branding, and user experience within the agent's interface. The parallel isn't "website reduced to API call" — it's "website rendered inside a browser the provider doesn't control." That's exactly what the web already is. Providers have lived with that bargain for three decades.

But the tension is real and deserves naming. Providers *will* resist. The degree to which MCP Apps actually preserve provider agency — versus becoming thin templates the platform constrains — determines adoption speed. If the platform starts overriding provider UIs for "consistency" or inserting its own elements, the widget fallacy comes true. The current architecture avoids that failure mode. Whether it stays that way as the platform matures is a governance question, not a technical one.

### What if the platform doesn't consolidate?

The most fundamental counterargument: LLMs become a distributed feature layer — every app gets an AI assistant, no cross-cutting platform emerges. Google's "AI in everything" strategy wins. The web stays the web, with better autocomplete.

I think this is genuinely possible. The platform thesis requires consumer attention to consolidate on a small number of agent interfaces. If it doesn't — if people prefer AI embedded in the products they already use — the platform economics I've described don't materialise.

What makes me think consolidation is more likely: cross-provider coordination. The killer advantage of a general agent isn't that it's better at any single task than a specialised in-app AI. It's that it handles the *coordination* across providers that no single product can. Trip planning across flights, hotels, and restaurants. Insurance comparison across carriers. Moving to a new city and handling address registration, utilities, internet, and GP in one flow. These coordination tasks are inherently cross-cutting. A distributed feature layer can't do them.

But "more likely" isn't "certain," and the timing gap between "clearly better in theory" and "actually used by consumers" has killed more theses than I can count.

## What I Think Is Actually at Stake

The race to own Web 4.0 isn't a race to build the best model. Models are converging — half a dozen companies produce roughly comparable ones, and the gap keeps closing. The race is to build the best platform services layer: discovery, payments, trust infrastructure, identity, dispute resolution, legal liability. The things that make delegated transactions work and that make providers willing to participate.

Google is playing defence against a threat that might not materialise. Apple has the strongest structural hand but may not play it in time. OpenAI is assembling the most complete stack but lacks the engagement depth and structural moats that made prior platforms durable. Anthropic is making the most technically elegant bet — that the protocol is the platform — against a historical pattern where protocol designers rarely capture the economics. And the sovereignty question means the answer might not be one company or even one geography.

I don't know who wins. I don't think anyone does yet. What I think is: whoever builds the discovery layer and bundles trust infrastructure around it captures the economics of the next era. The protocol is open. The platform built on top won't be — and the contest for that layer is barely underway.

*[Previously](/openclaw-end-of-saas-era-web4/): the architecture. [And](/web4-succeeds-where-web3-failed/): the consumer demand story. [And](/supply-side-of-web4/): what it means for builders. Next: what Web 4.0 does to us.*
