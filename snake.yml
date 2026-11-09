name: Generate Snake

on:
  schedule:
    - cron: "0 */12 * * *"   # อัปเดตทุก 12 ชั่วโมง
  workflow_dispatch:          # กดรันเองได้จากแท็บ Actions
  push:
    branches: [main]

permissions:
  contents: write

jobs:
  generate:
    runs-on: ubuntu-latest
    steps:
      - name: Generate snake SVGs
        uses: Platane/snk@v3
        with:
          github_user_name: ${{ github.repository_owner }}
          outputs: |
            dist/github-snake.svg
            dist/github-snake-dark.svg?palette=github-dark&color_snake=#00F723&color_dots=#161b22,#0e4429,#006d32,#26a641,#39d353

      - name: Push to output branch
        uses: crazy-max/ghaction-github-pages@v4
        with:
          target_branch: output
          build_dir: dist
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
