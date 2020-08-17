# Guest Lecture - Practical Development for Teams

- Never assume that your teammates code is correct.

## Workflows

- How is your team going to keep track of who's working on what?
- How is your team going to plan, scope, and ticket features?
- How is your supervisor going to see your progress?

### Trello Board

- Lists to have on board
  - Backlog
  - Doing
  - Review
  - Blocked
    - Needs another card to be completed first
  - Done

### Units of Estimation

- Ideal Days
  - If everything goes to plan, we expect $X$ to take $Y$ days.
- Story Points
  - The difficulty to implement the user story, usually accounting for risks, complexity, and size.
- Affinity Grouping
  - Features/Stories are grouped together in tiers, where each tier holds a similar level of "work".

Methods

- Planning Poker
  - Tickets are prepared ahead of time.
  - The team plays poker to decide how much work in their unit the ticket is worth.

### Development

1. Move ticket to "Doing".
   1. Ensure the ticket/card is correct.
2. Checkout feature branch.
   1. Checkout master and ensure its up to date.
   2. Checkout your feature branch using the agreed convention.
   3. `git checkout -b username/ticket_name`.
3. Code.
   1. Test locally.
   2. Check master for any new merges.
4. Move ticket to review.
5. Create pull request.
   1. Push to remote.
   2. Open pull request.
6. Merge and deploy.
   1. Protect master branch.
   2. Require approval before merge.

## Pipelines

Continuous Deployment

- Your code is packaged and delivered automatically to deployed resources.

Deployment Pipeline

- What happens between your code being merged into master and being run on your deployed resources.

### Practical Pipelines

Situation

- React frontend, node backend
- Repo on GitHub
- Server on DigitalOcean
