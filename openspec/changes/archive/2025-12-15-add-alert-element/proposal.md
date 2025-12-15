# Change: Add Alert Base UI Kit Element

## Why
The UI Kit Feedback & Status category lists Alert as a planned element but lacks implementation. Alert is a fundamental feedback component for displaying important messages to users with different severity levels (informational, destructive).

## What Changes
- Add `Alert`, `AlertTitle`, `AlertDescription` base components to `@hai3/uikit`
- Implement variant support (default, destructive) using class-variance-authority
- Add demo examples to FeedbackElements.tsx
- Add Alert to IMPLEMENTED_ELEMENTS array
- Add translations for Alert demo across 36 supported languages

## Impact
- Affected specs: `uikit-base`
- Affected code:
  - `packages/uikit/src/base/alert.tsx` (new)
  - `packages/uikit/src/index.ts` (export)
  - `src/screensets/demo/components/FeedbackElements.tsx` (demo)
  - `src/screensets/demo/screens/uikit/uikitCategories.ts` (IMPLEMENTED_ELEMENTS)
  - `src/screensets/demo/screens/uikit/i18n/*.json` (36 files)
