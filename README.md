以下は更新した`README.md`の内容です：

---

# JSON Schemas for TimeTracker NX WebAPI

This repository contains JSON Schemas for validating requests and responses for various API endpoints provided by the [TimeTracker NX WebAPI](https://docs.timetracker.jp/webapi/). The schemas are organized into directories based on the API endpoint structure.

> **Note:** While this repository provides the latest JSON Schemas based on the available documentation, we recommend checking the [official API documentation](https://docs.timetracker.jp/webapi/) for the most up-to-date information.

## 📂 Directory Structure

The directory structure mirrors the API's endpoint hierarchy for easier navigation and maintenance:

```
.
├── auth/
│   └── token/
│       ├── postToken.json
│       └── deleteToken.json
├── system/
│   ├── users/
│   │   ├── getUsers.json
│   │   ├── getUser.json
│   │   ├── getUserMe.json
│   │   ├── postUser.json
│   │   ├── putUser.json
│   │   ├── deleteUser.json
│   │   └── timeEntries/
│   │       ├── postTimeEntry.json
│   │       ├── getTimeEntries.json
│   │       └── deleteTimeEntry.json
│   ├── notifications/
│   │   └── getNotifications.json
│   ├── userGroups/
│   │   └── getUserGroups.json
│   └── organizations/
│       └── getOrganizations.json
├── project/
│   └── projects/
│       ├── getProjects.json
│       ├── getProject.json
│       ├── postProject.json
│       └── putProject.json
└── workitem/
    └── workItems/
        ├── getWorkItem.json
        ├── putWorkItem.json
        └── deleteWorkItem.json
```

## 🧩 JSON Schema Details

Each schema follows the [JSON Schema Draft 7](https://json-schema.org/specification-links.html#draft-7) standard.

### Examples

- **POST /auth/token**
  - Path: `auth/token/postToken.json`
  - Validates the request and response for token creation.

- **GET /system/users**
  - Path: `system/users/getUsers.json`
  - Validates the request and response for fetching user lists.

## 🚀 How to Use

1. Clone this repository:
   ```bash
   git clone https://github.com/aoinakanishi/timetracker-nx-api-json-schema.git
   ```

2. Use the schemas in your application or testing tools like Postman, AJV, or any JSON Schema validator.

3. Validate API requests/responses:
   ```javascript
   const Ajv = require("ajv");
   const schema = require("./auth/token/postToken.json");

   const ajv = new Ajv();
   const validate = ajv.compile(schema);

   const data = {
       loginName: "example",
       password: "securepassword"
   };

   const valid = validate(data);
   if (!valid) console.error(validate.errors);
   ```

## ⚠️ Disclaimer

- These schemas are based on the TimeTracker NX WebAPI documentation available at the time of creation.
- Always check the [official API documentation](https://docs.timetracker.jp/webapi/) for the latest updates and endpoint changes.

## 🛠️ Adding New Schemas

1. Create a new file in the appropriate directory based on the API endpoint.
2. Follow the JSON Schema Draft 7 specification to define the schema.
3. Commit and push your changes:
   ```bash
   git add .
   git commit -m "Add schema for [endpoint]"
   git push
   ```

## 📄 License

This repository is licensed under the MIT License. See the `LICENSE` file for more information.
