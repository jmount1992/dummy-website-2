# Dummy Website 1

This is a dummy website that is part of James Mount's website building guide. It utilise Jekyll and GitHub pages.

The approximate steps to recreate are as follows:

1. Installing Ruby and Jekyll following the instructions [here](jekyllrb.com/docs/installation).
2. Following the quick start Jekyll guide [here](jekyllrb.com/docs/)
3. Altering the `_config.yml`, `index.markdown`, and `gemfile` files created as part of the quick start.
    - Use the files in this repository to see the changes
    - If you get an error at some point about `Bundler found conflicting requirements for the Ruby version:`, delete the `Gemfile.lock` file and run `bundle install`
4. Creating a GitHub Repository and pushing the files to the remote.
5. In the GitHub repository settings, navigated to Pages (sidebar) to pages, and under `Build and Deployment`:
    1. Set Source to: `Deploy from a branch`
    2. Set Branch to: `main` and left the directory to `/(root)`
    3. Clicked save

Your website is now served!