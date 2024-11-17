# eCommerce Web App

A Work-in-Progress (WIP) eCommerce web application built with **Golang**.  
The project features a backend for handling payment processing using **Stripe** and a frontend powered by **Bootstrap** for a responsive user interface.

---

## Table of Contents

- [eCommerce Web App](#ecommerce-web-app)
  - [Table of Contents](#table-of-contents)
  - [Requirements](#requirements)
  - [Setup](#setup)
  - [Go Packages](#go-packages)
  - [Running The Application](#running-the-application)
  - [Project Structure](#project-structure)
  - [Future Improvements](#future-improvements)

---

## Requirements

Ensure the following dependencies are installed on your system:

1. **Golang** (version 1.19+ recommended)
2. **Make** (via Homebrew: `brew install make`)
3. **MariaDB** (via Homebrew: `brew install mariadb`)
4. **Bootstrap** for frontend styling ([Download Bootstrap](https://getbootstrap.com))

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

## Go Packages

The application requires the Stripe Go SDK for payment integration:

Install it with:

```
go get -u github.com/stripe/stripe-go/v72
```

## Running The Application

1. Start the backend:

   ```
   make start_back
   ```

2. Open your browser and navigate to the frontend:

   ```
   http://localhost:4000
   ```

3. The backend API can be accessed at:
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
