<!-- markdownlint-disable MD033 MD041 -->
<!-- @generated by .automation/build.py, please do not update manually -->

<div align="center">
  <a href="https://www.accurics.com/products/terrascan/" target="blank" title="Visit linter Web Site">
    <img src="https://raw.githubusercontent.com/tenable/runterrascan.io/main/static/images/TerrascanTM_BY_Logo.png" alt="terrascan" height="150px" class="megalinter-banner">
  </a>
</div>

[![GitHub last commit](https://img.shields.io/github/last-commit/accurics/terrascan)](https://github.com/accurics/terrascan/commits)

## terrascan documentation

- Version in MegaLinter: **1.15.2**
- Visit [Official Web Site](https://www.accurics.com/products/terrascan/){target=_blank}
- See [How to configure terrascan rules](https://docs.accurics.com/projects/accurics-terrascan/en/latest/policies/){target=_blank}
- See [Index of problems detected by terrascan](https://docs.accurics.com/projects/accurics-terrascan/en/latest/policies/){target=_blank}

[![terrascan - GitHub](https://gh-card.dev/repos/accurics/terrascan.svg?fullname=)](https://github.com/accurics/terrascan){target=_blank}

## Configuration in MegaLinter

- Enable terrascan by adding `TERRAFORM_TERRASCAN` in [ENABLE_LINTERS variable](https://oxsecurity.github.io/megalinter/beta/configuration/#activation-and-deactivation)
- Disable terrascan by adding `TERRAFORM_TERRASCAN` in [DISABLE_LINTERS variable](https://oxsecurity.github.io/megalinter/beta/configuration/#activation-and-deactivation)

| Variable                                        | Description                                                                                                                                                                                  | Default value                                   |
|-------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------|
| TERRAFORM_TERRASCAN_ARGUMENTS                   | User custom arguments to add in linter CLI call<br/>Ex: `-s --foo "bar"`                                                                                                                     |                                                 |
| TERRAFORM_TERRASCAN_FILE_EXTENSIONS             | Allowed file extensions. `"*"` matches any extension, `""` matches empty extension. Empty list excludes all files<br/>Ex: `[".py", ""]`                                                      | `[".tf"]`                                       |
| TERRAFORM_TERRASCAN_FILE_NAMES_REGEX            | File name regex filters. Regular expression list for filtering files by their base names using regex full match. Empty list includes all files<br/>Ex: `["Dockerfile(-.+)?", "Jenkinsfile"]` | Include every file                              |
| TERRAFORM_TERRASCAN_PRE_COMMANDS                | List of bash commands to run before the linter                                                                                                                                               | None                                            |
| TERRAFORM_TERRASCAN_POST_COMMANDS               | List of bash commands to run after the linter                                                                                                                                                | None                                            |
| TERRAFORM_TERRASCAN_CONFIG_FILE                 | terrascan configuration file name</br>Use `LINTER_DEFAULT` to let the linter find it                                                                                                         | `terrascan-config.toml`                         |
| TERRAFORM_TERRASCAN_RULES_PATH                  | Path where to find linter configuration file                                                                                                                                                 | Workspace folder, then MegaLinter default rules |
| TERRAFORM_TERRASCAN_DISABLE_ERRORS              | Run linter but consider errors as warnings                                                                                                                                                   | `false`                                         |
| TERRAFORM_TERRASCAN_DISABLE_ERRORS_IF_LESS_THAN | Maximum number of errors allowed                                                                                                                                                             | `0`                                             |

## MegaLinter Flavours

This linter is available in the following flavours

|                                                                         <!-- -->                                                                         | Flavor                                                                       | Description                            | Embedded linters |                                                                                                                                                                                         Info |
|:--------------------------------------------------------------------------------------------------------------------------------------------------------:|:-----------------------------------------------------------------------------|:---------------------------------------|:----------------:|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| <img src="https://github.com/oxsecurity/megalinter/raw/main/docs/assets/images/mega-linter-square.png" alt="" height="32px" class="megalinter-icon"></a> | [all](https://oxsecurity.github.io/megalinter/beta/supported-linters/)       | Default MegaLinter Flavor              |       106        |                     ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/oxsecurity/megalinter/v6) ![Docker Pulls](https://img.shields.io/docker/pulls/oxsecurity/megalinter) |
|      <img src="https://github.com/oxsecurity/megalinter/raw/main/docs/assets/icons/security.ico" alt="" height="32px" class="megalinter-icon"></a>       | [security](https://oxsecurity.github.io/megalinter/beta/flavors/security/)   | Optimized for security                 |        21        |   ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/oxsecurity/megalinter-security/v6) ![Docker Pulls](https://img.shields.io/docker/pulls/oxsecurity/megalinter-security) |
|      <img src="https://github.com/oxsecurity/megalinter/raw/main/docs/assets/icons/terraform.ico" alt="" height="32px" class="megalinter-icon"></a>      | [terraform](https://oxsecurity.github.io/megalinter/beta/flavors/terraform/) | Optimized for TERRAFORM based projects |        51        | ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/oxsecurity/megalinter-terraform/v6) ![Docker Pulls](https://img.shields.io/docker/pulls/oxsecurity/megalinter-terraform) |

## Behind the scenes

### How are identified applicable files

- File extensions: `.tf`

<!-- markdownlint-disable -->
<!-- /* cSpell:disable */ -->
### How the linting is performed

terrascan is called once on the whole project directory (`project` CLI lint mode)

- filtering can not be done using MegaLinter configuration variables,it must be done using terrascan configuration or ignore file (if existing)
- `VALIDATE_ALL_CODEBASE: false` does not make terrascan analyze only updated files

### Example calls

```shell
terrascan scan -i terraform -t all -f myfile.tf
```


### Help content

```shell
Terrascan

Detect compliance and security violations across Infrastructure as Code to mitigate risk before provisioning cloud native infrastructure.
For more information, please visit https://runterrascan.io/

Usage:
  terrascan [command]

Available Commands:
  init        Initializes Terrascan and clones policies from the Terrascan GitHub repository.
  scan        Detect compliance and security violations across Infrastructure as Code.
  server      Run Terrascan as an API server
  version     Terrascan version

Flags:
  -c, --config-path string      config file path
  -l, --log-level string        log level (debug, info, warn, error, panic, fatal) (default "info")
      --log-output-dir string   directory path to write the log and output files
  -x, --log-type string         log output type (console, json) (default "console")
  -o, --output string           output type (human, json, yaml, xml, junit-xml, sarif, github-sarif) (default "human")
      --temp-dir string         temporary directory path to download remote repository,module and templates

Use "terrascan [command] --help" for more information about a command.
```

### Installation on mega-linter Docker image

- Dockerfile commands :
```dockerfile
FROM tenable/terrascan:latest as terrascan
COPY --from=terrascan /go/bin/terrascan /usr/bin/
```

