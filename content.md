# How to write a lesson in learn.firstdraft.com

### Markdown basics

Gitlab has good guides to Markdown/Kramdown:

- [Markdown Kramdown Tips & Tricks](https://about.gitlab.com/blog/2016/07/19/markdown-kramdown-tips-and-tricks/)
- [Handbook Markdown Guide](https://about.gitlab.com/handbook/markdown-guide/)

### Links open in a new tab

We default all links to opening in a new tab. If you _don't_ want that, then include `{: target="_self" }` after the link.

### Images

You can drag-and-drop images into the editor.

![file](https://res.cloudinary.com/dmxgp9oq2/image/upload/v1674882464/image-1674882462430.jpeg.jpg?)

**TODO** In cloudinary generate more recognizable image names to make it easier to re-arrange them.

<aside>
Lorem ipsum dolor sit amet consectetur, adipisicing elit. Mollitia sapiente deleniti aliquam est dolorem natus provident quibusdam quisquam laboriosam. Omnis deserunt temporibus eaque facere vitae ea, non rerum perspiciatis ex!
		
Lorem ipsum dolor sit amet consectetur, adipisicing elit. Mollitia sapiente deleniti aliquam est dolorem natus provident quibusdam quisquam laboriosam. Omnis deserunt temporibus eaque facere vitae ea, non rerum perspiciatis ex!

Lorem ipsum dolor sit amet consectetur, adipisicing elit. Mollitia sapiente deleniti aliquam est dolorem natus provident quibusdam quisquam laboriosam. Omnis deserunt temporibus eaque facere vitae ea, non rerum perspiciatis ex!
</aside>

You can make images (or anything else) full-width by adding the `bleed-full` class:

```
![file](https://res.cloudinary.com/dmxgp9oq2/image/upload/v1674882464/image-1674882462430.jpeg.jpg)
{: .bleed-full }
```

![file](https://res.cloudinary.com/dmxgp9oq2/image/upload/v1674882464/image-1674882462430.jpeg.jpg)
{: .bleed-full }

### Things you can do with any element

On any element, you can:
{: class="bg-lime-100" }

**TODO** why are some Tailwind classes, e.g., border working? Some are, e.g. `background-color`.

- Use Tailwind classes. E.g., you could add a background-color with:

    ```html
  Call out this content
  {: class="bg-lime-100" }
    ```

    Which produces:

    Call out this content
    {: class="bg-lime-100" }

- Use raw HTML elements within your markdown.
    - Parse markdown within your HTML elements by adding `markdown="1"`.

        Don't forget to omit initial indentation within the element if you do this.

^

### Lists

In order to be sized properly, content of list items needs to be within a containing element (i.e. text nodes should not be direct children of the `<li>`).

[Here are a couple of methods for achieving this.](https://kramdown.gettalong.org/syntax.html#:~:text=You%20can%20circumvent%20this%20by%20leaving%20a%20blank%20line%20after%20the%20last%20list%20item%20and%20using%20an%20EOB%20marker%3A)

- Leave a blank line after every list item.

- Lorem ipsum dolor sit amet consectetur, adipisicing elit. Mollitia sapiente deleniti aliquam est dolorem natus provident quibusdam quisquam laboriosam. Omnis deserunt temporibus eaque facere vitae ea, non rerum perspiciatis ex!

- Lorem ipsum dolor sit amet consectetur, adipisicing elit. Mollitia sapiente deleniti aliquam est dolorem natus provident quibusdam quisquam laboriosam. Omnis deserunt temporibus eaque facere vitae ea, non rerum perspiciatis ex!

    Lorem ipsum dolor sit amet consectetur, adipisicing elit. Mollitia sapiente deleniti aliquam est dolorem natus provident quibusdam quisquam laboriosam. Omnis deserunt temporibus eaque facere vitae ea, non rerum perspiciatis ex!
		
   Lorem ipsum dolor sit amet consectetur, adipisicing elit. Mollitia sapiente deleniti aliquam est dolorem natus provident quibusdam quisquam laboriosam. Omnis deserunt temporibus eaque facere vitae ea, non rerum perspiciatis ex!

    Lorem ipsum dolor sit amet consectetur, adipisicing elit. Mollitia sapiente deleniti aliquam est dolorem natus provident quibusdam quisquam laboriosam. Omnis deserunt temporibus eaque facere vitae ea, non rerum perspiciatis ex!

- Code block within li:

    ```ruby
  class Person
   attr_accessor :first_name, :last_name
  end
		```
		
-  ```ruby
		class Person
		  attr_accessor :first_name, :last_name
		end
		```
- After the last item, leave a blank line and then an End Of Block (EOB) marker `^`.

^

**TODO** Modify the markdown parser to make adding children within li automatic.

**TODO** Fenced code blocks within list items not being parsed properly by Kramdown? Odd — it works fine in Chapters.

### How to write asides

- In your markdown, add the `<aside>` _after_ the element that you want it to appear next to.

- As with any other element, you can add any Tailwind classes. In particular:
    - `bg-lime-100` for fun, very optional stuff.
    - `bg-cyan-100` for slightly more important stuff.

- Avoid putting any critical path content in asides.

- Use traditional [markdown footnotes](https://github.blog/changelog/2021-09-30-footnotes-now-supported-in-markdown-fields/) for things that are not relevant to see in the flow, e.g. [citing sources](https://www.scribbr.com/category/citing-sources/), etc.

^


<aside class="bg-lime-100" markdown="1">
This aside is next to a `ul`. How does it look?

![file](https://res.cloudinary.com/dmxgp9oq2/image/upload/v1674882464/image-1674882462430.jpeg.jpg)

1. It has a list item inside it.

1. Lorem ipsum dolor sit amet consectetur, adipisicing elit. Mollitia sapiente deleniti aliquam est dolorem natus provident quibusdam quisquam laboriosam. Omnis deserunt temporibus eaque facere vitae ea, non rerum perspiciatis ex!

    Lorem ipsum dolor sit amet consectetur, adipisicing elit. Mollitia sapiente deleniti aliquam est dolorem natus provident quibusdam quisquam laboriosam. Omnis deserunt temporibus eaque facere vitae ea, non rerum perspiciatis ex!

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

### Blockquotes

```
> The ability to quote is a serviceable substitute for wit.
>
> — W. Somerset Maugham
```

> The ability to quote is a serviceable substitute for wit.
>
> — W. Somerset Maugham

### Nested lists with code

##     Lorem ipsum dolor sit amet consectetur, adipisicing elit. Mollitia sapiente deleniti aliquam est dolorem natus provident quibusdam quisquam laboriosam. Omnis deserunt temporibus eaque facere vitae ea, non rerum perspiciatis ex!
		
   Lorem ipsum dolor sit amet consectetur, adipisicing elit. Mollitia sapiente deleniti aliquam est dolorem natus provident quibusdam quisquam laboriosam. Omnis deserunt temporibus eaque facere vitae ea, non rerum perspiciatis ex!

    Lorem ipsum dolor sit amet consectetur, adipisicing elit. Mollitia sapiente deleniti aliquam est dolorem natus provident quibusdam quisquam laboriosam. Omnis deserunt temporibus eaque facere vitae ea, non rerum perspiciatis ex!

The below is raw HTML (not markdown) that demonstrates the proper behavior of lists. The markdown parser is currently messing up code blocks within list items.

<ul>
	<li><p>Most li children are narrow, except code blocks.</p></li>
	<li><p>List items without at least element within, i.e. no children, are not being properly constrained.</p></li>
	<li><p><a target="_blank" href="https://kramdown.gettalong.org/syntax.html#:~:text=The%20text%20of%20the%20last%20list%20item%20is%20also%20wrapped%20in%20a%20paragraph%20tag%20if%20all%20other%20list%20items%20contain%20a%20proper%20paragraph%20as%20first%20element.%20This%20makes%20the%20following%20use%20case%20work%20like%20expected%2C%20i.e.%20all%20the%20list%20items%20are%20wrapped%20in%20paragraphs%3A">Authors will have to ensure lines between list items</a> so that at least a paragraph is within each li. Or we'll have to modify the li parser to always add paragraphs. Or we'll have to autoformat the input markdown.</p></li>
	<li>
		<p>How</p>

		<p>are you</p>

		<p>Lorem ipsum dolor sit amet consectetur, adipisicing elit. Voluptatem placeat quidem accusantium, animi
			accusamus maxime dolor eum hic numquam ab architecto voluptatibus. Cupiditate quae assumenda nulla quod nisi
			facere fugiat!</p>
	</li>

	<li>
		<p>This code block is correctly bleeding right:</p>

		<pre>
				<code>
				<b>Lorem ipsum dolor</b>, sit amet consectetur adipisicing elit. Quaerat consectetur in enim eius
				facere animi alias fugit perspiciatis assumenda ea quisquam quasi cumque corporis temporibus, nihil amet est
				laborum ullam!

				hi there

				more
				</code>
			</pre>

		<p>Need to solve the extraneous left whitespace within the pre from the markdown's indentation</p>
	</li>

	<li>
		<ul>
			<li>
				<p>
					second-level
				</p>
			</li>
			<li>
				<pre>
					<code>
					<b>Lorem ipsum dolor</b>, sit amet consectetur adipisicing elit. Quaerat consectetur in enim eius
					facere animi alias fugit perspiciatis assumenda ea quisquam quasi cumque corporis temporibus, nihil amet est
					laborum ullam!

					hi there

					more
					</code>
				</pre>
			</li>
			<li>
				<ul>
					<li>
						<p>
							third-level
						</p>
					</li>
					<li>
						<pre>
							<code>
							<b>Lorem ipsum dolor</b>, sit amet consectetur adipisicing elit. Quaerat consectetur in enim eius
							facere animi alias fugit perspiciatis assumenda ea quisquam quasi cumque corporis temporibus, nihil amet est
							laborum ullam!

							hi there

							more
							</code>
						</pre>
					</li>
					<li>
						<ul>
							<li>
								<p>fourth-level</p>
							</li>
							<li>
								<p>Code blocks beyond this level don't bleed</p>
							</li>
							<li>
								<pre>
									<code>
									<b>Lorem ipsum dolor</b>, sit amet consectetur adipisicing elit. Quaerat consectetur in enim eius
									facere animi alias fugit perspiciatis assumenda ea quisquam quasi cumque corporis temporibus, nihil amet est
									laborum ullam!

									hi there

									more
									</code>
								</pre>
							</li>
							<li>
								<p>
									Lorem ipsum, dolor sit amet consectetur adipisicing elit. Eos ut deserunt officiis magnam enim, vel accusantium modi voluptas eaque, iure saepe sed suscipit fugit repellendus, corrupti ea commodi neque delectus.
								</p>
							</li>
						</ul>
					</li>
				</ul>
			</li>
		</ul>
	</li>
</ul>

<h2>Tables</h2>

<table>
	<thead>
		<tr>
			<th>First</th>
			<th>Last</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<td>Osha</td>
			<td>Groetz</td>
		</tr>
		<tr>
			<td>Jelani</td>
			<td>Woods</td>
		</tr>
		<tr>
			<td>Stephen</td>
			<td>Walter</td>
		</tr>
		<tr>
			<td>Jessie</td>
			<td>Chang</td>
		</tr>
		<tr>
			<td>Ainsley</td>
			<td>Galvez</td>
		</tr>
		<tr>
			<td>Diego</td>
			<td>Cruz</td>
		</tr>
		<tr>
			<td>Logan</td>
			<td>CoBell</td>
		</tr>
		<tr>
			<td>Mia</td>
			<td>Battle</td>
		</tr>
		<tr>
			<td>Romeo</td>
			<td>Sarangaya</td>
		</tr>
	</tbody>
</table>

<div class="bleed-full">
	<table>
		<thead>
			<tr>
				<th>First</th>
				<th>Last</th>
			</tr>
		</thead>
		<tbody>
			<tr>
				<td>Osha</td>
				<td>Groetz</td>
			</tr>
			<tr>
				<td>Jelani</td>
				<td>Woods</td>
			</tr>
			<tr>
				<td>Stephen</td>
				<td>Walter</td>
			</tr>
			<tr>
				<td>Jessie</td>
				<td>Chang</td>
			</tr>
			<tr>
				<td>Ainsley</td>
				<td>Galvez</td>
			</tr>
			<tr>
				<td>Diego</td>
				<td>Cruz</td>
			</tr>
			<tr>
				<td>Logan</td>
				<td>CoBell</td>
			</tr>
			<tr>
				<td>Mia</td>
				<td>Battle</td>
			</tr>
			<tr>
				<td>Romeo</td>
				<td>Sarangaya</td>
			</tr>
		</tbody>
	</table>
</div>

# Examples of markdown extensions

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
