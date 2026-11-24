# A connector worth publishing

A connector gives the assistant access to another system's data or actions through an MCP server. Its manifest declares how it is reached, how a person signs in and what each tool does. Take field names, formats and limits from `authoring_rules`; this page says what to decide and what to check.

## Prefer the vendor's own server

If the vendor hosts an MCP server, point the connector at it instead of writing and running one, and say in the entry that the server is the vendor's. A vendor's server stays current with the vendor's API and needs no runner. Write a server of your own only when the vendor has none, and then it reads and writes only what its tools declare.

## Choose the simplest sign-in for the person

Decide in this order:
1. OAuth with dynamic registration, when the vendor's authorization server advertises a registration endpoint. Read `/.well-known/oauth-authorization-server` on the vendor's authorization host and look for it. Nobody creates an app or pastes a key.
2. OAuth with an app, when the server supports OAuth but has no registration endpoint.
3. The person's own key, only when the vendor offers nothing else, with the narrowest permissions the tools need. Say in the entry which permissions to give it.

## Read the tools from the live server

Use a real test account on the vendor's server and read its `tools/list`. Declare from that list, never from the vendor's documentation or from memory. Re-read the list when the vendor releases a version.

For each tool, declare its side effect, which decides when the assistant may call it:
- **Reads** change nothing and run at every autonomy level that allows reads.
- **Writes** create or change something and follow the assistant's autonomy level, so a person who set the assistant to ask first is asked first.
- **Asks every time**: a tool that deletes, does anything else that cannot be undone, spends money, or runs arbitrary code or queries as the person. It asks approval at every autonomy level. Sending a message or publishing a post is a write: it follows the autonomy level.

Do not trust the server's own read-only or destructive hints; classify each tool by what it does. A tool that a later version adds and that you did not classify follows the hints, so check new versions.

Withhold a tool that sends the conversation to the vendor unprompted, and a tool that manages the server instead of the service. The assistant is given neither.

For each tool that asks approval, write what the person reads when asked: what the assistant wants to do, what approving does and what it did afterwards, in plain words for a non-technical reader, and a plain label for each argument the person approves. "Deletes the contact permanently" is a sentence a person can decide on; "executes delete_contact" is not.

## Do not

- Put a credential, token or key in any file, example or log.
- Add a warning about the vendor's terms of service or the platforms the tools act on.
- Name your own company, account or test data in the entry.

## Before validating

- Every tool in the live `tools/list` has a declared class, or is covered by a stated default.
- Every tool that asks approval has its sentences.
- The sign-in is the first option from the list that the vendor supports.
- A test with the test account ran at least one read and one write through the declared sign-in.
