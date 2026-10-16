# Ecom KV Skill v2.0

A Markdown skill for ecommerce product key visuals: confirm product facts, extract selling points, propose 2–3 directions, wait for approval, produce images or export prompts, and inspect the result.

[中文说明](README.md) · [English Skill](SKILL.en.md) · [Chinese Skill](SKILL.md) · [Original installation guide](INSTALL.md)

## Requirements

Use an AI assistant that can import skills or read local files. This package is not a standalone application and requires no Python, Node.js, or build command. Supply a clear product photograph, product name, price, and promotion details. Image production additionally requires image-editing capabilities or an external tool operated by the user.

The 20 original files are preserved. Only the main skill has an English translation; the knowledge library and platform documents remain in Chinese. See the [complete file index](README.md#文件导航).

## Installation

1. Download and extract the repository. Locate the directory containing `SKILL.md`, `knowledge/`, and `platforms/` together.
2. Copy the complete directory into your host's supported skill location and reload skills as required. The [original installation guide](INSTALL.md) records this version's platform conventions.
3. For ZIP import, archive the **contents** of that directory: `SKILL.md`, `knowledge/`, and `platforms/` must appear directly at the ZIP root. GitHub's **Code → Download ZIP** normally adds an outer repository folder; repackage its contents when necessary.
4. Explicitly set `Current platform: <actual host name>` in the host configuration or opening message.
5. Invoke `ecom-kv-designer`, or ask the assistant to read and follow the main skill with access to all referenced files.

For English, select `SKILL.en.md` if the host supports custom entry files. If it only recognizes `SKILL.md`, work in a **separate installation copy**: back up the Chinese entry as `SKILL.zh.md`, then copy `SKILL.en.md` to `SKILL.md`. Preserve the relative locations of `knowledge/` and `platforms/`. Both entries have the same skill name; avoid installing both as duplicate skills.

## First run

Attach an actual product photograph, replace the placeholders, and send:

```text
Current platform: <actual host name>
Use ecom-kv-designer to create an ecommerce product key visual.
Product name and category: <details>
Price and promotion: <details, or no promotion>
Target marketplace and placement: <details, or request suggestions>
Verified selling points: <details; mark uncertain claims for verification>
Brand colors, logo, and other constraints: <details, or none>
Confirm the Product Information Card first, then propose 2–3 directions.
Wait for my selection before producing images.
```

Expect a Product Information Card followed by proposals. After approval, follow the selected platform profile. Without image-editing capabilities, export bilingual prompts and typesetting instructions, then inspect the images returned by the user. Prompt export alone is not a finished image.

This version's [general CLI profile](platforms/agent-cli.md) specifies prompt export. Other profiles describe the supplied version's conventions; current host features, installation paths, quotas, and import mechanisms have not been independently verified for this publication.

## Smoke checks

- Ask the assistant to restate P1–P10 and identify the platform document it loaded.
- Request an image without product details: it should collect information instead of inventing a product.
- Supply the test phrase `全网最低`: it should apply the package's prohibited-word rules and rewrite it.
- Provide real product information: it should wait for proposal approval before production.
- Inspect the product, logos, text, and symbols; require the [self-check report](knowledge/07-self-check-list.md). Unchecked items must not be reported as a full 24/24 pass.

## Package boundaries

Backticked `knowledge/...` and `platforms/...` references resolve from the **skill root**, including when mentioned inside nested documents. Use the [file index](README.md#文件导航) for clickable GitHub navigation.

The Qwen font references mention `symbol_sweep.py`, but that retesting utility is absent from the supplied final directory. It is not needed for normal skill execution; obtain it separately for font retesting. The `platforms/_template.md` mentioned in `INSTALL.md` is a development template explicitly excluded from distribution.

No WorkBuddy `.codebuddy-plugin/plugin.json` manifest is supplied; this is a skill package, not a complete plugin project. Host directory examples and placeholder paths are not bundled files. Sibling test outputs, course slides, and test product assets are outside this package.

Publication adds usage documentation while preserving the finalized skill instructions. File and link accessibility checks do not establish successful execution on every host.
