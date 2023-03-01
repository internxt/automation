# automation
Automation release and notify

Example of use:
```
name: Use reusable workflow

on:
  pull_request:
    types: [ closed ]
    
jobs:  
  reusable:
    if: github.event.pull_request.merged == true
    uses: internxt/automation/.github/workflows/release-notify.yml@master
    with:
      github_username: MyUser
      github_email: MyUser@email.com
      repository: github.com/repository/project.git
      folder: project
      product: "Product"
      platform: "Platform"
      supported_platforms: "Chrome, Firefox, Safari and Brave, for example"
      repository_name: ${{ github.event.repository.name }}
      request_body: ${{github.event.pull_request.body}}
      branch: master
    secrets:
      gh_token: ${{ secrets.GH_TOKEN }}
      slack_webhook_url: ${{ secrets.SLACK_WEBHOOK }}
```
