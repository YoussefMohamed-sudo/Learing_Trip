# Project 001 - Products API with Database & Swagger

## 📋 Project Overview

This is the **first project** in the Learning Trip series. It's a simple **RESTful API** built with **ASP.NET Core** that demonstrates:

- ✅ Creating a Web API with .NET 9
- ✅ Connecting to SQL Server database using Entity Framework Core
- ✅ CRUD operations (Create, Read, Update, Delete)
- ✅ API documentation with Swagger/OpenAPI
- ✅ Testing APIs interactively

---

## 🎯 Learning Outcomes

By completing this project, you will learn:

1. **ASP.NET Core Basics**: How to create a minimal Web API
2. **Entity Framework Core**: Database connection and ORM usage
3. **Controllers**: Building API endpoints with proper HTTP methods
4. **Swagger**: Auto-generating API documentation
5. **Database Migrations**: Creating and updating database schema
6. **Dependency Injection**: Using DbContext in controllers

---

## 🏗️ Project Structure

```
001/
├── Controllers/
│   └── ProductsController.cs    # API endpoints for products
├── Data/
│   └── AppDbContext.cs          # Database context
├── Models/
│   └── Product.cs               # Product entity model
├── Program.cs                   # Application entry point & configuration
├── appsettings.json             # Configuration (database connection)
└── test.csproj                  # Project file with dependencies
```

---

## 📦 Technologies Used

- **.NET 9.0** - Latest .NET framework
- **ASP.NET Core Web API** - For building RESTful APIs
- **Entity Framework Core 9.0** - ORM for database operations
- **SQL Server** - Database
- **Swagger/Swashbuckle** - API documentation and testing UI

---

## 🔧 Prerequisites

Before running this project, make sure you have:

1. **.NET 9 SDK** installed ([Download here](https://dotnet.microsoft.com/download))
2. **SQL Server** (LocalDB, Express, or full version)
3. A code editor like **Visual Studio** or **VS Code**

---

## ⚙️ Configuration

### 1. Update Database Connection String

Open `appsettings.json` and update the connection string with your SQL Server details:

```json
{
  "ConnectionStrings": {
    "DefaultConnection": "Server=localhost;Database=DatabaseName;User Id=sa;Password=YourPass;Encrypt=True;TrustServerCertificate=True;MultipleActiveResultSets=true"
  }
}
```

**Replace:**
- `localhost` → Your SQL Server address
- `DatabaseName` → Your desired database name
- `sa` → Your SQL Server username
- `YourPass` → Your SQL Server password

---

## 🚀 How to Run

### Step 1: Restore Dependencies

```bash
cd 001
dotnet restore
```

### Step 2: Create Database Migration

```bash
dotnet ef migrations add InitialCreate
```

### Step 3: Update Database

```bash
dotnet ef database update
```

### Step 4: Run the Application

```bash
dotnet run
```

### Step 5: Open Swagger UI

The application will start and automatically open Swagger UI at:

```
https://localhost:5001
```

Or navigate to the URL shown in your terminal.

---

## 🧪 Testing the API

Once the application is running, you can test the API using **Swagger UI**:

### Available Endpoints:

| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/api/Products` | Get all products |
| `GET` | `/api/Products/{id}` | Get product by ID |
| `POST` | `/api/Products` | Create new product |
| `PUT` | `/api/Products/{id}` | Update existing product |
| `DELETE` | `/api/Products/{id}` | Delete product |

### Example: Create a Product

1. In Swagger UI, click on **POST /api/Products**
2. Click **"Try it out"**
3. Enter this JSON in the request body:

```json
{
  "name": "Laptop",
  "price": 999.99
}
```

4. Click **"Execute"**
5. You should get a `200 OK` response with the created product

---

## 📝 Code Highlights

### Product Model (`Models/Product.cs`)

```csharp
public class Product
{
    public int Id { get; set; }
    public string Name { get; set; }
    public decimal Price { get; set; }
}
```

### API Controller (`Controllers/ProductsController.cs`)

Implements all CRUD operations:
- `GetProducts()` - Returns all products
- `GetProduct(id)` - Returns single product
- `AddProduct(product)` - Creates new product
- `UpdateProduct(id, model)` - Updates product
- `DeleteProduct(id)` - Deletes product

---

## 🐛 Troubleshooting

### Issue: Database connection fails

**Solution**: 
- Verify SQL Server is running
- Check connection string in `appsettings.json`
- Ensure database user has proper permissions

### Issue: Migration commands not found

**Solution**: Install EF Core tools globally:

```bash
dotnet tool install --global dotnet-ef
```

### Issue: Port already in use

**Solution**: Change the port in `Properties/launchSettings.json` or kill the process using the port.

---

## 📚 What's Next?

After completing this project, you can:

1. Add **validation** to the Product model
2. Implement **pagination** for the GET all products endpoint
3. Add **search and filtering** capabilities
4. Implement **authentication and authorization**
5. Move on to **Project 002** in the Learning Trip!

---

## 📖 Resources

- [ASP.NET Core Documentation](https://docs.microsoft.com/aspnet/core)
- [Entity Framework Core](https://docs.microsoft.com/ef/core)
- [Swagger/OpenAPI](https://swagger.io/specification/)

---

**Happy Coding! 🚀**
