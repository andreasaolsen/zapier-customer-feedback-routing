# Customer Feedback Triage & Automated Routing

An AI-powered customer feedback workflow built with Zapier.

The workflow analyzes incoming customer feedback, classifies it using AI, and automatically routes it to the appropriate action based on priority and sentiment.

## Workflow

Google Forms → AI by Zapier → Paths by Zapier → Slack / Trello / Gmail

## Workflow Steps

1. **Google Forms** — Collects customer feedback.
2. **AI by Zapier** — Classifies the feedback by category, sentiment, priority, action and route.
3. **Paths by Zapier** — Routes the feedback based on the AI-generated `Route` value.
4. **Slack** — Receives high-priority feedback requiring immediate attention.
5. **Trello** — Creates a task for non-urgent problems, requests or suggestions.
6. **Gmail** — Sends an automated thank-you email for positive feedback.

## AI Classification

The AI classifies each submission using structured outputs:

- **Category** — Customer Support, Product Issue, Billing, Feature Request, General Feedback or Praise
- **Sentiment** — Positive, Neutral or Negative
- **Priority** — High, Medium or Low
- **Action** — Immediate follow-up, Create task, Send thank-you or No action
- **Route** — Slack, Trello, Gmail or None
- **Summary** — Short English summary of the feedback

## Routing Logic

| Route | Condition | Action |
|---|---|---|
| Slack | High-priority feedback | Send Slack alert |
| Trello | Non-urgent issue, request or suggestion | Create Trello task |
| Gmail | Positive feedback without a problem | Send thank-you email |
| None | No action required | Workflow ends |

## Data Flow

Customer feedback is submitted through Google Forms and passed to AI by Zapier for classification.

The resulting `Route` value is then used by Paths by Zapier to determine which downstream action should be executed.

## Stack

- Zapier
- Google Forms
- AI by Zapier
- Paths by Zapier
- Slack
- Trello
- Gmail

## Cost & Usage

The workflow used **3 credits per routed feedback flow** during testing.

Flows classified as requiring no action can consume fewer credits because no downstream action is triggered.

## Demo Data

The workflow was tested with fictional customer feedback covering different routing scenarios.

### High Priority → Slack

**Customer:** Thomas Nielsen  
**Email:** thomas.nielsen@example.com

> I have been unable to access my account for three days, and this is completely blocking my work. If this issue is not resolved immediately, I will have to cancel my subscription.

**Expected route:** Slack

---

### Feature Request → Trello

**Customer:** Maria Jensen  
**Email:** maria.jensen@example.com

> I would like to see an option to export my monthly reports as Excel files. This would make it easier to share reports with my team. It is not urgent, but it would be a useful improvement.

**Expected route:** Trello

---

### Positive Feedback → Gmail

**Customer:** Jonas Andersen  
**Email:** jonas.andersen@example.com

> I really enjoy using the platform. It has made my daily work much easier and saves me a lot of time every week. Great product!

**Expected route:** Gmail
