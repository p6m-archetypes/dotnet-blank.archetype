# Build stage
FROM mcr.microsoft.com/dotnet/sdk:9.0 AS build
WORKDIR /src
COPY . .

RUN --mount=type=secret,id=artifactory-username,env=ARTIFACTORY_USERNAME \
    --mount=type=secret,id=artifactory-identity-token,env=ARTIFACTORY_IDENTITY_TOKEN \
    dotnet restore

RUN dotnet publish -c Release -o /app/publish

# Runtime stage
FROM mcr.microsoft.com/dotnet/aspnet:9.0
WORKDIR /app
COPY --from=build /app/publish .
EXPOSE 8080
EXPOSE 8081
ENTRYPOINT ["dotnet", "{{ prefix-name }}-{{ suffix-name }}.dll"]
