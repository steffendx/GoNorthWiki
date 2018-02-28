At the moment GoNorth only supports a MongoDB system as the database system. If you want to save the data in a different database system you can extend GoNorth to use a SQL Server for example.  
The following steps are required for this:
 * You will have to implement all the different interfaces in the Data folder with an implementation that uses your database system
 * Change the mapping of the interface to your new implementation in the Startup.cs
 * Afterwards all database access will be handled using your new database access implementation instead of the MongoDB implementation

If you want to store the users in a SQL server for example you will have to implement the IUserDbAccess as a new class UserSqlDbAccess (or any other name that suits you). After changing the line

    services.AddScoped<IUserDbAccess, UserMongoDbAccess>();

to

    services.AddScoped<IUserDbAccess, UserSqlDbAccess>();

in the Startup.cs file the users will be stored and read from the SQL Server.