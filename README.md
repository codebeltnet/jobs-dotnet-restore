# Reusable Workflows for .NET CLI Restore

This repository contains reusable workflows for interacting with .NET CLI `restore` command in your CI/CD pipeline.

> These workflows is part of the Codebelt umbrella and ensures a consistent way of: 
> 
> - Defining your CI/CD pipeline 
> - Structuring your repository
> - Keeping your codebase small and feasible
> - Writing clean and maintainable code
> - Deploying your code to different environments
> - Automating as much as possible
>
> A paved path to excel as a DevSecOps Engineer.

## Available Workflows

- [default.yml](.github/workflows/default.yml) - the `dotnet restore` workflow that:
  - [fetches the codebase](https://github.com/codebeltnet/git-checkout),
  - [installs the .NET SDK](https://github.com/codebeltnet/install-dotnet),
  - conditionally either computes the restore cache key or uses a custom provided key,
  - conditionally generates the cache associated with the restore cache key,
  - [conditionally restores the dependencies](https://github.com/codebeltnet/dotnet-restore).

### Usage

To call this workflow in your GitHub repository, you can follow these steps:

```yaml
restore-call:
    uses: codebeltnet/jobs-dotnet-restore/.github/workflows/default.yml@v1
```

#### Inputs

```yaml
with:
  # Path to the project(s) file to restore. Pass empty to restore all dependencies of a solution. Supports globbing. Default is an empty string.
  projects: ''
  # Whether to use the restore cache or not. Default is not to use the restore cache.
  use-restore-cache: false
  # Allows for a custom provided key that will be used instead of the default implementation.
  restore-cache-key: ''
  # The type of machine to run the job on. Default is ubuntu-24.04.
  runs-on: 'ubuntu-24.04'
    # When set to true, includes preview versions of .NET. Default is false.
  include-preview: false
  # Sets the verbosity level of the command. Allowed values are quiet, minimal, normal, detailed, and diagnostic. Default is quiet.
  verbosity-level: 'quiet'
  # The maximum time in minutes to allow the job to run. Default is 15 minutes.
  timeout-minutes: 15
```

#### Secrets

This workflow has no secrets.

#### Outputs

```yaml
outputs:
  # The restore cache key that can be used by other actions and/or workflows.
  restore-cache-key: dotnet-restore-sha256
```

#### Example

```yaml
jobs:
  build:
    uses: codebeltnet/jobs-dotnet-restore/.github/workflows/default@v1
    with:
      use-restore-cache: true
```

## Caller workflows to showcase the Codebelt experience

### Basic CI/CD Pipeline

- Bootstrapper API - https://github.com/codebeltnet/bootstrapper/blob/main/.github/workflows/pipelines.yml
- Extensions for Asp.Versioning API - https://github.com/codebeltnet/asp-versioning/blob/main/.github/workflows/pipelines.yml
- Extensions for AWS Signature Version 4 API - https://github.com/codebeltnet/aws-signature-v4/blob/main/.github/workflows/pipelines.yml
- Extensions for Globalization API - https://github.com/codebeltnet/globalization/blob/main/.github/workflows/pipelines.yml
- Extensions for Newtonsoft.Json API - https://github.com/codebeltnet/newtonsoft-json/blob/main/.github/workflows/pipelines.yml
- Extensions for Swashbuckle.AspNetCore API - https://github.com/codebeltnet/swashbuckle-aspnetcore/blob/main/.github/workflows/pipelines.yml
- Extensions for xUnit API - https://github.com/codebeltnet/xunit/blob/main/.github/workflows/pipelines.yml
- Extensions for YamlDotNet API - https://github.com/codebeltnet/yamldotnet/blob/main/.github/workflows/pipelines.yml
- Shared Kernel API - https://github.com/codebeltnet/shared-kernel/blob/main/.github/workflows/pipelines.yml
- Unitify API - https://github.com/codebeltnet/unitify/blob/main/.github/workflows/pipelines.yml

### Intermediate CI/CD Pipeline

- Savvy I/O - https://github.com/codebeltnet/savvyio/blob/main/.github/workflows/pipelines.yml

### Advanced CI/CD Pipeline

- Cuemon for .NET - https://github.com/gimlichael/Cuemon/blob/main/.github/workflows/pipelines.yml

## Contributing to Reusable Workflows for .NET CLI Pack

Contributions are welcome! 
Feel free to submit issues, feature requests, or pull requests to help improve these workflows.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
