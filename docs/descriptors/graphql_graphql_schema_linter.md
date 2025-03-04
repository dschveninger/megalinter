<!-- markdownlint-disable MD033 MD041 -->
<!-- @generated by .automation/build.py, please do not update manually -->
# graphql-schema-linter [![GitHub last commit](https://img.shields.io/github/last-commit/cjoudrey/graphql-schema-linter)](https://github.com/cjoudrey/graphql-schema-linter/commits)

## graphql-schema-linter documentation

- Version in MegaLinter: **3.0.1**
- Visit [Official Web Site](https://github.com/cjoudrey/graphql-schema-linter#readme){target=_blank}
- See [How to configure graphql-schema-linter rules](https://github.com/cjoudrey/graphql-schema-linter#configuration-file){target=_blank}
- See [How to disable graphql-schema-linter rules in files](https://github.com/cjoudrey/graphql-schema-linter#inline-rule-overrides){target=_blank}
- See [Index of problems detected by graphql-schema-linter](https://github.com/cjoudrey/graphql-schema-linter#built-in-rules){target=_blank}

[![graphql-schema-linter - GitHub](https://gh-card.dev/repos/cjoudrey/graphql-schema-linter.svg?fullname=)](https://github.com/cjoudrey/graphql-schema-linter){target=_blank}

## Configuration in MegaLinter

- Enable graphql-schema-linter by adding `GRAPHQL_GRAPHQL_SCHEMA_LINTER` in [ENABLE_LINTERS variable](https://oxsecurity.github.io/megalinter/beta/configuration/#activation-and-deactivation)
- Disable graphql-schema-linter by adding `GRAPHQL_GRAPHQL_SCHEMA_LINTER` in [DISABLE_LINTERS variable](https://oxsecurity.github.io/megalinter/beta/configuration/#activation-and-deactivation)

| Variable                                                  | Description                                                                                                                                                                                                         | Default value                                   |
|-----------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------|
| GRAPHQL_GRAPHQL_SCHEMA_LINTER_ARGUMENTS                   | User custom arguments to add in linter CLI call<br/>Ex: `-s --foo "bar"`                                                                                                                                            |                                                 |
| GRAPHQL_GRAPHQL_SCHEMA_LINTER_FILTER_REGEX_INCLUDE        | Custom regex including filter<br/>Ex: `(src\|lib)`                                                                                                                                                                  | Include every file                              |
| GRAPHQL_GRAPHQL_SCHEMA_LINTER_FILTER_REGEX_EXCLUDE        | Custom regex excluding filter<br/>Ex: `(test\|examples)`                                                                                                                                                            | Exclude no file                                 |
| GRAPHQL_GRAPHQL_SCHEMA_LINTER_CLI_LINT_MODE               | Override default CLI lint mode<br/>- `file`: Calls the linter for each file<br/>- `list_of_files`: Call the linter with the list of files as argument<br/>- `project`: Call the linter from the root of the project | `file`                                          |
| GRAPHQL_GRAPHQL_SCHEMA_LINTER_FILE_EXTENSIONS             | Allowed file extensions. `"*"` matches any extension, `""` matches empty extension. Empty list excludes all files<br/>Ex: `[".py", ""]`                                                                             | `[".graphql"]`                                  |
| GRAPHQL_GRAPHQL_SCHEMA_LINTER_FILE_NAMES_REGEX            | File name regex filters. Regular expression list for filtering files by their base names using regex full match. Empty list includes all files<br/>Ex: `["Dockerfile(-.+)?", "Jenkinsfile"]`                        | Include every file                              |
| GRAPHQL_GRAPHQL_SCHEMA_LINTER_PRE_COMMANDS                | List of bash commands to run before the linter                                                                                                                                                                      | None                                            |
| GRAPHQL_GRAPHQL_SCHEMA_LINTER_POST_COMMANDS               | List of bash commands to run after the linter                                                                                                                                                                       | None                                            |
| GRAPHQL_GRAPHQL_SCHEMA_LINTER_CONFIG_FILE                 | graphql-schema-linter configuration file name</br>Use `LINTER_DEFAULT` to let the linter find it                                                                                                                    | `.graphql-schema-linterrc`                      |
| GRAPHQL_GRAPHQL_SCHEMA_LINTER_RULES_PATH                  | Path where to find linter configuration file                                                                                                                                                                        | Workspace folder, then MegaLinter default rules |
| GRAPHQL_GRAPHQL_SCHEMA_LINTER_DISABLE_ERRORS              | Run linter but consider errors as warnings                                                                                                                                                                          | `false`                                         |
| GRAPHQL_GRAPHQL_SCHEMA_LINTER_DISABLE_ERRORS_IF_LESS_THAN | Maximum number of errors allowed                                                                                                                                                                                    | `0`                                             |

## MegaLinter Flavours

This linter is available in the following flavours

|                                                                         <!-- -->                                                                         | Flavor                                                                               | Description                                           | Embedded linters |                                                                                                                                                                                                 Info |
|:--------------------------------------------------------------------------------------------------------------------------------------------------------:|:-------------------------------------------------------------------------------------|:------------------------------------------------------|:----------------:|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| <img src="https://github.com/oxsecurity/megalinter/raw/main/docs/assets/images/mega-linter-square.png" alt="" height="32px" class="megalinter-icon"></a> | [all](https://oxsecurity.github.io/megalinter/beta/supported-linters/)               | Default MegaLinter Flavor                             |       106        |                             ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/oxsecurity/megalinter/v6) ![Docker Pulls](https://img.shields.io/docker/pulls/oxsecurity/megalinter) |
|    <img src="https://github.com/oxsecurity/megalinter/raw/main/docs/assets/icons/documentation.ico" alt="" height="32px" class="megalinter-icon"></a>    | [documentation](https://oxsecurity.github.io/megalinter/beta/flavors/documentation/) | MegaLinter for documentation projects                 |        45        | ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/oxsecurity/megalinter-documentation/v6) ![Docker Pulls](https://img.shields.io/docker/pulls/oxsecurity/megalinter-documentation) |
|       <img src="https://github.com/oxsecurity/megalinter/raw/main/docs/assets/icons/dotnet.ico" alt="" height="32px" class="megalinter-icon"></a>        | [dotnet](https://oxsecurity.github.io/megalinter/beta/flavors/dotnet/)               | Optimized for C, C++, C# or VB based projects         |        54        |               ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/oxsecurity/megalinter-dotnet/v6) ![Docker Pulls](https://img.shields.io/docker/pulls/oxsecurity/megalinter-dotnet) |
|         <img src="https://github.com/oxsecurity/megalinter/raw/main/docs/assets/icons/go.ico" alt="" height="32px" class="megalinter-icon"></a>          | [go](https://oxsecurity.github.io/megalinter/beta/flavors/go/)                       | Optimized for GO based projects                       |        47        |                       ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/oxsecurity/megalinter-go/v6) ![Docker Pulls](https://img.shields.io/docker/pulls/oxsecurity/megalinter-go) |
|        <img src="https://github.com/oxsecurity/megalinter/raw/main/docs/assets/icons/java.ico" alt="" height="32px" class="megalinter-icon"></a>         | [java](https://oxsecurity.github.io/megalinter/beta/flavors/java/)                   | Optimized for JAVA based projects                     |        48        |                   ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/oxsecurity/megalinter-java/v6) ![Docker Pulls](https://img.shields.io/docker/pulls/oxsecurity/megalinter-java) |
|     <img src="https://github.com/oxsecurity/megalinter/raw/main/docs/assets/icons/javascript.ico" alt="" height="32px" class="megalinter-icon"></a>      | [javascript](https://oxsecurity.github.io/megalinter/beta/flavors/javascript/)       | Optimized for JAVASCRIPT or TYPESCRIPT based projects |        54        |       ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/oxsecurity/megalinter-javascript/v6) ![Docker Pulls](https://img.shields.io/docker/pulls/oxsecurity/megalinter-javascript) |
|         <img src="https://github.com/oxsecurity/megalinter/raw/main/docs/assets/icons/php.ico" alt="" height="32px" class="megalinter-icon"></a>         | [php](https://oxsecurity.github.io/megalinter/beta/flavors/php/)                     | Optimized for PHP based projects                      |        49        |                     ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/oxsecurity/megalinter-php/v6) ![Docker Pulls](https://img.shields.io/docker/pulls/oxsecurity/megalinter-php) |
|       <img src="https://github.com/oxsecurity/megalinter/raw/main/docs/assets/icons/python.ico" alt="" height="32px" class="megalinter-icon"></a>        | [python](https://oxsecurity.github.io/megalinter/beta/flavors/python/)               | Optimized for PYTHON based projects                   |        54        |               ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/oxsecurity/megalinter-python/v6) ![Docker Pulls](https://img.shields.io/docker/pulls/oxsecurity/megalinter-python) |
|        <img src="https://github.com/oxsecurity/megalinter/raw/main/docs/assets/icons/ruby.ico" alt="" height="32px" class="megalinter-icon"></a>         | [ruby](https://oxsecurity.github.io/megalinter/beta/flavors/ruby/)                   | Optimized for RUBY based projects                     |        46        |                   ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/oxsecurity/megalinter-ruby/v6) ![Docker Pulls](https://img.shields.io/docker/pulls/oxsecurity/megalinter-ruby) |
|        <img src="https://github.com/oxsecurity/megalinter/raw/main/docs/assets/icons/rust.ico" alt="" height="32px" class="megalinter-icon"></a>         | [rust](https://oxsecurity.github.io/megalinter/beta/flavors/rust/)                   | Optimized for RUST based projects                     |        46        |                   ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/oxsecurity/megalinter-rust/v6) ![Docker Pulls](https://img.shields.io/docker/pulls/oxsecurity/megalinter-rust) |
|     <img src="https://github.com/oxsecurity/megalinter/raw/main/docs/assets/icons/salesforce.ico" alt="" height="32px" class="megalinter-icon"></a>      | [salesforce](https://oxsecurity.github.io/megalinter/beta/flavors/salesforce/)       | Optimized for Salesforce based projects               |        48        |       ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/oxsecurity/megalinter-salesforce/v6) ![Docker Pulls](https://img.shields.io/docker/pulls/oxsecurity/megalinter-salesforce) |
|        <img src="https://github.com/oxsecurity/megalinter/raw/main/docs/assets/icons/swift.ico" alt="" height="32px" class="megalinter-icon"></a>        | [swift](https://oxsecurity.github.io/megalinter/beta/flavors/swift/)                 | Optimized for SWIFT based projects                    |        46        |                 ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/oxsecurity/megalinter-swift/v6) ![Docker Pulls](https://img.shields.io/docker/pulls/oxsecurity/megalinter-swift) |
|      <img src="https://github.com/oxsecurity/megalinter/raw/main/docs/assets/icons/terraform.ico" alt="" height="32px" class="megalinter-icon"></a>      | [terraform](https://oxsecurity.github.io/megalinter/beta/flavors/terraform/)         | Optimized for TERRAFORM based projects                |        51        |         ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/oxsecurity/megalinter-terraform/v6) ![Docker Pulls](https://img.shields.io/docker/pulls/oxsecurity/megalinter-terraform) |

## Behind the scenes

### How are identified applicable files

- File extensions: `.graphql`

<!-- markdownlint-disable -->
<!-- /* cSpell:disable */ -->
### How the linting is performed

- graphql-schema-linter is called one time by identified file (`file` CLI lint mode)

### Example calls

```shell
graphql-schema-linter myfile.graphql
```


### Help content

```shell
Usage: graphql-schema-linter [options] [schema.graphql ...]

Options:
  -r, --rules <rules>                 only the rules specified will be used to validate the schema. Example: fields-have-descriptions,types-have-descriptions
  -o, --rules-options <rulesOptions>  configure the specified rules with the passed in configuration options. example: {"enum-values-sorted-alphabetically":{"sortOrder":"lexicographical"}}
  -i, --ignore <ignore list>          ignore errors for specific schema members, example: {'fields-have-descriptions':['Obvious','Query.obvious','Query.something.obvious']}
  -f, --format <format>               choose the output format of the report. Possible values: json, text, compact
  -s, --stdin                         schema definition will be read from STDIN instead of specified file.
  -c, --config-directory <path>       path to begin searching for config files.
  -p, --custom-rule-paths <paths>     path to additional custom rules to be loaded. Example: rules/*.js
  --comment-descriptions              use old way of defining descriptions in GraphQL SDL
  --old-implements-syntax             use old way of defining implemented interfaces in GraphQL SDL
  -o, --only <rules>                  This option is DEPRECATED. Use `--rules` instead.
  -e, --except <rules>                This option is DEPRECATED. Use `--rules` instead.
  --version                           output the version number
  -h, --help                          output usage information
```

### Installation on mega-linter Docker image

- NPM packages (node.js):
  - [graphql](https://www.npmjs.com/package/graphql)
  - [graphql-schema-linter](https://www.npmjs.com/package/graphql-schema-linter)
