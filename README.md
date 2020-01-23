# awesome-git-alias
All the awesome git aliases will come here.

# git diffla [-a]:
difference by count of current branch with all other branches. It return all the branches which its behind value is not zero. if you want to see all the branches pass `-a`.

    [alias]
        tree = log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit
	logl = log --pretty=oneline
	ba = "!f() { \
		                LEFT=${1-master}; \
		                RIGHT=${2-HEAD}; \
		                OUTPUT=$(echo $(git rev-list --left-right --count $LEFT...$RIGHT) "$LEFT $RIGHT" | awk '{print $4\" is \"$1\" behind and \"$2\" ahead of \"$3}');\
		                echo $OUTPUT; \
		}; f"
	diffla = "!f() { \
				echo current branch is: $(git rev-parse --abbrev-ref HEAD); \
				echo $1; \
				echo format: ------------------------------------ \\<behind\\>:\\<ahead\\>; \
				for branch in $(git for-each-ref --format='%(refname)'); do \
					AHEAD=$(git log --oneline $(git rev-parse --abbrev-ref HEAD) ^"$branch" | echo $(wc -l)); \
					BEHIND=$(git log --oneline "$branch" ^$(git rev-parse --abbrev-ref HEAD) | echo $(wc -l));  \
					if [ ! -z "$1" ]; then \
						if [ $1 == "-a" ]; then \
							echo $branch ---- \\<$BEHIND\\>:\\<$AHEAD\\>; \
						fi \
					else \
						if [ $BEHIND != "0" ]; then \
							echo $branch ---- \\<$AHEAD\\>:\\<$BEHIND\\>; \
						fi \
					fi \
				done; \
			}; f"
	sb = status -sb

