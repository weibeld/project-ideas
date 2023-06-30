---
created: 2023-06-15T14:36:28+02:00
edited: 2023-06-15T14:36:28+02:00
name: Note Markdown Format
---

## Requirements

Define a note format in Markdown that satisfies the following criteria:

1. It can be properly displayed on GitHub (i.e. it conforms to the [GitHub Flavored Markdown Specification](https://github.github.com/gfm/).
1. Links between notes in the same repository can be handled by wiki.vim. This includes:
  1. Auto-completion of the target file name
  1. Following links
1. Each note contains the following metadata:
  1. Creation date: date and time the note was created (in ISO 8601 or RFC 3339 format)
  1. Modifcation date: date and time the note was last edited (in ISO 8601 or RFC 3339 format)
  1. Title
1. New notes can be created with dynamic initial content. This includes the creation and modification date that should be inserted automatically when creating a new note.
1. Whenever a note is saved, the modification date is updated to the current date and time.

The above criteria should be transparent, i.e. they are just enforced without the user having to take any specific actions.

Below are additional functions that have to be explicitly triggered (possibly as part of a pre-push hook or CI/CD) to support the efficient management of the notes:

1. Adapt file name of a note to the title of the note:
  1. Convert the title of the note to kebab case (str2kebab)
  1. Compare converted title to the file name of the note (stripping the `.md` extension)
  1. If they match, do nothing
  1. If they don't match, do the following:
    1. Rename the file to match the converted title
    1. Update all links to this note throughout all other notes to match the new file name
1. Adapt link text of an internal note-link to the title of the target note
  - TODO: since GitHub Markdown supports only Markdown link (no wiki links), each link must contain a link text. There should be a process that goes through all links in all notes, checks whether the link text matches the title of the target note, and updates the link text if it does not.
  - This would allow typing links without a link text and then having them automatically filled in by an automatic process.
  - This has no side effects with the above "Adapt file name to title" function because both use the note title as the ground truth and the note title is never updated by an automated process
1. Detect notes that are not linked to by any other notes (orphans)
  - If an orphan is detected, show an error

The above functions are ideally executed across all the notes in the repository in a pre-push hook so that only a consistent state of the notes system is pushed to GitHub.

## Motivation

Notes are a special type of the data structures in the PKMS. They contain just three pieces of metadata (creation date, modification date, and title) and otherwise consist exclusively of text. Thus, notes don't need a sophisticated rendering engine, but they can be perfectly displayed on GitHub where they are anyway hosted. For that reason, the note format should be compatible with GitHub Markdown so that they can be properly displayed on GitHub.

Rendering on a dedicated platform (e.g. a static website) is still preferred, however, by making the note format compatible with GitHub Markdown, the notes already provide value before such a rendering system is implemented. Furthermore, smaller projects (e.g. work project notes) for which a dedicated rendering platform is not intended could then also be created with this format and then be "rendered" on GitHub, which is enough for this purpose.

Links are an essential part of the envisioned notes system as there is no metadata for orgnanisatino purposes, such as tags or hierarchies. Organisation and navigation through the notes happens exclusively through links. For that reason, there is a lot of emphasis on the efficient and consistent editing and maintenance of links.

## Tools

- For checking links with wiki.vim, see ':h wiki-graph-check-links'
