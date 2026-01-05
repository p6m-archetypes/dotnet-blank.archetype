# {{ PrefixName }} {{ SuffixName }}

**// TODO:** Add description of your project's business function.

Generated from the [.NET Blank Archetype](https://github.com/p6m-archetypes/dotnet-blank.archetype).

## What You Get

This project contains only the essential infrastructure files:

- **GitHub Actions workflows** for CI/CD pipeline
- **Kubernetes platform configuration** for deployment
- **Basic project structure** with gitignore

## What You Need to Add

This is a completely blank .NET project. You'll need to add:

- Your .NET application code
- Project files (`.csproj`, `.sln`)
- Dependencies and NuGet packages
- Dockerfile with your application entry point
- Tests
- Any framework-specific files

## Infrastructure Included

### GitHub Actions
- `build.yml` - Build and deploy to development
- `cut-tag.yml` - Cut patch, minor or major release tags
- `promote-stg.yml` - Promote to an environment

### Kubernetes Platform
- `application.yaml` - Platform application configuration

## Getting Started

1. Add your .NET application code
2. Create project files (`.csproj`, `.sln`)
3. Add dependencies via NuGet
4. Create a Dockerfile for your application
5. Update the GitHub Actions workflows to match your build process
6. Configure your deployment settings

## Contributions

**// TODO:** Add description of how you would like issues to be reported and people to reach out.