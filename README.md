# awesome-git-alias
All the awesome git aliases will come here.

# find the difference of current branch with all the branches:

    [alias]
    	diffla = "!echo current branch is: $(git rev-parse --abbrev-ref HEAD); \
                for branch in $(git for-each-ref --format='%(refname)'); do \
                    AHEAD=$(git log --oneline $(git rev-parse --abbrev-ref HEAD) ^"$branch" | echo \\<$(wc -l)\\>); \
                    BEHIND=$(git log --oneline "$branch" ^$(git rev-parse --abbrev-ref HEAD) | echo \\<$(wc -l)\\>);  \
                    echo $branch ---- $BEHIND:$AHEAD; \
                done;"

