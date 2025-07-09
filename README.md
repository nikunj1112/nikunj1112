<div align="center">
  <img src="https://streak-stats.demolab.com?user=maurodesouza&locale=en&mode=daily&theme=dracula&hide_border=false&border_radius=5&order=3" height="150" alt="streak graph"  />
  <img src="https://github-profile-trophy.vercel.app?username=maurodesouza&theme=dracula&column=-1&row=1&margin-w=8&margin-h=8&no-bg=false&no-frame=false&order=4" height="150" alt="trophy graph"  />
</div>


name: Generate Snake Animation

on:
  schedule:
    - cron: "0 0 * * *" # Runs once a day at midnight UTC
  workflow_dispatch: # Allows manual execution

jobs:
  generate:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout repository
        uses: actions/checkout@v4

      - name: Generate Snake Animation
        uses: Platane/snk@v3
        with:
          github_user_name: Rohit-Pakhre09
          outputs: |
            dist/github-snake.svg

      - name: Commit and push
        run: |
          git config --global user.email "github-actions[bot]@users.noreply.github.com"
          git config --global user.name "GitHub Actions"
          git add dist/github-snake.svg
          git commit -m "Updated Snake Animation" || echo "No changes to commit"
          git push
