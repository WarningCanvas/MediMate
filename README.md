# MediMate — Flutter Medicine Reminder

MediMate is a cross-platform Flutter app that helps users manage medication schedules and never miss a dose. It combines reliable local notifications with intelligent AI features to make adding medicines fast, accurate, and personalized.

---

## Key features (what this repo contains)

* Add medicines with custom name, dosage (mg/ml/tablets), and schedule (times, repeat).
* Pre-loaded medicine database with search and option to add custom medicines.
* Persistent local storage (Hive / SQLite) for offline usage.
* Daily local notifications (works when app is backgrounded or terminated).
* Customizable medicine icons: choose shape (round, capsule, square, bottle) and color.
* **AI features** (planned & integrated):

  1. **OCR Prescription Auto-fill** — snap a photo of a prescription/pill strip and auto-extract medicine names and dosages to pre-fill reminders (Google ML Kit + parsing + DB mapping).
  2. **AI-powered search & suggestions** — smart autocomplete and dosage suggestions using fuzzy matching or embeddings + optional LLM suggestions.
  3. **Chatbot Assistant** — ask general questions about medicines, dosing patterns, or missed doses. Powered by an LLM with a medical disclaimer (not a substitute for professional advice).
  4. **Voice Input** — add reminders using natural speech (speech-to-text + NLP parsing / LLM for structured extraction).

---

## Built with

* **Flutter** — cross-platform UI
* Notifications: `flutter_local_notifications` + `timezone`
* Local DB: `hive` or `sqflite` (your choice)
* OCR: `google_ml_kit` (text recognition)
* Voice: `speech_to_text`
* AI / LLM: OpenAI (or an alternative LLM provider) for search & chat features
* Optional: Firebase (Auth + Firestore + Cloud Functions + FCM) for sync & cross-device notifications

---

## Getting started — development setup

### Prerequisites

* Flutter SDK (stable channel) installed.
* Android Studio or Xcode for platform builds.
* A device or emulator (Android or iOS).
* (Optional for AI features) OpenAI API key or other LLM provider key.
* (Optional for cross-device sync) Firebase project + service account.


### Add a medicine (typical flow)

1. Tap **Add** → choose a medicine from the database or create a custom entry.
2. Enter dosage (e.g., `500 mg`, `1 tablet`) and select times.
3. Optionally customize icon shape and color.
4. Save → the app schedules local notifications and stores the reminder locally.

### OCR Auto-fill

1. Tap **Scan prescription** → allow camera permission.
2. The app extracts text using on-device OCR and suggests matches from the medicines DB.
3. Confirm matches, edit dosage/time if necessary, and save reminder.

### Voice add

1. Tap the **Voice** icon → say:
   *“Add Paracetamol 500 mg twice daily at 9 AM and 9 PM”*
2. Speech is converted to text, parsed (locally or via LLM), and the app fills the add-reminder form.

### Chatbot

* Ask general questions like: *“What should I do if I miss a dose?”*
* Chatbot returns general guidance with a **medical disclaimer**. It does not replace professional medical advice.

---

## Data model (high level)

* `Medicine` (id, name, type, defaultStrength, unit, iconMeta)
* `UserReminder` (id, medicineId or custom name, dosage, unit, scheduleTimes, iconMeta, enabled)
* `IconMeta` (shape, primaryColor, secondaryColor)

---

## Privacy & Safety

* **Medical disclaimer:** This app is **not** a substitute for professional medical advice. AI responses are informational only.
* Local-first: Personal data (medicines, reminders) is stored locally by default. If you enable cloud sync (Firebase), you will be asked to sign in and explicitly allow uploading your reminders.
* **Security:** do not commit API keys or private config to the repo. Use `.env` and secure storage.

---

## Roadmap / Planned improvements

* Improve OCR mapping using embeddings and larger medicine database.
* Add drug-interaction checks (requires integration with trusted medical APIs).
* Add snooze / missed-dose analytics and AI suggestions to improve adherence.
* Publish Play Store & App Store builds with complete testing & privacy documentation.

---

## Contributing

Contributions welcome! Please open an issue for features/bugs or submit a PR.

---


## Contact

Created by Krishiva Dhiman(WarningCanvas). If you want me to walk you through building any specific part (OCR integration, LLM chat, voice parsing, or Firebase sync), open an issue or message me directly and I’ll provide step-by-step code for that feature.
