# Git Branching Exercise

This repository contains a simple exercise to practice Git branching and merging.

## Forking this Repository

To get started, you need to fork this repository to your own GitHub account. Follow these steps:
1. Go to the GitHub page of this repository.
2. Click on the "Fork" button in the top-right corner of the page.
3. Select your GitHub account as the destination for the fork.
4. Wait for GitHub to create the forked repository in your account.
5. Once the fork is complete, you will be redirected to your forked repository.
6. Copy the URL of your forked repository from the address bar of your browser.
7. Open a terminal on your local machine.
8. Change to the directory where you want to clone the repository (e.g. `cd ~/Desktop`).
9. Clone the forked repository to your local machine by running the following command, replacing `<your-username>` with your GitHub username:
   ```
   git clone https://github.com/<your-username>/software-dev-course-git-branching.git
   ```

## Running the Application

This repository contains a simple Node.js application. To run the application, follow these steps:

1. Open a terminal and navigate to the project directory.
2. Install the dependencies by running:
   ```
   npm install
   ```
3. Start the application by running:
   ```
   npm start
   ```

Once you have run the application, you should see a message in the terminal saying "Hello, World!", 
and the numbers 0 to 9 printed on separate lines.  If you want to understand the application, you 
can review the code in `src/index.js`.  It is not a very complicated application, and it is not
very important to understand it fully for the purposes of this exercise.

## Opening the Application in VS Code 

To open the project in Visual Studio Code, follow these steps:
1. Open Visual Studio Code.
2. Click on "File" in the top menu and select "Open Folder...".
3. Navigate to the directory where you cloned the repository and select it.
4. Click "Select Folder" to open the project in VS Code.

## Making a Simple Commit

First, let's make a small change to the application and commit it to the `main` branch.
1. Open the `src/index.js` file in VS Code.
2. Add a comment at the top of the file with your name and the date, like this:
   ```javascript
   // [Your Name] - [Date]
   ```
3. Save the file.
4. Click on the Source Control icon in the left sidebar of VS Code.
5. You should see the modified `src/index.js` file listed under "Changes".
6. In the "Message" box at the top, type a commit message like "Add author comment".
7. Click the checkmark icon to commit the change to the `main` branch.

![A Simple Commit](doc-images/simple-commit.png)

Verify your commit by looking at the "Graph" section in the Source Control panel.
You should see your new commit at the top of the list.

## Adjusting the Graph View

Throughout this exercise, we will be working with branches, which can make the commit graph more complex.
We are going to adjust the graph view in VS Code to make it easier to see branching and merging.

To adjust the graph view to make it easier to see branching and merging, follow these steps:

1. Locate the "Graph" section in the Source Control panel.
2. Click the picture of the branch icon with the word "Auto" next to it.
3. From the dropdown menu at the top of the screen, choose "All".
4. This will display all branches and their commits in the graph view.

![Adjusting the Graph View](doc-images/adjust-graph-view.png)

Nothing will change in the graph view yet, but as we create branches and make commits,
you will start to see the branching structure more clearly.

## Creating a New Branch

Next, let's create a new branch for our next set of changes:

1. At the very bottom of the "Graph" section in the Source Control panel, click on the current branch name (which should be `main`).

![Branch Selection](doc-images/branch-selection.png)

2. In the dropdown menu that appears, click on "Create new branch".
3. Enter `feature-square` as the name of the new branch and press Enter.
4. VS Code will switch to the new `feature-square` branch automatically.
5. You can verify that you are on the `feature-square` branch by looking at the bottom-left corner of VS Code, where the current branch name is displayed.

## Making Changes in the New Branch

Now that we are on the `feature-square` branch, let's make some changes to the application:

1. Open the `src/index.js` file in VS Code.
2. Locate the line that says `console.log(i);` inside the `for` loop.
3. Add a new line below it that squares the number before logging it, like this:
   ```javascript
   console.log(i * i);
   ```
4. Save the file.

The completed file should look like this:

```javascript
// Michael Lambert 10/19/2025

console.log("Hello world!");

for (let i = 0; i < 10; i++) {
    console.log(i);
   console.log(i * i);
}
```

5. Click on the Source Control icon in the left sidebar of VS Code.
6. You should see the modified `src/index.js` file listed under "Changes".
7. In the "Message" box at the top, type a commit message like "Log square of numbers".
8. Click the checkmark icon to commit the change to the `feature-square` branch.

![Commit in New Branch](doc-images/commit-in-new-branch.png)

You should see your new commit at the top of the list in the "Graph" section,
and will notice that the "main" label is still on the previous commit, indicating that
the `main` branch has not been updated with your new commit.

While, we have branches at this point, and they are on different commits, we have not yet
created any divergence in the commit history.  Main is simply a step behind `feature-square`.
This is why we aren't really seeing "branching" in the graph view yet, just labels that are
at different points in history.

## Updating the Main Branch

Now, let's switch back to the `main` branch and add a bit more to our comment header.

1. At the very bottom of the "Graph" section in the Source Control panel, click on the current branch name (which should be `feature-square`).
2. In the dropdown menu that appears, click on `main` to switch back to the `main` branch.
3. Open the `src/index.js` file in VS Code.  Notice that the squaring line we added in the `feature-square` branch is not present here.
   This is because we are now viewing the code as it exists in the `main` branch which is one commit behind.
4. Update the comment at the top of the file to include the purpose of the application, like this:
   ```javascript
   // [Your Name] - [Date]
   // This application prints "Hello, World!" and the numbers 0 to 9.
   ```
5. Save the file.
6. Click on the Source Control icon in the left sidebar of VS Code.
7. You should see the modified `src/index.js` file listed under "Changes".
8. In the "Message" box at the top, type a commit message like "Update author comment with purpose".
9. Click the checkmark icon to commit the change to the `main` branch.

And now, we have divergence in the commit history!  The `main` branch and the `feature-square`
branch have both advanced from their common ancestor commit, but they have different changes.
You should now see branching in the graph view, with the `main` and `feature-square` branches
pointing to different commits that originate from a common ancestor:

![Diverged Branches](doc-images/diverged-branches.png)

You should try clicking the bottom-left branch indicator to switch between branches while index.js
is open in the editor.  Notice how the contents of the file change based on which branch you are on.
Notice that both have made changes, but the changes are different.

## Merging the Feature Branch

Finally, let's merge the changes from the `feature-square` branch back into the `main` branch.
Remember that for merging, we need to be on the branch that we want to merge *into*, that is the
*target* branch.  In this case, we want to merge `feature-square` *into* `main`, so we need to
be on `main` when we do the merge.  If you are not on `main` already, switch to it now by clicking
the branch indicator in the bottom-left corner of VS Code and selecting `main`.

Once you are on the `main` branch, follow these steps to perform the merge:

1. Click on the Source Control icon in the left sidebar of VS Code.
2. Click on the three-dot menu icon next to the "Changes" header. (**Not** the one at the top of the Source Control panel.)
3. From the dropdown menu, select "Branch" > "Merge...".
4. In the prompt that appears at the top of the screen, select `feature-square` to merge it into `main`.
5. VS Code will perform the merge and you should see a message indicating that the merge was successful.
6. You should see a new commit in the "Graph" section representing the merge, with both `main` and `feature-square` branches now pointing to this new commit.

![Merge Branch](doc-images/merge-branch.png)

You have now successfully merged the `feature-square` branch into the `main` branch!

Open the `src/index.js` file to see that it now contains both the updated comment and the squaring logic.
The completed file should look like this:

```javascript
// Michael Lambert 10/19/2025
// This application prints "Hello, World!" and the numbers 0 to 9.
console.log("Hello world!");
for (let i = 0; i < 10; i++) {
    console.log(i);
    console.log(i * i);
}
``` 

It contains both changes from the `main` branch and the `feature-square` branch.

## Bonus: Creating and Resolving a Merge Conflict

To further practice your Git skills, let's create a merge conflict and resolve it.  These steps
will be a bit less guided to practice and develop your skills, so pay close attention to the instructions.

1. First, create and switch to a new branch called `feature-conflict` from the `main` branch.
2. In the `src/index.js` file, modify the comment at the top to say
    ```javascript
    // [Your Name] - [Date]
    // This application prints "Hello, World!" and the numbers 0 to 9, along with their squares.
    ```
3. Save the file and commit the change with a message like "Update comment in feature-conflict branch".
4. Now, switch back to the `main` branch.
5. In the `src/index.js` file, modify the comment at the top to say
    ```javascript
    // [Your Name] - [Date]
    // This application prints "Hello, World!" and the numbers 0 to 9. It does not print squares.
    ```
6. Save the file and commit the change with a message like "Update comment in main branch".
7. Now, try to merge the `feature-conflict` branch into the `main` branch by following the same merge steps as before.
8. You should see a merge conflict message indicating that there is a conflict in the `src/index.js` file.
9. Open the `src/index.js` file. You will see conflict markers (`<<<<<<<`, `=======`, `>>>>>>>`) indicating the conflicting changes.
10. Visual Studio Code provides a user-friendly interface to resolve merge conflicts. You can choose to accept the changes from either branch or manually edit the file to combine the changes as desired.
11. After resolving the conflict, save the file.
12. In the Source Control panel, you will see that the conflict has been resolved. Stage the changes by clicking the "+" icon next to the file.
13. Finally, commit the merge with a message like "Resolve merge conflict between main and feature-conflict".

## Pushing Everything to GitHub

Now that you have completed the exercise, let's push all your changes to your forked repository on GitHub.

1. Switch to the `main` branch if you are not already on it.
2. Click on the Source Control icon in the left sidebar of VS Code.
3. Click on the three-dot menu icon next to the "Changes" header.
4. From the dropdown menu, select "Push".
5. VS Code will push all your commits from the `main` branch to your forked repository on GitHub.
6. Repeat the push process for any other branches you created (e.g., `feature-square`, `feature-conflict`)
   by switching to each branch and pushing them individually.

Your instructor will verify your work by checking your forked repository on GitHub to ensure that all branches, commits, and merges are present.

## Conclusion

You have completed the Git branching exercise! You have learned how to create branches, make commits
in different branches, and merge branches back into the main branch.
First commit on main branch.
This change was made on the feature branch.
