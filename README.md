### **Description**  
This Laravel project is a lightweight and flexible solution for creating and testing mock APIs. It allows you to define custom endpoints with configurable headers, request bodies, and success/error responses. The project leverages SQLite for seamless setup without the need for external database installations, making it portable and easy to use across different systems.  

Key Features:  
- Define mock APIs with customizable headers, request bodies, and responses.  
- Handle different HTTP methods (GET, POST, PUT, DELETE, etc.).  
- Test APIs easily using cURL or any HTTP client.  
- SQLite database for minimal configuration and easy portability.  

---

### **README**  

# Mock API Generator  

## Introduction  
The **Mock API Generator** is a Laravel-based tool designed to simplify API testing and development. By defining mock endpoints, developers can simulate real-world API interactions without depending on external systems.  

## Features  
- **Custom Endpoints:** Define endpoints with specific HTTP methods, headers, and request bodies.  
- **Flexible Responses:** Set success and error responses for each endpoint.  
- **Database:** Uses SQLite for out-of-the-box functionality with zero installation.  
- **Test-Friendly:** Easily test using cURL, Postman, or other tools.  

## Installation  

1. **Clone the Repository:**  
   ```bash
   git clone https://github.com/your-username/mock-api-generator.git
   cd mock-api-generator
   ```

2. **Install Dependencies:**  
   ```bash
   composer install
   ```

3. **Set Up Environment:**  
   Create a `.env` file and configure it as follows:  
   ```env
   APP_NAME=MockApi
   APP_ENV=local
   APP_KEY=base64:YOUR_KEY
   DB_CONNECTION=sqlite
   DB_DATABASE=/absolute/path/to/database.sqlite
   ```

4. **Set Up Database:**  
   ```bash
   mkdir -p database
   touch database/database.sqlite
   php artisan migrate
   ```

5. **Run the Application:**  
   ```bash
   php artisan serve
   ```

6. **Access the Application:**  
   Open your browser and navigate to `http://127.0.0.1:8000`.

---

## Usage  

### **Create a Mock API**  
Send a POST request to `/api/create` with the following JSON payload:  

```json
{
    "method": "POST",
    "route": "example-api",
    "headers": {"Authorization": "Bearer test"},
    "body": {"key": "value"},
    "response_success": {"message": "API call was successful"},
    "response_error": {"message": "API call failed"}
}
```

### **Test a Mock API**  
Send a request to the defined route, for example:  

```bash
curl -X POST http://127.0.0.1:8000/mock/example-api \
-H "Content-Type: application/json" \
-H "Authorization: Bearer test" \
-d '{"key": "value"}'
```

### **Expected Responses:**  
- **Success:** Returns the `response_success` JSON if the request matches the expected body.  
- **Error:** Returns the `response_error` JSON if the request body or headers are incorrect.  

---

## Contribution  
Contributions are welcome! Please fork the repository and submit a pull request for any improvements or features you would like to add.  

## License  
This project is open-sourced under the [MIT License](https://opensource.org/licenses/MIT).  
