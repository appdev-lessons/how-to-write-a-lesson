# How to write a lesson in learn.firstdraft.com

## Create the lesson

Sign in and visit the author lesson index, [learn.firstdraft.com/authors/lessons](https://learn.firstdraft.com/authors/lessons), and click "New lesson". You can either fill in a "title" and "content" directly in the markdown GUI interface, or "Connect GitHub" to add the URL of a lesson on GitHub in our pre-defined format, which is detailed below.

### Connect a lesson via GitHub

The [appdev-lessons GitHub organization](https://github.com/appdev-lessons) contains all GitHub-connected lessons on Learn. A template lesson (`appdev-lessons/learn-lesson-template`) is pinned in that repository, which can be used to generate a new lesson. The new lesson "owner" _must_ be the `appdev-lessons` organization:

[Create a new repository from the appdev-lessons/learn-lesson-template repo](https://github.com/new?template_name=learn-lesson-template&template_owner=appdev-lessons)

The following details the lesson repository files and how to use each. **Do not rename these files**:

<div class="bleed-full" markdown="1">

| File | Purpose | Usage  | 
|-----------------|-------------|---------------|
| `assets/` | Folder containing images, gifs, etc. that should be rendered in the lesson | Place all asset files in this folder and reference them within `content.md` with the syntax `![](local-path-to-assets/my-image.png)` |
|-----------------+--------------+-----------------|
| `.gitignore` | Ignore any local files in the folder (i.e. do not commit these to the repo) | The template ignores a few common files that should not be included in the commit history. More can be added if required. |
|-----------------+--------------+-----------------|
| `README.md` | General repo information  | Replace the first heading with the name of the repo and replace the URL with that of the learn lesson after connecting the lesson with Learn |
|-----------------+--------------+-----------------|
| `content.md` | Contains the lesson "title" and "content" | The file should begin with a level one (`<h1>`) markdown heading `# My Title`, which will be parsed to form the lesson title on Learn. Everything after this first `#` line will be parsed into the lesson content. All `assets/` will be rendered from their raw GitHub URL when opened on Learn: `![](https://raw.githubusercontent.com/appdev-lessons/REPO/BRANCH/assets/example-image.png)` |

</div>

When a URL like `https://github.com/appdev-lessons/how-to-write-a-lesson` is input on Learn in the "Connect GitHub" tab of a lesson, the `content.md` file on the `main` branch is parsed and the lesson receives a Learn URL that contains a unique ID followed by the repo name, which provides a handy reference in the browser for what the lesson contains and the GitHub repo the raw lesson can be found at, e.g. 

[learn.firstdraft.com/lessons/3-**how-to-write-a-lesson**](https://learn.firstdraft.com/lessons/3-how-to-write-a-lesson)

We recommend adding that URL to the `README.md` file in the repo to keep track of the connection.

### Updates

Once the Learn lesson is connected with a GitHub repo, any updates made to the lesson repo `content.md` file at e.g. `https://github.com/appdev-lessons/how-to-write-a-lesson` via commits and pushes will cause the lesson on Learn to **automatically update** with those changes.

### Branches and pull requests

Any branch made on a Learn-connected GitHub repo will automatically generate a new, independent lesson on Learn. For example, for this lesson, this URL was generated:

[https://learn.firstdraft.com/lessons/246-how-to-write-a-lesson](https://learn.firstdraft.com/lessons/246-how-to-write-a-lesson)

during a re-write on this branch:

[https://github.com/appdev-lessons/how-to-write-a-lesson/tree/bp-rewrite](https://github.com/appdev-lessons/how-to-write-a-lesson/tree/bp-rewrite)

This new lesson can be used to view changes to the rendered lesson as edits are made to the `content.md` file. Access to lesson branches is not available from the `authors/lessons` lessons index on Learn; rather, the branch can be found by navigating to the `main` lesson on the index page, and then finding the UI button for "Other branches", which brings the author to a `/branches` page e.g.

[https://learn.firstdraft.com/lessons/3-how-to-write-a-lesson/branches](https://learn.firstdraft.com/lessons/3-how-to-write-a-lesson/branches)

Just as with the `main` lesson, any commits and pushes made on the development branch will automatically update the Learn lesson.

When working on a lesson, a pull request can be opened for the new branch and the reviewer can view the changes to the lesson, e.g.

[https://github.com/appdev-lessons/how-to-write-a-lesson/pull/1](https://github.com/appdev-lessons/how-to-write-a-lesson/pull/1)

When the lesson is eventually merged to `main` the `authors/lessons` primary lesson will automatically update with the changes and the author can optionally delete the lesson that was automatically generated from the feature branch.

### In-line editing of the lesson on Learn

Currently, when a lesson is connected to a GitHub repo, the author loses the ability to edit the lesson in-line with the markdown GUI on Learn. We are working to re-implement this feature for quick edits on e.g. typos. Stay tuned.

## Write the lesson

The next sections cover how to write a lesson via the in-line editor or in the `content.md` file for a GitHub-connected lesson. First, there are some [markdown basics](#markdown-basics){: target="_self" }, then the author should become familiar with our [Learn-flavored markdown extensions](#learn-flavored-markdown-extensions){: target="_self" }, which are important for writing interactive lessons with quizzes and projects.

## Markdown basics

These sections contain a basic overview of the markdown syntax for writing lessons on Learn. 

- Gitlab has good, complete guides to Markdown/Kramdown: [Handbook Markdown Guide](https://about.gitlab.com/handbook/markdown-guide/); 
- and our own [short cheat-sheet can be found here](https://gist.github.com/raghubetina/a1b6e89e24a8c3acae6f0b63a1fd3323).

### Links open in a new tab

We default all links to opening in a new tab. If you _don't_ want that, then include `{: target="_self" }` after the link. For instance, to [reference the next section](#images){: target="_self" }, I wrote:

```
[reference the next section](#images){: target="_self" }
```

### Images

You can drag-and-drop images into the in-line editor, which will generate an external asset URL:

```
![file](https://res.cloudinary.com/dmxgp9oq2/image/upload/v1674882464/image-1674882462430.jpeg.jpg)
```

![file](https://res.cloudinary.com/dmxgp9oq2/image/upload/v1674882464/image-1674882462430.jpeg.jpg?)

Or reference a file from the `assets/` directory in a GitHub-connected lesson repo:

```
![](local-path-to-assets/example-image.jpg)
```

![](assets/example-image.jpg)

You can make images (or anything else) full-width by adding the `bleed-full` class:

```
![](local-path-to-assets/example-image.jpg)
{: .bleed-full }
```

![](assets/example-image.jpg)
{: .bleed-full }

### Things you can do with any element

On any element, you can:

- Use Tailwind classes. E.g., you could add a background-color and border with:

    ```html
    Call out this content
    {: class="bg-lime-100 border" }
    ```

    Which produces:

    Call out this content
    {: class="bg-lime-100 border" }

- Use raw HTML elements within your markdown.
    - Parse markdown within your HTML elements by adding `markdown="1"`.

        Don't forget to omit initial indentation within the element if you do this.

- Here is a combined example to make call-out alert and notice boxes

    ```html
    <div class="bg-red-100 py-1 px-5" markdown="1">
    **Some Alert** 
    
    `some code`
    </div>
    ```

    <div class="bg-red-100 py-1 px-5" markdown="1">
    **Some Alert** 
    
    `some code`
    </div>

    ```html
    <div class="bg-blue-100 py-1 px-5" markdown="1">
    **Some Notice** 
    
    `some code`
    </div>
    ```

    <div class="bg-blue-100 py-1 px-5" markdown="1">
    **Some Notice** 
    
    `some code`
    </div>


### Lists

In order to be sized properly, content of list items needs to be within a containing element (i.e. text nodes should not be direct children of the `<li>`).

[Here are a couple of methods for achieving this.](https://kramdown.gettalong.org/syntax.html#:~:text=You%20can%20circumvent%20this%20by%20leaving%20a%20blank%20line%20after%20the%20last%20list%20item%20and%20using%20an%20EOB%20marker%3A)

- Leave a blank line after every list item.

- First item

- Second item

  To add indented content within an li:

  Add new lines and indent one level.

- Code block within li:

  ```ruby
  class Person
    attr_accessor :first_name, :last_name
  end
  ```
		
- ```ruby
  class Person
    attr_accessor :first_name, :last_name
  end
  ```

### How to write asides

- In your markdown, add the `<aside>` _after_ the element that you want it to appear next to.

- Avoid putting any critical path content in asides.

- Use traditional [markdown footnotes](https://github.blog/changelog/2021-09-30-footnotes-now-supported-in-markdown-fields/) for things that are not relevant to see in the flow, e.g. [citing sources](https://www.scribbr.com/category/citing-sources/), etc.


<aside markdown="1">
This aside is next to a `ul`. How does it look?

![file](https://res.cloudinary.com/dmxgp9oq2/image/upload/v1674882464/image-1674882462430.jpeg.jpg)

1. It has a list item inside it.

1. And some of those list items have indented content

    I'm indented content!

1. ![file](https://res.cloudinary.com/dmxgp9oq2/image/upload/v1674882464/image-1674882462430.jpeg.jpg)

  ```ruby
  class Person
    attr_accessor :first_name, :last_name
  end
  ```

Outside list.

```ruby
class Person
	attr_accessor :first_name, :last_name
end
```
</aside>

The aside on the right was generated with:

```html
<aside markdown="1">

This aside is next to a `ul`. How does it look?

...
</aside>
```

### Blockquotes

```
> The ability to quote is a serviceable substitute for wit.
>
> — W. Somerset Maugham
```

Adding those `>` symbols at the beginning of the quoted lines produces:

> The ability to quote is a serviceable substitute for wit.
>
> — W. Somerset Maugham

## Learn-flavored markdown extensions

We have a number of markdown features specific to Learn that are important for authors to familiarize themselves with.

### Line 

## Quiz questions

- Example of choose_all. First bullet is the prompt
- First option (incorrect)
    - This is not correct because of xyz reason
    - Also not correct because of abc reason
- Second option (correct)
    - This is correct because of xyz reason
    - Also correct because of abc reason
- Third option (correct)
    - That's right! Because of xyz reason
- Fourth option (incorrect)
    - This is not correct because of xyz reason
{: .choose_all #zebra points="20" answer="[2, 3]" }

- Example of choose_one. First bullet is the prompt
- First option (incorrect)
    - This is not correct because of xyz reason
- Second option (incorrect)
    - This is not correct because of xyz reason
    - Also not correct because of abc reason
- Third option (correct)
    - That's right! Because of xyz reason
    - Also correct because of abc reason
- Fourth option (incorrect)
    - This is not correct because of xyz reason
{: .choose_best #giraffe points="30" answer="3" }

### Free text (correct: create)

- Which action will be triggered when the user visits `/posts/new`?
- create
    - The `posts#create` action is triggered after the user _submits_ the form, not when they visit the form before filling it out.
- new
    - Correct! The `posts#new` action is responsible for displaying a blank form to be filled out.
{: .free_text #elephant points="30" answer="2" }

### No right answer

- Is there a pain point in your life that you might be able to solve with a small CRUD app?
- any
    - Okay! I have a note in my phone's Notes app dedicated to collecting pain points/app ideas. I recommend that you do something like that, too.
{: .broken #lion points="30" }

## LTI iframe

LTI{}(https://lti-provider-example.herokuapp.com/lti_tool)[test]{secret}(20)[hyena]{400}

- Launch URL: https://lti-provider-example.herokuapp.com/lti_tool (required, no default)
- Button: Load TP Example in new tab (optional, default: "Load resource in new tab", if blank then assume iframe),
- Key: ...
- Secret: ...
{: .lti #elephant title="TP Example" points="30" answer="2" }

## LTI button

LTI{Load assignment}(https://lti-provider-example.herokuapp.com/lti_tool)[test]{secret}(20)[baboon]{400}
