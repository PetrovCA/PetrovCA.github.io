![Docker](image_8.png)

# Working with PostgreSQL in Docker: A Beginner's Guide

## Introduction

Welcome to this easy-to-follow guide on setting up a PostgreSQL database using Docker! 🐳 Whether you're a developer, a database enthusiast, or just curious about Docker and databases, this tutorial is for you. We'll go step-by-step to ensure you can follow along without any hassle.

### Prerequisites

Before we dive in, make sure you have:

- Docker installed on your system (we'll use Docker for Windows in this tutorial).
- An IDE for database management, like JetBrains DataGrip, to test your database setup.

Ready? Let's get started!

---

## Part 1: Pulling the PostgreSQL Image 📥

First, we need to get the PostgreSQL image from Docker Hub.

1. Open Docker Desktop.
2. In the search bar, type `postgres` and select the `Images` tab.
3. Find the official PostgreSQL image and click `Pull`.

   ![Pull PostgreSQL Image](image.png)

Great! You should now see the PostgreSQL image in the `Images` tab of Docker.

![PostgreSQL Image in Docker](image_1.png)

---

## Part 2: Creating a Persistent Volume 💾

Docker containers are ephemeral, meaning they don't retain data when turned off. To keep our database data safe, we'll create a volume.

1. Go to the `Volumes` tab in Docker Desktop.
2. Click on `Create a Volume`.

   ![Create Volume](image_3.png)

3. Name your volume `postgres_data` for easy identification.
4. Click `Create`.

   ![Name and Create Volume](image_4.png)

---

## Part 3: Setting Up the Container 🛠️

Now, let's create and configure our PostgreSQL container.

Open your terminal and run:

```bash
    docker run --name postgres_container -e POSTGRES_PASSWORD=admin -d -p 5432:5432 -v postgres_data:/var/lib/postgresql/data postgres
```

### Command Breakdown

- `docker run`: Starts a new Docker container.
- `--name postgres_container`: Names our container `postgres_container`.
- `-e POSTGRES_PASSWORD=admin`: Sets the superuser password to `admin`.
- `-d`: Runs the container in detached mode (in the background).
- `-p 5432:5432`: Maps port 5432 on your machine to port 5432 in the container.
- `-v postgres_data:/var/lib/postgresql/data`: Uses our `postgres_data` volume for persistent storage.
- `postgres`: Specifies the PostgreSQL image to use. If a specific version isn't mentioned, Docker will automatically pull the latest version available from Docker Hub. For instance, if you haven't previously pulled a PostgreSQL image, or if you haven't specified a version like `postgres:13`, Docker will default to retrieving the latest version (e.g., `postgres:latest`). This ensures that you're working with the most up-to-date stable release of PostgreSQL. However, if you need a specific version for compatibility or other reasons, you can specify it directly (e.g., `postgres:12`).


Connection details for your new PostgreSQL container:

- **Host:** localhost
- **Port:** 5432
- **Database:** (default `postgres`)
- **Username:** (default `postgres`)
- **Password:** `admin`

---

## Part 4: Testing the Connection 🧪

Time to test our setup with DataGrip.

1. Open DataGrip and add a new data source.

   ![Add New Data Source](image_5.png)

2. Enter the connection details from Part 3.

   ![Enter Connection Details](image_6.png)

3. Test the connection. If everything is set up correctly, it should work!

   ![Successful Connection](image_7.png)

Congratulations! You now have a functioning PostgreSQL database running in Docker.

---

## What You've Learned 🌟

By completing this tutorial, you've achieved several key milestones:

- **Pulling a Docker Image:** You've learned how to search for and pull an image from Docker Hub.
- **Volume Creation for Data Persistence:** You now know how to create a volume in Docker, ensuring your data isn't lost when the container is stopped or removed.
- **Container Setup and Configuration:** You've successfully set up a PostgreSQL container with custom configurations.
- **Testing Database Connectivity:** Finally, you've tested and confirmed the successful setup of your PostgreSQL database using an IDE.

This knowledge forms a strong foundation for working with databases in Docker, giving you the flexibility and skills to manage data effectively in containerized environments.

Happy coding and data managing! 🚀

<table>
  <tr>
    <td align="center"><img alt="DataGrip" height="32" src="image_9.png"/></td>
    <td align="center"><img alt="Docker" height="32" src="image_10.png"/></td>
    <td align="center"><img alt="PostgreSQL" height="32" src="image_11.png"/></td>
  </tr>
</table>
