# A knowledge package worth publishing

A knowledge package is material the assistant consults: text files, and common document formats, that are indexed when the package is installed so a search returns passages. It is a repository of files plus a `cerase.json`; the manifest can point at a subfolder that holds the material. Take every field and limit from `authoring_rules`.

## Rules

- Include only material whose licence allows redistribution. A page being public does not make it redistributable. If the licence is unknown or forbids copying, do not include the text; write an original summary and cite the source, or leave it out.
- Keep a sources file. For each source give its title, its address and the date it was read, and its licence. The date lets a reader judge how old the material is.
- One topic per file, with a heading that names it. Split long documents so that a passage returned by a search stands on its own: it does not depend on a table, a paragraph above it or a pronoun that points outside it. State the subject in the passage instead of writing "this" or "the above".
- No personal data: no names of private individuals, contact details or records about identifiable people. Public figures cited for a public role are the only exception.
- Say how often the material needs refreshing, in the package description or the sources file: for example when the source publishes a new edition, or a number of months. Material that never goes stale says so.
- Keep to the topic in the description. Material outside the topic is a different package.
- Plain text or Markdown is the safest format. Prefer it to scans and images of text, which are not searched.

## Before validating

- Open three files at random and read one paragraph of each alone. If it is unclear what it is about, split or rewrite the file.
- Check every source has a title, address, read date and licence.
- Search the files for names, emails, phone numbers and internal paths.
