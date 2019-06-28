# awesome-git-alias
All the awesome git aliases will come here.

# find the difference of current branch with all the branches:

    echo current branch is: $(git rev-parse --abbrev-ref HEAD); 
    for branch in $(git for-each-ref --format='%(refname)'); do 
    echo "$branch"; 
    	git log --oneline $(git rev-parse --abbrev-ref HEAD) ^"$branch" | echo behind: $(wc -l); 
    	git log --oneline "$branch" ^$(git rev-parse --abbrev-ref HEAD) | echo ahead: $(wc -l);  
    done
