# eCommerce Web App

A Work-in-Progress (WIP) eCommerce web application built with **Golang**.  
The project features a backend for handling payment processing using **Stripe** and a frontend powered by **Bootstrap** for a responsive user interface.

---

## Table of Contents

- [eCommerce Web App](#ecommerce-web-app)
  - [Table of Contents](#table-of-contents)
  - [Requirements](#requirements)
  - [Setup](#setup)
    - [How to Set Up and Connect to MariaDB Using Docker](#how-to-set-up-and-connect-to-mariadb-using-docker)
  - [Go Packages](#go-packages)
  - [Running The Application](#running-the-application)
  - [Project Structure](#project-structure)
  - [Future Improvements](#future-improvements)
  - [Reference](#reference)

---

## Requirements

Ensure the following dependencies are installed on your system:

1. **Golang** (version 1.19+ recommended)
2. **Make** (via Homebrew: `brew install make`)
3. **MariaDB** (via Homebrew: `brew install mariadb`)
4. **Bootstrap** for frontend styling ([Download Bootstrap](https://getbootstrap.com))
5. **Soda** for database migration (via Homebrew: `brew install gobuffalo/tap/pop`)

---

## Setup

1. Clone the repository:

   ```bash
   git clone https://github.com/yourusername/e-commerce-webapp.git
   cd e-commerce-webapp
   ```

2. Install required Go packages (see [Go Packages](#go-packages)).

3. Set up the database:

4. Configure environment variables (e.g., database credentials, Stripe API keys):

   ```
   STRIPE_KEY=your_stripe_key
   ```

5. Insert data to database:
   ```
   cd migrations
   soda migrate
   ```

### How to Set Up and Connect to MariaDB Using Docker

This guide provides a step-by-step process to set up and connect to MariaDB using Docker.

1. Start MariaDB Using Docker
   To run MariaDB in a Docker container, create a docker-compose.yml file with the following content:

   This setup will:

   - Expose port 3306 for database access
   - Set the root password, default database, and a user with a password
   - Use a volume to persist MariaDB data

2. Start the Docker Containers
   Once you have the docker-compose.yml file in place, start the MariaDB container by running:

   ```
   docker-compose up -d
   ```

   This will download the MariaDB image (if not already available) and start the container in detached mode.

3. Connect to MariaDB
   After starting the container, you can connect to MariaDB using the following command:

   ```
   mysql -u root -p -h 127.0.0.1
   ```

   When prompted for a password, enter the one you set in the MYSQL_ROOT_PASSWORD environment variable (in this case, password).

4. To connect with user other than root, open you db client, and run the following:
   ```
   grant all on widgets.* to '<your-user-name>'@'%' identified by 'password';
   ```

## Go Packages

```
go get -u github.com/stripe/stripe-go/v72

go get github.com/go-sql-driver/mysql
```

## Running The Application

1. Connect to DB. Open a DB client and enter

   ```
   host = 'localhost'
   username = 'root'
   password = <leave_blank>
   ```

2. Start the backend and frontend:

   ```
   make start
   ```

3. Open your browser and navigate to the frontend:

   ```
   http://localhost:4000
   ```

4. The backend API can be accessed at:
   ```
   http://localhost:4001
   ```

## Project Structure

```
e-commerce-webapp/
├── cmd/
│   ├── api/                # API-related application entry point
│   └── web/                # Web application entry point
├── dist/                   # Distribution files for deployment (e.g., static assets, binaries)
├── internal/
│   └── card/               # Internal business logic for handling card-related operations
│       └── card.go
├── .env                    # Environment configuration file (ignored by Git)
├── .gitignore              # Files and directories ignored by Git
├── go.mod                  # Go module dependencies
├── go.sum                  # Dependency checksums
├── Makefile                # Makefile for build and run commands
└── README.md               # Project documentation

```

## Future Improvements

1. macOS Connection Permissions: Configure the build to avoid repeated connection permission prompts when running on macOS.

## Reference

Stripe integration testing: https://docs.stripe.com/testing
