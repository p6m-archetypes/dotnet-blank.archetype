# .NET Blank Service Archetype

![Latest Release](https://img.shields.io/github/v/release/p6m-archetypes/dotnet-blank.archetype?style=flat-square&label=Latest%20Release&color=blue)

## Usage

To get started, [install archetect](https://github.com/p6m-archetypes/development-handbook)
and render this template to your current working directory:

```bash
archetect render git@github.com:p6m-archetypes/dotnet-blank.archetype.git
```

For information about interacting with the service, refer to the README at the generated
project's root.

## Prompts

When rendering the archetype, you'll be prompted for the following values:

| Property       | Description                                                                                                         | Example          |
| -------------- | ------------------------------------------------------------------------------------------------------------------- | ---------------- |
| `project`      | General name that represents the service domain that is used to set the entity, service, and API names.           | Shopping Cart    |
| `suffix`       | Used in conjunction with `project` to set package names.                                                           | Service          |
| `group-prefix` | Used in conjunction with `project` to set package names.                                                           | {{ group-id }}   |
| `team-name`    | Identifies the team that owns the generated project. Used to label published artifacts and in the generated README.| Growth           |

For a list of all derived properties and examples of the property relationships, see [archetype.yml](./archetype.yml).

## What's Inside

Features include:

- ASP.NET Core Web API with minimal APIs
- Entity Framework Core [EF](https://learn.microsoft.com/en-us/ef/core/)
- Testcontainers .NET (https://dotnet.testcontainers.org/)
- Simple REST API endpoints
- Docker image publication to artifactory
- Health checks and metrics endpoints
- Application configuration through property files, environment variables, and CLI arguments
- Integration with Kubernetes for deployment