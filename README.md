# Volt MX Go documentation

## Usage

[View the documentation](https://opensource.hcltechsw.com/voltmxgo-documentation) for product features and usage information.  

## Contributing

You are welcome to report bugs or provide feedback on the **product documentation** using pull requests on GitHub at https://github.com/HCL-TECH-SOFTWARE/voltmxgo-documentation. This is the Volt MX Go product documentation website and not the product support platform, so all bug reports and pull requests shall pertain to product documentation. **You are expected to update only the markdown files in the `docs` directory**.

### How to contribute?

Perform the following steps to contribute to the documentation.

1. Update the documentation.

    1. Clone the [Volt MX Go documentation repo](https://github.com/HCL-TECH-SOFTWARE/voltmxgo-documentation).

        If you do not have write access to the repo, [fork the repository](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/working-with-forks/fork-a-repo#forking-a-repository) and then [clone your forked repository](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/working-with-forks/fork-a-repo#cloning-your-forked-repository).

    2. Create a new working branch for your changes.
    3. Edit the Markdown files (.md) in the `docs` directory that you want to update using your preferred text or code editor, and then save the changes.

2. Validate your changes

    Perform the following steps if you want to preview how your changes render as HTML using MkDocs.

    1. [Install MkDocs](https://www.mkdocs.org/user-guide/installation/) (if not already installed) to build and preview the documentation locally.
    2. Install the MkDocs plugins:

        ```
        pip install mkdocs-material
        pip install mkdocs-awesome-pages-plugin 
        pip install mkdocs-git-revision-date-localized-plugin 
        ```

    3. Preview your changes in a web browser by running the [`mkdocs serve`](https://www.mkdocs.org/user-guide/cli/#mkdocs-serve) command.

        Make sure you're in the same directory as the `mkdocs.yml` configuration file when running the `mkdocs serve` command.

    4. Open `http://127.0.0.1:8000` in your browser to check the formatting, links, and rendering of your changes.

3. Submit your documentation changes.

    1. Stage and commit your changes with a clear commit message.
    2. Push your branch to remote [Volt MX Go repo](https://github.com/HCL-TECH-SOFTWARE/voltmxgo-documentation).

        In case you created your branch from your fork, push your branch to your fork of the Volt MX Go repository.

    3. Navigate to the [Volt MX Go repo](https://github.com/HCL-TECH-SOFTWARE/voltmxgo-documentation) on GitHub, then create a pull request (PR) from your branch targeting the main branch.

        In case you pushed your branch to your fork of the Volt MX Go repository, see [create a pull request from a fork](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/creating-a-pull-request-from-a-fork).

    4. Respond to review comments and update your PR as needed until approved.

        Once the pull request is approved and merged, your changes will be published on the documentation site.

<!--
- Install [MkDocs](https://github.com/squidfunk/mkdocs-material).
- Clone [Volt MX Go docs repository](https://github.com/HCL-TECH-SOFTWARE/voltmxgo-documentation).
- Create a new branch.
- Update the markdown files in the `docs` directory as needed.
- Verify, test, and commit the changes.
- Submit a pull request. 
- Await the review, approval, and merging of the pull request.
-->
## Set up GitHub email notifications

Configure your email notification preferences to receive notifications.

1. Go to [Notifications](https://github.com/settings/notifications).
2. Make sure that your preferred email address is correctly set as the **Default notification email**.
3. Make sure that the following options are selected to receive email updates for conversations you are involved in or watching under **Customize email updates**:

    - Pull Request reviews
    - Pull Request pushes
    - Comments on Issues and Pull Requests

## License

The documentation is available as open source under the terms of the [Apache License 2.0](http://www.apache.org/licenses/).