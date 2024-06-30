---
label: "Documentation"
icon: book
order: 1000
---

# TypeScriptSQL Class Documentation

## Overview

The `TypeScriptSQL` class provides a convenient wrapper around MySQL operations using promises. It allows for basic CRUD operations, table creation, and connection handling.

## Class Definition

```typescript
import * as mysql from "mysql";

export class TypeScriptSQL {
  private connection: mysql.Connection;

  constructor(config: mysql.ConnectionConfig) {
    this.connection = mysql.createConnection(config);
    this.connection.connect((err) => {
      if (err) {
        console.error("Error connecting to the database:", err.stack);
        return;
      }
      console.log("Connected to the database as ID", this.connection.threadId);
    });
  }

  query(sql: string, args?: any[]): Promise<any> {
    /* ... */
  }
  createTable(table: string, tableDefinition: string): Promise<any> {
    /* ... */
  }
  create(table: string, data: object): Promise<any> {
    /* ... */
  }
  read(table: string, conditions?: object): Promise<any> {
    /* ... */
  }
  createOrUpdate(table: string, data: object): Promise<any> {
    /* ... */
  }
  update(table: string, data: object, conditions: object): Promise<any> {
    /* ... */
  }
  delete(table: string, conditions: object): Promise<any> {
    /* ... */
  }
  close(): Promise<void> {
    /* ... */
  }
}
```

## Methods

### Constructor

```typescript
constructor(config: mysql.ConnectionConfig)
```

- **Description**: Initializes a new instance of the `TypeScriptSQL` class and establishes a database connection.
- **Parameters**:
  - `config` (mysql.ConnectionConfig): The configuration object for the database connection.

### query

```typescript
query(sql: string, args?: any[]): Promise<any>
```

- **Description**: Executes a SQL query.
- **Parameters**:
  - `sql` (string): The SQL query string.
  - `args` (any[], optional): An array of arguments for parameterized queries.
- **Returns**: A promise that resolves with the query results.

### createTable

```typescript
createTable(table: string, tableDefinition: string): Promise<any>
```

- **Description**: Creates a table if it does not exist.
- **Parameters**:
  - `table` (string): The name of the table.
  - `tableDefinition` (string): The SQL table definition.
- **Returns**: A promise that resolves when the table is created.

### create

```typescript
create(table: string, data: object): Promise<any>
```

- **Description**: Inserts a new record into a table.
- **Parameters**:
  - `table` (string): The name of the table.
  - `data` (object): An object representing the record to insert.
- **Returns**: A promise that resolves when the record is inserted.

### read

```typescript
read(table: string, conditions?: object): Promise<any>
```

- **Description**: Reads records from a table.
- **Parameters**:
  - `table` (string): The name of the table.
  - `conditions` (object, optional): An object representing query conditions.
- **Returns**: A promise that resolves with the query results.

### createOrUpdate

```typescript
createOrUpdate(table: string, data: object): Promise<any>
```

- **Description**: Inserts a new record or updates an existing record.
- **Parameters**:
  - `table` (string): The name of the table.
  - `data` (object): An object representing the record to insert or update.
- **Returns**: A promise that resolves when the operation is complete.

### update

```typescript
update(table: string, data: object, conditions: object): Promise<any>
```

- **Description**: Updates existing records in a table.
- **Parameters**:
  - `table` (string): The name of the table.
  - `data` (object): An object representing the new data.
  - `conditions` (object): An object representing the query conditions.
- **Returns**: A promise that resolves when the records are updated.

### delete

```typescript
delete(table: string, conditions: object): Promise<any>
```

- **Description**: Deletes records from a table.
- **Parameters**:
  - `table` (string): The name of the table.
  - `conditions` (object): An object representing the query conditions.
- **Returns**: A promise that resolves when the records are deleted.

### close

```typescript
close(): Promise<void>
```

- **Description**: Closes the database connection.
- **Returns**: A promise that resolves when the connection is closed.

## Examples

### Setting up the Connection

```typescript
import { TypeScriptSQL } from "./TypeScriptSQL";
import * as mysql from "mysql";

const config: mysql.ConnectionConfig = {
  host: "localhost",
  user: "your-username",
  password: "your-password",
  database: "your-database",
};

const db = new TypeScriptSQL(config);
```

### Creating a Table

```typescript
const tableDefinition = `
  id INT AUTO_INCREMENT PRIMARY KEY,
  name VARCHAR(255) NOT NULL,
  age INT NOT NULL
`;

db.createTable("users", tableDefinition)
  .then(() => console.log("Table created successfully"))
  .catch((err) => console.error("Error creating table:", err));
```

### Inserting a Record

```typescript
const user = {
  name: "John Doe",
  age: 30,
};

db.create("users", user)
  .then(() => console.log("User created successfully"))
  .catch((err) => console.error("Error creating user:", err));
```

### Reading Records

```typescript
db.read("users")
  .then((results) => console.log("Users:", results))
  .catch((err) => console.error("Error reading users:", err));

// Reading with conditions
const conditions = { age: 30 };

db.read("users", conditions)
  .then((results) => console.log("Users aged 30:", results))
  .catch((err) => console.error("Error reading users:", err));
```

### Updating Records

```typescript
const data = { name: "Jane Doe", age: 25 };
const conditions = { id: 1 };

db.update("users", data, conditions)
  .then(() => console.log("User updated successfully"))
  .catch((err) => console.error("Error updating user:", err));
```

### Deleting Records

```typescript
const conditions = { id: 1 };

db.delete("users", conditions)
  .then(() => console.log("User deleted successfully"))
  .catch((err) => console.error("Error deleting user:", err));
```

### Closing the Connection

```typescript
db.close()
  .then(() => console.log("Database connection closed"))
  .catch((err) => console.error("Error closing connection:", err));
```
