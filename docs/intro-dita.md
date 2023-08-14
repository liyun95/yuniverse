# Introduction to DITA

A markup language is a way of tagging content in a plain text file. The markup language you might be most familiar with is HTML, which is the fundamental markup language for the world wide web.

DITA stands for Darwin Information Typing Architecture, which is an open standard originally created by IBM. IBM donated DITA to the Organization for the Advancement of Structured Information Standards (OASIS) in 2005.

DITA is an XML-based, tool-independent way to create, organize, and manage content. DITA is built on:

- Topic-based authoring
- Separating content from formatting
- Minimalism
- Structured authoring concepts

DITA is built based on the XML markup language. They both use angle brackets (< and >) to identify markup tags. In both languages, a forward slash identifies a close tag (`</title>`).

In HTML and XML, the tags can also have attributes (in the form attribute="value") that provide further info about the tag.

```xml
<note type="warning">Keep your arms and legs inside the vehicle at all times.</note>
```

There are two main differences between HTML and XML:

- HTML can be quite forgiving when you forget to close tags or put quotation marks around attribute values; XML is strict in requiring them.
- HTML uses a predefined set of tags (`<body>`, `<p>`, `<span>`, and so on). In XML, the tags are defined in a separate file and can be changed and added to by an information architect.

DITA uses this tag naming feature in XML to define its own set of tag names or “elements”. The DITA elements allow you to mark up content using names for things that make sense, such as `<note>` for notes, `<section>` for sections, `<image>` for images, and so on. However, because many HTML tag names make sense, their names are also used for DITA elements, such as `<p>` for paragraph, and `<ul>` and `<ol>` for unordered and ordered lists.

One other difference in naming: in HTML, the outer-most or “root” tag is `<html>`. In DITA, the name of the root tag depends on the type of topic you’re creating, such as `<concept>`, `<task>`, or `<reference>` (among others).

## Topics

A DITA topic is a building block of content, the basic unit of authoring and reuse.

In topic-based authoring, you create a number of individual topics, each of which addresses a single idea or answers a single question. These topics can then be used and reused in any order, in a number of different documents. In DITA, the topics are organized in *maps*, which are much like a table of contents; the map allows you to specify the order and the hierachy of the topics.

To make your topics reusable:

- A topic should address a single idea or answer a single question.
- A topic should contain enough info to stand on its own.
- A topic should not assume any context. You should not make assumptions about what comes before or after the topic.
- A single file should contain a single topic.

All DITA topics must have **at least a title element** and an **id attribute** for the root topic. The following is a valid DITA topic:

```xml
<topic id="sample">
    <title>Topic title goes here</tile>
</topic>
```

### Generic topics

All DITA topic types are based on a single generic topic type. The generic topic type is used as the basis to create the specific topic types. All topic types have this general structure:

```xml
<topic id="sample">

   <title>Topic title goes here</title>

   <shortdesc>A short description</shortdesc>

   <body>

        (Most of the elements go here.)

   </body>

</topic> 
```

- `<title>` is the only required element in a topic.
- `<body>` contains the bulk of info in the topic. In the specific topic types the body element has a related name, such as `<conbody>` for concepts and `<taskbody>` for tasks.

### Concept topics

A concept topic answers the question **“Why?”** It provides background information about a subject that the reader needs to know.

Concepts usually contain paragraphs of text and lists, but also include notes, tables, and graphics needed to understand the ideas behind a particular subject.

Common elements used in a concept topic include:

- `<conbody>` (the body of the concept topic)
- `<p>` (a paragraph)
- `<ul>` (an unordered or bulleted list)
- `<ol>` (an ordered or numbered list)
- `<li>` (a list item inside a `<ul>` or `<ol>`)
- `<fig>` (a figure, including an optional title)
- `<image>` (a graphic inside a figure, or inline in text)
- `<section>` (a subdivision in the topic, with an optional title)

### Task topics

A task topic answers the question **"How do I?"** It includes step-by-step instructions to complete a procedure. DITA also allows step results, graphics, notes, and one level of substeps.

Technical content is often heavy on tasks. DITA provides two task types:

- **Strict task**: requires all elements to appear in a specific order, only allows one `<example>` element, and has two very formal elements for steps (`<steps>` or `<steps-unordered>`).
- **General task**: also known as **loose task**, allows more flexibility in the order of the elements, allows multiple `<example>` elements, and allows a `<step-informal>` element for the steps, which can contain much more varied content.

Strict tasks are appropriate for items that require step-by-step instructions; general tasks are useful for process overviews.

Common elements used in a strict task topic include:

- `<taskbody>` (the body of the task topic)
- `<steps>` (the sequence of actions)
- `<step>` (each individual action)
  - `<cmd>` (the action the user takes; this is a required element in a `<step>`)
  - `<info>` (additional info about the step)
  - `<stepresult>` (what happens after performing an action)
  - `<stepxmp>` (an example of how to do the step)
- `<example>` (an example of how to do the entire task)

### Reference topics

A reference topic answers th question of **"What is it?"** A reference topic typically contains descriptive facts, such as the syntax of a command or API function call.

Reference topics do not include steps or background info. Reference topics are similar to dictionary entries and provide facts only.

Common elements used in a reference topic include:

- `<refbody>` (the body of the reference topic)
- `<section>` (a subdivision in the reference topic, with an optional title)
- `<table>` (a table)
- `<fig>` (a figure, including an optional title)
- `<properties>` (a list of properties)
- `<refsyn>` (a syntax diagram)

### Glossary topics

A glossary entry topic answers the question **"What does this word or phrase mean?"** Glossary topics typically contain one term, along with one or more definitions.

Common elements used in the glossary topic are:

- `<glossentry>` (the glossary entry topic type)
- `<glossterm>` (the word or phrase)
- `<glossdef>` (the definition of the glossary term)

## Metadata

Metadata means "beyond data" or data about data. In XML, metadata lets you classify and manipulate info. In DITA, you can assign metadata to topics, individual elements, and more.

You can assign metadata to DITA content in several different locations:

- At the topic level
- At the element level
- At the map file level (a map file lets you collect multiple topics to create a document, help system, and so on)

At the topic level, DITA provides a `<prolog>` element in which you can store metadata for the entire topic. Here is an example of basic topic metadata:

```xml
<topic id="xyz">

  <title>Metadata example</title>

  <prolog>

    <author>Sarah O’Keefe, Scriptorium</author>

    <critdates>

      <created date="2015-05-01"/>

    </critdates>

  </prolog>

  <body>

    <p>Body content goes here</p>

  </body>

</topic>
```

!!! note

    Use the `<prolog>` metadata only for system information, such as the author and created/revised dataes.