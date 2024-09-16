# Use the official .NET image to build the app
FROM mcr.microsoft.com/dotnet/sdk:7.0 AS build
WORKDIR /source

# Copy everything to /source
COPY . .

# Restore the dependencies
RUN dotnet restore

# Build the project
RUN dotnet publish -c Release -o /app

# Use the official ASP.NET runtime image
FROM mcr.microsoft.com/dotnet/aspnet:7.0 AS runtime
WORKDIR /app

# Copy the build app to runtime
COPY --from=build /app .

# Expose port 80
EXPOSE 80

# Set the entry point to the app
ENTRYPOINT ["dotnet", "HelloWorldAspNet.dll"]
