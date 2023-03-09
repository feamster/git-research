# Research

Pointers to research project submodules

# Setting Up a Master Repository

## Initial Setup
  - Adding a repo as submoudule: `git submodule add [repo_url] [directory name]`
  - First time fetching the repository: `git submodule update --init --recursive`

## Fetching Submodules
  - Updating all submodules to the latest version `git submodule foreach git pull`
  - Fetching updates from all submodules: `git submodule update --recursive --remote`
