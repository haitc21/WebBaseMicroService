FROM mcr.microsoft.com/dotnet/aspnet:6.0 AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build
WORKDIR /src
COPY ["src/WebBase.IDP.STS.Identity/WebBase.IDP.STS.Identity.csproj", "src/WebBase.IDP.STS.Identity/"]
COPY ["src/WebBase.IDP.Admin.EntityFramework.Shared/WebBase.IDP.Admin.EntityFramework.Shared.csproj", "src/WebBase.IDP.Admin.EntityFramework.Shared/"]
COPY ["src/WebBase.IDP.Shared/WebBase.IDP.Shared.csproj", "src/WebBase.IDP.Shared/"]
RUN dotnet restore "src/WebBase.IDP.STS.Identity/WebBase.IDP.STS.Identity.csproj"
COPY . .
WORKDIR "/src/src/WebBase.IDP.STS.Identity"
RUN dotnet build "WebBase.IDP.STS.Identity.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "WebBase.IDP.STS.Identity.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENV ASPNETCORE_FORWARDEDHEADERS_ENABLED=true
ENTRYPOINT ["dotnet", "WebBase.IDP.STS.Identity.dll"]