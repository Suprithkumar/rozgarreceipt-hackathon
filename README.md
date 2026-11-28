# RozgarReceipt

**Every shift, clearly agreed.** RozgarReceipt is a voice-first prototype that helps daily-wage workers and employers review the same work terms and keep a shared shift receipt.

## Run with Docker Compose

```sh
docker compose up --build
```

Open [http://localhost:8080](http://localhost:8080).

## Run without Docker

With Python installed, run `python -m http.server 8000` from this folder, then open [http://localhost:8000](http://localhost:8000). The voice flow has separate app, hirer speech, and worker listening language choices for English, Hindi, Kannada, Tamil, Telugu, and Malayalam. App and speech-language choices are saved on the device. The hirer language controls recognition; the worker language controls the spoken announcement. Use **Use hirer language for worker** to set both to the same language, or change the language in the worker review panel to refresh and hear the announcement again. The full announcement is also shown in the selected language. The app chooses a matching browser speech voice when available and explains when that voice is missing. Browser speech recognition and playback depend on browser/device support and an internet connection; use Chrome or Edge and allow microphone access. If browser recognition fails, the app shows a transcript box that can use the device keyboard microphone or accept typed words. English speech fills shift fields on-device. The prototype recognizes natural phrases such as “two workers needed for painting, from 9 to 5, at MG Road, Bengaluru, ₹900 each,” including comma-separated addresses. It builds the worker announcement from a sentence template in the selected language; when requested, it translates only the address for that announcement. For other hirer languages, the user can consent to send the transcript to MyMemory for English translation before the app extracts shift details. Translation needs internet, no API key, and the provider may limit or fail requests. Every filled value must be checked before saving; if translation fails, the original transcript and typed fields remain available, and the announcement still uses the selected language.

## Prototype flow

1. Create or fill a sample shift.
2. Review the work, date, hours, location, and pay.
3. Switch to the worker review and confirm or flag the offer.
4. Open a receipt to mark work complete and record payment or a review issue.

Demo records are stored in the browser's local storage. The prototype sends no messages and moves no money. When the user explicitly requests translation, it sends the transcript and/or work address to MyMemory. Use **Reset demo** above the receipt list to restore the initial sample records.

## Scope and limitations

- This is a demonstration prototype, not a legal contract or payroll system.
- It does not verify identity, mediate disputes, or guarantee payment.
- The worker confirmation screen is simulated on the same device. A real pilot should let workers review privately on their own phone or with a trusted facilitator.
- The MyMemory translation API is used only after the user checks the consent box and taps the voice form button. Depending on language choices, it receives the hirer's transcript and/or work address. Avoid sending names, phone numbers, or highly sensitive information. Its public anonymous API has usage limits; if it is unavailable, use the original transcript and type the shift details manually. See [MyMemory API limits](https://mymemory.translated.net/doc/usagelimits.php).

