Account Trade Management API

Overview

This is a RESTful API for managing accounts and trades. The API supports CRUD operations for accounts, searching for accounts, placing and updating trades, and caching frequently accessed data. The backend uses C# with ASP.NET Core, PostgreSQL for persistence, and supports caching for improved performance.

Technologies Used

C# (ASP.NET Core 9)

PostgreSQL (Database)

Entity Framework Core (ORM)

MoQ & xUnit (Unit Testing)

Memory Cache (Caching Mechanism)

Prerequisites

.NET 9 SDK

PostgreSQL installed and running

Visual Studio 2022 (or any IDE supporting .NET 9)

Database Setup (PostgreSQL)

Install PostgreSQL if not already installed.

Create a new database:

CREATE DATABASE AccountTradeDB;

Update the appsettings.json with the connection string:

"ConnectionStrings": {
  "DefaultConnection": "Host=localhost;Port=5432;Database=AccountTradeDB;Username=your_username;Password=your_password"
}

Run database migrations to create tables:

dotnet ef migrations add InitialCreate
dotnet ef database update

API Endpoints

Account Management

Create an AccountPOST /api/accounts

{
  "firstName": "John",
  "lastName": "Doe"
}

Get Account by IDGET /api/accounts/{id}

Search Accounts by Last NameGET /api/accounts/search?lastName=Doe

Delete an AccountDELETE /api/accounts/{id}

Trade Management

Place a TradePOST /api/trades

{
  "accountId": "guid-value",
  "securityCode": "AAPL",
  "amount": 1000,
  "status": "Placed"
}

Get Trade by IDGET /api/trades/{id}

Update Trade StatusPUT /api/trades/{id}

"Executed"

Caching Mechanism

Caching is implemented using MemoryCache.

Cached data expires after 5 minutes or is refreshed if accessed within 2 minutes.

Improves performance by reducing database queries.

Running the Project

Restore dependencies:

dotnet restore

Run the application:

dotnet run

The API should now be available at https://localhost:5001

Running Unit Tests

Tests are written using xUnit and MoQ

Run tests using:

dotnet test

Future Enhancements

Implement authentication & authorization

Add logging for better debugging

Implement Redis for distributed caching


