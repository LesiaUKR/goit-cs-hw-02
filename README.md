# HW | Fundamentals of Operating Systems

Today's homework consists of two independent tasks aimed at using the Bash command line to automate processes and deepen your understanding of Docker and containerization.

In this homework, you will practice:

Interacting with the operating system via the command line by creating bash scripts and using the curl command—a powerful command-line tool for interacting with web servers, especially for executing HTTP requests.
Configuring and using Docker Compose to manage an environment containing both an application and a PostgreSQL database.
You’ll gain practical skills applicable in real-world scenarios for working with operating systems and networks, along with hands-on experience containerizing a FastAPI application alongside its PostgreSQL database.

Let’s get started! 💪🏼

## Technical Task Descriptions

### Task 1

Write a script that automatically checks the availability of specific websites. The script should use the curl command to send HTTP GET requests to each site in the list and check the response.

### Step-by-Step Instructions

1. List of Websites: Your script should define an array of website URLs to check. For example, https://google.com, https://facebook.com, https://twitter.com.

2. Availability Check: The script should check each site in the list using curl to ensure the site responds with an HTTP status code of 200, indicating successful availability.

3. Log Results to a File: For each site, the check result (available or unavailable) should be recorded in a log file. The log file name should be specified in the script.

4. Output Formatting: Results should be clearly formatted, for example: "<https://google.com> is UP" or "<https://twitter.com> is DOWN".

5. Output Message: After the script runs, it should display a message indicating that the results have been saved to the log file along with its name.

### Example Script Execution

The script executes commands and logs the results in website_status.log. Log entries display each site's status (UP or DOWN) at the time of script execution.

```vbnet
https://google.com is UP
https://facebook.com is UP
https://twitter.com is UP

```

### Acceptance Criteria

- The script is written in Bash.
- The script handles redirection.
- A loop is used to iterate through all sites in the list.
- The curl command is used to check HTTP responses.
- Check results are saved in a log file, and a message about it is displayed.
- The code formatting is clean and tidy.

## Task 2

Clone a FastAPI application, configure and run it in a Docker container, and check the application's functionality and database connection.

### Step-by-Step Instructions

1. Clone the repository at https://github.com/GoIT-Python-Web/Computer-Systems-hw02 using git clone and navigate to the cloned directory.

2. Create a Dockerfile with instructions to build the Docker image for the application.

3. Write a docker-compose.yaml file with the configuration for the application and PostgreSQL.

4. Use Docker Compose to build the environment and the docker-compose up command to launch the environment.

💡 Hint: Modify the SQLALCHEMY_DATABASE_URL connection string found in conf/db.py. Instead of localhost, insert the PostgreSQL service name from your docker-compose.yaml.

#### Example:

```python
SQLALCHEMY_DATABASE_URL = f"postgresql+psycopg2://postgres:567234@localhost:5432/hw02"
```

When using Docker Compose, each service (container) has its own network, and they usually can’t communicate via localhost. Instead, use the service name as the hostname.

5. Verify the application’s functionality and the database’s availability.
   💡 Hint:

After running the container with the application, the browser view should appear as follows:

![Container](./assets/Screenshot_1.jpg)

If correctly configured in docker-compose.yaml, pressing the “Check DB” button should display the following:

![Container](./assets/Screenshot_2.jpg)

If you see a red error box instead of “Welcome to FastAPI!”, it means docker-compose.yaml is incorrectly configured.

### Acceptance Criteria

- The repository is cloned, and a Dockerfile for building the application’s Docker image is created.
- A docker-compose.yaml file is written with configuration for the application and PostgreSQL.
- Docker Compose and the docker-compose up command are used to build and run the environment.
- The application is functional, and the database is accessible, as confirmed by pressing the “Check DB” button.
