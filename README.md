# RozgarReceipt

**Every shift, clearly agreed.** RozgarReceipt is a voice-first prototype that helps daily-wage workers and employers review the same work terms and keep a shared shift receipt.

## Run with Docker Compose

```sh
docker compose up --build
```

Open [http://localhost:8080](http://localhost:8080).

## Run without Docker

With Python installed, run `python -m http.server 8000` from this folder, then open [http://localhost:8000](http://localhost:8000). The voice flow has separate hirer and worker language choices for English, Hindi, Kannada, Tamil, Telugu, and Malayalam. Browser speech recognition and playback depend on browser/device support. When the languages differ, the user can explicitly send the short transcript to MyMemory for translation and read-aloud. Translation needs internet, no API key, and the provider may limit or fail requests; the original transcript and typed form remain available. Automatic shift-field extraction currently understands English speech; other captured speech must be entered or checked manually.

## Prototype flow

1. Create or fill a sample shift.
2. Review the work, date, hours, location, and pay.
3. Switch to the worker review and confirm or flag the offer.
4. Open a receipt to mark work complete and record payment or a review issue.

Demo records are stored in the browser's local storage. The prototype makes no calls, sends no messages, and moves no money. Use **Reset demo** above the receipt list to restore the initial sample records.

## Scope and limitations

- This is a demonstration prototype, not a legal contract or payroll system.
- It does not verify identity, mediate disputes, or guarantee payment.
- The worker confirmation screen is simulated on the same device. A real pilot should let workers review privately on their own phone or with a trusted facilitator.
- The MyMemory translation API is used only after the user checks the consent box and taps Translate. Avoid sending names, phone numbers, or highly sensitive information. Its public anonymous API has usage limits; if it is unavailable, use the original transcript and type the shift details manually. See [MyMemory API limits](https://mymemory.translated.net/doc/usagelimits.php).
