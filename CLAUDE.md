# Admin Dashboard: how we work

An HTML/CSS practice project that rebuilds `Admin Dashboard final look.png`. All layout uses CSS Grid (no flexbox), the icons are inline MDI SVGs and the font is Roboto.

## Where things are
- **Tasks:** [.todo4vcode/shared-tasks.json](.todo4vcode/shared-tasks.json). This is the todo4vcode board with tasks `AD-01` … `AD-13`, in order.
- **Plan:** [docs/implementation-plan.md](docs/implementation-plan.md) has the design tokens, the grid layout and the commit message for each task.
- **Mockup:** `Admin Dashboard final look.png`.

## Picking up where we left off
Open the task file. The next task is the first one whose status isn't `Done`. If a task is `In Progress`, finish it first.

## Workflow per task
1. Set the task's `status` to `In Progress`.
2. Implement only that task, and tick its `subtasks` as each one is done.
3. Check the result in a browser at 1440px, plus 1024, 768 and 375px for the responsive tasks.
4. When it's finished, add code-reference tags such as `index.html:18-24` or `styles/style.css:26-54` to its `tags`, and set `status` to `Done` and `completed` to `true`.
5. Propose the commit message and **wait for an OK** before committing.

## Commits
- One commit per task, with the task ID as the scope, e.g. `feat(AD-04): build sidebar navigation`. The exact messages are in the task descriptions and the plan.
- Include the task file update in the same commit.
- **Never** add `Co-Authored-By` or any other Claude/AI attribution line, in commits or in PRs.
- Changes that don't belong to a task (docs, tooling) use no scope, e.g. `docs: ...`.
- Don't run `git push`. Pushing is the user's job, and the editor may sync on its own after a commit.
