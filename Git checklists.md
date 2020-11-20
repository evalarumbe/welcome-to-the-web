# Git checklists

These checklists are intended as training wheels for incorporating git into daily practice, after doing beginner tutorials on terminal commands and git.

Go through these for each project, until you've memorized the commands you need for each step, and they become second nature.

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

- My terminal is open to the same dir as the package.json that belongs to my project. Open it and check the project info if you're confused between several package.json files. We don't need to do anything with package-lock.json but it should stay there and be included in your commits if it changes.

- I should have a node_modules dir (if I don't have one, I need to run $ npm i and remember not to type the $ — it just means that the following things are intended for the terminal. I'll totally quiz you on this)

- Now that I have a node_modules dir, I also need to have a .gitignore file that says node_modules (just text, no quotes or trailing slash needed)
