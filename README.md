# awesome-git-alias
All the awesome git aliases will come here.

# find the difference of current branch with all the branches:

    [alias]
        diffla = "!f() { \
                    echo current branch is: $(git rev-parse --abbrev-ref HEAD); \
					echo $1; \
                    for branch in $(git for-each-ref --format='%(refname)'); do \
                        AHEAD=$(git log --oneline $(git rev-parse --abbrev-ref HEAD) ^"$branch" | echo $(wc -l)); \
                        BEHIND=$(git log --oneline "$branch" ^$(git rev-parse --abbrev-ref HEAD) | echo $(wc -l));  \
						if [ ! -z "$1" ]; then \
							if [ $1 == "-a" ]; then \
								echo $branch ---- \\<$BEHIND\\>:\\<$AHEAD\\>; \
							fi \
                        else \
                            if [ $BEHIND != "0" ]; then \
                                echo $branch ---- \\<$BEHIND\\>:\\<$AHEAD\\>; \
                            fi \
                        fi \
                    done; \
                }; f"

