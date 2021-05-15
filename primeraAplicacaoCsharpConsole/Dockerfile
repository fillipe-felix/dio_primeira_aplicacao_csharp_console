FROM mcr.microsoft.com/dotnet/runtime:5.0 AS base
WORKDIR /app

FROM mcr.microsoft.com/dotnet/sdk:5.0 AS build
WORKDIR /src
COPY ["primeraAplicacaoCsharpConsole/primeraAplicacaoCsharpConsole.csproj", "primeraAplicacaoCsharpConsole/"]
RUN dotnet restore "primeraAplicacaoCsharpConsole/primeraAplicacaoCsharpConsole.csproj"
COPY . .
WORKDIR "/src/primeraAplicacaoCsharpConsole"
RUN dotnet build "primeraAplicacaoCsharpConsole.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "primeraAplicacaoCsharpConsole.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "primeraAplicacaoCsharpConsole.dll"]
