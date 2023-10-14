---
aliases: graph
---
Visual representation of the [[UML Design]]

``` mermaid

classDiagram
    class Quote {
        + quoteID: int
        + projectID: int
        + windows: list<Window>
        + subtotal: double
        + tax: double
        + total: double
        + status: QuoteStatus
        + dateCreated: date
        + dateModified: date
        + notes: string
        + AddWindow(window: Window): void
        + RemoveWindow(windowID: int): void
        + UpdateWindow(window: Window): void
        + CalculateSubtotal(): double
        + CalculateTax(): double
        + CalculateTotal(): double
        + GetQuoteDetails(): dict
        + GeneratePDF(): void
    }

    class Customer {
        + customerID: int
        + name: string
        + email: string
        + phoneNumber: string
        + address: string
        + projectAddress: string
        + projects: list<Project>
        + UpdateDetails(details: dict): void
        + GetCustomerDetails(): dict
    }

    class Project {
        + projectID: int
        + customer: Customer
        + quotes: list<Quote>
        + status: ProjectStatus
        + dateStarted: date
        + estimatedCompletionDate: date
        + AddQuote(quote: Quote): void
        + RemoveQuote(quoteID: int): void
        + UpdateStatus(status: string): void
        + GetProjectDetails(): dict
    }

    class Window {
        + windowID: int
        + type: WindowType
        + width: double
        + height: double
        + description: string
        + sashes: list<Sash>
        + installationCost: double
        + AddSash(sash: Sash): void
        + RemoveSash(sashID: int): void
        + GetSashes(): list<Sash>
        + CalculateCost()
        + PrintData()
    }

    class Sash {
        + sashID: int
        + windowID: int
        + width: double
        + height: double
        + perimeter: double
        + frameCost: double
        + numLites: int
        + design: Design
        + finish: Finish
        + glazings: list<Glazing>
        + CalculatePerimeter()
        + CalculateDesignCost()
        + CalculateFinishCost()
        + AddGlazing(glazing: Glazing): void
        + RemoveGlazing(glazingID: int): void
        + GetGlazings(): list<Glazing>
    }

    class Glazing {
        + glazingID: int
        + type: GlazingType
        + area: double
        + cost: double
        + addOns: list<AddOn>
        + CalculateArea()
        + CalculateAddOnCost()
        + AddAddOn(addOn: Addon): void
        + RemoveAddOn(addOnID: int): void
        + GetAddOns(): list<AddOn>
    }

    class RateCard {
        + itemType: string
        + itemName: string
        + rate: double
        + GetRate(itemType: string, itemName: string): double
        + UpdateRate(itemType: string, itemName: string, newRate: double): void
    }

    Quote "1" --> "many" Window : contains
    Customer "1" --> "many" Project : has
    Project "1" --> "many" Quote : has
    Window "1" --> "many" Sash : contains
    Sash "1" --> "many" Glazing : has
```
