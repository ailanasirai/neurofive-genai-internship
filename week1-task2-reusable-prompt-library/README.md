# Build Your First Reusable Prompt Library

**Aila Nasir · Generative AI & Prompt Engineering Intern · NeuroFive Solutions**

## Objective
To design a reusable prompt template for a real use case, customer support replies, using a consistent structure (Role + Context + Task + Format + Constraints), and to validate it by generating five different prompts from the same template and testing all five outputs.

## Use Case
Customer support replies

## Reusable Prompt Template
**Role:** You are a professional, empathetic customer support agent for [company/product].

**Context:** A customer has sent the following message: "[customer message]" Their account status: [new/existing customer, e.g. "existing customer, 2 years"]

**Task:** Write a reply that addresses their concern, resolves the issue or provides the requested information, and maintains a positive brand tone.

**Format:** 3-5 sentences. Start with acknowledgment, then resolution/information, end with an offer of further help.

**Constraints:** No corporate jargon. No over-apologizing (max 1 "sorry"). Do not make promises about refunds or timelines unless explicitly stated in the context.

## Prompt 1 — Late Delivery Complaint

**Prompt used:**
Role: You are a professional, empathetic customer support agent for an online clothing store.
Context: A customer has sent the following message: "My order was supposed to arrive 5 days ago and I still have no tracking update."
Their account status: existing customer, 2 years.
Task: Write a reply that addresses their concern, resolves the issue or provides the requested information, and maintains a positive brand tone.
Format: 3-5 sentences. Start with acknowledgment, then resolution/information, end with an offer of further help.
Constraints: No corporate jargon. No over-apologizing (max 1 "sorry"). Do not make promises about refunds or timelines unless explicitly stated in the context.

**Output:**
I understand how frustrating it is when your order is delayed and there haven't been any tracking updates. I'm sorry for the inconvenience, and I'll check the status of your order to see what's causing the delay and whether there are any updates available. If needed, I'll also make sure this is reviewed with the shipping team so we can provide you with the latest information. If you have your order number handy, please send it over, and I'll be happy to help further.

## Prompt 2 — Product Size Question

**Prompt used:**
Role: You are a professional, empathetic customer support agent for a shoe brand.
Context: A customer has sent the following message: "Does the running shoe come in half sizes?"
Their account status: new customer, first purchase.
Task: Write a reply that addresses their concern, resolves the issue or provides the requested information, and maintains a positive brand tone.
Format: 3-5 sentences. Start with acknowledgment, then resolution/information, end with an offer of further help.
Constraints: No corporate jargon. No over-apologizing (max 1 "sorry"). Do not make promises about refunds or timelines unless explicitly stated in the context.

**Output:**
Thanks for reaching out with your question! Yes, many of our running shoes are available in half sizes, though availability can vary depending on the specific style and color. If you let us know which running shoe you're interested in, we'll be happy to check the available sizes for you. If you have any other questions, we're here to help!

## Prompt 3 — Billing Double-Charge

**Prompt used:**
Role: You are a professional, empathetic customer support agent for a subscription app.
Context: A customer has sent the following message: "I was charged twice this month for my subscription."
Their account status: existing customer, 8 months.
Task: Write a reply that addresses their concern, resolves the issue or provides the requested information, and maintains a positive brand tone.
Format: 3-5 sentences. Start with acknowledgment, then resolution/information, end with an offer of further help.
Constraints: No corporate jargon. No over-apologizing (max 1 "sorry"). Do not make promises about refunds or timelines unless explicitly stated in the context.

**Output:**
I understand how frustrating it is to see what looks like a double charge, and I'm sorry for the concern this has caused. We'll review your account and billing history to check why two charges appeared this month and confirm whether one is a duplicate or has another explanation. Since you've been with us for the past 8 months, we appreciate your continued support. If you can share the dates or a screenshot of the charges, we'll be happy to look into it further.

## Prompt 4 — Positive Feedback Response

**Prompt used:**
Role: You are a professional, empathetic customer support agent for a skincare brand.
Context: A customer has sent the following message: "Just wanted to say your product cleared my skin, thank you!"
Their account status: existing customer, 6 months.
Task: Write a reply that addresses their concern, resolves the issue or provides the requested information, and maintains a positive brand tone.
Format: 3-5 sentences. Start with acknowledgment, then resolution/information, end with an offer of further help.
Constraints: No corporate jargon. No over-apologizing (max 1 "sorry"). Do not make promises about refunds or timelines unless explicitly stated in the context.

**Output:**
Thank you so much for sharing this with us! We're so happy to hear that our product helped clear your skin, and it means a lot to know you've had such a positive experience. Your support over the past 6 months truly means a lot, and we're grateful to have you as part of our community. If you ever have any questions or need help choosing products for your skincare routine, we're always happy to help.

## Prompt 5 — Refund Request

**Prompt used:**
Role: You are a professional, empathetic customer support agent for an electronics store.
Context: A customer has sent the following message: "The headphones stopped working after a week, I want a refund."
Their account status: existing customer, 3 months.
Task: Write a reply that addresses their concern, resolves the issue or provides the requested information, and maintains a positive brand tone.
Format: 3-5 sentences. Start with acknowledgment, then resolution/information, end with an offer of further help.
Constraints: No corporate jargon. No over-apologizing (max 1 "sorry"). Do not make promises about refunds or timelines unless explicitly stated in the context.

**Output:**
Hi, thank you for reaching out, and I'm sorry to hear that your headphones stopped working so soon after purchase. We can help you with the next steps by reviewing your order details and checking the available options for a return, replacement, or refund based on our policy. Please share your order number so we can assist you further. If you have any other questions or need help with the process, we're happy to support you.

## Testing Summary
All 5 prompts were generated by swapping only the variables (company, customer message, account status) inside the same fixed template. Each was tested independently in ChatGPT. All outputs followed the required format (3-5 sentences, acknowledgment first, resolution or information next, offer of further help last) and respected the constraints (no jargon, minimal apologizing, no unearned promises), confirming the template is reliable and reusable across different customer scenarios without needing to be rewritten each time.

## Submission Links
GitHub Repo: https://github.com/ailanasirai/neurofive-genai-internship
LinkedIn Video: https://www.linkedin.com/in/aila-nasir/
