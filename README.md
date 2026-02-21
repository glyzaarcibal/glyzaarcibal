name: Generate snake animation

on:
  schedule: # execute every 12 hours
    - cron: "* */12 * * *"

  workflow_dispatch:

  push:
    branches:
    - main

jobs:
  generate:
    permissions:
      contents: write
    runs-on: ubuntu-latest
    timeout-minutes: 5

    steps:
      - name: generate snake.svg
        uses: Platane/snk/svg-only@v3
        with:
          github_user_name: ${{ github.repository_owner }}
          outputs: dist/snake.svg?palette=github-dark


      - name: push snake.svg to the output branch
        uses: crazy-max/ghaction-github-pages@v3.1.0
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}

###

<div align="center">
  <img src="https://streak-stats.demolab.com?user=glyzaarcibal&locale=en&mode=daily&theme=dracula&hide_border=false&border_radius=5&order=3" height="150" alt="streak graph"  />
  <img src="https://github-readme-activity-graph.vercel.app/graph?username=glyzaarcibal&radius=16&theme=react&area=true&order=5" height="300" alt="activity-graph graph"  />
</div>

###
