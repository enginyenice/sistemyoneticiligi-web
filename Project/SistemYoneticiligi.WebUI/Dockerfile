FROM mcr.microsoft.com/dotnet/sdk:5.0-buster-slim as build
WORKDIR /app
COPY Project/SistemYoneticiligi.WebUI/*.csproj SistemYoneticiligi.WebUI/
RUN dotnet restore SistemYoneticiligi.WebUI/*.csproj
COPY ./Project .
RUN dotnet publish SistemYoneticiligi.WebUI/*.csproj -c Release -o out
FROM mcr.microsoft.com/dotnet/aspnet:5.0-buster-slim as runtime
ENV TZ=Europe/Istanbul
WORKDIR /app
COPY --from=build /app/out .
ENTRYPOINT [ "dotnet","SistemYoneticiligi.WebUI.dll"]
