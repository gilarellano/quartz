---
aliases:
  - UML Diagrams
  - UML Diagram
  - design
  - diagram
---
Textual representation of the [[UML Graph]]
## Classes

### Quote
- **Attributes**:
	- `quoteID: int`
	- `projectID: int`
	- `windows: list<Window>`
	- `subtotal: double`
	- `tax: double`
	- `total: double`
	- `status: QuoteStatus`
	- `reasonForStatus: string`
	- `dateCreated: date`
	- `dateModified: date`
	- `notes: string`
- **Methods**:
	- `AddWindow(window: Window): void`
	- `RemoveWindow(windowID: int): void`
	- `UpdateWindow(window: Window): void`
	- `CalculateSubtotal(): double`
	- `CalculateTax(): double`
	- `CalculateTotal(): double`
	- `GetQuoteDetails(): dict`
	- `GeneratePDF(): void`

### Customer
- **Attributes**:
	- `customerID: int`
	- `name: string`
	- `email: string`
	- `phoneNumber: string`
	- `address: string`
	- `projectAddress: string`
	- `projects: list<Project>`
- **Methods**:
	- `UpdateDetails(details: dict): void`
	- `GetCustomerDetails(): dict`

### Project
- **Attributes**:
	- `projectID: int`
	- `customer: Customer`
	- `quotes: list<Quote>`
	- `status: ProjectStatus`
	- `dateStarted: date`
	- `estimatedCompletionDate: date`
- **Methods**:
	- `AddQuote(quote: Quote): void`
	- `RemoveQuote(quoteID: int): void`
	- `UpdateStatus(status: string): void`
	- `GetProjectDetails(): dict`

### Window
- **Attributes**:
	- `windowID: int`
	- `type: WindowType`
	- `width: double`
	- `height: double`
	- `description: string`
	- `sashes: list<Sash>`
	- `installationCost: double`
- **Methods**:
	- `AddSash(sash: Sash): void`
	- `RemoveSash(sashID: int): void`
	- `GetSashes(): list<Sash>`
	- `CalculateCost()`
	- `PrintData()`

### Sash
- **Attributes**:
	- `sashID: int`
	- `windowID: int`
	- `width: double`
	- `height: double`
	- `perimeter: double`
	- `frameCost: double`
	- `numLites: int`
	- `design: Design`
	- `finish: Finish`
	- `glazings: list<Glazing>`
- **Methods**:
	- `CalculatePerimeter()`
	- `CalculateDesignCost()`
	- `CalculateFinishCost()`
	- `AddGlazing(glazing: Glazing): void`
	- `RemoveGlazing(glazingID: int): void`
	- `GetGlazings(): list<Glazing>`

### Glazing
- **Attributes**:
	- `glazingID: int`
	- `type: GlazingType`
	- `area: double`
	- `cost: double`
	- `addOns: list<AddOn>`
- **Methods**:
	- `CalculateArea()`
	- `CalculateAddOnCost()`
	- `AddAddOn(addOn: Addon): void`
	- `RemoveAddOn(addOnID: int): void`
	- `GetAddOns(): list<AddOn>`

### RateCard
- **Attributes**:
	- `itemType: string` (e.g., "wood", "glazing", "design", "finish")
	- `itemName: string` (e.g., "`DOUGLAS_FIR`", "`LAMINATED`")
	- `rate: double`
- **Methods**:
	- `GetRate(itemType: string, itemName: string): double`
	- `UpdateRate(itemType: string, itemName: string, newRate: double): void`

## Enumerations

1. **[[QuoteStatus]]**: `PENDING`, `APPROVED`, `REJECTED`, `REVISED`, `SUPERSEDED`, `WITHDRAWN`, `EXPIRED`
2. **[[ProjectStatus]]**: `INITIATED`, `IN_PROGRESS`, `COMPLETED`, `ON_HOLD`
3. **[[WindowType]]**: `SINGLE_HUNG`, `DOUBLE_HUNG`, `FIXED`, `CASEMENT`, `DOUBLE_CASEMENT`, `TRANSOM`, `AWNING`, `PIVOT`
4. **[[GlazingType]]**: `SINGLE_PANE`, `DUAL_PANE`
5. **[[AddOn]]**: `LAMINATED`, `TEMPERED`, `SOLARBAN_60`,  `SOLARBAN_70`, `OBSCURED`, `SATIN_ETCHED`, `ARGON_GAS`
6. **[[Design]]**: `DEFAULT`, `ARCH`, `BENT`, `CUSTOM`
7. **[[Finish]]**: `PRIMED`, `PAINTED`, `STAINED`, `CUSTOM`

## Relationships

- `Quote` has a one-to-many relationship with `Window`.
- `Quote` has a many-to-one relationship with `Project`.
- `Customer` has a one-to-many relationship with `Project`.
- `Project` has a one-to-many relationship with `Quote`.
- `Window` has a one-to-many relationship with `Sash`.
- `Window` has a many-to-one relationship with `Quote`.
- `Sash` has a many-to-one relationship with `Window`.
- `Sash` has a one-to-many relationship with `Glazing`.