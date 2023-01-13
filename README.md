# PLN (Pipe Loves Nord)

## Overview
This is a personal theme I started creating for 0.16.

![Light Screenshot](PLN_Light.png)
![Dark Screenshot](PLN_Dark.png)

## Changes
### Basics
- Fonts are generally smaller
- Stacked titles are flipped 180 degrees, and more compact
- The active editor line and gutter lines are highlighted
- Many icons are removed, I use the command pallete more than a mouse. All removals can be controlled via [Style Settings](https://github.com/mgmeyers/obsidian-style-settings).
    - Sidebar icons are removed
    - Editor icons are removed
    - The statusbar is removed
    - Close icons are removed
    - Tab file icons are removed
- Scrollbars are hidden until hovered over
- A frameless mac window no longer has sidebar icons under the window buttons

### Embeds
- Embeds are stripped of all "indicators" and flow as written text
- H1-3 of embeds are hidden with options to hide all headers or no headers via [Style Settings](https://github.com/mgmeyers/obsidian-style-settings).

### Links
- Internal links are not underlined
- Unresolved links are not transparent, and appear like any other internal link
- External link icons are removed

### Dataview
- Styling is removed like embeds so they flow like written text. Edits can be toggled via [Style Settings](https://github.com/mgmeyers/obsidian-style-settings).
- Hide the item count on task lists

### Custom checkboxes
- Completed tasks are not crossed out
- I added various checkboxes that can be seen in the images. 
    ```
    - [ ] open
    - [x] complete
    - [!] important
    - [>] deferred
    - [?] question
    - [i] info
    - [-] canceled 
    - [/] partial
    ```
- Custom checkboxes can be queried for in DV:
    - Find all Important tasks
    ```js
    task from "PATH\PATH"
    WHERE !completed
    WHERE status = "!"
    GROUP by file.link
    ```

### Callouts
- Danger is a unique design now
- Callouts are condensed
- Idea has been added
- Links and Meta have been added, I use them for holding a DV backlinks query and my meta-data as opposed to native frontmatter or the backlinks pane.
    - Both of these callouts can be toggled to appear in Reading and PDF exports.

![links_meta.png](links_meta.png)

Query for Links callout
```js
TABLE without id file.inlinks AS "Links from", file.outlinks AS "Links to"
WHERE file.path = this.file.path
```

### Calendar plugin
- It has been condensed
- More colour

### Folders
- Folder colours are applied automatically, iterating over `n`

### Highlights and text colours
The original snippet came from soggymuse but it only worked in LP. I expanded it to work in Reading view and added many more forms to it.

```markdown
==Yellow==
<mark class='edit'>dfddrtrtrt</mark>
<mark class='unfinished'>I will be going to</mark>
<mark class='verify'>hippos are extinct</mark>
<mark class='important'>april 8th</mark>

<mark class='red'>Red Text</mark>
<mark class='blue'>Blue Text</mark>
<mark class='green'>Green Text</mark>
<mark class='purple'>Purple Text</mark>
<mark class='underline'>Underlined Text</mark>
<mark class='path'>C:\Users\Roo\Foo</mark>
<mark class='borders'>Bordered text</mark>
```

#### Bonus
If you use [Espanso](https://espanso.org/) the following form can be used to insert marks easily.

```yml
name: obsidian
parent: default
matches:
  - trigger: ";;mark"
    replace: "<mark class='{{form.type}}'>{{form.content}}</mark>"
    vars:
    - name: "form"
      type: form
      params:
        layout: "Mark type: {{type}} Content: {{content}}"
```

## FAQ
### Why remove things when [Kepano's Hider](https://github.com/kepano/obsidian-hider) exists?
I prefer having a minimal number of plugins, so if it can be done with CSS I will use CSS.

### How do you have columns?
I am using [Efemkay's MCL solutions](https://efemkay.github.io/obsidian-modular-css-layout/) which are more CSS snippets to avoid column plugins.
