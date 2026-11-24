---
name: package-authoring
description: "Guides a person through writing a package for the Cerase Marketplace: a skill, a knowledge package or a connector. Load it when the person wants to publish, submit or update a package, or asks how to make a skill, a knowledge package or a connector that others can install. It searches the Marketplace first, chooses the type, follows the Marketplace rules, validates the files and submits a private draft only when asked."
---
# Package authoring

This skill takes a person from an idea to a package on the Cerase Marketplace: a skill, a knowledge package, a connector or a template. It works in any client that has the Marketplace's MCP server connected.

## Before anything else: the Marketplace tools

The procedure needs these tools from the Marketplace's MCP server: `search_packages`, `get_package`, `authoring_rules`, `validate_package`, and, for submitting, `submit_package` and `update_package`. If they are not in your tool list, stop and tell the person to connect the server at `https://marketplace.cerase.ai/mcp`: in Claude Code, `claude mcp add --transport http cerase-marketplace https://marketplace.cerase.ai/mcp`; on a Cerase box, an administrator adds it as a connector. Write nothing that depends on the tools until they are connected.

`search_packages`, `get_package`, `authoring_rules` and `validate_package` need no key. `submit_package` and `update_package` need a publisher key of the person's organization; if the person has none, say that the package can be written and validated now, and submitted once someone in the organization mints a key in its Marketplace panel.

## Procedure

1. **Search first.** Call `search_packages` with the vendor, the task and synonyms of both. If a package already does the job, show it with `get_package` and propose improving it instead of writing a second one. If it belongs to the person's organization, the change goes through `update_package`. If it belongs to another publisher, tell the person it is not theirs to change and stop, unless what they want is clearly a different package.
2. **Choose the type** from what the package holds, and say the choice and the reason in one line:
   - steps the assistant follows: a skill, see `references/skill.md`;
   - material the assistant consults: a knowledge package, see `references/knowledge.md`;
   - access to another system's data or actions: a connector, see `references/connector.md`;
   - a starting file or layout: a template.
   Read only the reference for the chosen type. If the idea mixes two types, write it as two packages.
3. **Read `authoring_rules`** for that type and follow it for every field. The rules the server gives are the limits; this skill does not repeat them, and when this skill and the server differ, the server is right.
4. **Write the files**, following the reference for the type and the rules below.
5. **Run `validate_package`** on the result and fix every refusal it returns, then run it again. Repeat until it returns none. Never submit a package that has a refusal.
6. **Submit only when the person asks**, with `submit_package`. Say before the call that a submission always lands private, and that the organization makes it public from its Marketplace panel. After it, report what the server answered.

## Rules for every package

- A stranger can install it. It names no client, person, account, mailbox, address, internal path or other project. For each string, ask whether it would still make sense if a stranger installed it in their own company. Use invented subjects in examples, such as a bakery or a tool called "Acme Tasks".
- It is written in English, so that publishers and installers in any country can read it, in plain declarative sentences, without slogans or motivational framing.
- One package does one job. A second job is a second package.
- It holds no credential, token, key or password, in any file or example.
- Its text covers what the package does and what it needs to work. A vendor's terms of service, and the rules of the platforms a connector acts on, are agreed between the customer and the vendor when the customer connects an account, and the package leaves them to that agreement.

## When something is missing

- No tool of the server answers, or `authoring_rules` has no entry for the type: tell the person what failed and stop. Do not write a package from memory of the rules.
- The person's idea fits no type: say so and ask what the assistant should do with the package, instead of picking one.
- A fact the package needs, such as a licence, a source address or the vendor's server address, is not known: ask for it. Do not invent it.
