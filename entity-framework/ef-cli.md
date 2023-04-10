# entity framework cli

## setup

- install

  `dotnet tool install --global dotnet-ef --version 6.0.0`

- create new app

  `dotnet new console -n MyApp`
  `cd MyApp`

- add sql server package

  `dotnet add package Microsoft.EntityFrameworkCore.SqlServer`

- add sqlite package

  `dotnet add package Microsoft.EntityFrameworkCore.Sqlite`

- add ef core tools package

  `dotnet add package Microsoft.EntityFrameworkCore.Tools`

## scaffolding

- scaffold from db

  `dotnet ef dbcontext scaffold "Data Source=MyDatabase.db" Microsoft.EntityFrameworkCore.Sqlite -o Models`

## migrations

- create migration

  `dotnet ef migrations add V1`

- list migrations

  `dotnet ef migrations list`

- script migrations

  `dotnet ef migrations script`

- script migration to file

  `--dotnet ef migrations script V1 -o MyDbScript.sql`

- update database

`dotnet ef database update`

### resources

- [learn entity frameworks](https://www.learnentityframeworkcore.com/)
