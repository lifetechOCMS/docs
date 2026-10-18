# LifeTechOCMS Documentation Conventions

Use these conventions when creating or updating LifeTechOCMS documentation. They keep the guides consistent, easy to navigate and straightforward to extend as new topics are added.

## On this page

- [Repository organisation](#repository-organisation)
- [Filenames and lesson order](#filenames-and-lesson-order)
- [Page structure](#page-structure)
- [Navigation](#navigation)
- [Beginner friendly writing](#beginner-friendly-writing)
- [Code examples and technical accuracy](#code-examples-and-technical-accuracy)
- [Links tables and images](#links-tables-and-images)
- [Adding or changing a lesson](#adding-or-changing-a-lesson)
- [Complete guides and Word documents](#complete-guides-and-word-documents)
- [Website hierarchy and guide organisation](#website-hierarchy-and-guide-organisation)
- [Stable topic identifiers](#stable-topic-identifiers)
- [Tutorials and reference pages](#tutorials-and-reference-pages)
- [Version applicability and review information](#version-applicability-and-review-information)
- [Website and file synchronisation](#website-and-file-synchronisation)
- [Validation and migration](#validation-and-migration)
- [Reusable lesson template](#reusable-lesson-template)
- [Review checklist](#review-checklist)

## Repository organisation

The repository has a main contents page and guide contents pages. Additional nested contents pages are allowed when a subject needs several lesson groups:

1. The main `README.md` lists documentation areas, such as Getting Started, Theme Development and Module Development.
2. Each guide has its own folder and a `README.md` listing its lessons in learning order.
3. A larger area can contain nested guide folders, each with its own README. Every lesson belongs to one clearly defined learning sequence.

Example paths:

| Path | Purpose |
| --- | --- |
| README.md | Main documentation contents |
| getting-started/README.md | Getting Started contents |
| getting-started/installation-process.md | An individual lesson |
| theme-dev/README.md | Theme Development contents |
| theme-dev/accessing-themes-development.md | An individual lesson |
| theme-dev/add-theme-package.md | An individual lesson |
| module-dev/README.md | Module Development contents |

These folder names illustrate the structure. Preserve established repository folder names unless a rename is part of the requested update.

## Filenames and lesson order

- Use descriptive lowercase filenames with words separated by hyphens.
- Do not add number prefixes to lesson filenames.
- Use the `.md` extension.
- Use `README.md` consistently for contents pages. Match actual filename capitalization in every link.
- Keep filenames stable where possible so shared URLs continue to work.

Examples:

```text
accessing-themes-development.md
add-theme-package.md
understand-the-default-layout-and-custom-layouts.md
```

The folder's README and the Previous/Next links determine lesson order. The README can display a numbered list even though filenames have no numbers.

Adding a lesson in the middle must not require renaming every later file.

**Lesson order belongs in the contents page and navigation, not in filenames.**

## Page structure

Each lesson covers one main topic.

| Markdown | Use |
| --- | --- |
| # Page title | One main title per lesson |
| ## Subtopic | Main sections within the lesson |
| ### Further explanation | Detail within a subtopic |

For longer lessons, include an **On this page** list with links to the subheadings. Keep headings descriptive and avoid numbering that would require widespread changes when inserting new sections.

Start with a short introduction explaining what the reader will learn. Develop the explanation with steps and examples, and state the expected result where useful.

## Navigation

Every lesson has four navigation positions at both the top and bottom:

**Previous · Main documentation · Guide contents · Next**

| Position | Destination |
| --- | --- |
| Previous | Previous lesson in the current learning sequence |
| Main documentation | Repository's main README |
| Guide contents | README controlling the current lesson sequence |
| Next | Next lesson in the current learning sequence |

For a lesson directly inside `theme-dev/`, use:

```markdown
[Previous](theme-development-overview.md) · [Main documentation](../README.md) · [Theme contents](README.md) · [Next](add-theme-package.md)
```

Use a guide-specific label such as Theme contents, Module contents or Getting Started contents. In the usual structure this points to the current folder's README. For a nested lesson, it points to the explicitly selected guide index.

On the first lesson, Previous is plain text:

```markdown
Previous · [Main documentation](../README.md) · [Theme contents](README.md) · [Next](accessing-themes-development.md)
```

On the last lesson, Next is plain text:

```markdown
[Previous](troubleshooting-and-development-checklist.md) · [Main documentation](../README.md) · [Theme contents](README.md) · Next
```

A guide with only one lesson uses plain text for both Previous and Next. Keep all four positions without creating broken or circular links.

Use relative links within the repository. Calculate `../` depth from the actual file location; do not copy a one-level path into a deeper folder. Each guide README should link to the main documentation and, where relevant, its parent category index.

For example, a lesson at backend-tutorial/pages/edit-page.md reaches the root README with ../../README.md and its own guide contents with README.md.

## Beginner friendly writing

Explain:

1. What the concept or feature means.
2. Why a developer needs it.
3. How to use it, in the correct order.
4. What the developer should expect afterwards.

Define unfamiliar keywords, folders and fields when first introduced. Use small practical examples before more complex examples. Explain what code does instead of assuming the reader already understands it.

Use consistent example package and content names throughout a guide. Distinguish creating a new package from installing an existing package, publishing it and setting it as default.

## Code examples and technical accuracy

- Label fenced code blocks with their language: `php`, `html`, `css`, `javascript`, `json`, `bash` or `text`.
- Keep code readable and indented.
- Preserve exact function names, filenames, paths, field names, endpoints and capitalization.
- Distinguish compulsory platform instructions from optional HTML wrappers, CSS classes and teaching examples.
- State dependencies and prerequisites when an example needs another package or backend endpoint.
- Do not invent buttons, API endpoints, processing triggers or platform behaviour.
- Identify version-dependent behaviour when relevant. If behaviour is unconfirmed, say so rather than presenting it as a requirement.

Documentation filename conventions do not change theme package conventions. For example, the documentation file can be `add-theme-package.md` while the example package remains `ThemeStarter` and its content remains `Home.html`.

## Links tables and images

- Use relative links for lessons, contents pages and other files in the repository.
- Use heading anchors for links to a particular section.
- Use complete HTTPS URLs for external resources.
- Use tables for comparable fields, file purposes, options or expected results.
- Give images descriptive alternative text and useful captions.
- Keep essential instructions in text so a reader does not need to interpret a screenshot to complete a task.

Check link targets and heading anchors after editing. A renamed heading can break an anchor link even when its file has not moved.

## Adding or changing a lesson

When adding a lesson between two existing lessons:

1. Create the new file with a descriptive filename and no number prefix.
2. Add its link in the correct place in the folder's README.
3. Set the new lesson's Previous and Next links.
4. Update the preceding lesson's Next link.
5. Update the following lesson's Previous link.
6. Confirm Main documentation and Guide contents links at the top and bottom.
7. Update related cross-references and any complete-guide edition.

When renaming or moving a file, update all links that point to it. When migrating existing numbered filenames, update the contents pages, lesson navigation and cross-references together.

## Complete guides and Word documents

Individual lesson files are the main content source. When a complete Markdown guide or MS Word document is requested, assemble it from the same lesson content in the README's learning order.

Keep explanations, examples and technical rules consistent across formats. Adapt navigation for the format: a complete guide can use internal section links, while Word can use document headings and hyperlinks.

Do not maintain separate conflicting explanations in the split lessons, complete Markdown guide and Word document.

## Website hierarchy and guide organisation

Group the main README under the same major areas as the LifeTechOCMS website. The following mapping guides organisation; it does not require renaming established repository folders.

| Website area | Markdown organisation |
| --- | --- |
| Get Started | Getting Started guide and its lesson index |
| Backend Tutorial | Administration guides for site information, roles, content, menus, pages, users and files |
| Backend Development | Links to development guides such as Theme Development and Module Development |
| Functions and Classes | Central references for helpers, classes and their methods |
| Request and Respond Management | Request and response documentation |

The main README can group links under headings without creating an extra physical folder for every heading. For example, Theme Development and Module Development can remain in their existing folders while both appear under Backend Development in the main index.

A category README introduces its area and lists its guides. A guide README defines its lesson sequence. Avoid empty index pages that add navigation depth without helping readers.

## Stable topic identifiers

Each topic has a stable identifier independent of its position in the lesson sequence. Prefer the same identifier for its Markdown filename stem and website target:

| Representation | Example |
| --- | --- |
| Topic identifier | add-theme-package |
| Markdown filename | add-theme-package.md |
| Website section | https://www.lifetech.host/hubs/Docs#add-theme-package |

Use lowercase letters, numbers where meaningful, and hyphens between words. Do not include sequence numbers, spaces, commas, parentheses, slashes or ampersands in new identifiers.

Keep website topic targets unique across the documentation page, including parent and child records. Similar titles in different areas may need qualified identifiers, such as theme-installation and module-installation.

Subheading anchors inside a Markdown lesson are local to that file. Topic identifiers identify pages or website sections; they are not interchangeable with every subsection anchor.

Keep ordering in README lists and website sortOrder values. Inserting a lesson changes the sequence, not the stable identifier. If the title changes but the subject remains the same, retain the filename and website target where practical.

For existing identifiers, plan a migration rather than silently breaking published links. Update repository references and preserve old website targets through aliases or redirects where supported. GitHub file URLs do not automatically redirect merely because documentation mentions an old filename; record old-to-new paths and provide a temporary forwarding page when needed.

## Tutorials and reference pages

Tutorials teach a task in a useful learning order. Reference pages describe exact functions, classes, methods, parameters, return values and supported behaviour.

A tutorial should provide enough explanation to complete its example and link to the central reference for further detail. Keep shared technical rules in agreement with that reference rather than maintaining conflicting copies.

For example, the Theme Development menu lesson demonstrates navigation in a theme. The central menu reference explains the supported API or PHP interface. Cross-link them without forcing beginners to read the entire reference before completing a basic example.

## Version applicability and review information

Record version applicability when instructions depend on a particular core release. State a confirmed version or range only when verified. If a feature requires an update but the minimum version is not confirmed, say that explicitly.

Distinguish the LifeTechOCMS core version, an example package version, and a documentation revision. They are separate values.

Where useful, place simple metadata below the introduction:

```text
Topic identifier: understand-the-default-layout-and-custom-layouts
Applies to: Core versions supporting automatic Default.html selection; minimum version to be confirmed
Last reviewed: YYYY-MM-DD
```

Replace placeholders before publication. Update the review date only after checking the content. A website version selector does not by itself establish compatibility for every lesson returned under that version.

## Website and file synchronisation

The LifeTechOCMS website is the published platform documentation reference. Keep approved Markdown lessons and website topics aligned in meaning, examples and technical rules.

For the current manual workflow:

1. Identify the approved change and the topic it affects.
2. Update the relevant website topic and Markdown lesson together.
3. Update titles, indexes, navigation and cross-references where affected.
4. Check identifiers and ordering in both representations.
5. Regenerate complete Markdown and Word editions when requested, marking an older edition as outdated if it is retained.

Use the approved lesson content as the assembly source for downloadable complete guides. Do not independently rewrite technical rules for each output format.

A future shared-source publishing process may generate the website, split Markdown, complete guide and Word output from one source. This is a proposed improvement, not a claim that automatic synchronisation already exists. Choose and document the authoritative editing source before implementing it.

## Validation and migration

Before publishing a documentation change, verify:

- Topic filenames have no learning-order prefixes.
- Website topic identifiers are unique and follow the agreed format for new topics.
- README learning order matches the intended Previous and Next sequence.
- Local file links resolve with exact filename capitalization.
- Heading anchors exist and repeated headings use the renderer's actual anchor names.
- Both navigation bars match and have four positions.
- Main documentation points to the root README at the correct relative depth.
- Guide contents points to the README controlling the lesson's sequence.
- First and last lessons have plain text at unavailable navigation positions.
- Code fences are balanced and their language labels are appropriate.
- Relevant website and downloadable editions agree.

These checks should be automated as the documentation build grows. Review technical accuracy separately; passing link checks does not prove runtime examples work.

For migration from numbered filenames, prepare an old-to-new filename map, rename files and update every reference together. Check existing shared links and provide forwarding pages or documented replacements where practical. Do not publish a mixture of old and new navigation paths accidentally.

## Reusable lesson template

Replace the example names and links to match the lesson and its neighbours. The template assumes the lesson is directly inside a topic folder.

````markdown
# Lesson title

[Previous](previous-topic.md) · [Main documentation](../README.md) · [Theme contents](README.md) · [Next](next-topic.md)

Explain what the reader will learn and any prerequisites.

## On this page

- [Understand the concept](#understand-the-concept)
- [Follow the steps](#follow-the-steps)
- [Example](#example)
- [Expected result](#expected-result)

## Understand the concept

Explain the feature, relevant keywords and why it is useful.

## Follow the steps

1. Describe the first documented action.
2. Explain the required fields or choices.
3. Describe how to check the result.

## Example

```php
<?php ltImport('ThemeStarter', 'Header.html'); ?>
```

Explain the example and distinguish required syntax from example values.

## Expected result

Describe what the reader should see or have completed.

[Previous](previous-topic.md) · [Main documentation](../README.md) · [Theme contents](README.md) · [Next](next-topic.md)
````

## Review checklist

- [ ] Main README lists the relevant documentation area.
- [ ] Topic folder has its own README with lessons in learning order.
- [ ] Lesson filenames are descriptive, lowercase and have no number prefixes.
- [ ] Each lesson has one main title and clear subheadings.
- [ ] Longer lessons include working On this page links.
- [ ] Four navigation positions appear at both the top and bottom.
- [ ] First and last lesson boundaries use plain text where appropriate.
- [ ] Relative paths and filename capitalization are correct.
- [ ] Code fences have appropriate language labels and readable indentation.
- [ ] Requirements, optional examples and dependencies are clearly explained.
- [ ] New or renamed lessons have updated neighbouring navigation and cross-references.
- [ ] Topic identifiers are stable and unique on the website.
- [ ] Main README grouping matches the website hierarchy.
- [ ] Tutorials link to shared function and class references where appropriate.
- [ ] Version applicability is verified or its uncertainty is stated.
- [ ] Approved website and Markdown updates have been synchronised.
- [ ] Migration links and old-to-new paths have been considered.
- [ ] Complete Markdown and Word editions match the lesson content when produced.
