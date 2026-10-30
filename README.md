name: Profile Summary Cards

on:
  schedule:
    - cron: "0 0 * * *"   # cập nhật mỗi ngày
  workflow_dispatch:       # cho phép bấm chạy tay

jobs:
  build:
    runs-on: ubuntu-latest
    permissions:
      contents: write
    steps:
      - uses: actions/checkout@v4
      - uses: vn7n24fzkq/github-profile-summary-cards@release
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
        with:
          USERNAME: ${{ github.repository_owner }}
          BRANCH_NAME: main
          UTC_OFFSET: 7
