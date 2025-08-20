# .NET Blank Archetype

![Latest Release](https://img.shields.io/github/v/release/p6m-archetypes/dotnet-blank.archetype?style=flat-square&label=Latest%20Release&color=blue)

## Usage

To get started, [install archetect](https://github.com/p6m-archetypes/development-handbook)
and render this template to your current working directory:

```bash
archetect render git@github.com:p6m-archetypes/dotnet-blank.archetype.git
```

This creates a completely empty .NET project with only the necessary infrastructure and CI/CD files.

## Prompts

When rendering the archetype, you'll be prompted for the following values:

| Property       | Description                                                                                                         | Example          |
| -------------- | ------------------------------------------------------------------------------------------------------------------- | ---------------- |
| `project`      | General name that represents the service domain                                                                     | Shopping Cart    |
| `suffix`       | Used in conjunction with `project` to set package names                                                            | Service          |
| `group-prefix` | Used in conjunction with `project` to set package names                                                            | {{ group-id }}   |
| `team-name`    | Identifies the team that owns the generated project                                                                 | Growth           |

## What's Inside

This archetype provides only infrastructure and CI/CD files:

- **GitHub Actions workflows** for CI/CD pipeline (build, promote to staging/production)
- **Kubernetes platform configuration** for deployment
- **Basic project structure** with gitignore
- **No application code, dependencies, or framework opinions**

You add your own .NET application code, project files, and build configuration.