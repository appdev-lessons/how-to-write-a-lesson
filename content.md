# How to write a lesson in learn.firstdraft.com

## Create the lesson

Sign in and visit the author lessons index, [learn.firstdraft.com/authors/lessons](https://learn.firstdraft.com/authors/lessons), and click "New lesson". You can either fill in a "title" and "content" directly in the markdown GUI interface, or "Connect GitHub" to add the URL of a lesson on GitHub in our pre-defined format, which is detailed below.

### Connect a lesson via GitHub

The [appdev-lessons GitHub organization](https://github.com/appdev-lessons) contains all GitHub-connected lessons on Learn. A template lesson (`appdev-lessons/learn-lesson-template`) is pinned in that repository, which can be used to generate a new lesson. The new lesson "owner" _must_ be the `appdev-lessons` organization:

[Create a new repository from the appdev-lessons/learn-lesson-template repo](https://github.com/new?template_name=learn-lesson-template&template_owner=appdev-lessons)

The following details the lesson repository files and how to use each. **Do not rename these files**:

<div class="bleed-full">

| File | Purpose | Usage  | 
|-----------------|-------------|---------------|
| `assets/` | Folder containing images, gifs, etc. that should be rendered in the lesson | Place all asset files in this folder and reference them within `content.md` with the syntax `![Alt text here](local-path-to-assets/my-image.png)`. You can use the path `/assets/my-image.png` or `assets/my-image.png`, both will render in your local markdown preview; and when you connect the repository with a Learn Lesson, the assets will upload to Cloudinary and the paths will automatically be converted to a hosted URL.  |
|-----------------+--------------+-----------------|
| `.gitignore` | Ignore any local files in the folder (i.e. do not commit these to the repo) | The template ignores a few common files that should not be included in the commit history. More can be added if required. |
|-----------------+--------------+-----------------|
| `README.md` | General repo information  | Replace the first heading with the name of the repo and replace the URL with that of the learn lesson after connecting the lesson with Learn |
|-----------------+--------------+-----------------|
| `content.md` | Contains the lesson "title" and "content" | The file should begin with a level one (`<h1>`) markdown heading `# My Title`, which will be parsed to form the lesson title on Learn. Everything after this first `#` line will be parsed into the lesson content. |

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

When a lesson is connected to a GitHub repo, the Author can still make edits to the lesson in the markdown GUI interface on Learn. When edits are made and the "Update Lesson" button is clicked, a commit is sent to the GitHub repository with the generic message "Inline update of content.md on Learn". This ensures that edits can be made either directly to the GitHub repository, or here on Learn, and both locations stay in sync. It is recommended that small updates like fixing typos, or drag and dropping additional images into a lesson be made directly here on Learn, with larger updates like rewritten sections carried out via GitHub pull requests and merges.

## Write the lesson

The next sections cover how to write a lesson via the in-line editor or in the `content.md` file for a GitHub-connected lesson. First, there are some [markdown basics](#markdown-basics){: target="_self" }, then the author should become familiar with our [Learn-flavored markdown extensions](#learn-flavored-markdown-extensions){: target="_self" }, which are important for writing interactive lessons with quizzes and projects.

## Markdown basics

These sections contain a basic overview of the markdown syntax for writing lessons on Learn. 

- Gitlab has good, complete guides to Markdown/Kramdown: [Handbook Markdown Guide](https://about.gitlab.com/handbook/markdown-guide/); 
- and our own [short cheat-sheet can be found here](https://gist.github.com/raghubetina/a1b6e89e24a8c3acae6f0b63a1fd3323).

<div class="alert alert-primary">

A handy reference for lesson markdown can be found in [this kitchen sink example](https://raw.githubusercontent.com/appdev-lessons/contact-book-first-database/main/content.md).

Here is how that lesson looks when rendered Learn: [**Contact Book: Our very first database**](https://learn.firstdraft.com/lessons/130-contact-book-first-database)
</div>

### Links open in a new tab

We default all links to opening in a new tab. If you _don't_ want that, then include `{: target="_self" }` after the link. For instance, to [reference the next section](#images){: target="_self" }, I wrote:

```
[reference the next section](#images){: target="_self" }
```

### Images

You can drag-and-drop images into the in-line editor, which will generate an external asset URL:

```
![file](https://res.cloudinary.com/[CLOUD_NAME]/image/upload/[IMAGE_VERSION]/appdev-lessons/[REPO_NAME]/[BRANCH]/[IMAGE_NAME])
```

![file](https://res.cloudinary.com/dmxgp9oq2/image/upload/v1674882464/image-1674882462430.jpeg.jpg?)

Or reference a file from the `assets/` directory in a GitHub-connected lesson repo:

```
![Alt text here](local-path-to-assets/example-image.jpg)
```

![Alt text here](assets/example-image.jpg)

You can make images (or anything else) full-width by adding the `bleed-full` class:

```
![Alt text here](local-path-to-assets/example-image.jpg)
{: .bleed-full }
```

![Alt text here](assets/example-image.jpg)
{: .bleed-full }

### Things you can do with any element

On any element, you can:

- [Use Bootstrap classes](https://getbootstrap.com/docs/5.3/getting-started/introduction/). E.g., you could [add a background-color](https://getbootstrap.com/docs/5.3/utilities/background/) and [border](https://getbootstrap.com/docs/5.3/utilities/borders/) with:

    ```html
    Call out this content
    {: class="bg-warning-subtle border" }
    ```
    {: copyable }

    Which produces:

    Call out this content
    {: class="bg-warning-subtle border" }

- Use raw HTML elements within your markdown.
    - Don't forget to omit initial indentation within the element if you do this.

- Here is a combined example to make call-out [Bootstrap alert boxes](https://getbootstrap.com/docs/5.3/components/alerts/)

    ```html
    <div class="alert alert-danger">
    **Some Alert** 
    
    `some code`
    </div>
    ```
    {: copyable }

    <div class="alert alert-danger">
    **Some Alert** 
    
    `some code`
    </div>

    ```html
    <div class="alert alert-primary">
    **Some Notice** 
    
    `some code`
    </div>
    ```

    <div class="alert alert-primary">
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


<aside>
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
</aside>

The aside on the right was generated with:

```html
<aside>

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

### Mermaid diagrams

Authors can create [mermaid diagrams](https://mermaid.js.org/syntax/examples.html) in fenced mermaid type codeblocks. For example:

    ```mermaid
    graph TD
      A-->B
      A-->C
      B-->D
      C-->D
    ```
    {: copyable }

renders as:

```mermaid
graph TD
  A-->B
  A-->C
  B-->D
  C-->D
```

### LaTeX math equations

Authors can write [LaTeX math equations](https://tilburgsciencehub.com/topics/research-skills/templates-dynamic-content/templates/amsmath-latex-cheatsheet/) by fencing inline or block expressions with two dollar signs, `$$`. For example:

```
$$\Large x + y = 5$$
```

Produces:

$$\Large x + y = 5$$

or

```
$$
\Large
\begin{aligned}
  & \phi(x,y) = \phi \left(\sum_{i=1}^n x_ie_i, \sum_{j=1}^n y_je_j \right)
  = \sum_{i=1}^n \sum_{j=1}^n x_i y_j \phi(e_i, e_j) = \\
  & (x_1, \ldots, x_n) \left( \begin{array}{ccc}
      \phi(e_1, e_1) & \cdots & \phi(e_1, e_n) \\
      \vdots & \ddots & \vdots \\
      \phi(e_n, e_1) & \cdots & \phi(e_n, e_n)
    \end{array} \right)
  \left( \begin{array}{c}
      y_1 \\
      \vdots \\
      y_n
    \end{array} \right)
\end{aligned}
$$
```

Produces:

$$
\Large
\begin{aligned}
  & \phi(x,y) = \phi \left(\sum_{i=1}^n x_ie_i, \sum_{j=1}^n y_je_j \right)
  = \sum_{i=1}^n \sum_{j=1}^n x_i y_j \phi(e_i, e_j) = \\
  & (x_1, \ldots, x_n) \left( \begin{array}{ccc}
      \phi(e_1, e_1) & \cdots & \phi(e_1, e_n) \\
      \vdots & \ddots & \vdots \\
      \phi(e_n, e_1) & \cdots & \phi(e_n, e_n)
    \end{array} \right)
  \left( \begin{array}{c}
      y_1 \\
      \vdots \\
      y_n
    \end{array} \right)
\end{aligned}
$$

## Learn-flavored markdown extensions

We have a number of markdown features specific to Learn that are important for authors to familiarize themselves with.

### Time taken question

To collect _average_ user completion times, which are calculated as the mean of the 25th to 75th percentile to avoid outliers, **copy and paste this exact question into the bottom of your lesson**:

```
---

- Approximately how long (in minutes) did this lesson take you to complete?
{: .free_text_number #time_taken title="Time taken" points="1" answer="any" }
```
{: copyable }

When rendered in the lesson, that will produce:

---

- Approximately how long (in minutes) did this lesson take you to complete?
{: .free_text_number #time_taken title="Time taken" points="1" answer="any" }

As soon as there are at least four answers to that question in the lesson, a time-taken badge will appear next to the lesson on the User-facing course page:

---

![Time taken badge](/assets/time-taken-badge.png)

---

And the totals will be tallied on the Author-facing course configuration page:

---

![Time taken author tally](/assets/time-taken-author-tally.png)

---

### Copyable codeblocks

In general, our mantra is "type don't copy-paste!". However, there are times when an author might want a copyable codeblock for e.g. API keys, boilerplate HTML, etc. 

In that case, an author can add a `{: copyable }` keyword below a static codeblock to add the ability to copy to clipboard with a click on the icon:

    ```
    copy instead of type!
    ```
    {: copyable }

Produces:

```
copy instead of type!
```
{: copyable }


### Codeblock titles

An author can title a static codeblock, typically with the filename of the code in question, with this syntax:

    ```ruby
    get("/movies", { :controller => "movies", :action => "index" })
    ```
    {: filename="config/routes.rb" }

That produces:

```ruby
get("/movies", { :controller => "movies", :action => "index" })
```
{: filename="config/routes.rb" }


### Codeblock line and column highlighting

You add the highlight options after the language tag in a codeblock within brackets.

- You can highlight individual lines: `ruby{1}`
- You can highlight multiple lines: `ruby{1,2,4,5}`
- You can highlight a range of lines: `ruby{1-3}`
- You can highlight individual columns: `ruby{1:(3)}`
- You can highlight multiple columns: `ruby{1:(3,4,5)}`
- You can highlight a range of columns: `ruby{1:(3-6)}`

Any combination should work.

    ```ruby{1:(1-6),3:(9-13)}
    tokens = ["hello", "world", "!"]
    tokens.each do |token|
      print token
      print " " if token.count("a-zA-Z") > 0
    end
    ```
    {: copyable }

Produces:

```ruby{1:(1-6),3:(9-13)}
tokens = ["hello", "world", "!"]
tokens.each do |token|
  print token
  print " " if token.count("a-zA-Z") > 0
end
```

Highlighting also works with HTML and ERB codeblocks.

    ```erb{1:(1-3)}
    <% newsfeed_photos.each do |the_photo| %>
      <div class="card">
    ```
    {: copyable }

Produces:

```erb{1:(1-3)}
<% newsfeed_photos.each do |the_photo| %>
  <div class="card">
```

### Quiz questions

A quiz question is built like so:

```
- The question:
- First option.
  - Correct! (Copy to show when first option is selected.)
- Second option.
  - Not quite. (Copy to show when second option is selected.)
- Third option.
  - Not quite. (Copy to show when third option is selected.)
{: .question_type #unique_identifier title="Some title" points="1" answer="1" needs_approval="false" }
```
{: copyable }

The options contained in the `{: }` tags on a new line directly below the question options are:

- `.question_type`
  - An HTML `class`. One of `.choose_all`, `.choose_best`, `.free_text`, or `.free_text_number`; details for each in the sections below
- `#unique_identifier`
  - An HTML `id`. Used to identify the question in the database. 
  - Each ID must be unique within a lesson. Any questions with the same ID in the same lesson will be treated as the same question. The last question with that ID will be saved in the database.
- `title`
  - Used by the user to identify the question in the progress table. 
  - It is not used to identify the question in the database. It does not have to be unique.
  - For runnable code blocks, this title is also used as a header to the code editor displayed to the user.
- `points`
  - Number of points the question is worth.
- `answer`
  - Indicates the index of the correct answer in the list of options (indexing begins at 1 with the first option.
- `needs_approval`
  - If set to `true`, the student will not receive points until an instructor "approves" the answer on the instructor dashboard for the course.

#### `needs_approval` option

The `needs_approval` option listed above is a boolean that defaults to `false`. If set to `true`, the student will not receive points until an instructor "approves" the answer on the instructor dashboard for the course.

This option is most useful for `.free_text` questions ([described below](#free_text){: target="_self"}), where e.g. a submitted URL needs to be viewed by an instructor to determine if the answer is correct. This option should only be used for lessons contained in a course, and not standalone lessons. When using this option, **it is advised to lower passing scores on the lesson to less than 100% (the default passing score of 80% is a good value)** so that students are not blocked from further progress while awaiting approval.

Once this option is added to a question, the student will see this message when they submit a correct answer:

---

![Needs approval message](/assets/needs-approval-student-view.png)

---

And they will not receive the points right away.

When an instructor of the course navigates to the "Instructor dashboard" > "Lessons" > "Lesson title" page, they will see the ability to "approve" the submission, which will then award the points to the student:

![Needs approval instructor view](/assets/needs-approval-instructor-view.png)

Here is an example of a `.free_text` question that uses the `needs_approval` option:

```
- Enter the URL of your GitHub project repository (e.g. `https://github.com/your-username/your-repo`):
- https://github.com
  - Thanks for your submission.
- any
  - Not quite, make sure you submit a URL like `https://github.com/your-username/your-repo`.
{: .free_text #otter title="The needs_approval question type" points="1" answer="1" needs_approval="true" }
```
{: copyable }

Which renders as:

- Enter the URL of your GitHub project repository (e.g. `https://github.com/your-username/your-repo`):
- https://github.com
  - Thanks for your submission.
- any
  - Not quite, make sure you submit a URL like `https://github.com/your-username/your-repo`.
{: .free_text #otter title="The needs_approval question type" points="1" answer="1" needs_approval="true" }

#### choose_all

A choose all question type is a multiple choice question where the user can select multiple answers. The user can select the answer by clicking on the checkbox next to the answer.

To add a choose all question to your lesson, use the following markdown syntax,

```
- Example of choose_all. First bullet is the prompt
- First option (incorrect)
  - This is not correct because of xyz reason
  - Also not correct because of abc reason
- Second option (correct)
  - This is correct because of xyz reason
  - Also correct because of abc reason
- Third option (correct)
  - That's right! Because of xyz reason
{: .choose_all #zebra title="The choose_all question type" points="2" answer="[2, 3]" }
```
{: copyable }

The user will receive partial points for each correct answer they select. The user will receive all points only after they select all the correct answers. Partial points are awarded by dividing the total points by the number of correct answers. For example, if the question has 3 points and there are 3 correct answers, then the user will receive 1 point for each correct answer.

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
{: .choose_all #zebra title="The choose_all question type" points="2" answer="[2, 3]" }

#### choose_best

A choose best question type is a multiple choice question where the user can select only one answer. The user can select the answer by clicking on the radio button next to the answer.

To add a choose best question to your lesson, use the following markdown syntax,

```
- Example of choose_best. First bullet is the prompt
- First option (incorrect)
  - This is not correct because of xyz reason
- Second option (incorrect)
  - This is not correct because of xyz reason
  - Also not correct because of abc reason
- Third option (correct)
  - That's right! Because of xyz reason
  - Also correct because of abc reason
{: .choose_best #giraffe title="The choose_best question type" points="1" answer="3" }
```
{: copyable }

Once the user selects the one correct answer, they will receive all the points.

- Example of choose_best. First bullet is the prompt
- First option (incorrect)
  - This is not correct because of xyz reason
- Second option (incorrect)
  - This is not correct because of xyz reason
  - Also not correct because of abc reason
- Third option (correct)
  - That's right! Because of xyz reason
  - Also correct because of abc reason
{: .choose_best #giraffe title="The choose_best question type" points="1" answer="3" }

**Special Cases for choose_all and choose_best:**

- "any correct answer": If you want to accept any answer, you can use the `any` option in the answer array. For example,

  `{: .choose_all #zebra title="The choose_all question type" points="2" answer="any" }`

  This will mark all answers in the given options as correct.

- "optional answer": A `choose_all` or `choose_best` question must have a correct answer selected. It is not optional. If you leave out the answer attribute then any answer a user selects will be marked as incorrect.

#### free_text

A free text question type allows the respondent to enter any text they wish.

To add a free text question to your lesson, use the following markdown syntax,

```
- Which action will be triggered when the user visits `/posts/new`?
- create
  - The `posts#create` action is triggered after the user _submits_ the form, not when they visit the form before filling it out.
- new
  - Correct! The `posts#new` action is responsible for displaying a blank form to be filled out.
{: .free_text #elephant title="The free_text question type" points="1" answer="2" }
```
{: copyable }

A user can type in the exact or a partial match for the correct answer. For example, if the correct answer is `Ruby`, the user can type in `Ruby`, `R`, `r`, etc. as the answer checking is done with a lenient regex.

- Which action will be triggered when the user visits `/posts/new`?
- create
  - Not quite. The `posts#create` action is triggered after the user _submits_ the form, not when they visit the form before filling it out.
- new
  - Correct! The `posts#new` action is responsible for displaying a blank form to be filled out.
{: .free_text #elephant title="The free_text question type" points="1" answer="2" }

#### free_text_number

A free text number question type allows the respondent to enter any number or decimal they wish. To add a free text number question to your lesson, use the following markdown syntax,

```
- What does 2+2 evaluate to?
- 4
  - That's right!
- any
  - Not quite.
{: .free_text_number #two_plus_two title="Two plus two" points="1" answer="1" }
```
{: copyable }

If options are given for the correct answer, a user can type in only the exact match of the answer. For example, if the answer is 5, the user can type in 5, 5.0, 5.00, 5.000, etc. but not 5.1, 5.01, 5.001, etc.

- What does 2+2 evaluate to?
- 4
	- That's right!
- any
	- Not quite.
{: .free_text_number #two_plus_two title="Two plus two" points="1" answer="1" }

**Special Cases for free_text and free_text_number:**

- "fallback option": If you want to show a custom message when a user enters an incorrect answer, you can use the `any` option. For example,

  ```
  - What programming language are we learning today?
  - Ruby
    - Correct.
  - any
    - Not quite right. Re-read the previous sections and try again.
  {: .free_text #what_language title="Language we are learning" points="1" answer="[1]" }
  ```

- "any correct answer": If you want to accept any answer, you can use the `any` option in the answer array. For example,

  `{: .free_text #elephant title="The free_text question type" points="1" answer="any" }`

  This will mark all answers in the given options as correct.

- "optional answer": If you want to accept any answer as the correct one, you can skip the answer attribute. For example,

  `{: .free_text #elephant title="The free_text question type" points="1" }`

### Runnable and graded codeblocks

An author can insert runnable or graded codeblocks into the lesson.

#### Runnable Ruby (codeblock)

A Ruby runnable question type allows the user to modify and execute Ruby code.

To add a Ruby question to your lesson, use the following markdown syntax,


    ```ruby
    x = "Hello"
    y = "World"
    z = x + y

    pp z
    ```
    {: .codeblock #bear title="Runnable Ruby" points="1"}

After the user executes the code at least once, they are awarded all the points.

```ruby
x = "Hello"
y = "World"
z = x + y

pp z
```
{: .codeblock #bear title="Runnable Ruby" points="1"}

**Additional attributes available on codeblock type questions:**

- `readonly_lines`
  - Some lines can be marked as "readonly". The user will not be able to modify these lines. This attribute accepts an array of line numbers.
  - Example: `readonly_lines="[10, 16, 17]"`
- `setup_code`
  - A single line or a range of lines can be marked as setup code. These lines will not be shown to the user. The line numbers shown on the left margin of the code editor will not include those lines marked as `setup_code`.
  - Example: `setup_code="1"`
  - Example: `setup_code="1-4"`

#### Graded Ruby (codeblock + codeblock-test)

Each Ruby question can have multiple tests. When a student clicks on the "Run" button for a test, the test executes, and an output and summary are displayed to the student. The output represents the result of each individual test, indicating whether it passed or failed. The summary provides an overview of the test results, including the number of tests that passed.

Here's an example,

    ```ruby
    pp "change me :)"
    ```
    {: .codeblock #graded_codeblock title="First graded code block"}

    ```ruby
    describe "First graded code block" do
      it "should print 'Hello, world!'" do
        output = run_codeblock
        expect(output).to match("Hello, world!")
      end
    end
    ```
    {: .codeblock-test #graded_codeblock_test_1 for="graded_codeblock" title="First graded code block should print 'Hello, world!'" points="1"}

Notice that the first block has no points associated with it. Total points for a graded Ruby question are calculated by summing the individual question test points. 

It is advisable to give the test a `describe` line using the copy from the runnable code `title`, and then use the `it` line's copy to form the `title` for the test; here: `"First graded code block should print 'Hello, world!'"`.

Note the key attribute of the `codeblock-test`: `for="graded_codeblock"`. This `for` attribute **must** match the `#unique_identifier` attribute of the question associated with it, here that is `#graded_codeblock` / `for="graded_codeblock"`.

Each test is associated with a specific Ruby question using the Ruby question ID parameter. This association allows the system to identify the related tests for a particular question and calculate the score received by the student based on the pass percentage.

```ruby
pp "change me :)"
```
{: .codeblock #graded_codeblock title="First graded code block"}

```ruby
describe "First graded code block" do
  it "should print 'Hello, world!'" do
    output = run_codeblock
    expect(output).to match("Hello, world!")
  end
end
```
{: .codeblock-test #graded_codeblock_test_1 for="graded_codeblock" title="First graded code block should print 'Hello, world!'" points="1"}

#### Our guide to graded codeblocks

You can read _much_ more about writing graded codeblocks in our guide: [_How to write Ruby codeblock tests_](https://learn.firstdraft.com/lessons/684-how-to-write-ruby-codeblock-tests).

You should review those notes before you begin writing tests for the first time.

The source code for a few lessons with extensive graded code blocks are also helpful for reference (search the source code for `.codeblock-test` to find the relevant examples):

- [Ruby Intro: Each](https://raw.githubusercontent.com/appdev-lessons/ruby-intro-each/main/content.md)
- [Ruby Gym: Think Fast](https://raw.githubusercontent.com/appdev-lessons/ruby-gym-think-fast/main/content.md)

#### Runnable HTML (codeblock)

An HTML runnable question type allows the user to modify and execute HTML code.

To add an HTML question to your lesson, just specify the code type in the beginning of the code block,

    ```html
    <h1>Hi</h1>

    <p>there</p>
    ```
    {: .codeblock #salmon title="Runnable HTML" points="1"}

```html
<h1>Hi</h1>

<p>there</p>
```
{: .codeblock #salmon title="Runnable HTML" points="1"}

We do not yet support grading via connected tests on runnable HTML code blocks.

### LTI button

An LTI launch button can also be inserted into a lesson, allowing connections to `rake grade` projects:

```
LTI{Load MSM Queries assignment}(https://grades.firstdraft.com/launch)[test]{secret}(10)[MSM Queries Project]
```
{: copyable }

which renders as:

LTI{Load MSM Queries assignment}(https://grades.firstdraft.com/launch)[kcKih6i68NmbdcmcdeCEjg2J]{jhytB1uc3YrCA26fFWDEw23U}(10)[MSM Queries Project]

This line of markdown is made up of:

- `LTI`
  - The line must start with this to render the launch button.
- `{Load MSM Queries assignment}`
  - The copy shown on the button.
- `(https://grades.firstdraft.com/launch)`
  - The launch URL, which will need to be configured on the first click of the button by the author.
- `[test]{secret}`
  - The consumer (`test`) and secret (`secret`) key provided by the tool. **You will need to find or request these keys on Grades to properly configure the button for launching.**
- `(10)`
  - The number of points the project is worth within the current lesson.
- `[MSM Queries Project]`
  - The name of the project displayed to the user in the progress table.
