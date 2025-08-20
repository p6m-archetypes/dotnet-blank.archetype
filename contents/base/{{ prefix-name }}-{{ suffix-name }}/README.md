# {{ PrefixName }} {{ SuffixName }}

**// TODO:** Add description of your project's business function.

Generated from the [.NET Blank Service Archetype](https://github.com/p6m-archetypes/dotnet-blank.archetype).

## Table of Contents

- [Prerequisites](#prerequisites)
  - [1. .NET SDK](#1-net-sdk)
  - [2. NuGet Package Management](#2-nuget-package-management)
  - [3. Docker Installed and Running](#3-docker-installed-and-running)
- [Overview](#overview)
  - [Project Structure](#project-structure)
  - [Build System](#build-system)
- [Build](#build)
- [Run Server](#run-server)
  - [Using your service's APIs](#using-your-services-apis)
- [Ephemeral Mode (Recommended for Development)](#ephemeral-mode-recommended-for-development)
  - [Running with Ephemeral Database](#running-with-ephemeral-database)
  - [Integration Tests](#integration-tests)
- [Management API](#management-api)
  - [Health Checks](#health-checks)
  - [Metrics](#metrics)
- [Database Migrations](#database-migrations)
- [Contributions](#contributions)

## Prerequisites

### 1. .NET SDK

- **Version:** 8.0 or higher
- **Verify:**
  ```bash
  dotnet --version # → 8.x.x or greater
  ```
- See https://developer.p6m.dev/docs/workstation/dotnet for instructions

### 2. NuGet Package Management

- **Verify** you've configured **Artifactory**
  ```bash
  echo $ARTIFACTORY_USERNAME
  echo $ARTIFACTORY_IDENTITY_TOKEN
  ```
- See https://developer.p6m.dev/docs/workstation/core/artifacts for instructions

### 3. Docker Installed and Running

- **Verify** you have installed docker
  ```bash
  docker --version # Should be version X.X.+
  docker info # Should list server info without any errors
  ```
- See https://developer.p6m.dev/docs/workstation/core/docker for instructions

## Overview

### Project Structure

This is a minimal .NET Web API service with the following structure:

- **{{ PrefixName }}{{ SuffixName }}**: Main Web API project with controllers and endpoints
- **Entity Framework Core**: For database operations and migrations
- **Health Checks**: Built-in health monitoring
- **Metrics**: Prometheus metrics support
- **Docker**: Containerized deployment
- **Tests**: Unit and integration tests

### Build System

This project uses [dotnet](https://learn.microsoft.com/en-us/dotnet/core/tools/dotnet#general) as its build system. Common commands:

| Command | Description                                        |
| ------- | -------------------------------------------------- |
| clean   | Clean build outputs                                |
| build   | Builds the .NET application                        |
| restore | Restores the dependencies for the application      |
| run     | Runs the application from source                   |
| test    | Runs tests using the test runner                   |

## Build

```bash
dotnet build
```

## Run Server

Start the server locally with:

```bash
dotnet run
```

Or run with ephemeral database mode (recommended for development):

```bash
dotnet run -- --ephemeral
```

The server accepts connections on:

- **Port 80**: HTTP API endpoints
- **Port 26257**: PostgreSQL database (when using docker-compose)

### Using your service's APIs

The service exposes REST API endpoints. Here are some examples:

**Health Check:**
```bash
curl http://localhost:80/health
```

**API Endpoints:**
```bash
# Get all items
curl http://localhost:80/api/{{ prefix-name }}

# Create a new item
curl -X POST http://localhost:80/api/{{ prefix-name }} \
    -H "Content-Type: application/json" \
    -d '{"name": "example"}'

# Get specific item
curl http://localhost:80/api/{{ prefix-name }}/1

# Update item
curl -X PUT http://localhost:80/api/{{ prefix-name }}/1 \
    -H "Content-Type: application/json" \
    -d '{"name": "updated"}'

# Delete item
curl -X DELETE http://localhost:80/api/{{ prefix-name }}/1
```

## Ephemeral Mode (Recommended for Development)

The service supports **ephemeral mode** that automatically starts a PostgreSQL database in a Docker container using [Testcontainers](https://dotnet.testcontainers.org/). This provides a real PostgreSQL database for development without manual setup.

### Running with Ephemeral Database

Start the server with the `--ephemeral` flag:

```bash
dotnet run -- --ephemeral
```

**What happens:**

- Automatically downloads and starts a PostgreSQL 15 Alpine container
- Creates a fresh database with a random port
- Creates database schema from current Entity Framework model
- Starts the Web API service
- Cleans up the container when the service stops

**Benefits:**

- ✅ **Zero setup** - No need to install PostgreSQL or run docker-compose
- ✅ **Real database** - Uses actual PostgreSQL, not in-memory simulation
- ✅ **Clean state** - Fresh database on every startup
- ✅ **Automatic cleanup** - Container is removed when service stops
- ✅ **Perfect for development** - Matches production database behavior

**Requirements:**

- Docker must be installed and running
- Internet connection (first time only, to download PostgreSQL image)

### Integration Tests

Integration tests automatically use ephemeral mode:

```bash
dotnet test
```

Each test run gets:

- Fresh PostgreSQL container on a random port
- Clean database state
- Real database transactions and constraints
- Automatic cleanup after tests complete

## Management API

### Health Checks

Verify the service is running:

```bash
curl http://localhost:80/health
```

### Metrics

Prometheus metrics are available at:

```bash
curl http://localhost:80/metrics
```

## Database Migrations

### Create DB Migration

```bash
dotnet ef migrations add InitialCreation
```

### Apply DB migrations

```bash
dotnet ef database update
```

### Remove DB migrations

```bash
dotnet ef migrations remove
```

## Contributions

**// TODO:** Add description of how you would like issues to be reported and people to reach out.