FROM mcr.microsoft.com/dotnet/core/sdk:2.2 AS build-env
WORKDIR /app

COPY *.csproj ./
RUN dotnet restore

COPY . ./
RUN dotnet publish -c Release -o out

FROM mcr.microsoft.com/dotnet/core/aspnet:2.2

EXPOSE 80
EXPOSE 443
EXPOSE 5000
EXPOSE 5001

WORKDIR /app
COPY --from=build-env /app/out .
ENTRYPOINT ["dotnet", "dotnetapi.dll"]