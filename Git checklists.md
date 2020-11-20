# Git checklists

If you've been learning **terminal** and **git** but need some practice, this is for you.

These checklists are intended as

- training wheels until you get used to riding solo

- a pop quiz to test yourself on terminal and git commands

- guidance in pursuit of the question that plagues you at the start of every project:

  "Where the *bleep* am I, and how do I drive this thing?"

Go through these for each project, until you've memorized how to do each step and they become second nature.

Until opening a dusty old project folder feels like a cool breeze on a Summer's day.

## Checklist to run through

- Which directory am I in?

- Which branch am I on?

- Am I looking at the latest version?

- What were the last few commits?

- What remote/s am I connected to?

- What the last thing I pushed? Check this in the CLI and GitHub

- Has everything in my working directory been (staged and then) committed?

- What's in my staging area?

- Does the code run how I'd expect right now?

## Extra checks for projects that have a **package.json** file

- My terminal is open to the same dir as the **package.json** that belongs to my project.
Open it and check the project info if you're confused between several **package.json** files.
We don't need to do anything with **package-lock.json**, just leave it wherever you see it.

- I should have a **node_modules** dir.
If I don't have one, I need to run `$ npm i` but remember not to type the `$` — it just means
that the following things are intended for the terminal. Remember this, you'll see that `$` everywhere.

- Now that I have a **node_modules** dir, I also need to have a **.gitignore** file that says `node_modules` (just text, no quotes or trailing slash needed).
