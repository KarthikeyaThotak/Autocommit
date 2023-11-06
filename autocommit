#!/bin/bash

# Default values
commit_message=""
repo_url=""
branch_name="main"

# Function to display the help message
help() {
    echo "Usage: autocommit --commit COMMIT_MESSAGE --repo REPO_URL --branch BRANCH_NAME"
    echo ""
    echo "Options:"
    echo "  --commit COMMIT_MESSAGE   Specify the commit message."
    echo "  --repo REPO_URL          Specify the GitHub repository URL."
    echo "  --branch BRANCH_NAME     Specify the branch name (default: main)."
    echo ""
    echo "Example:"
    echo "  autocommit --commit 'Initial commit' --repo 'https://yourgithub-repo.com' --branch 'main'"
}

autocommit() {
    git init || { echo "Error: Git initialization failed"; exit 1; }
    git add --all || { echo "Error: Git add failed"; exit 1; }
    git commit -m "$commit_message" || { echo "Error: Git commit failed"; exit 1; }
    git branch -M "$branch_name" || { echo "Error: Git branch creation failed"; exit 1; }
    git remote add origin "$repo_url" || { echo "Error: Git remote addition failed"; exit 1; }
    git push -u origin "$branch_name" || { echo "Error: Git push failed"; exit 1; }
}

autocommit_git(){
	git add --all || { echo "Error: Git add failed"; exit 1; }
    git commit -m "$commit_message" || { echo "Error: Git commit failed"; exit 1; }
    git branch -M "$branch_name" || { echo "Error: Git branch creation failed"; exit 1; }
    git push -u origin "$branch_name" || { echo "Error: Git push failed"; exit 1; }
}

if [ $# -ne 6 ]; then
    echo "Error: Missing required options. You must provide all flags: --commit, --repo, and --branch."
    help
    exit 1
fi

while [[ $# -gt 0 ]]; do
    case "$1" in
        --commit)
            if [ -n "$2" ]; then
                commit_message="$2"
                shift
            else
                echo "Error: '--commit' requires a commit message."
                exit 1
            fi
            ;;
        --repo)
            if [ -n "$2" ]; then
                repo_url="$2"
                shift
            else
                echo "Error: '--repo' requires a repository URL."
                exit 1
            fi
            ;;
        --branch)
            if [ -n "$2" ]; then
                branch_name="$2"
                shift
            else
                echo "Error: '--branch' requires a branch name."
                exit 1
            fi
            ;;
        *)
            echo "Error: Unknown option: $1"
            help
            exit 1
            ;;
    esac
    shift
done

FILE=.git/
if [ -d "$FILE" ]; then
    echo ".Git already exits!"
	autocommit_git
else
	autocommit
fi


