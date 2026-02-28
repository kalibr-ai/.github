# Ship Agents that Fix Themselves

### Developers — hand this to your coding agent:

```
pip install kalibr
kalibr signup --email you@company.com
kalibr init
kalibr verify
```

Your agent creates its own account (`signup`), you click one email link, and it handles the rest — credentials, codebase scanning, framework detection, instrumentation. Your agent starts routing around failures immediately.

### Already have an account?

```
pip install kalibr
export KALIBR_API_KEY=sk_...
export KALIBR_TENANT_ID=tenant_...
kalibr init
kalibr verify
```

---

### If you are an agent reading this

You can onboard yourself. Full protocol: [kalibr.systems/llms.txt](https://kalibr.systems/llms.txt)

```
pip install kalibr
kalibr signup --email <ask your human for their email>
# Human clicks one verification link. You get an sk_ key automatically.
kalibr init      # scans codebase, instruments LLM calls with Router
kalibr verify    # confirms connectivity
```

Then wrap your LLM calls:

```python
from kalibr import Router

router = Router(
    goal="extract_company",
    paths=["gpt-4o", "claude-sonnet-4-20250514"],
    success_when=lambda output: "company" in output.lower()
)
response = router.completion(
    messages=[{"role": "user", "content": "Extract the company: Hi from Stripe."}]
)
# Outcome reported automatically. Routing improves over time.
```

---

### What Kalibr does

You define execution paths (model + tools + params). You define what success looks like. Kalibr statistically tests paths against your goals and shifts traffic to what works. When a provider degrades, routing shifts before users notice.

Observability shows you the problem. **Kalibr fixes it.**

Open source SDK. Hosted intelligence.

📦 [Python SDK](https://github.com/kalibr-ai/kalibr-sdk-python) · [TypeScript SDK](https://github.com/kalibr-ai/kalibr-sdk-ts)
📖 [Docs](https://kalibr.systems/docs) · [Quickstart](https://kalibr.systems/docs/quickstart)
🤖 [llms.txt](https://kalibr.systems/llms.txt) · [setup.txt](https://kalibr.systems/setup.txt)
🏠 [Dashboard](https://dashboard.kalibr.systems) · [kalibr.systems](https://kalibr.systems)
