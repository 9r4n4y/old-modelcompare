# Blind A/B Voting

## Intent

Make the comparison site default to a blind A/B experience so visitors judge outputs before seeing model names. After voting, reveal the model names and show current aggregate results. Keep the full labeled gallery available as a secondary view.

## Desired Experience

- First-time visitors land on a blind comparison, not the labeled gallery.
- The page shows two anonymous live previews labeled only A and B.
- Visitors can choose A, choose B, mark a tie, or skip.
- After a choice, the site reveals both model names and records the vote.
- Visitors can continue to another randomized matchup.
- Visitors can open the full labeled gallery when they want to inspect all outputs directly.
- Visitors can open a leaderboard showing aggregate results.

## Voting Rules

- Pairings should be randomized.
- A/B side order should be randomized.
- A model should not be paired against itself.
- A visitor should not repeatedly see the same pair until other pairs have been exhausted locally.
- Votes should be anonymous.
- Store a local browser identifier only for light duplicate/rate control; do not ask users to sign in.

## Leaderboard

- Show a clear ranking of models from aggregate blind votes.
- Include total votes, wins, losses, ties, and a simple win-rate style score.
- Make clear that results are informal and based on visitor votes, not a controlled benchmark.

## Backend

- Use Cloudflare Workers with D1 for public vote aggregation.
- Provide endpoints for submitting a vote and reading leaderboard/pair summary data.
- Apply basic validation and light abuse controls.
- Do not require secrets in the static frontend.

## Site Framing

- Use neutral naming: "Canvas Car Scene Compare".
- Do not make the page sound like a promotion for any harness.
- Keep attribution links available but secondary: the Reddit inspiration post and the source harness repository.

## Acceptance Criteria

- The default public page starts in blind A/B mode.
- The full labeled gallery remains reachable.
- A vote reveals model names after selection.
- Aggregate leaderboard updates from stored public votes.
- The site remains static-hosted on GitHub Pages, with only voting handled by Cloudflare.
