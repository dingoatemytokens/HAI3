## ADDED Requirements

### Requirement: Alert Component

The UI kit SHALL provide `Alert`, `AlertTitle`, and `AlertDescription` components for displaying feedback messages with optional icons and severity variants.

#### Scenario: Alert component is available

- **WHEN** importing Alert from `@hai3/uikit`
- **THEN** the Alert, AlertTitle, and AlertDescription components are available for use
- **AND** components support all standard React div props

#### Scenario: Alert with variant prop

- **WHEN** using Alert with variant="default"
- **THEN** the alert displays with bg-card and text-card-foreground styling
- **WHEN** using Alert with variant="destructive"
- **THEN** the alert displays with text-destructive styling
- **AND** the icon inherits text-current color
- **AND** the description uses text-destructive/90 opacity

#### Scenario: Alert with icon

- **WHEN** an SVG icon is placed as direct child of Alert
- **THEN** the alert uses CSS grid with icon column and content column
- **AND** the icon is sized at 4 (--spacing * 4) with translate-y-0.5 alignment
- **AND** the icon inherits text-current color

#### Scenario: Alert without icon

- **WHEN** Alert has no SVG icon as direct child
- **THEN** the alert uses single-column grid layout
- **AND** title and description start at column 2

#### Scenario: AlertTitle rendering

- **WHEN** using AlertTitle component
- **THEN** the title displays with font-medium, tracking-tight, and line-clamp-1 styling
- **AND** the title has min-h-4 and starts at col-start-2

#### Scenario: AlertDescription rendering

- **WHEN** using AlertDescription component
- **THEN** the description displays with text-muted-foreground and text-sm styling
- **AND** the description starts at col-start-2 and supports gap-1 for nested content
- **AND** paragraph elements within have leading-relaxed line height

#### Scenario: Alert accessibility

- **WHEN** Alert is rendered
- **THEN** it has role="alert" attribute
- **AND** it has data-slot="alert" for styling hooks

### Requirement: Alert Demo Examples

The UI kit demo SHALL provide examples for the Alert component in the Feedback & Status category demonstrating:
- Success alert with icon, title, and description
- Alert with icon and title only (no description)
- Destructive alert with icon, title, and description containing structured content (list)

#### Scenario: Alert section in FeedbackElements

- **WHEN** viewing the Feedback & Status category in UIKitElementsScreen
- **THEN** an Alert section is displayed with heading and examples
- **AND** the section includes `data-element-id="element-alert"` for navigation

#### Scenario: Alert examples use translations

- **WHEN** Alert examples are rendered
- **THEN** all text content uses the `tk()` translation helper
- **AND** all translated text is wrapped with TextLoader component

#### Scenario: Multiple Alert examples

- **WHEN** viewing the Alert section
- **THEN** three examples are displayed demonstrating different use cases
- **AND** examples include icons from lucide-react (CheckCircle2Icon, PopcornIcon, AlertCircleIcon)

### Requirement: Alert in Category System

The UI kit element registry SHALL include 'Alert' in the `IMPLEMENTED_ELEMENTS` array to mark it as an available component in the Feedback & Status category.

#### Scenario: Category Menu Shows Alert

- **WHEN** viewing the UIKit category menu
- **THEN** Alert appears as an implemented element in Feedback & Status category
- **AND** Alert is positioned alphabetically among other feedback elements

### Requirement: Alert Translations

The UI kit translations SHALL provide localized strings for all 36 supported languages with keys including:
- `alert_heading` - Section heading
- `alert_success_title` - Success alert title
- `alert_success_description` - Success alert description
- `alert_info_title` - Info/icon-only alert title
- `alert_error_title` - Destructive alert title
- `alert_error_description` - Destructive alert description
- `alert_error_check_card` - Error list item: check card
- `alert_error_ensure_funds` - Error list item: ensure funds
- `alert_error_verify_address` - Error list item: verify address

#### Scenario: Translated Alert Labels

- **WHEN** viewing the Alert demo in a non-English language
- **THEN** all Alert text displays in the selected language
- **AND** translations are contextually appropriate for feedback messaging
