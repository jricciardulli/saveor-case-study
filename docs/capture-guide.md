# Capture guide

The three required screenshots and two recordings have been supplied and integrated. See the [demo manifest](../assets/demo/README.md) and [screenshot manifest](../assets/screenshots/README.md) for the current files. The shot list below is a reference for future recaptures, not outstanding work. The current demo uses a desk lamp and splits creation and inventory browsing into separate recordings.

## Prepare the demo

Use a demo account with synthetic inventory named **Demo Home**. Photograph an ordinary object such as a blue ceramic mug. Suggested context: “Blue ceramic mug, kitchen shelf, gift from a friend.” Avoid real customer information, family photos, receipts, shipping labels, addresses, and account/payment identifiers. Enable Do Not Disturb and keep notifications and developer tools out of frame.

Use one primary device/orientation throughout. Capture legible UI at its native resolution. Keep original recordings outside this repository; add only edited public exports to the paths below.

## 60–90 second product walkthrough

| Time | Capture | Suggested caption |
| --- | --- | --- |
| 0–7 s | Open the synthetic inventory and begin adding an item. | SaveOr: from an object to an organized inventory. CTO, product creator, and current sole maintainer. |
| 7–22 s | Photograph the mug and show the actual background-removal step. | Initial Gemini/camera implementation: David Koffi. |
| 22–38 s | Add the sample context and start AI-assisted creation. | My work extends and maintains the surrounding context and inventory workflow. |
| 38–53 s | Review the generated draft; correct a field if useful. | Review and edit AI-generated information before saving. |
| 53–65 s | Save and show the item in Demo Home. | Capture, review, and inventory management in one workflow. |
| 65–80 s | Search/filter the inventory and reopen the saved item. | My inventory redesign separates the searchable index from full item details. |
| 80–90 s | End on the inventory or item detail. | Engineering case studies: inventory loading and payment reliability. |

Adapt the order to the real UI. Trim long waits only with a visible “wait shortened” caption; do not turn an edited video into an implied latency benchmark. Keep credit visible long enough to read. Do not describe background removal or initial camera/Gemini work as solely yours.

Export to **`assets/demo/saveor-product-demo.mp4`**. Use a widely playable MP4 export (H.264 video, AAC audio if narrated). Provide readable on-screen captions even if you narrate. Export an 8–12 second excerpt to **`assets/demo/saveor-preview.gif`** and a clear inventory frame to **`assets/demo/saveor-demo-poster.jpg`**. Keep the GIF small enough to load comfortably in a README.

## Three required screenshots

1. **`assets/screenshots/01-capture-and-context.png`** — show the captured object and contextual input after background removal. Caption: “I maintain and extend the surrounding context, review, and inventory workflow. Initial Gemini/camera implementation: David Koffi.”
2. **`assets/screenshots/02-review-and-save.png`** — show the generated draft and editable fields. Caption: “My ongoing product work integrates AI-assisted item review and saving into the inventory experience.”
3. **`assets/screenshots/03-inventory-search.png`** — show a search/filter result containing the saved item. Caption: “I redesigned inventory loading around a complete searchable index with incremental detail loading and bounded card rendering.”

## Optional fourth and fifth screenshots

- **`assets/screenshots/04-item-details.png`** — reopen the saved item. Caption: “Full item details are resolved when an action needs them, while browsing uses the inventory index.”
- **`assets/screenshots/05-access-recovery.png`** — capture a controlled sandbox verification failure/retry. Caption: “My entitlement work distinguishes unavailable verification from revoked access, allowing a clear retry path.” Do not capture a real payment or customer account.

## Final review

Watch the exported video from beginning to end and inspect all screenshots at full size. Confirm text is readable, personal information is absent, captions describe your actual contribution, and David Koffi’s credit appears. Follow [publishing.md](publishing.md) to embed only the files you have actually added.
