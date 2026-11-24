# A skill worth publishing

A skill is a procedure the assistant follows whenever a kind of request comes in. It is a `SKILL.md` with `name` and `description` in the frontmatter, and nothing else there, plus a `cerase.json`. Take every limit and format from `authoring_rules`.

## Rules

- The description is in the third person. It says what the skill does and when to load it, because the assistant reads the body only after the description has loaded the skill. A description that says only what the skill is called or what it is about loads it at the wrong times or never.
- The body holds steps. Explanation, background and history stay out of it. Reference material that a step needs only sometimes goes in a separate file under `references/`, named in the step that needs it, so it is read only then.
- Name only tools that exist, and check each name against the tool list of the connected server before writing it. If a step needs a tool that does not exist, say so to the person and leave the step out; never invent a call.
- A value that changes on each run (a date, a recipient, a record, an amount) is asked for or looked up when the skill runs, never stored in it. The skill carries no time and no day of the week; a schedule belongs to whatever starts the skill.
- Refer to the person as "the person", and to a system by its connection or connector, never by an account, address or name taken from the author's own setup.
- Every sentence passes this test: would it still be right if a colleague at another company installed the skill?
- A skill that writes through a connector names the tool and says where each value comes from, and leaves the form of each argument to the tool's own description.

## Shape

```
---
name: open-orders-summary
description: Summarises a supplier's open orders and lists the late ones. Use when the person asks where the orders of a supplier stand.
---

# Open orders summary

1. Ask which supplier, or read it from the request.
2. Read that supplier's open orders with the connector's list tool.
3. Group them by status and list the late ones.
4. Report the result as a short list.
```

## Before validating

- Read the description alone: does it tell an assistant when to load the skill and when not to?
- Count the jobs. If the steps branch into two unrelated outcomes, split the package.
- Search the text for names, addresses and paths that belong to the author.
