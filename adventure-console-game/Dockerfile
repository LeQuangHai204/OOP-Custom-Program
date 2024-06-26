FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build

WORKDIR /app

COPY *.csproj .

RUN dotnet restore

COPY . .

RUN dotnet publish -c Release -o out

FROM mcr.microsoft.com/dotnet/sdk:8.0

WORKDIR /app

# Copy built application from build stage
COPY --from=build /app/out .

# Set the entry point of the container
ENTRYPOINT ["dotnet", "adventure-console-game.dll"]
