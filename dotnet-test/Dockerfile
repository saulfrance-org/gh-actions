FROM mcr.microsoft.com/dotnet/runtime:8.0 AS base
WORKDIR /app

FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build
WORKDIR /src

COPY ["dotnet-test/PrimeService/PrimeService.csproj", "dotnet-test/PrimeService/PrimeService.csproj"]
RUN dotnet restore "dotnet-test/PrimeService/PrimeService.csproj"

COPY ./dotnet-test/ ./dotnet-test/

WORKDIR "/src/dotnet-test/PrimeService/"
RUN dotnet build "PrimeService.csproj" -c Release -o /app/build

FROM build AS test
LABEL test=true
WORKDIR "/src/dotnet-test"
RUN mkdir /testresults
RUN dotnet test --logger trx '--collect:XPlat Code Coverage' --results-directory /testresults 

FROM build AS publish
RUN dotnet publish "PrimeService.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "PrimeService.dll"]