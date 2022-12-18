# WebBaseMicroService

# Create new project IDP
github: https://github.com/skoruba/Duende.IdentityServer.Admin.git

dotnet new -i Skoruba.Duende.IdentityServer.Admin.Templates::1.1.0

dotnet new skoruba.duende.isadmin --name "WebBase.IDP" --title "WebBase.IDP" --adminemail "admin@gmail.com" --adminpassword "Admin@123" --adminrole ADMIN --adminclientid "WebBase.IDP" --adminclientsecret "WebBase.IDP" --dockersupport true

# Run Frontend
npm i -f
npm start