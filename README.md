# CodeSniffer

A GitHub action for performing static analysis on Drupal code. It runs PHPCS and PHPCPD on the directory you give it.

 
## Inputs
- **path:** The path (or paths) to run the analysis on (optional)(Default: ./).
- **extensions:** Comma separated list of file extensions to test (optional)(Default: php,module,inc,install,test,profile,theme,css,info,md,yml).
- **suffix:** Comma separated list of file extensions to test used by phpcs (optional)(Default: .php,\*.module,\*.inc,\*.install,\*.test,\*.profile,\*.theme,\*.js,\*.css,\*.info).
- **lint:** Comma separated list of file extentions to lint. (optional)(Default: php,module,inc,install,test).
- **phpcs-ignore:** Comma separated list of files/folder for phpcs to ignore (optional)(Default: \*.md).
- **phpcpd-exclude:** Comma separated list of folders to ignore (optional).

## Outputs
This action does not output any artifacts.

## Secrets
This action does not use any secrets.

## Usage
Learn more about GitHub Actions in general [here](https://docs.github.com/en/actions/quickstart). 

To use this action in your repo, follow these steps:

 1. Create a YAML file in the `.github/workflows/` directory of your repo.
 2.  Copy the following into the YAML file:
```yaml
name: Code Linting
on: pull_request
jobs:
  Lint:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout Repo
        uses: actions/checkout@v2
      
      - name: Run CodeSniffer
        uses: discoverygarden/CodeSniffer@v1
        with:
          path: ./
```
This will run the sniffer each time code is pushed to your repo.

In order for this action to be triggered by pull requests generated by forked repositories, it's necessary to enable `Run workflows from fork pull requests` under `Fork pull request workflows` on the `settings/actions` configuration page for the repository this action is used within. 
