# flow2know

A new project based on fastapi_supabase_template.

## Description

[Add a brief description of your project here.]

## Getting Started

### Prerequisites

-   [Python](https://www.python.org/)
-   [uv](https://github.com/astral-sh/uv)
-   [Supabase CLI](https://supabase.com/docs/guides/cli)
-   [Docker](https://www.docker.com/)

### Environment Setup

1.  **Install Python dependencies:**

    ```bash
    cd backend
    uv sync --all-groups --dev
    ```

2.  **Start Supabase services:**

    Make sure you have the [Supabase CLI](https://supabase.com/docs/guides/cli) installed.

    ```bash
    # From the project root
    supabase start
    ```

    After running `supabase start`, your Supabase credentials will be displayed. You need to update the `.env` file with these credentials. You can do this manually or by running the provided script:

    ```bash
    # This script will update your .env file with the credentials from Supabase.
    bash scripts/update-env.sh
    ```

    > **Note:** Always check your `.env` file to ensure it has the correct Supabase URL and keys.

## Testing

You can run tests to ensure everything is set up correctly.

```bash
cd backend
# Test database connection and migrations
./scripts/pre-start.sh
# Run unit tests
./scripts/test.sh
# Run tests that require a database connection
./scripts/tests-start.sh
```

## Docker

You can build and run the application using Docker.

1.  **Build the Docker image:**

    Remember to replace `your-docker-hub-username/flow2know` with your actual Docker image name.

    ```bash
    cd backend
    docker build -t your-docker-hub-username/flow2know .
    ```

2.  **Run tests using the Docker image:**

    This command runs the test suite within a Docker container.

    ```bash
    # Make sure Supabase is running
    supabase start

    # Run the tests
    cd backend
    docker run --network host \
      --env-file ../.env \
      -it your-docker-hub-username/flow2know:latest \
      bash -c "sh scripts/pre-start.sh && sh scripts/tests-start.sh"
    ```

## Contributing

Please read `CONTRIBUTING.md` for details on our code of conduct, and the process for submitting pull requests to us.

## License

This project is licensed under the MIT License - see the `LICENSE` file for details.
