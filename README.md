name: Generate Snake SVG

on:
  push:
    branches:
      - main  # or your desired branch

jobs:
  generate:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v2
        
      - name: Generate Snake SVG
        uses: Platane/snk@v3.3.0
        with:
          github_user_name: spencergit-tech
          github_token: ${{ secrets.GITHUB_TOKEN }}  # Use the default token
          outputs: dark.svg?palette=github-dark&color_snake=blue

      - name: Upload Snake SVG
        uses: actions/upload-artifact@v4  # Updated to v4
        with:
          name: snake-svg
          path: dark.svg
