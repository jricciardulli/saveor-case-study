# Architecture and responsibility boundaries

The diagram in the [README](../README.md#architecture) summarizes the product without exposing deployment details.

| Component | Responsibility |
| --- | --- |
| Angular / Ionic | Shared application UI, inventory state, search/filter interactions, item review, and access feedback. |
| Capacitor and native components | Device capture/media capabilities and native purchase integration where supported. Browser flows use web capabilities. |
| Express API and supporting services | Authentication, inventory authorization, detail resolution, provider integrations, and entitlement evaluation. |
| MySQL | Structured inventory, account, relationship, and subscription state. |
| Object storage | Item images and other media; application records reference media. |
| AI and image-processing providers | Inference and media transformations used by the item-creation workflow. |
| Payment providers | Native purchases and Stripe billing; server validation and reconciliation translate provider state into product access. |

The arrows represent logical responsibilities, not a claim that every platform takes the same upload route. Provider secrets and authorization decisions belong on the server. Client loading and access states communicate progress; they do not replace server authorization.

The inventory case study separates list data from action data. The payments case study separates provider payment state from the application’s access decision. Both reduce accidental coupling between a responsive interface and a slower external dependency.
