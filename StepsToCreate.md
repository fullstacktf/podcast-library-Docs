# site created with Eleventy, for the documentation of Podbuster.live



## Begin the Project 

`npm init`

`npm install @11ty/eleventy`

```jsx
  "scripts": {
    "start": "eleventy --serve",
    "build": "eleventy"
  },
```

## Add Eleventy Config

`.eleventy.js`

```jsx
module.exports = function (eleventyConfig) {
  return {
    dir: {
      input: "src",
      output: "public",
    },
  };
};
```

## Run the Develop Server

`npm run develop`

## Create the Site Index File

Create `src/`
Create `src/index.md`

## Create the `base` Layout

Create `_includes/base.njk`
Emmet: `html:5`

- `<title>{{ title }}</title>`

Add `layout: base.njk` to `index.md` frontmatter

```md
---
layout: base.njk
---
```

_Optional_: Create `src/about.md`

## Use Frontmatter in the Layout

Within `base.njk`- Emmet: `header>h1` with value `{{ title }}`

## Create the Blog

Create `blog/`
Create `front-end.md`

## Create the `post` Layout

Create `_includes/post.njk`

Content:

```js
<article>
{{ content | safe}}
</article>
```

## Chain the `post` Layout to the `blog` Layout

In `post.njk` add frontmatter:

```md
---
layout: base.njk
---
```

## Create `blog` Directory Data File

Create `blog/blog.json`

```jsx
{
  "layout": "post"
}
```

## Modify the Blog Post Permalinks

```jsx
{
  "layout": "post",
  "permalink": "/{{ page.fileSlug }}/"
}
```

## Create `posts` Collection Via `tags`

```jsx
{
  "layout": "post",
  "permalink": "/{{ page.fileSlug }}/",
  "tags": "posts"
}
```

## Display `posts` Collection on Home Page

Add to `index.md`:

```jsx
## Blog Posts

{% for post in collections.posts %}
{{ post.data.title }}
{% endfor %}
```

## Create Linked List of Posts

Modify previous `for` loop:

```jsx
<ul>
{% for post in collections.posts %}
<li><a href="{{ post.url }}">{{ post.data.title }}</a></li>
{% endfor %}
</ul>
```

## Create Partial from Blog Post Links

Create `_includes/postlist.njk`

Update `index.md` to use `{% include "postlist.njk" %}`

## Instruct 11ty How to Handle Template Processing

Add `templateEngineOverride: njk,md` to `index.md` frontmatter

## Create CSS File

Create `css/`

Create `css/style.css`:

```css
body {
  font-family: sans-serif;
}
```

## Passthrough CSS

Modify `.eleventy.js`:

```jsx
eleventyConfig.addPassthroughCopy("./src/css");
```

## Link to Stylesheet in `base` Layout

`<link rel="stylesheet" href="/css/style.css" />`

## Custom Data

Create `_data/`

Create `_data/facts.json`:

```json
[
  "Did you know horses can swim?",
  "Did you know that the average human can hold their breath for 2 minutes?",
  "Did you know that we live on Earth?"
]
```

## Add `facts` Loop to `post` Layout

Add after `article` in `_includes/post.njk`:

```jsx
<aside>
{% for fact in facts %}
<p>{{ fact }}</p>
{% endfor %}
</aside>
```


Add within the `module.exports` in `.eleventy.js`

```jsx
eleventyConfig.addFilter("randomItem", (arr) => {
  arr.sort(() => {
    return 0.5 - Math.random();
  });
  return arr.slice(0, 1);
});
```

## Add to `facts` Loop

`{% for fact in facts | randomItem %}`

```

## Push to Github

Create a repo and push project to Github (_instructions outside the scope of these steps_).

## Deploy to Github pages
