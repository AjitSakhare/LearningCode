#Below code is to run application from visual studio direclty running locally.
FROM mcr.microsoft.com/dotnet/aspnet:10.0 as base
WORKDIR /app
EXPOSE 8080

#steps we need to follow to create a docker image for our application:

#publish command interally will restore and publish - But this is not good way. we need to add anotehr step called restore befoere publish


FROM mcr.microsoft.com/dotnet/sdk:10.0 as build
WORKDIR /src 

#Restore step 
COPY  "./ManualDockerCreation.csproj" .
RUN dotnet restore  "./ManualDockerCreation.csproj"

#step  - Build the application

COPY . .
RUN dotnet publish "./ManualDockerCreation.csproj" -c Release -o /app/publish --no-restore


#step  - Run the application
FROM mcr.microsoft.com/dotnet/aspnet:10.0
WORKDIR /app
COPY --from=build /app/publish .
ENTRYPOINT ["dotnet", "ManualDockerCreation.dll"]