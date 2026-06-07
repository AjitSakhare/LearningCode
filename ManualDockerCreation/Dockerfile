#Two steps we need to follow to create a docker image for our application:

#step 1 - Build the application
FROM mcr.microsoft.com/dotnet/sdk:10.0 as build
WORKDIR /src 
COPY . .
RUN dotnet publish "./ManualDockerCreation.csproj" -c Release -o /app/publish



#step 2 - Run the application
FROM mcr.microsoft.com/dotnet/aspnet:10.0
WORKDIR /app
COPY --from=build /app/publish .
ENTRYPOINT ["dotnet", "ManualDockerCreation.dll"]