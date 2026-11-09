---
description: Welcome to the Autoresponder Guide!
---

# Advanced Autoresponder Guide

The autoresponder system allows you to create dynamic, interactive, and automated bot responses for your server. It supports match modes, user variables, argument capturing, randomization, probability weights, rich embeds, background economy updates, inventory modifications, and persistent cooldowns.

### 📋 Table of Contents

1. [Match Modes](advanced-autoresponder-guide.md#id-1.-match-modes)
2. [User Variables](advanced-autoresponder-guide.md#id-2.-user-variables)
3. [Server & Economy Variables](advanced-autoresponder-guide.md#id-3.-server-and-economy-variables)
4. [Channel & Message Variables](advanced-autoresponder-guide.md#id-4.-channel-and-message-variables)
5. [Argument Placeholders](advanced-autoresponder-guide.md#id-5.-argument-placeholders)
6. [Randomization & Probabilities](advanced-autoresponder-guide.md#id-6.-randomization-and-probabilities)
7. [Embed Styling Functions](advanced-autoresponder-guide.md#id-7.-embed-styling-functions)
8. [Restrictions, Cooldowns & Side-Effect Actions](advanced-autoresponder-guide.md#id-8.-restrictions-cooldowns-and-side-effect-actions)
9. [Complete Example Configurations](advanced-autoresponder-guide.md#id-9.-complete-example-configurations)

### 1. Match Modes

When creating an autoresponder with `/autoresponder add`, you can specify how the bot detects your trigger phrase:

* **`includes`** _(Default)_: Triggers if the trigger word appears anywhere inside the user's message.
* **`exact`**: Triggers only if the user's message is an exact, letter-for-letter match to the trigger.
* **`startswith`**: Triggers if the user's message starts with the trigger phrase (ideal for command-style triggers).
* **`endswith`**: Triggers if the user's message ends with the trigger phrase.

### 2. User Variables

These placeholders pull information about the user who triggered the autoresponder:

| **Variable**        | **Description**                             | **Example Output**               |
| ------------------- | ------------------------------------------- | -------------------------------- |
| `{user}`            | Mentions the user                           | `@Joseph`                        |
| `{user_tag}`        | The user's tag                              | `joseph_dev#0`                   |
| `{user_name}`       | The user's username                         | `joseph_dev`                     |
| `{user_id}`         | The user's Discord ID                       | `586918941084090368`             |
| `{user_nick}`       | The user's server nickname                  | `Joseph • Dev`                   |
| `{user_joindate}`   | Date the user joined the server             | `Wed, Aug 15, 2018`              |
| `{user_createdate}` | Date the user's Discord account was created | `Wed, Dec 27, 2017`              |
| `{user_avatar}`     | Direct URL to the user's avatar image       | `https://cdn.discordapp.com/...` |
| `{user_balance}`    | The user's current cash balance             | `1,250`                          |

### 3. Server & Economy Variables

These variables pull info about your server and local economy system:

| **Variable**           | **Description**                            | **Example Output**               |
| ---------------------- | ------------------------------------------ | -------------------------------- |
| `{server_name}`        | Name of the Discord server                 | `The Honeycomb Meadow`           |
| `{server_id}`          | Server ID                                  | `1342732576258916382`            |
| `{server_membercount}` | Total server members                       | `407`                            |
| `{server_icon}`        | Direct URL to the server icon              | `https://cdn.discordapp.com/...` |
| `{server_currency}`    | Your server's custom currency symbol/emoji | `🪙` (or `🐝`)                   |

### 4. Channel & Message Variables

| **Variable**        | **Description**                            | **Example Output**                 |
| ------------------- | ------------------------------------------ | ---------------------------------- |
| `{channel}`         | Mentions the channel where triggered       | `#general`                         |
| `{channel_name}`    | Name of the channel                        | `general`                          |
| `{message_content}` | The full text of the user's message        | `hello everyone!`                  |
| `{message_link}`    | Direct jump link to the triggering message | `https://discord.com/channels/...` |
| `{newline}`         | Inserts a line break (new line)            | _(Starts a new line)_              |
| `{date}`            | Current UTC date and time                  | `Mon, Nov 9, 2026`                 |

### 5. Argument Placeholders

_Note: Only works with non-exact match modes (`startswith`, `includes`, `endswith`)._

When users type words after your trigger phrase, you can capture them as arguments:

* **`[$1]`**, **`[$2]`**: Grabs the 1st, 2nd, etc. word typed after your trigger.
* **`[$1+]`**: Grabs _all_ words typed starting from argument 1 onwards as a full sentence.

> **Example:** If trigger is `say` and user types `say hello world`:
>
> * Response: `You wanted me to say: [$1+]`
> * Bot Output: `You wanted me to say: hello world`

### 6. Randomization & Probabilities

#### 🎲 Number Ranges (`{range:min-max}` & `[range]`)

Picks a random number between a minimum and maximum value. You can use multiple ranges (`{range:}`, `{range1:}`, `{range2:}`, etc.).

* **Syntax:** `{range:1-100}` paired with placeholder `[range]` (or `[range1]`, etc.).
* **Example:** `You found {range:10-50} {server_currency} in the hive! You earned [range] cash!`

#### 🔀 List Choices (`{choose:a|b|c}` & `[choice]`)

Picks a random option from a custom list separated by pipes (`|`).

* **Syntax:** `{choose:apples|bananas|grapes}` paired with placeholder `[choice]`.

#### ⚖️ Weighted Choices (`{weightedchoose:...}`)

Pairs with `{choose}` to assign custom percentage weights or numerical odds to your options (making rare outcomes less frequent).

* **Syntax:** `{choose:common|rare|epic|legendary} {weightedchoose:60%|30%|8%|2%}`
* **Example:** `You opened a chest and got a {choose:Common|Rare|Legendary} {weightedchoose:70%|25%|5%} prize!`

### 7. Embed Styling Functions

You can transform your responses into polished Discord embeds. If you include text without an explicit description tag, it will automatically populate the embed description!

* **`{embed:title:Text}`**: Sets the embed header title.
* **`{embed:description:Text}`**: Sets the main body text of the embed.
* **`{embed:color:#HEX}`**: Sets the sidebar accent color (e.g., `{embed:color:#FFB834}`).
* **`{embed:footer:Text}`**: Sets the small footer text at the bottom.

> **Example:** `{embed:title:🎉 Daily Reward}{embed:color:#57F287}{user}, you claimed your daily reward!`

### 8. Restrictions, Cooldowns & Side-Effect Actions

Autoresponders can check user permissions, apply rate limits, and perform background database actions:

* **`{requirerole:RoleName}`**: Restricts the trigger to members possessing the specified role name or ID.
* **`{requirebal:Amount}`**: Restricts the trigger to users who have at least the specified amount of cash.
* **`{cooldown:Seconds}`**: Enforces a rate limit timer per user for that specific trigger.
* **`{modifybal:+50}`**, `{-20}`, or `:=100`: Adds, subtracts, or sets the user's server economy balance. You can also use keywords like `{modifybal:add 50}` or `{modifybal:set 500}`.
* **`{modifyinv:apple|1}`**: Adds or removes items from the user's server inventory.
* **`{delete}`**: Automatically deletes the user's original triggering message.
* **`{delete_reply:N}`**: Automatically deletes the bot's response message after `N` seconds.

### 9. Complete Example Configurations

#### 🐝 1. Daily Claim Embed (With Cooldown & Economy Reward)

* **Trigger:** `!daily` (Match Mode: `startswith`)
*   **Response:**

    ```
    {cooldown:86400} {range:100-500} {modifybal:+[range]} {embed:title:🍯 Daily Honey Collected}{embed:color:#FFB300}{user}, you collected **[range] {server_currency}** from your hive! You now have `{user_balance}` cash.

    ```

#### 🎁 2. Gamble / Gacha Box (With Weighted Odds & Balance Check)

* **Trigger:** `!roll` (Match Mode: `exact`)
*   **Response:**

    ```
    {requirebal:50} {modifybal:-50} {choose:common|rare|epic|legendary} {weightedchoose:65%|25%|8%|2%} {embed:title:🎲 Mystery Box Rolled}{embed:color:#9b59b6}{user}, you opened a mystery box for 50 {server_currency} and won a **[choice]** tier reward!

    ```
