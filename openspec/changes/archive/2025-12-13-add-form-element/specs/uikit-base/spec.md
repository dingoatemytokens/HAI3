# Spec Delta: uikit-base

## ADDED Requirements

### Requirement: Form Composite Component

The UI kit SHALL provide Form, FormField, FormItem, FormLabel, FormControl, FormDescription, and FormMessage components as a composite element that wraps react-hook-form for controlled form state management with schema validation and automatic accessibility attributes.

#### Scenario: Form component is available

Given a developer importing from @hai3/uikit
When they import Form, FormField, FormItem, FormLabel, FormControl, FormDescription, FormMessage
Then all components should be available for use

#### Scenario: Form with zod validation

Given a form schema defined with zod
When the form is submitted with invalid data
Then validation errors are displayed in FormMessage components
And aria-invalid is set to true on invalid fields

#### Scenario: Form field accessibility

Given a FormItem with FormLabel, FormControl, FormDescription, and FormMessage
When the FormItem renders
Then FormControl has aria-describedby linking to description and message IDs
And FormLabel htmlFor points to the control element ID

### Requirement: FormField Controller Integration

The FormField component SHALL wrap react-hook-form's Controller and provide field context to descendant components via FormFieldContext.

#### Scenario: FormField with render prop

Given a FormField with name and render prop
When the field renders
Then the render prop receives field state and handlers from react-hook-form
And FormFieldContext provides the field name to descendants

#### Scenario: FormField error state

Given a FormField with a validation error
When the field is invalid
Then useFormField hook returns the error state
And FormLabel displays with destructive styling

### Requirement: FormItem ID Generation

Each FormItem component SHALL generate unique IDs via React.useId() for accessibility linking between label, control, description, and message elements.

#### Scenario: Unique IDs per FormItem

Given multiple FormItems in a form
When they render
Then each has unique IDs generated via React.useId()
And child components use correct ID patterns (formItemId, formDescriptionId, formMessageId)

#### Scenario: Aria attributes linkage

Given a FormItem with all child components
When FormControl renders
Then aria-describedby includes formDescriptionId and formMessageId when error exists
And id is set to formItemId

### Requirement: useFormField Hook

The UI kit SHALL export a useFormField hook that provides access to form field state including id, name, formItemId, formDescriptionId, formMessageId, and error state.

#### Scenario: useFormField in custom component

Given a custom component inside FormItem
When calling useFormField()
Then it returns the field context with all ID values and error state

#### Scenario: useFormField outside FormField

Given useFormField called outside a FormField
When the hook executes
Then it throws an error indicating it should be used within FormField

### Requirement: Form Demo Examples

The UI kit demo SHALL provide examples for the Form component in the Forms & Inputs category demonstrating:
- Profile form with username field using zod validation (min 2 chars)
- FormField with render prop pattern for controlled input
- FormLabel, FormControl, FormDescription, and FormMessage composition
- Form submission with validation feedback

#### Scenario: Form section in FormElements

Given a user viewing the Forms & Inputs category in UIKitElementsScreen
When they scroll to the Form section
Then they should see the heading and profile form demo example

#### Scenario: Profile form structure

Given the profile form demo
When viewing the form
Then it should display a username field with label "Username"
And a description "This is your public display name."
And a Submit button

#### Scenario: Profile form validation error

Given the profile form demo with empty or single-character input
When the user clicks Submit
Then a validation error "Username must be at least 2 characters." appears in FormMessage
And the input shows aria-invalid="true"
And the form does not submit

#### Scenario: Profile form successful submission

Given the profile form demo with valid input (2+ characters)
When the user clicks Submit
Then no validation errors appear
And the form submits successfully (console.log or toast)

#### Scenario: Demo uses zodResolver

Given the profile form demo implementation
When examining the useForm configuration
Then it should use zodResolver with a zod schema for validation

### Requirement: Form in Category System

The UI kit element registry SHALL include 'Form' in the IMPLEMENTED_ELEMENTS array to mark it as an available component in the Forms & Inputs category.

#### Scenario: Form in IMPLEMENTED_ELEMENTS

Given the uikitCategories.ts file
When checking the IMPLEMENTED_ELEMENTS array
Then 'Form' should be present and alphabetically ordered

### Requirement: Form Translations

The UI kit translations SHALL provide localized strings for all 36 supported languages with keys including form_heading and form demo labels.

#### Scenario: Translation keys exist

Given any of the 36 supported language files
When checking for form_* keys
Then all required keys should be present
