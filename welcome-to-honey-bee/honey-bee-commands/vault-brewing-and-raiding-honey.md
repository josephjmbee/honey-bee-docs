---
description: >-
  Manage your companion's health, forage flowers, brew server honey, store
  reserves globally, and raid rival beekeepers.
---

# 🍯 Vault, Brewing & Raiding (/honey)

| **Usage**                         | **Subcommand** | **Variables**                                                                                             | **Description**                                                                                                                                                            |
| --------------------------------- | -------------- | --------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `/honey balance`                  | Balance        | None                                                                                                      | Displays your active companion status (HP/rarity), local guild honey/nectar tanks, global vault storage, and lifetime stats.                                               |
| `/honey forage`                   | Forage         | None                                                                                                      | Sends your bee out on a 30-minute foraging flight to gather pure nectar and XP. Features a 30–40% chance to trigger a Spider Web Ambush requiring a rescue or self-escape. |
| `/honey brew [amount]`            | Brew           | `amount` (Optional string: specify number or `"all"` / `"max"`)                                           | Converts local server nectar into brewed honey at a 10:1 ratio. Respects a 15-minute brewing cooldown and server storage caps.                                             |
| `/honey store [amount]`           | Store          | `amount` (Optional string: specify number or `"all"` / `"max"`)                                           | Transfers local server honey into your permanent Global Honey Vault for cross-server security.                                                                             |
| `/honey shop`                     | Shop           | None                                                                                                      | Opens the Honey Market catalog displaying available healing ointments, shields, and companion packs.                                                                       |
| `/honey buy item:<id> [quantity]` | Buy            | <p><code>item</code> (Required autocomplete)</p><p><br></p><p><code>quantity</code> (Optional min: 1)</p> | Purchases items from the Honey Market using your Global Vault honey reserves. Autocomplete is fully supported.                                                             |
| `/honey sting target:<user>`      | Sting          | `target` (Required user mention)                                                                          | Launches an aggressive sting raid against a rival beekeeper's server honey tank. Has a base 55% success rate modified by defender shields, and triggers a 2-hour cooldown. |
