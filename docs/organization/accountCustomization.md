---
title: Account customization
description: Control visibility and edit permissions for each user account field.
keywords: [account customization, view rule, modify rule]
authors: [leo220yuyaodog]
---

You can customize **account items** per organization: whether each field is visible and who can view or modify it. These settings apply to every member’s profile/home page in that organization.

## Configuring account items

Each account item has five settings:

| Column Name | Selectable Value | Description |
| :---------: | :--------------: | ----------- |
|    Name     |        -         | Account item name. |
|   Visible   | `True` / `False` | Select whether this account item is visible on the user home page. |
|  ViewRule  |    Rule Items    | Select a rule to use when viewing the account item. Controls who can **view** this field. |
| ModifyRule |    Rule Items    | Select a rule to use when modifying the account item. Controls who can **edit** this field. |
|    Tab      |        -         | Tab label to group this item under on the user edit page. Items with the same tab value are shown together; items with no tab value appear in the default (un-tabbed) section. |

### Grouping fields into tabs

Setting a **Tab** value on account items splits the user edit page into labelled tabs. All items that share the same tab string are grouped under one tab. Items with an empty tab value always appear first, outside any tab group.

For example, to create a "Contact" tab containing Email, Phone, and Location:

1. Open your organization and scroll to **Account items**.
2. Set the **Tab** column to `Contact` for the Email, Phone, and Location rows.
3. Save. The user edit page will show a "Contact" tab containing those three fields.

### View rule and modify rule

- **View rule** — Who can see this field (e.g. email, phone).
- **Modify rule** — Who can edit this field.

This is separate from [Permissions](/docs/permission/overview), which control access to applications and resources; view/modify rules apply to individual profile fields.

### Steps

1. Navigate to **Organizations** in the Casdoor sidebar
2. Click on your organization to open the **Edit Organization** page
3. Scroll down to the **Account items** section

   ![account_customize.png](/img/organization/account_customize.png)

4. For each item you can:

   - **Set visibility** — Show or hide the field on the user home page.

   ![account_visible.png](/img/organization/account_visible.png)

   - **Set view and modify rules** — Who can view or edit the field.

   ![account_rule.png](/img/organization/account_rule.png)

### Rule options

- **Public** — Anyone can view or modify this field for any user.
- **Self** — Users can only view or modify their own value (matched by user ID, or by org + username if ID is missing).
- **Admin** — Only organization admins can view or modify this field.

### Example patterns

Here are some common configuration patterns:

| Field | View Rule | Modify Rule | Use Case |
|-------|-----------|-------------|----------|
| Name | Public | Self | Everyone can see names, but users can only change their own |
| Email | Self | Self | Users can only see and change their own email |
| Phone | Admin | Admin | Only admins can see and change phone numbers (for privacy) |
| Display name | Public | Self | Public profile name visible to all |
| Password | Self | Self | Users can only change their own password |

:::tip

Use **Admin** rules for sensitive fields like phone numbers, addresses, or internal identifiers that should only be managed by administrators.

:::

:::note

These field-level permissions work in conjunction with the broader [Permission system](/docs/permission/overview) in Casdoor. The Permission system controls access to applications and API resources, while View rule and Modify rule control access to specific user profile fields within the **Edit Organization** page configuration.

:::

## Account Table

Below are all the fields in the account item. For field descriptions, see [User](/docs/user/overview).

- `Organization`
- `ID`
- `Name`
- `Display name`
- `Avatar`
- `User type`
- `Password`
- `Email`
- `Phone`
- `Country code`
- `Country/Region`
- `Location`
- `Affiliation`
- `Title`
- `ID card type`
- `ID card`
- `Real name` - The user's verified real name (locked after ID verification)
- `ID verification` - Controls visibility and access to the verify identity button
- `Homepage`
- `Bio`
- `Tag`
- `Signup application`
- `Register type`
- `Register source`
- `Roles`
- `Permissions`
- `Groups`
- `3rd-party logins`
- `Properties`
- `Is admin`
- `Is forbidden`
- `Is deleted`
- `Multi-factor authentication`
- `WebAuthn credentials`
- `Managed accounts`
- `MFA accounts`
