## Hi there 👋

<!--
**Divyesh1510/Divyesh1510** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->
### 🛠️ Tech Stack & Tools

<p align="left">
  <a href="https://skillicons.dev">
    <img src="https://skillicons.dev" />
  </a>
</p>
name: Generate Snake Animation

on:
  # Run automatically every 24 hours
  schedule:
    - cron: "0 0 * * *" 
  
  # Allows you to manually run the job at any time
  workflow_dispatch:
  
  # Run on every push to the main branch
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
      # Generates a snake game from a github user contributions graph, output a svg animation
      - name: generate github-contribution-grid-snake.svg
        uses: Platane/snk/svg-only@v3
        with:
          github_user_name: Divyesh1510
          outputs: |
            dist/github-contribution-grid-snake.svg
            dist/github-contribution-grid-snake-dark.svg?palette=github-dark
          
      # Push the content of <build_dir> to a branch
      # The content will be available at https://githubusercontent.com<github_user>/<repository>/<target_branch>/<file>
      - name: push github-contribution-grid-snake.svg to the output branch
        uses: crazy-max/ghaction-github-pages@v3.1.0
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
### 🐍 My Contribution Snake

![Snake Animation](https://githubusercontent.com)
