# PAUSE — Escalation Radar

A small tool for people getting trapped in "like videos and earn ₹150–₹500" WhatsApp/Telegram task groups. These scams pay a little real money first to build trust, then slowly ask for ₹35,000+ as VIP task, verification and release fees.

PAUSE reads the whole chat instead of one message. It shows:

- the scam stage (for example 4/5 — ESCALATION)
- a Receipt: money promised vs money asked, with the ratio
- the next message the scammer is likely to send
- a calm Hinglish/English message telling the person to stop paying and report on 1930

All chats used in the demo are made up. No real victim data was used.

## Demo case note

```
Day 1: Review task completed. Promised payment Rs 150. Paid Rs 150.
Day 3: VIP task offered. Promised reward Rs 1200. Deposit Rs 500 demanded.
Day 9: Account frozen. Verification fee Rs 8000 demanded.
Day 14: Final release fee Rs 35000 demanded. Borrow from family today.
```

With this note the Receipt reads:

- PROMISED_TOTAL ₹1,350
- ASKED_TOTAL ₹43,500
- RATIO 32.2×

## How it was built on Adaption AI

1. **Adaptive Data → Invent a Dataset**: generated 1,581 multilingual prompt/completion pairs (Hinglish, English, Tamil, Telugu). Each completion has `STAGE`, `LABEL`, `PROMISED_TOTAL`, `ASKED_TOTAL`, `RATIO`, `NEXT_ASK` and `PAUSE`. 20% are benign freelance examples. Same-domain and general-purpose augmentation brought training to about 20,000 rows.
2. **AutoScientist**: trained a Gemma 3 4B PT model with LoRA (rank 32, alpha 64, 3 epochs, cosine) on `enhanced_prompt` / `enhanced_completion`.
3. **Interfaces**: built the PAUSE app with Stage, Receipt and Next Ask cards, a promised-vs-asked chart, and the outreach draft.

## Files

- `demo_case_note.txt` — the chat used in the demo
- `dataset_prompt.txt` — the prompt used in Invent a Dataset
- `model_recipe.txt` — the AutoScientist recipe

## Links

- Deployed app: add your published Adaption link here
- Demo video: add your video link here
