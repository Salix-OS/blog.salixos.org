# blog.salixos.org

This is the Salix blog, found at [blog.salixos.org](https://blog.salixos.org).
It is written with [Hugo](https://gohugo.io/).

## Making new posts

To make a new post, create a new markdown file in `content/post` with:

```
hugo new content/post/my-post-title.md
```

At this time, this uses hugo version 0.111.3. There might be breakages,
especially with the theme, if you use a newer version.

## Cloning this repo

You need to clone this repo, including the submodule which contains the theme
we're using. Also, you need to clone the `source` branch instead of the
`master` branch, this is where the markdown files are. So, run:

```
git clone -b source --recursive git@github.com:Salix-OS/blog.salixos.org.git
```

## Publishing the blog

The `master` branch
includes the files that are used for publishing and can be updated by running:

```
make publish
```

The `master` branch resides inside the `public` directory.
**You should not update it manually**, only by using the above command.
The contents of the `master` branch are used by Github pages to show the
actual blog.

