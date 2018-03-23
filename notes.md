// run the api
dotnet run

// run the api on watch mode
dotnet watch run

//restores the dependencies and tools of a project.
dotnet restore

export ASPNETCORE_ENVIRONMENT=development 

// test




If your migration involves renaming a column in the table, then this will not work with SQLite due to its limitations, more details here.  I presume you have renamed one of the properties in a model?
https://docs.microsoft.com/en-us/ef/core/providers/sqlite/limitations

The easiest fix to this situation is to do the following:

1. Drop the existing database (dotnet ef database drop)

2. Delete the migrations folder to remove any existing migrations.

3. Create a new migration (dotnet ef migrations add initialCreate)

4. Run dotnet ef database update.

This will resolve the issue.