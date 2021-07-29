# Hugo Firebase Action
Github Action which builds a static HTML/CSS site from your Hugo site Github repository and deploys it on the Firebase Hosting.

# Usage
Add a simple example Github Action workflow like this in your Github Hugo site repository at `.github/workflows/main.yml`

```yaml
# This is a simple workflow to build a Hugo site and then deploy it on Firebase Hosting 

name: Set Hugo-On-Fire

# Triggers when any commit is pushed on Master
on:
  push:
    branches: [ master ]

jobs:
  build:
    # The type of runner that the job will run on
    runs-on: ubuntu-latest

    # Steps represent a sequence of tasks that will be executed as part of the job
    steps:
    # Checks-out your repository under $GITHUB_WORKSPACE, so your job can access it
    - uses: actions/checkout@v2

    # Fetch Hugo to Firebase docker image
    - uses: streamprocessor/hugo-firebase-action@master
      env:
        FIREBASE_TOKEN: ${{ secrets.FIREBASE_TOKEN }}
```

# Add Firebase Token as Github Secret 
You also need to add your Firebase Hosting's token as a Github Secret. You can get it using command `'firebase login:ci'` and then set it in Github Secrets as `FIREBASE_TOKEN` variable.
