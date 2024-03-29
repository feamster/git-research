# Research

Pointers to research project submodules. Some basic maintenance tips below.

# Setting Up a Master Repository

## Initial Setup

  - Adding a repo as submoudule: `git submodule add [repo_url] [directory name]`
  - First time fetching the repository: `git submodule update --init --recursive`

## Fetching Submodules

  - Updating all submodules to the latest version `git submodule foreach git pull`
  - Fetching updates from all submodules: `git submodule update --recursive --remote`


## Removing Submodules

1. Run git rm <path-to-submodule>, and commit.
   This removes the filetree at <path-to-submodule>, and the submodule's entry in
   the .gitmodules file. I.e. all traces of the submodule in your repository
   proper are removed.

   As the docs note however, the .git dir of the submodule is kept around (in the
   modules/ directory of the main project's .git dir), "to make it possible to
   checkout past commits without requiring fetching from another repository".


If you nonetheless want to remove this info, manually delete the submodule's
directory in .git/modules/, and remove the submodule's entry in the file
.git/config. These steps can be automated using the commands

2. `rm -rf .git/modules/<path-to-submodule>`
3. `git config --remove-section submodule.<path-to-submodule>`

## Moving Submodules

1. Navigate to the root directory of the repository that contains the
   submodule.

2. Update the submodule’s configuration file, which is located
   at `.gitmodules` in the root directory of the repository. Open this file and find
   the entry for the submodule that you want to move.

3. In the `.gitmodules` file, change the path parameter of the submodule to the new
   subdirectory where you want to move it. Save the changes to the file.

4. Move the actual submodule directory to the new location using `git mv
   old_submodule_dir new_subdirectory/`. If you receive an error saying that the
   file is unmerged, try `git add` the file and then run the `git mv` command again.

5. Commit the changes using `git commit -m "Moved submodule to new subdirectory"`.

6. Push the changes to the remote repository using `git push`.



