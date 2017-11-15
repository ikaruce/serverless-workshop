# Deploying to Multiple Stages

When building real world applications it's recommended that you leverage multiple stages to avoid breaking things for users when adding new features.

Typically companies will leverage stages like:

- `dev` -  Stage for developers to test things out in
- `qa` - Stage for QA folks to battle harden the application and test for edge cases.
- `prod` - Live application users use and love.

The serverless framework makes it extremely easy to leverage as many stages as you wish.

By default, when running the `serverless deploy` command the stage is set to `dev`

However, you can override this value in a number of ways.

1. via command line flags

    ```
    sls deploy --stage prod
    ```

2. In `serverless.yml`

    ```
    service: using-multiple-stages

    provider:
      name: aws
      runtime: nodejs6.10
      stage: qa
    ```

3. Using custom variables in `serverless.yml`

    ```
    service: using-multiple-stages

    provider:
      name: aws
      runtime: nodejs6.10
      stage: ${opt:stage, 'dev'}
    ```

    The above example will use the default stage of `dev` but override it if a `--stage` flag is passed to the cli command.

    See `serverless.yml` [variable syntax](http://bit.ly/2zw4DM9) for more information.

## Steps

<!-- AUTO-GENERATED-CONTENT:START (GENERATE_LESSONS_STEPS)-->
1. **Deploy to `dev` stage**

    Run the following command in your CLI
    ```bash
    sls deploy
    ```

    Then get the info about the service
    ```bash
    sls info
    ```

2. **Deploy to `prod` stage**

    Run the following command in your CLI
    ```bash
    sls deploy --stage prod
    ```

    Run the following command in your CLI
    ```bash
    sls info --stage prod
    ```

    Note that the `sls info` needs the `--stage` flag to pull back the correct `prod` information

3. In `serverless.yml`, add a `custom` block and define a `stage` property. Set that property to a serverless `${variable, defaultValue}` with a default value of 'dev'

4. In `serverless.yml`, set the stage key to the custom.stage value set in previous step

5. In `serverless.yml`, set an environment variable that uses the serverless file variable syntax to grab a file name with the current stage in it. Example `config.dev.json`. Hint this uses nested variables http://bit.ly/2AHvkKO
<!-- AUTO-GENERATED-CONTENT:END -->


<!-- IGNORE BELOW COMMENTS! SCROLL UP FOR STEPS -->

<!-- Step 1. **Deploy to `dev` stage**

    Run the following command in your CLI
    ```bash
    sls deploy
    ```

    Then get the info about the service
    ```bash
    sls info
    ```
-->

<!-- Step 2. **Deploy to `prod` stage**

    Run the following command in your CLI
    ```bash
    sls deploy --stage prod
    ```

    Run the following command in your CLI
    ```bash
    sls info --stage prod
    ```

    Note that the `sls info` needs the `--stage` flag to pull back the correct `prod` information
-->