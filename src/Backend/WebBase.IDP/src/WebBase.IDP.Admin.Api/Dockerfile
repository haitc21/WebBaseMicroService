FROM mcr.microsoft.com/dotnet/aspnet:6.0 AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/sdk:6.0 AS build
WORKDIR /src
COPY ["src/WebBase.IDP.Admin.Api/WebBase.IDP.Admin.Api.csproj", "src/WebBase.IDP.Admin.Api/"]
COPY ["src/WebBase.IDP.Admin.EntityFramework.Shared/WebBase.IDP.Admin.EntityFramework.Shared.csproj", "src/WebBase.IDP.Admin.EntityFramework.Shared/"]
COPY ["src/WebBase.IDP.Admin.EntityFramework.SqlServer/WebBase.IDP.Admin.EntityFramework.SqlServer.csproj", "src/WebBase.IDP.Admin.EntityFramework.SqlServer/"]
COPY ["src/WebBase.IDP.Shared/WebBase.IDP.Shared.csproj", "src/WebBase.IDP.Shared/"]
COPY ["src/WebBase.IDP.Admin.EntityFramework.PostgreSQL/WebBase.IDP.Admin.EntityFramework.PostgreSQL.csproj", "src/WebBase.IDP.Admin.EntityFramework.PostgreSQL/"]
COPY ["src/WebBase.IDP.Admin.EntityFramework.MySql/WebBase.IDP.Admin.EntityFramework.MySql.csproj", "src/WebBase.IDP.Admin.EntityFramework.MySql/"]
RUN dotnet restore "src/WebBase.IDP.Admin.Api/WebBase.IDP.Admin.Api.csproj"
COPY . .
WORKDIR "/src/src/WebBase.IDP.Admin.Api"
RUN dotnet build "WebBase.IDP.Admin.Api.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "WebBase.IDP.Admin.Api.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENV ASPNETCORE_FORWARDEDHEADERS_ENABLED=true
ENTRYPOINT ["dotnet", "WebBase.IDP.Admin.Api.dll"]