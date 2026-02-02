---
name: api-documentation
description: "A skill for creating comprehensive API documentation using OpenAPI/Swagger, including interactive examples. Use this skill when users want to generate, create, or update API documentation, OpenAPI specs, or Swagger files. Triggers: api documentation, openapi, swagger, api spec, swagger.json, openapi.yaml, documentar api, documentação de api."
allowed-tools: [Read, Write, Edit, Bash, Browser]
license: MIT License
metadata:
    skill-author: Lucas Kefler Bergamaschi
---

# API Documentation with OpenAPI/Swagger

## Overview
This skill empowers Manus to generate detailed, structured, and interactive API documentation using the OpenAPI Specification (formerly Swagger). It can analyze source code, existing documentation, or user requirements to produce a `swagger.json` or `openapi.yaml` file. This file can then be used to render interactive API documentation, generate client SDKs, and perform automated testing. The primary goal is to create clear, consistent, and easy-to-use documentation that helps developers understand and integrate with an API effectively.

## Automatic Triggers

**ALWAYS activate this skill when user mentions:**
- Keywords: api documentation, openapi, swagger, api spec, swagger.json, openapi.yaml, documentar api, documentação de api, interactive documentation, api console
- Phrases: "create api documentation", "generate swagger file", "document my api", "criar documentação de api", "gerar um swagger"
- Context: Any discussion about creating, generating, or updating documentation for an API.

## When to Use This Skill
This skill is particularly useful in the following scenarios:

*   **New API Development:** When a new API is being built, this skill can be used to create the documentation from scratch based on the API's design and endpoints.
*   **Documenting Existing APIs:** For APIs that lack proper documentation, this skill can analyze the codebase or existing partial documentation to generate a complete OpenAPI specification.
*   **Maintaining API Documentation:** As an API evolves, this skill can be used to update the documentation to reflect new endpoints, modified data models, or changes in authentication.
*   **Generating Interactive API Consoles:** When you need to provide developers with a "try it out" feature, allowing them to make live API calls from the documentation itself.
*   **Automating Client SDK Generation:** The generated OpenAPI file can be used with tools like Swagger Codegen or OpenAPI Generator to create client libraries in various programming languages.
*   **Standardizing API Documentation:** To ensure all APIs within an organization follow a consistent documentation style and structure.

## Core Capabilities

### 1. OpenAPI Specification Generation
The core of this skill is its ability to generate OpenAPI 3.0.x (or Swagger 2.0) specification files in either YAML or JSON format.

*   **From Source Code:** The skill can analyze source code (e.g., Python with Flask/FastAPI, Node.js with Express) and use annotations or docstrings to automatically generate the specification. For example, in FastAPI, it can extract information from path operation decorators and Pydantic models.
*   **From User Input:** The skill can engage in a dialogue with the user to gather all necessary information about the API, including:
    *   API metadata (title, version, description).
    *   Server information (URL, description).
    *   Authentication methods (API Key, OAuth2, JWT).
    *   Paths and operations (endpoints, HTTP methods).
    *   Parameters (path, query, header, cookie).
    *   Request bodies (content types, schemas).
    *   Responses (status codes, descriptions, schemas).
    *   Reusable components (schemas, security schemes).

### 2. Interactive Documentation Rendering
Once the specification file is created, the skill can use tools like **Swagger UI** or **Redoc** to render it as a user-friendly, interactive HTML documentation page.

*   **Swagger UI:** Provides a classic, interactive UI where users can not only read about the endpoints but also execute them directly in the browser.
*   **Redoc:** Generates a clean, three-panel documentation layout that is highly readable and well-structured, though it doesn't have the built-in "try it out" console by default.

The skill can set up a simple web server (e.g., using Python's `http.server` or a simple Node.js server) to serve the HTML documentation locally.

### 3. Code Analysis and Endpoint Discovery
The skill can read and analyze project files to automatically identify API endpoints, data models (DTOs/Pydantic models), and other relevant components. This reduces the manual effort required to document an existing API.

*   **Framework-Specific Parsing:** It has knowledge of common web frameworks and can look for route definitions (e.g., `@app.route('/users')` in Flask, `app.get('/users', ...)` in Express).
*   **Model Definition Extraction:** It can parse class definitions to create reusable schemas in the OpenAPI specification, ensuring that the documentation is consistent with the actual data structures used in the API.

## Step-by-Step Workflow

1.  **Gather API Information:** The skill starts by collecting all necessary details about the API. This can be done by:
    *   Asking the user for a high-level description of the API.
    *   Requesting access to the source code repository or relevant files.
    *   Looking for existing (even incomplete) documentation files.

2.  **Analyze and Structure:** The skill processes the gathered information.
    *   If source code is provided, it scans the files to identify endpoints, HTTP methods, parameters, and data models.
    *   It organizes this information according to the OpenAPI Specification structure.

3.  **Generate OpenAPI Specification File:** Based on the analysis, the skill writes the `openapi.yaml` or `swagger.json` file. It will populate all the required sections:
    *   `info`: Contains the API's title, version, and description.
    *   `servers`: Lists the base URLs for the API.
    *   `paths`: Details each endpoint, its operations (GET, POST, etc.), parameters, request bodies, and possible responses.
    *   `components`: Defines reusable elements like data schemas, security schemes, and parameter definitions.

4.  **Create an Interactive HTML Viewer:** The skill generates an `index.html` file that embeds Swagger UI or Redoc and points it to the generated specification file.

5.  **Serve the Documentation:** The skill can start a local web server to allow the user to immediately view the interactive documentation in their browser.

6.  **Iterate and Refine:** The user can review the generated documentation and provide feedback. The skill can then use the `Edit` tool to make corrections or additions to the `openapi.yaml` file and regenerate the documentation.

## Best Practices

*   **Be Descriptive:** Always add clear and concise descriptions for every endpoint, parameter, and schema. Explain the purpose and expected behavior.
*   **Use Examples:** Provide example values for parameters and example request/response bodies. This is crucial for developers to understand how to use the API correctly. The `examples` keyword in OpenAPI is perfect for this.
*   **Define Reusable Components:** For data models (schemas) that are used in multiple places, define them once in the `components/schemas` section and reference them using `$ref`. This keeps the specification DRY (Don't Repeat Yourself).
*   **Specify Authentication:** Clearly document how to authenticate with the API. Use the `securitySchemes` and `security` keywords to define the authentication method (e.g., API Key in header, OAuth2 flow).
*   **Use Semantic Versioning:** Use a clear versioning scheme for your API (e.g., `v1.0.0`) and update it in the `info` section when you make changes.
*   **Validate the Specification:** Before finalizing, use a linter or validator (like the online Swagger Editor) to check for any syntax errors or inconsistencies in the OpenAPI file.

## Examples

### Example 1: Generating a simple `openapi.yaml`

Here is a template for a basic API with one endpoint. The skill would generate this file.

```yaml
# SKILL.md:openapi-template.yaml
openapi: 3.0.3
info:
  title: Simple User API
  description: A simple API to manage users.
  version: 1.0.0
servers:
  - url: https://api.example.com/v1
description: Production server
paths:
  /users/{userId}:
    get:
      summary: Get a user by ID
      description: Retrieve a single user's information.
      tags:
        - Users
      parameters:
        - name: userId
          in: path
          required: true
          description: ID of the user to retrieve.
          schema:
            type: string
            example: "user123"
      responses:
        '200':
          description: A single user object.
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/User'
        '404':
          description: User not found.

components:
  schemas:
    User:
      type: object
      properties:
        id:
          type: string
          description: Unique identifier for the user.
          example: "user123"
        name:
          type: string
          description: The user's full name.
          example: "John Doe"
        email:
          type: string
          format: email
          description: The user's email address.
          example: "john.doe@example.com"
```

### Example 2: Creating the `index.html` for Swagger UI

The skill would create this file to render the documentation.

```html
<!-- SKILL.md:swagger-ui-template.html -->
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Swagger UI</title>
  <link rel="stylesheet" type="text/css" href="https://unpkg.com/swagger-ui-dist@5/swagger-ui.css">
  <style>
    html { box-sizing: border-box; overflow: -moz-scrollbars-vertical; overflow-y: scroll; }
    *, *:before, *:after { box-sizing: inherit; }
    body { margin:0; background: #fafafa; }
  </style>
</head>
<body>
  <div id="swagger-ui"></div>
  <script src="https://unpkg.com/swagger-ui-dist@5/swagger-ui-bundle.js" charset="UTF-8"></script>
  <script src="https://unpkg.com/swagger-ui-dist@5/swagger-ui-standalone-preset.js" charset="UTF-8"></script>
  <script>
    window.onload = function() {
      const ui = SwaggerUIBundle({
        url: "./openapi.yaml", // Path to your generated spec
        dom_id: '#swagger-ui',
        deepLinking: true,
        presets: [
          SwaggerUIBundle.presets.apis,
          SwaggerUIStandalonePreset
        ],
        plugins: [
          SwaggerUIBundle.plugins.DownloadUrl
        ],
        layout: "StandaloneLayout"
      });
      window.ui = ui;
    };
  </script>
</body>
</html>
```

### Example 3: Command to Serve the Documentation

The skill would use a simple shell command to start a local server.

```bash
# Start a simple web server in the current directory
python3 -m http.server 8000
```

Then, the user can navigate to `http://localhost:8000` to view the interactive documentation.

## References

*   **OpenAPI Specification 3.0.3:** [https://spec.openapis.org/oas/v3.0.3](https://spec.openapis.org/oas/v3.0.3)
*   **Swagger UI Documentation:** [https://swagger.io/tools/swagger-ui/](https://swagger.io/tools/swagger-ui/)
*   **Redoc Documentation:** [https://github.com/Redocly/redoc](https://github.com/Redocly/redoc)
*   **OpenAPI Generator:** [https://openapi-generator.tech/](https://openapi-generator.tech/)
*   **Swagger Editor:** [https://editor.swagger.io/](https://editor.swagger.io/)


### 4. Validation and Linting
To ensure the quality and correctness of the OpenAPI specification, the skill can integrate with validation tools.

*   **Automated Validation:** The skill can programmatically use libraries like `openapi-spec-validator` in Python to check the generated `openapi.yaml` against the official schema.
*   **Style and Best Practice Linting:** Using tools like Spectral, the skill can enforce stylistic conventions and best practices, such as ensuring all operations have summaries and tags.

## Advanced Workflow: Documenting a Live API

1.  **Initial Scan:** The user provides a base URL for an existing, running API.
