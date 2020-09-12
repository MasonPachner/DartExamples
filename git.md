# Git

- Git overview
  - Git is a tool that records the history of a project and manages multiple developers
  - A repository is a collection of Git history
  - Local repository (Git history on your machine)
    - To save your work locally, Git has a process called "Committing". A commit is a set of differences
    between the current state and the previous state.
    - Your local repository is a collection of all changes you have committed on your computer
    - To add new changed to your local repository, you must stage and commit your changes
      - Staging is selecting what files you want to commit.
    - Whenever you have made a discrete change to a file, press the green check. This will give you
    an overview of everything that has happened. The top panel will show all files that have changed.
    The middle panel is where you put in a message about what you changed in your commit (i.e. Changed
    profile widget to use Database queries). The bottom panel gives you a more precise view of what
    has changed in a file. (You can expand the panel.) On the right side on the screen I would advise
    checking "Reformat code", "Optimize imports", and "Preform code analysis". Once you are done, press 
    commit.
    - This will update your local repository.
    
## Branches (Collections of commits)
    - Branches are collections of commits. We use them to separate work into discrete units.
      - An example branch may be "collapsing-profile-card", which may contain a set of commits where you
      modify the profile tab to have a collapsing profile card.
    - The main branch of a Git repository is called "master". It is bad practice to modify master directly
    - Creating a new branch, and changing your current branch is called "Checking out".
    - Branches can be passed between repositories, and I'll get into that after Remote Repositories
    - The "Head" of your project is on the current branch you are on. By default this is on the master
    branch. Checking out a branch changes your head to the new branch.
    - When you create a new branch, the history of the branch is identical to the branch you checkout from
    - When you add a new commit to the branch, only the current branch has that commit in history.
    - The process of bringing two branches back together is called "Merging".
    - The proper order of merging is to have your head on the branch with new commits, and merge in the old
    branch.
      - On Git Extensions, this is very easy to do. Select your branch on the left side of the screen. (It
      is probably already selected if you have been working on it.). Next, right click the branch you wish to 
      merge into, and merge into current branch -> (Select the branch)
  - Remote repositories (Online repositories, called "Remotes")
    - To make your local changes viewable by other developers, you need to upload your current repository
    to a remote repository. This process is called "Pushing".
    - Without pushing, you cannot collaborate with the rest of the team
    - On a solo project, it is still a good idea to have a remote repository to you can edit the code on 
    other devices and have a backup on a separate device
    - The default remote name is "origin"
    - In the same screen as committing, (Green checkmark), you can select the dropdown on the commit button
    and select commit and push. I would advise doing this instead of just committing.
    - If you have commits (Local repository changes) that have not been pushed, you can access the push 
    menu by pressing (Ctrl + Shift + k) and push commits there.
    - Other developers may have created changes since you have worked on your code, so you may need to update
    your local repository from the remote repository. This process is called "Pulling". How we have setup
    the project, pulling will likely not be a process you use in Android Studio.
  - Bringing a remote repository to a local repository (Setup)
    - The initial pull of a remote repository to a local repository is called a "Clone"
    - You will do this when you setup your Android Studio project.
## Team Programming with Git
    - The master online repository is called "Upstream". Upstream does not get directly merged into.
    - Forks are clones of repositories. Every team member should have their own fork of the upstream repository
      - To fork the upstream repository, go to the upstream repository on Bitbucket, select the plus
      sign on the left side of the screen and say "Fork this repository". I named mine "dumb-bell-mason" to 
      distinguish it from the upstream ("dumb-bell").
    - Create branches on the master branch of your fork.
    - When you have finished your branch, do not merge it into your master branch. Instead, create a "Pull Request"
      - On Bitbucket, go to your fork and select pull requests. Create a pull request of your feature branch into
      the upstream master branch. (jnhyatt/dumb-bell, master). Do not select remove branch when approved.
    - Pull requests are safe methods of moving new features into the upstream branch.
    - Pull requests must be reviewed by other members of the dev team. You can choose who is on the list of
    reviewers when your create the request, but you must select Mason and Josh.
    - Pull requests are managed inside Bitbucket. Reviewers can post comments and critiques on the changes. While
    your code is under review, you can still add commits to your branch (Just be sure to push!). The pull request
    will automatically update.
    - Once your pull request has been approved, a GUARDIAN OF THE UPSTREAM REPOSITORY (Josh or Mason), will merge it in.
    - Once ANY pull request has been approved and merged, you should update your fork to have the most recent
    code.
      - To update your fork with other remotes, click the dropdown next to the blue down arrow (Pull) and
      select fetch and prune all. You will have to confirm the fetch and prune.
      - To do this in Git Extensions, checkout your master branch, right click the upstream/master branch
      and select merge into current branch -> upstream/master. Make sure fast-forward is selected, and confirm.
    - If the pull request was your branch, you may delete it from your local and remote repositories.
      - In Git Extensions, right click the branch and select delete branch. (Be sure to get your local and remote)
      You will have to confirm the remote branch delete.
    - In Git Extensions, you can add other team member's remotes. This way you can checkout their branches
    and help them out / test their branch. Do not make changes to a team member's remote without their 
    permission.
 ## Merge conflicts (Uh-ohs)
    - "Merge conflicts" are when a branch is merged into another but git cannot find a safe way to merge
    the code. This occurs when changes have occurred in the same location in a file, so Git is not sure
    what the correct code is.
    - It is good to ask for help if you run into them.
    - To solve a merge conflict, just select which branch you want to accept the changes from.
    - Example. Josh changes a file in his branch from "x=1" to "x=3", and Mason changes the same file in his branch
     to "x=5". No conflict occurs until Mason's branch gets merged in after Josh's and now Git cannot 
     figure out how to merge the file at that location. You select the correct version, say "x=3",
      and the merge conflict is now resolved
    - Sometime you might not know what the correct version should be, so you can check with who owned the branch that you had a merge conflict with to decide.
    - Merge conflicts can happen in individual or team projects, there just needs to be at least 2 branches 
    and a merge on a file location with conflicting edits.
  - What you should have learned (Key topics)
    - Repositories, Commits, Branches, Pushing, Pulling, Pull Requests, Merge Conflicts.
    
## Quick git (review)
  - In Git Extensions, fetch and prune all
  - Make sure your "master" branch is up to date with upstream master
    - "checkout" (Change to) your master branch
    - right-click upstream master and select merge into current branch -> upstream/master
  - Create a new branch, give it a descriptive name (i.e. profile-progress-menu)
  - Code!
    - Commit and push changes often
    - Different colors on the filenames in Android Studio mean different things
      - Yellow files are NOT TRACKED by Git. No edit you make there will change anything
      - White files are tracked, but have no updates since the last commit
      - Blue files have un-commited changes
      - Green files are new files that will be tracked
      - Red files are new files that will not be tracked
  - When the feature is complete (And building!) submit a pull request
    - On your Bitbucket forked repository, goto pull requests and create a new request
      - Select the branch you are working on and the upstream master branch
  - Once the pull request has been accepted, delete your local and remote branches 
