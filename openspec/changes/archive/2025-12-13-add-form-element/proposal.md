# Add Form Composite UI Kit Element

## Why

The UI Kit currently lacks a standardized way to build forms with validation, controlled state, and proper accessibility attributes. While the existing `Field` components handle layout (labels, descriptions, error display), there's no integration with form libraries for state management and validation.

Adding a `Form` component that wraps `react-hook-form` will provide:
- Composable components for building controlled forms
- Built-in zod validation support via `@hookform/resolvers`
- Automatic accessibility attributes (aria-invalid, aria-describedby)
- Unique ID generation via `React.useId()`
- Seamless integration with all existing Radix UI components

## What Changes

### New Dependencies
- `react-hook-form` - Form state management
- `@hookform/resolvers` - Schema validation adapters (zod, yup, etc.)

### New Components
- `Form` - Re-export of `FormProvider` from react-hook-form
- `FormField` - Controller wrapper with field context
- `FormItem` - Container with auto-generated ID context
- `FormLabel` - Label with error state styling
- `FormControl` - Slot with aria attributes for form controls
- `FormDescription` - Help text linked via aria-describedby
- `FormMessage` - Error message display

### New Hook
- `useFormField` - Access field state (id, name, error, etc.)

## Affected Specs
- `uikit-base` - New Form composite component requirements
