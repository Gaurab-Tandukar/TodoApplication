# Todo App

A simple Todo application built with **ASP.NET Core MVC**, a **Web API** for CRUD operations, and **SQL Server** as the database, using **Entity Framework Core**.

## Tech Stack

- **Backend:** ASP.NET Core (MVC + Web API)
- **ORM:** Entity Framework Core
- **Database:** Microsoft SQL Server
- **Frontend:** Razor View (`.cshtml`) with vanilla JavaScript (fetch API)

## Features

- Create, read, update, and delete tasks
- Mark tasks as complete/incomplete
- Set task priority (High / Medium / Low) and due date
- Simple, responsive UI served directly from the app (no separate frontend build step)

## Project Structure

```
WebApplicationTest/
├── Controllers/
│   ├── HomeController.cs       # Default MVC controller
│   ├── TasksController.cs      # Web API controller — CRUD endpoints
│   └── TodoController.cs       # Serves the Todo frontend view
├── Data/
│   └── AppDbContext.cs         # EF Core database context
├── Models/
│   └── TodoTask.cs             # Task entity
├── Views/
│   ├── Home/
│   └── Todo/
│       └── Index.cshtml        # Todo app frontend
├── appsettings.json            # App configuration
└── Program.cs                  # App startup & service configuration
```

## API Endpoints

| Method | Endpoint | Description |
|---|---|---|
| GET | `/api/tasks` | Get all tasks |
| GET | `/api/tasks/{id}` | Get a single task by ID |
| POST | `/api/tasks` | Create a new task |
| PUT | `/api/tasks/{id}` | Update an existing task |
| DELETE | `/api/tasks/{id}` | Delete a task |

## Getting Started

### Prerequisites

- [.NET SDK](https://dotnet.microsoft.com/download) (8.0 or later)
- SQL Server (local or remote instance)
- Visual Studio 2022 (recommended) or VS Code

### Setup

1. **Clone the repository**
   ```bash
   git clone <your-repo-url>
   cd WebApplicationTest
   ```

2. **Configure the database connection**

   Update the connection string in `appsettings.json`:
   ```json
   "ConnectionStrings": {
     "DefaultConnection": "Server=localhost;Database=TodoAppDB;Trusted_Connection=True;TrustServerCertificate=True;"
   }
   ```

3. **Restore dependencies**
   ```bash
   dotnet restore
   ```

4. **Run the application**

   In Visual Studio, press **F5**, or from the command line:
   ```bash
   dotnet run
   ```

5. **Open the app**

   - Frontend: `https://localhost:<port>/Todo`
   - API (via Swagger, if enabled): `https://localhost:<port>/swagger`

## Task Model

| Field | Type | Notes |
|---|---|---|
| TaskID | int | Primary key |
| ListID | int? | Optional — groups tasks into lists |
| UserID | int | Owning user |
| Title | string | Required |
| Description | string? | Optional |
| IsCompleted | bool | Default: false |
| Priority | byte | 1 = High, 2 = Medium, 3 = Low |
| DueDate | DateTime? | Optional |
| CreatedAt | DateTime | Auto-set on creation |
| UpdatedAt | DateTime | Auto-set on update |

## License

This project is for personal/educational use.
