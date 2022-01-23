# Demonstration of system testing issue

## Setup

1. You'll need Postgres running (see below for a way to do that)
   - Modify `.env.development` and `.env.test` for your postgres credentials
1. `bin/setup`
1. `bin/rails test test/system`
   - Everything should pass
1. `bin/rails test:system`
   - Should get failures when FactoryBot creates a factory that violates a unique index

### How to Setup Postgres

1. Install Docker
1. Create this `docker-compose.yml` file:

   ```yaml
   version: "3.7"
   services:
     db:
       image: postgres:13
       ports:
         - "5432:5432"
       environment:
         POSTGRES_PASSWORD: postgres
   ```
1. `docker-compose up`

Postgre is now available on localhost at port 5432
