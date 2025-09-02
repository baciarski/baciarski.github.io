+++
title = "Technical page - technically not a part of the blog"
date = "2025-09-02"


[taxonomies]
tags=["documentation"]

[extra]
repo_view = true
comment = true
+++


## This page is for author's use - I don't remember all the shortcodes and features of my blog CMS :D


Here is an example of the `note` shortcode:

This one is static!
{{ note(header="Note!", body="This blog assumes basic terminal maturity") }}

This one is clickable!
{{ note(clickable=true, hidden = true, header="Quiz!", body="The answer to the quiz!") }}


Syntax:
```
{{/* note(header="Note!", body="This blog assumes basic terminal maturity") */}}
{{/* note(clickable=true, hidden = true, header="Quiz!", body="The answer to the quiz!") */}}
```

You can also use some HTML in the text:
{{ note(header="Note!", body="<h1>This blog assumes basic terminal maturity</h1>") }}


Literal shortcode:
```
{{/* note(header="Note!", body="<h1>This blog assumes basic terminal maturity</h1>") */}}
```

Pretty cool, right?

Finally, you can do something like this (hopefully):

{% note(clickable=true, header="Quiz!") %}

# Hello this is markdown inside a note shortcode

```rust
fn main() {
    println!("Hello World");
}
```

We can't call another shortcode inside a shortcode, but this is good enough.

{% end %}

Here is the raw markdown:

```markdown
{{/* note(clickable=true, header="Quiz!") */}}

# Hello this is markdown inside a note shortcode

\`\`\`rust
fn main() {
    println!("Hello World");
}
\`\`\`

We can't call another shortcode inside a shortcode, but this is good enough.

{{/* end */}}
```

Finally, we have center
{{ note(center=true, header="Centered Text", body="This is centered text") }}

```markdown
{{/* note(center=true, header="Centered Text", body="This is centered text") */}}
```
It works good enough for me!


Note: This requires the `mathjax` and `mathjax_dollar_inline_enable` option set to `true` in `[extra]` section.

# Inline Math

- $(a+b)^2$ = $a^2 + 2ab + b^2$
- A polynomial P of degree d over $\mathbb{F}_p$ is an expression of the form
  $P(s) = a_0 + a_1 . s + a_2 . s^2 + ... + a_d . s^d$ for some
  $a_0,..,a_d \in \mathbb{F}_p$

# Displayed Math

$$
p := (\sum_{k∈I}{c_k.v_k} + \delta_v.t(x))·(\sum_{k∈I}{c_k.w_k} + \delta_w.t(x)) − (\sum_{k∈I}{c_k.y_k} + \delta_y.t(x))
$$
This Theme supports [mermaid](https://mermaid.js.org/) markdown diagram rendering.

To use mermaid diagrams in your posts, see the example in the raw markdown code.
https://raw.githubusercontent.com/not-matthias/apollo/refs/heads/main/content/posts/mermaid.md

## Rendered Example

{% mermaid() %}
graph LR
    A[Start] --> B[Initialize]
    B --> C[Processing]
    C --> D[Complete]
    D --> E[Success]

    style A fill:#f9f,stroke:#333
    style E fill:#9f9,stroke:#333
{% end %}

# H1

## H2

### H3

Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Aliquet sagittis id consectetur purus ut. In pellentesque massa placerat duis ultricies. Neque laoreet suspendisse interdum consectetur libero id. Justo nec ultrices dui sapien eget mi proin. Nunc consequat interdum varius sit amet mattis vulputate. Sollicitudin tempor id eu nisl nunc mi ipsum. Non odio euismod lacinia at quis. Sit amet nisl suscipit adipiscing. Amet mattis vulputate enim nulla aliquet porttitor lacus luctus accumsan. Sit amet consectetur adipiscing elit pellentesque habitant. Ac placerat vestibulum lectus mauris. Molestie ac feugiat sed lectus vestibulum mattis ullamcorper velit sed. [Google](https://www.google.com)

![Markdown Logo](https://markdown-here.com/img/icon256.png)

## Code Block

```rust
fn main() {
    println!("Hello World");
}
```

```rust,hl_lines=2,linenos
fn main() {
    println!("Hello World");
}
```

## Ordered List

1. First item
2. Second item
3. Third item

## Unordered List

- List item
- Another item
- And another item

## Nested list

- Fruit
  - Apple
  - Orange
  - Banana
- Dairy
  - Milk
  - Cheese

## Quote

> Two things are infinite: the universe and human stupidity; and I'm not sure about the
> universe.<br>
> — <cite>Albert Einstein</cite>

## Table Inline Markdown

| Italics   | Bold     | Code   | StrikeThrough     |
| --------- | -------- | ------ | ----------------- |
| _italics_ | **bold** | `code` | ~~strikethrough~~ |

## Foldable Text

<details>
    <summary>Title 1</summary>
    <p>IT'S A SECRET TO EVERYBODY.</p>
</details>

<details>
    <summary>Title 2</summary>
    <p>Stay awhile, and listen!</p>
</details>

## Code tags

Lorem ipsum `dolor` sit amet, `consectetur adipiscing` elit.
`Lorem ipsum dolor sit amet, consectetur adipiscing elit.`



The Apollo theme provides a default homepage that lists your recent blog posts. However, you might want to create a custom homepage that better reflects your personality and work. This guide will walk you through the process of creating a custom homepage with the Apollo theme.

## 1. Create a Custom Homepage Template

The first step is to create a custom homepage template. In the root of your Zola project, create a new file at `templates/home.html`. This file will contain the HTML for your custom homepage.

You can use the following code as a starting point:

```html
{% extends "base.html" %}

{% block main_content %}
    <main>
        <article>
            <section class="body">
                <h1>Welcome to my custom homepage!</h1>
                <p>This is where you can introduce yourself and your work.</p>
            </section>
        </article>
    </main>
{% endblock main_content %}
```

This template extends the theme's `base.html` template and overrides the `main_content` block with your own content.

## 2. Set the Homepage Template

Next, you need to tell Zola to use your custom homepage template. In the `content` directory of your Zola project, you should have a `_index.md` file. If you don't have one, create one.

In this file, add the following front matter:

```toml
+++
template = "home.html"
+++
```

This tells Zola to use the `templates/home.html` file to render your homepage.

## 3. Add Content to Your Homepage

Now you can add content to your homepage. The content of the `content/_index.md` file will be available in your `templates/home.html` template as the `section` variable.

For example, you can add a title and some introductory text to your `content/_index.md` file:

```toml
+++
title = "Hey there! 👋🏼"
template = "home.html"
+++

I'm a software engineer who loves to write about technology and programming.
```

You can then display this content in your `templates/home.html` template:

```html
{% extends "base.html" %}

{% macro home_page(section) %}
    <main>
        <article>
            <section class="body">
                {{ post_macros::page_header(title=section.title) }}
                {{ section.content | safe }}
            </section>
        </article>
    </main>
{% endmacro home_page %}

{% block main_content %}
    {{ self::home_page(section=section) }}
{% endblock main_content %}
```

## 4. Displaying Posts

You can also display a list of your recent posts on your homepage. The following code shows how to display the 5 most recent posts:

```html
{% extends "base.html" %}

{% macro home_page(section) %}
    <main>
        <article>
            <section class="body">
                {{ post_macros::page_header(title=section.title) }}
                {{ section.content | safe }}
            </section>
        </article>
    </main>
{% endmacro home_page %}

{% block main_content %}
    {{ self::home_page(section=section) }}

    <h1>Recent articles</h1>
    <main class="post-list">
        {% set section = get_section(path="posts/_index.md") %}
        {{ post_macros::list_posts(pages=section.pages | slice(end=5)) }}
    </main>
{% endblock main_content %}
```

This code gets the `posts` section and then uses the `post_macros::list_posts` macro to display the 5 most recent posts.

You can also highlight specific posts by getting them by their path:

```html
{% set highlights = [
    get_page(path="posts/my-first-post.md"),
    get_page(path="posts/my-second-post.md"),
] %}
<main class="post-list">
    {{ post_macros::list_posts(pages=highlights) }}
</main>
```

This is just a starting point. You can customize your homepage as much as you want.



# Site Configuration

## Search (`build_search_index`)

Enables or disables the search functionality for your blog.

- Type: Boolean
- Default: false
- Usage: `build_search_index = false`

When enabled, a search index will be generated for your blog, allowing visitors to search for specific content.
Additionally, a search button will be displayed in the navigation bar.

Configure the search like this:

```toml
build_search_index = true

[search]
include_title = true
include_description = true
include_path = true
include_content = true
index_format = "elasticlunr_json"
```

## Theme Mode (`theme`)

Sets the color theme for your blog.

- Type: String
- Options: "light", "dark", "auto", "toggle"
- Default: "toggle"
- Usage: `theme = "toggle"`

The "toggle" option allows users to switch between light and dark modes, while "auto" typically follows the user's system preferences.

## Menu

Defines the navigation menu items for your blog.

- Type: Array of objects
- Default: []
- Usage:
  ```toml
  menu = [
    { name = "/posts", url = "/posts", weight = 1 },
    { name = "/projects", url = "/projects", weight = 2 },
    { name = "/about", url = "/about", weight = 3 },
    { name = "/tags", url = "/tags", weight = 4 },
  ]
  ```

## Logo

Defines the site logo image file.

- Type: String
- Usage:
  ```toml
  logo = "site_logo.svg"
  ```

## Socials

Defines the social media links.

- Type: Array of objects
- Default: []
- Usage:
  ```toml
  socials = [
    { name = "twitter", url = "https://twitter.com/not_matthias", icon = "twitter" },
    { name = "github", url = "https://github.com/not-matthias/", icon = "github" },
  ]
  ```

## Table of Contents (`toc`)

Enables or disables the table of contents for posts.

- Type: Boolean
- Default: true
- Usage: `toc = true`

When enabled, a table of contents will be generated for posts, making it easier for readers to navigate through longer articles.

Note: This feature adds additional JavaScript to your site.

## CDN Usage (`use_cdn`)

Determines whether to use a Content Delivery Network (CDN) for assets.

- Type: Boolean
- Default: false
- Usage: `use_cdn = false`

When set to true, the theme will attempt to load assets from a CDN, which can improve loading times for visitors from different geographic locations.

## Favicon (`favicon`)

Specifies the path to the favicon image for your blog.

- Type: String
- Default: "/icon/favicon.png"
- Usage: `favicon = "/icon/favicon.png"`

This sets the small icon that appears in the browser tab for your website.

## Custom Stylesheets (`stylesheets`)

Allows you to add custom stylesheets to your blog.

- Type: Array of files located in the `static` directory
- Default: []
- Usage:
  ```toml
  stylesheets = [
    "custom.css",           # static/custom.css
    "/css/another.css"      # static/css/another.css
  ]
  ```

## Fancy Code Styling (`fancy_code`)

Enables enhanced styling for code blocks.

- Type: Boolean
- Default: true
- Usage: `fancy_code = true`

This option adds the language label and a copy button.

## Dynamic Notes (`dynamic_note`)

Allows for the creation of togglable note sections in your content.

- Type: Boolean
- Default: true
- Usage: `dynamic_note = true`

When enabled, you can create expandable/collapsible note sections in your blog posts.

## Anchor Links

You can add anchor links by adding the following to your `_index.md`:

```toml
insert_anchor_links = "heading"
```

## Taxonomy sorting

You can sort the taxonomies page with the following config:
```toml
[extra.taxonomies]
sort_by = "page_count"         # e.g. name, page_count
reverse = true
```

The `sort_by` argument is directly passed to the `sort_by` function:
```jinja
{% set sort_by = config.extra.taxonomies.sort_by | default(value="name") %}
{% set terms = terms | default(value=[]) | sort(attribute=sort_by) %}

{% if config.extra.taxonomies.reverse | default(value=false) %}
    {% set terms = terms | reverse %}
{% endif %}

{% for term in terms %}
    <li>
        <a href="{{ term.permalink | safe }}">
            {{ term.name }} ({{ term.pages | length }} post{{ term.pages | length | pluralize }})
        </a>
    </li>
{% endfor %}
```

Possible values include anything within the [TaxonomyTerm object](https://www.getzola.org/documentation/templates/taxonomies/):
```rust
name: String;
slug: String;
path: String;
permalink: String;
pages: Array<Page>;
page_count: Number;
```

Examples:
- `name` to sort by name
- `page_count` to sort by page count

## Analytics

Enable or disable analytics tracking:

```toml
[extra.analytics]
enabled = false
```

After enabling analytics, configure GoatCounter or Umami.

### GoatCounter

Configure GoatCounter analytics:

```toml
[extra.analytics.goatcounter]
user = "your_user"           # Your GoatCounter username
host = "example.com"         # Optional: Custom host
```

### Umami Analytics

Configure Umami analytics:

```toml
[extra.analytics.umami]
website_id = "43929cd1-1e83...."                    # Your Umami website ID
host_url = "https://stats.mywebsite.com"            # Optional: Custom host URL
```

---

# Page configuration

## Source code (`repo_view`)

Do you want to link to the source code of your blog post? You can turn on the `repo_view` inside the `[extra]` section of your blog post.

```toml
[extra]
repo_view = true
repo_url = "https://github.com/not-matthias/apollo/tree/main/content" # Alternatively add the repo here
```

The `repo_url` can be set in the `[extra]` section or in your `config.toml`.

## Comments (`comment`)

Enables or disables the comment system for posts.

- Type: Boolean
- Default: false
- Usage: `comment = false`

After making `comment = true` in `[extra]` section of you post, save your script from [Giscus](https://giscus.app) to `templates/_giscus_script.html`.
When enabled, this allows readers to leave comments on your blog posts. This feature has to be set for each individual post and is not supported at higher levels.

Example configuration in [content/posts/configuration.md](https://github.com/not-matthias/apollo/blob/main/content/posts/configuration.md):

```toml
+++
title = "Configuring Apollo"

[extra]
comment = true
+++
```

Comments via [utterances](https://utteranc.es) can be configured in `template/_giscus_script.html` like this:

```html
<script src="https://utteranc.es/client.js"
        repo="YOUR_NAME/YOUR_REPO"
        issue-term="pathname"
        theme="github-light"
        crossorigin="anonymous"
        async>
</script>
```

# Cards Page

The `cards.html` template allows you to display a list of items in a card format. This is ideal for showcasing projects, but can be used for any list of items you want to display in a visually appealing way.

To create a cards page, you need to create a `_index.md` file in a content directory (e.g., `content/projects`). The following front matter is recommended:

```toml
+++
title = "Projects"
sort_by = "weight"
template = "cards.html"
+++
```

Each item in the list should be a separate markdown file in the same directory. The following front matter is supported:

- `title`: The title of the item.
- `description`: A short description of the item.
- `weight`: The order in which the item appears on the page.
- `local_image`: A path to a local image for the item's thumbnail. See the [Local Image](#local-image) section for more details.
- `local_video`: A path to a local video for the item's thumbnail. See the [Local Video](#local-video) section for more details.
- `remote_video`: A URL to a remote video for the item's thumbnail.
- `link_to`: A URL the card should link to.

# Talks Page

To create a talks page, you need to create a `_index.md` file in the `content/talks` directory. The following front matter is recommended:

```toml
+++
title = "Talks"
sort_by = "date"
template = "talks.html"
+++
```

Each talk should be a separate markdown file in the `content/talks` directory. The following front matter is supported:

- `title`: The title of the talk.
- `description`: A short description of the talk.
- `local_image`: A path to a local image for the item's thumbnail. See the [Local Image](#local-image) section for more details.
- `date`: The date of the talk.
- `video`: A map with a `link` and `thumbnail` for the talk video.
- `organizer`: A map with a `name` and `link` for the event organizer.
- `slides`: A URL to the presentation slides.
- `code`: A URL to the source code.

# Local Image

The `local_image` front matter parameter allows you to specify a path to a local image that will be used as the thumbnail for a page. This is particularly useful for social media previews and other places where a representative image is needed.

The path resolution for `local_image` works as follows:

- If the path starts with a `/`, it is treated as an absolute path from the `content` directory. For example, `local_image = "/projects/project-1.jpg"` will resolve to `content/projects/project-1.jpg`.
- If the path does not start with a `/`, it is treated as a relative path. The theme will prepend the `section.path` to the `local_image` path. For example, if you are in a page at `content/posts/my-post/index.md` and you set `local_image = "thumbnail.png"`, the theme will look for the image at `posts/my-post/thumbnail.png`.

# Local Video

The `local_video` front matter parameter allows you to specify a path to a local video file that will be displayed as the thumbnail for a page. This is particularly useful for showcasing projects with dynamic content.

The path resolution for `local_video` works the same as `local_image`:

- If the path starts with a `/`, it is treated as an absolute path from the `content` directory. For example, `local_video = "/projects/demo.mp4"` will resolve to `content/projects/demo.mp4`.
- If the path does not start with a `/`, it is treated as a relative path. The theme will prepend the `section.path` to the `local_video` path. For example, if you are in a page at `content/projects/my-project/index.md` and you set `local_video = "demo.webm"`, the theme will look for the video at `projects/my-project/demo.webm`.

## Remote Video

The `remote_video` front matter parameter allows you to specify a URL to a remote video file that will be displayed as the thumbnail for a page.

Example usage:
```toml
[extra]
remote_video = "https://example.com/videos/demo.mp4"
```

The browser will automatically detect the video format, so you don't need to worry about specifying the MIME type.
