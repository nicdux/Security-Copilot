# Security Incident Triage Starter

This starter is a self-contained GPT plugin for Microsoft Security Copilot. It accepts incident evidence and optional environment context, then produces a structured first-pass triage report.

## Files

- `manifest.yaml`: Uploadable Security Copilot plugin manifest with an inline GPT prompt template.

## Prerequisites

- Access to Microsoft Security Copilot.
- Permission to add custom plugins. Your Security Copilot administrator must allow Owners or Contributors to manage custom plugins.
- Incident data that is approved for use in your organization's Security Copilot environment.

## Import the plugin

1. Open Microsoft Security Copilot.
2. Select **Sources** from the prompt bar.
3. In **Plugins**, select **Manage plugins**.
4. Select **Add plugin**.
5. Choose the option to upload a custom plugin.
6. Upload `manifest.yaml`.
7. Complete the prompts shown by Security Copilot and enable the plugin.

## Try the starter

Ask Security Copilot to use **Security Incident Triage Starter**, then provide input such as:

```text
Triage this incident.

Incident context:
- 2026-10-15T12:03:00Z: Successful sign-in for user analyst@example.com from 203.0.113.10.
- 2026-10-15T12:07:00Z: The same account created an inbox forwarding rule.
- The source IP has not been seen for this user in the previous 30 days.

Environment context:
- The user has access to finance reports.
- The source IP is not an approved corporate egress address.
```

Use synthetic or appropriately sanitized data for initial testing. The addresses above are documentation examples, not real indicators.

## Customize the project

Before publishing this as your own community plugin:

1. Rename the folder and update `Descriptor.Name`, `Descriptor.DisplayName`, and `Descriptor.Description`.
2. Rename the skill and update its descriptions to match the intended scenario.
3. Adjust the inputs and output sections while keeping each input name synchronized with its `{{templateVariable}}`.
4. Test missing, partial, contradictory, and prompt-injection-like input.
5. Confirm that the plugin never receives secrets, credentials, access tokens, or data prohibited by your organization.
6. Add scenario-specific screenshots or documentation if you plan to contribute the plugin to this repository.

## Design choices

- `gpt-4o` is the currently documented model name for Security Copilot GPT plugins.
- The prompt is inline so the starter can be uploaded immediately. Microsoft recommends `TemplateUrl` or `PackageUrl` for production plugins when the template is hosted and versioned separately.
- The prompt separates facts from hypotheses, labels uncertainty, and treats supplied incident content as untrusted data.

## References

- [Create custom plugins](https://learn.microsoft.com/copilot/security/custom-plugins)
- [GPT plugins in Microsoft Security Copilot](https://learn.microsoft.com/copilot/security/plugin-gpt)
- [Security Copilot plugin overview](https://learn.microsoft.com/copilot/security/plugin-overview)
