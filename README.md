# WebBaseMicroService

# Create new project IDP
github: https://github.com/skoruba/Duende.IdentityServer.Admin.git

```sh 
dotnet new -i Skoruba.Duende.IdentityServer.Admin.Templates::1.1.0

dotnet new skoruba.duende.isadmin --name "WebBase.IDP" --title "WebBase.IDP" --adminemail "admin@gmail.com" --adminpassword "Admin@123" --adminrole ADMIN --adminclientid "WebBase.IDP" --adminclientsecret "WebBase.IDP" --dockersupport true
```
Project template options:

```
--name: [string value] for project name
--adminpassword: [string value] admin password
--adminemail: [string value] admin email
--title: [string value] for title and footer of the administration in UI
--adminrole: [string value] for name of admin role, that is used to authorize the administration
--adminclientid: [string value] for client name, that is used in the Duende IdentityServer configuration for admin client
--adminclientsecret: [string value] for client secret, that is used in the Duende IdentityServer configuration for admin client
--dockersupport: [boolean value] include docker support
```

# mMgration IDP
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
```sh 
npm i -f
npm start
```sh 