# Git checklists

If you've been learning **terminal** and **git** but need some practice, this is for you.

These checklists are intended as

- training wheels until you get used to riding solo

- a pop quiz to test yourself on terminal and git commands

- guidance in pursuit of the question that plagues you at the start of every project:

  "Where the *bleep* am I, and how do I drive this thing?"

Go through these for each project, until you've memorized how to do each step and they become second nature.

Until opening a dusty old project folder feels like a cool breeze on a Summer's day.

## Terminology

A directory is a folder. Dir is short for directory; three very common terms with the exact same meaning.

A repo is a version-controlled directory, i.e. one that contains a hidden `.git` dir. A common recommended setup is to initialize version control at the root level of each project folder.

## Checklists to run through

### Get comfortable in the file system

- Which directory am I in?

- Is this directory version-controlled?
  (In other words: is this directory currently a git repo?)
  (In other words: has git been initialized in this directory?)

- Do I accidentally have any nested repos (git repos inside of git repos)?

  (if these questions are challenging for your level of Git,
  then I wouldn't recommend creating nested repos on purpose,
  but they do often happen by accident and cause problems)
  
  Make sure none of the folders above this one (ancestors) are git repos.

  Make sure none of the folders inside this one (descendants) are git repos.

  Only the current directory should be a repo.

  Repos (version-controlled projects) should be siblings, or more distant relations,
  but not ancestors or descendants of another repo.

### Work on your repo

- Which branch am I on?

- Am I looking at the latest version of my project?

- What were the last few commits?

- What remote/s am I connected to?

- What the last thing I pushed? Check this in the CLI and GitHub

- Has everything in my working directory been (staged and then) committed?

- What's in my staging area?

- Does the code run how I'd expect right now?

#### Extra checks for projects that have a **package.json** file

- My terminal is open to the same dir as the **package.json** that belongs to my project.
Open it and check the project info if you're confused between several **package.json** files.
We don't need to do anything with **package-lock.json**, just leave it wherever you see it.

- I should have a **node_modules** dir.
If I don't have one, I need to run `$ npm i` but remember not to type the `$` — it just means
that the following things are intended for the terminal. Remember this, you'll see that `$` everywhere.

- Now that I have a **node_modules** dir, I also need to have a **.gitignore** file that says `node_modules` (just text, no quotes or trailing slash needed).
