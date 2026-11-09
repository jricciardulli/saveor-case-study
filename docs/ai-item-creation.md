# AI-assisted item creation

**David Koffi built the initial Gemini/camera implementation.** This note focuses on the surrounding contextual workflow and its ongoing integration and maintenance.

## Problem

An image alone does not convey everything a user knows about an item. The workflow needs to preserve context, let users review generated information, and place the saved item in the intended inventory. Inference and media operations can also fail independently of the final save.

## Decision

The application carries contextual inputs through AI-assisted item creation and supports retrying inference with revised context. Inventory identity accompanies retry requests. List and box context need explicit handling so stale context from an earlier camera session does not place a new item incorrectly.

The user can review the generated draft and continue to saving. Background-removal and inference progress should be shown as actual product behavior in the recording, with any edited wait clearly labeled. Generated content should be presented as an editable draft, not a guaranteed factual identification.

## Tradeoff and verification

More contextual state improves the draft but adds opportunities for an old inventory, list, or box selection to leak into the next capture. Existing focused tests cover box context and inference retry authorization/inventory context. The public capture should also show that the saved item appears in the intended inventory and can be opened again.

A successful capture alone does not verify retry behavior. For a separate failure demonstration, use a synthetic account and a controlled failure, then show the actual error/retry UI. Do not claim that inference, upload, and save form one atomic operation or that every failure is automatically recoverable.

Suggested contribution caption: “I maintain and extend the surrounding context, review, and inventory workflow. Initial Gemini/camera implementation: David Koffi.”
