# book-source

This is the source repo for the EDA student handbook. Below you'll find instructions for creating, provisioning, updating, building and deploying a cohort's handbook.


## Creating a handbook for a new cohort

1. Fork this repo into your cohort's org

2. Rename the repo to `student-handbook`

3. Clone the fork from the cohort's org to your computer

4. Jump in and install dependencies
    ```
    cd student-handbook && yarn
    ```

5. Run the following command to add an `upstream` remote, create a deployment branch, rename the `README` and install `gitbook-cli` globally:

    ```
    ./setup
    ```

6. Find a nice photo of the cohort's bird/tree and save it in this folder as `cover.jpg`.

7. Manually customize `book.json` and `README.md` for your cohort.

8. Save, stage, commit and push your changes.


## Provisioning the hosting environment

1. Create a new Heroku app called `COHORT-YEAR-handbook`

    ```sh
    # Be sure you're already logged into the Heroku Toolbelt CLI tool
    heroku apps:create COHORT-YEAR-handbook
    ```

2. Deploy the application

    ```sh
    ./deploy # Note: do NOT use the typical git push heroku master approach
    ```

3. Create two environment variables in the Heroku app with the following values:

    ```sh
    heroku config:set USERNAME=COHORT-YEAR
    heroku config:set PASSWORD=THE-PASSWORD-ON-THE-BOOTCAMP-COMPUTERS
    ```

4. Put these same values in the `.env` file


## Building and deploying the book

To publish any changes you make to the book:

1. In the cohort's `student-handbook` repo on your computer, pull from `upstream` to ensure you have the latest changes from `book-source`.

    ```
    git pull upstream master
    ```

2. Make your changes to `SUMMARY.md` and stage and commit them.

3. To build and test locally:

    ```sh
    gitbook install
    gitbook serve
    ```

    Run `gitbook help` to see more build options.

4. Build and deploy the book: `./deploy` (this can take a few minutes)


## Gitbook Inclusions

If you need to do inclusions, they look like this:

```
{% include book.repo.concepts + 'README.md' %}
```

`book.repo.concepts` is a global/book-level variable defined in `book.json`.

More info at https://help.gitbook.com/format/conrefs.html.

