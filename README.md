# Visiting-Card-Cropping
Step by Step CI CD Pipeline with Jenkins
```bash
step 1: Go to Jenlins Dashboard
step 2: Go to New Item
step 3: Enter an item name
step 5: Select pipeline
step 6: Press OK button
```

```bash
step 7: Select Discard old builds
```

Discard old builds: Enables you to automatically discard old builds to free up disk space. You can set rules to keep a certain number of builds or to keep builds for a certain number of days.

```bash
step 8: GitHub project
```

GitHub project: If the pipeline is linked to a GitHub repository, you can specify the GitHub project URL here. This can be used for integration with GitHub features like commit status updates.

```bash
In Build Triggers
step 9: Select GitHub hook trigger for GITScm polling
```

GitHub hook trigger for GITScm polling: Enables the pipeline to be triggered by GitHub webhook events. This allows the pipeline to start automatically when there are changes in the GitHub repository, such as code commits.

SCM (Source Control Management)
This field lets you select the type of source control system from which Jenkins will pull the pipeline script. Options commonly include Git, Subversion (SVN), etc.

```bash
step 10: Select SCM --> Git
```

Indicates that you are using Git as your source control management system. This means Jenkins will pull the pipeline script from a Git repository.

Repositories

```bash
step 11: Provide your Repository URL which you want to CI CD
```

This is where you specify the URL of your Git repository. Jenkins will use this URL to connect to your Git repository and fetch the pipeline script.

```bash
step 12: Provide your Git Credentials using Token of git
```

If your Git repository requires authentication, you can provide the necessary credentials here. This ensures that Jenkins can access the repository securely. If no credentials are needed, you can select "none."


Branches to Build

```bash
Branch Specifier (blank for 'any'):
step 13: Select your repo branch from where the Jenkins pull the code
```

Defines which branches in the repository Jenkins should build. If left blank, Jenkins will build from any branch. You can specify a particular branch, such as */master, to limit builds to that branch.

Script Path

```bash
step 14: Select Jenkins Script Path. If your jenkins file stay in a folder in your repo then use folder_name/Jenkinsfile 
```

Specifies the path within the repository to the Jenkinsfile. The Jenkinsfile contains the pipeline script that defines the stages and steps of the pipeline. By default, this is often set to Jenkinsfile, but you can specify a different path if your file is located elsewhere in the repository.

```bash
step 15: Press Save Button
```

