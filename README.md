# Push commits to an additional Git repository and AWS Codecommit same time

You can configure your local repo to push changes to two remote repositories. For example, you might want to continue using your existing Git repository solution while you try out AWS CodeCommit. Follow these basic steps to push changes in your local repo to CodeCommit and a separate Git repository.

1. From the command prompt or terminal, switch to your local repo directory and run the git remote -v command. You should see output similar to the following:

   For HTTPS:
   
   `
   origin  https://git-codecommit.us-east-2.amazonaws.com/v1/repos/MyDemoRepo (fetch)
   origin  https://git-codecommit.us-east-2.amazonaws.com/v1/repos/MyDemoRepo (push)
   `     
   
   For SSH:
   
   `
   origin  ssh://git-codecommit.us-east-2.amazonaws.com/v1/repos/MyDemoRepo (fetch)
   origin  ssh://git-codecommit.us-east-2.amazonaws.com/v1/repos/MyDemoRepo (push)
   `
   
 2. Run the git remote set-url --add --push origin git-repository-name command where git-repository-name is the URL and name of the Git repository where you want to host your code. This changes the push destination of origin to that Git repository.
    `git remote set-url --add --push origin some-URL/MyDestinationRepo`
    
 3. Run the git remote -v command again, which should create output similar to the following:
    `
    origin  ssh://git-codecommit.us-east-2.amazonaws.com/v1/repos/MyDemoRepo (fetch)
    origin  some-URL/MyDestinationRepo (push)
    `
    
 4. Now add the CodeCommit repository. Run git remote set-url --add --push origin again, this time with the URL and repository name of your CodeCommit repository.
    For HTTPS:
     `git remote set-url --add --push origin https://git-codecommit.us-east-2.amazonaws.com/v1/repos/MyDemoRepo`
     
 5. Run the git remote -v command again, which should create output similar to the following:
    For HTTPS: 
    `
    origin  https://git-codecommit.us-east-2.amazonaws.com/v1/repos/MyDemoRepo (fetch)
    origin  some-URL/MyDestinationRepo (push)        
    origin  https://git-codecommit.us-east-2.amazonaws.com/v1/repos/MyDemoRepo (push)      
    `
6. Run git add to stage the change in your local repo:
7. Run git commit to commit the change in your local repo:
8. To push the commit from the local repo to your remote repositories, run git push -u remote-name branch-name where remote-name is the nickname the local repo uses for the remote repositories and branch-name is the name of the branch to push to the repository. For example, running git push -u origin main would show the push went to both remote repositories in the expected branches
