
<!--

HELLO AND WELCOME TO THE TODO
=============================

GUIDE PEOPLE THROUGH SETTING UP THEIR FIRST EVER PACKAGE.JSON
Because that is your audience here.

WTF IS THIS node_modules/ thingy? And why do I not want to commit it?

SHOW THEM WHAT SCRIPTS TO ADD IN.
They might have this "test" one already that they don't need just yet
Outline those in beautiful detail.

In the video you can be like "sayHi": "echo heeiiiii" to illustrate what scripts do

-->

# CSS pipeline

This `package.json` file contains handy scripts that process CSS from dev to production as follows:

Sass => CSS => Autoprefixed CSS for whichever browsers you want to support

## Why should I care?

Here are some reasons you might have been crying, that this pipeline hopes to help with:

- I want to code HTML and CSS without trying to figure out what a bundler even is.
- I want to write Sass because it has nicer features than plain CSS.
- I want to write modern CSS but still support older browsers as much as possible.
- I've heard I'm supposed to [add prefixes](https://autoprefixer.github.io/) to my CSS to get this browser support, but I want the prefixing to be handled automatically, so I don't have to think about it.

<!-- TODO: Will this code make me cry? Pre-requisite knowledge and installed node version -->

## File system starting point

Here's what my project directory looks like.

`main.scss` has one job, which is to load [Sass partials](https://sass-lang.com/guide#:~:text=A%20partial%20is%20a%20Sass,used%20with%20the%20%40use%20rule.). No style rules are in this file.
Style rules are defined in partials.
This project example has just one partial, `_base.scss`, but a real-world project will usually have more.

The `modules/` dir is optional. We can organise your Sass partials however we like, depending on what structure makes life easier for each project. People have different ways they like to do this, and many have published articles about it. Google *sass file structure something something* for ideas. With practice, you'll find what works for you.

```fs
.
├── README.md
├── index.html
├── node_modules/
├── package-lock.json
├── package.json
└── src
    └── scss
        ├── main.scss
        └── modules
            └── _base.scss
```

## Usage

### Install (do this once at the start of each project)

Install the latest versions of the tools needed for this pipeline.

#### Understand what we're about to install

We are going to install the following packages as "dev dependencies", because they're tools that we only need during development (our users never have to run them, otherwise they would just be regular "dependencies").

I'm going to list them in the order that makes it easier to explain, but you may find them listed alphabetically elsewhere.

| Package        | Why         | Docs worth reading |
| :------------- | :---------- | :----------------- |
| `dart-sass`    | Takes our Sass and compile it into CSS | [Sass](https://sass-lang.com/) |
| `autoprefixer` | Creates new CSS with the required prefixes, based on our CSS and our list of supported browsers | [Autoprefixer](https://github.com/postcss/autoprefixer/blob/master/README.md) |
| `postcss`      | Allows autoprefixer to do its job |
| `postcss-cli`  | Allows us to use an npm script to handle autoprefixing |

#### Install stuff

```console
$ npm install --save-dev dart-sass autoprefixer postcss-cli postcss
```

#### Check it worked

This should update `package.json` to include devDependencies similar to the following (your version numbers may vary, since you'll get the latest):

```json
  "devDependencies": {
    "autoprefixer": "^10.0.3",
    "dart-sass": "^1.25.0",
    "postcss": "^8.1.10",
    "postcss-cli": "^8.3.0",
  }
```

### Dev script (keep this running during development)

Every time `main.scss` changes (or any of the partials it's loading), compile SCSS to CSS with a source map.

```console
$ npm run dev
```

Run this in a terminal that you keep open, so it can run in the background and actively watches for every time you hit 'save' on your Sass files. When you need to stop the process, hit `Ctrl + c` (or close the terminal window). You should stop the process when you're happy with how things look, and you don't need to make any more style changes.

This script creates two files at the project root (the same folder that contains `index.html` above), based on the contents of `src/scss/main.scss`:

- style.css
- style.map.css

The source map `style.map.css` is useful so that our browser dev tools can tell us exactly which Sass files are responsible for each style. This way, when we need to make a change, it's easy to see where to do that.

Without the source map, the dev tools would just give us a very unhelpful "lol I just got the style from style.css. You figure out which Sass file, buddy."

In `index.html`, it is enough to just link to `style.css`. The browser will detect the source map automatically.

### Build scripts (run once before shipping to production)

Remove source map because it messes with Autoprefixer

```console
$ npm run build
```

This one command will run two scripts in sequence:

1. prebuild script
  a. Remove files that mess with Autoprefixer: `style.map.css`
  b. Compile Sass to a new temporary file: `src/no-prefix.css`

2. build script
  Use Autoprefixer to take all the styles from `src/no-prefix.css` (created in the previous step) and create a new file with added prefixes at `style.css` (this overwrites the one generated by `npm run dev`).

  Prefixes are added depending on CSS features supported by the browsers that are listed in `package.json` under `browserslist`. We should update this list according to the browser support required for each project. See the [Browserslist docs](https://github.com/browserslist/browserslist/blob/master/README.md) to learn what kinds of values are valid here.

  <!-- TODO: update build script to minify the output -->

## Troubleshooting

If you get this error after running ```npm run build```

```console
rm: ./style.css.map: No such file or directory
```

It might be because ```npm run dev``` creates a file that ```npm run build``` expects to delete.
<!-- TODO: update build script to first check if files exist before attempting to remove them -->

To fix it, try this:

1. Run ```npm run dev```
2. Save one of your Sass files so that `style.map.css` is automatically created
3. Stop ```npm run dev```
4. Try again to run ```npm run build```

If you run into problems and Google is no help, please feel free to [file an issue](https://docs.github.com/en/free-pro-team@latest/github/managing-your-work-on-github/creating-an-issue).
