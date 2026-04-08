# Pricing Service — Coding Assessment

Thank you for taking the time to complete this assessment. This challenge is designed to take around **90 minutes** of active development time — feel free to spend more or less as needed, as long as the specified functionality is complete.

---

## The Challenge

Build a RESTful API that acts as a pricing service. Using the product and VAT data in [`pricing.json`](./pricing.json), create an endpoint that calculates prices and VAT for an order.

---

## Requirements

### Endpoint

Your API must expose exactly one endpoint:

```
POST /pricing
```

### Request Format

```json
{
  "order": {
    "id": 12345,
    "customer": {},
    "items": [
      { "product_id": 1, "quantity": 1 },
      { "product_id": 2, "quantity": 5 },
      { "product_id": 3, "quantity": 1 }
    ]
  }
}
```

### Response Format

The response structure is up to you, but it **must include**:

- The **total price** for the order (excluding VAT)
- The **total VAT** for the order
- The **price and VAT for each item** in the order

### Currency

All values in `pricing.json` are in **Kenya Shillings (KES)**. Your response should also be in KES.

### Rounding

All monetary values must be **whole shillings** — no decimals. Use standard arithmetic rounding (0.5 rounds up).

### Going International *(optional stretch goal)*

Expand the API to accept an optional `currency` parameter in the request. When provided, return all prices converted to that currency using the latest exchange rates from a free API such as [exchangerate-api.com](https://www.exchangerate-api.com) or similar.

- The same VAT rates apply regardless of currency
- Think about how you would cache exchange rate data
- If no currency is provided, default to KES

---

## Technical Requirements

You may use **any language, framework, or library** you like. We want to see how you think about and solve problems in code — make sure there is a meaningful chunk of your own logic in there.

Your server **must**:

| Requirement | Detail |
|---|---|
| Listen on `PORT` | Read the port from the `PORT` environment variable. Default to `3000` if not set. |
| Expose `POST /pricing` | The main pricing endpoint described above |
| Expose `GET /health` | Return HTTP `200` with any body — this is used by the automated grader to confirm your server started correctly |

---

## Testing

We would like to see **tests** written in the testing framework of your choice for the pricing logic.

If you run out of time to write tests, include a comment in your README explaining:
- What level of testing you would add
- What specific test cases you would cover
- How you would approach mocking the currency API

---

## Submission

Your work is submitted automatically every time you **push to this repository**. The automated grader will:

1. Detect your language
2. Install your dependencies
3. Start your server
4. Run a suite of correctness tests against `POST /pricing`
5. Run your own test suite and report the results

You can check the results in the **Actions tab** of your repository after each push. You will see two sections:

- **Suite A** — your own tests (quality signal)
- **Suite B** — grader correctness tests (scored)

Feel free to push as many times as you like — only your final push before the deadline is evaluated.

---

## Getting Started

### Step 1 — Accept your repository invitation

You will receive an email from GitHub with the subject **"You've been invited to collaborate"**. 

- Open the email and click **"View invitation"**
- Click **"Accept invitation"** on the GitHub page that opens
- You now have access to your personal assessment repository at:
  `https://github.com/kopo-kopo-hiring/pricing-assessment-[your-github-username]`

> ⚠️ If you can't find the invitation email, check your spam folder. You can also accept it directly by visiting `https://github.com/kopo-kopo-hiring` — the invitation banner will appear at the top of the page.

### Step 2 — Clone your repo

Once you have accepted the invitation, clone the repo to your local machine:

```bash
git clone https://github.com/kopo-kopo-hiring/pricing-assessment-[your-github-username].git
cd pricing-assessment-[your-github-username]
```

Replace `[your-github-username]` with your actual GitHub username.

### Step 3 — Build your solution

Create your API in whatever language and structure you prefer. For example, a Node.js solution might look like:

```
pricing-assessment-[your-github-username]/
├── src/
│   └── index.js
├── tests/
│   └── pricing.test.js
├── pricing.json
├── package.json
└── README.md        ← update this with your setup notes
```

### Step 4 — Update the README

Add a section to this README explaining:
- How to install dependencies and run your server locally
- How to run your tests
- Any design decisions or trade-offs you made

### Step 5 — Push and check the grader

```bash
git add .
git commit -m "Initial solution"
git push
```

Then go to the **Actions tab** in your repo and watch the grader run. You can get there directly at:

`https://github.com/kopo-kopo-hiring/pricing-assessment-[your-github-username]/actions`

If your server doesn't start, check the logs — the most common issues are:
- Missing `GET /health` endpoint
- Not reading the `PORT` environment variable
- Entry point file not found (make sure your start command is in `package.json` scripts, or your main file is named `app.py`, `main.go`, etc.)

---

## What We're Looking For

| Area | What good looks like |
|---|---|
| **Correctness** | Prices and VAT calculated accurately, rounding handled properly |
| **Code quality** | Clean, readable, well-structured code you'd be happy to review in a PR |
| **Error handling** | Sensible HTTP status codes for bad inputs (unknown product, missing fields, etc.) |
| **Testing** | Meaningful tests that cover the pricing logic, not just happy-path smoke tests |
| **README** | Clear instructions for running the project locally |

---

## Notes

- The `customer` field in the order is intentionally empty for this assessment — you don't need to do anything with it
- You don't need a database — reading from `pricing.json` at startup is perfectly fine
- Commit regularly so we can see how your thinking evolved
- If you get stuck or have questions, reach out — we'd rather you ask than get blocked

Good luck! 🚀
