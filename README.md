# WebBaseMicroService

# Create new project IDP
github: https://github.com/skoruba/Duende.IdentityServer.Admin.git

```sh 
dotnet new -i Skoruba.Duende.IdentityServer.Admin.Templates::1.1.0

dotnet new skoruba.duende.isadmin --name "WebBase.IDP" --title "WebBase.IDP" --adminemail "admin@gmail.com" --adminpassword "Admin@123" --adminrole ADMIN --adminclientid "WebBase.IDP" --adminclientsecret "WebBase.IDP" --dockersupport true
```
# migration IDP
```sh 
#cd build
.\add-migrations.ps1 -migration DbInit -migrationProviderName SqlServer
```

Migration Options
```
 --migration (migration name)
 --migrationProviderName (provider type - available choices: All, SqlServer, MySql, PostgreSQL)
 ```

# Run Frontend
npm i -f
npm start