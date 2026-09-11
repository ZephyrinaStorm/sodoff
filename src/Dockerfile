# Place this file at src/Dockerfile in your fork of SoDOff.
# Build with the repository root as the Docker build context.
FROM mcr.microsoft.com/dotnet/sdk:10.0 AS build
WORKDIR /source
COPY . .
RUN dotnet publish src/sodoff.csproj -c Release -o /publish --no-self-contained
FROM mcr.microsoft.com/dotnet/aspnet:10.0
WORKDIR /app
COPY --from=build /publish/ ./
COPY --from=build /source/src/assets/ ./assets/
COPY --from=build /source/src/mods/ ./mods/
EXPOSE 5000 5001
ENTRYPOINT ["dotnet", "sodoff.dll"]

