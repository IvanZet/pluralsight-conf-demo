## Description
Coding along while doing Spring Framework 2: Creating Your First Spring Boot Application course by Dan Bunker on
Pluralsight.

This app demonstrates basic CRUD functionality against a database with conference sessions and related speakers. 

## Versions of this app
- `main` branch contains a version of the app which compiles into a `.jar` with Jetty container
  included 
- `release-2` branch compiles into a .war and requires an external Tomcat container

## Setup

### Connection Info:
- JDBC URL: `jdbc:postgresql://localhost:5432/conference_app`
- Username: `postgres`
- Password: `Welcome`

### Create database
Create Docker container with Postgres database:
```shell
docker create --name postgres-demo -e POSTGRES_PASSWORD=Welcome -p 5432:5432 postgres:11.5-alpine
```
Start container:
```shell
docker start postgres-demo
```
Run following scripts against the database:
```
postgresql/create_tables.sql
postgresql/insert_data.sql
```

### Connect the app to the database
Set the following environment variables:
```
DB_URL=jdbc:postgresql://localhost:5432/conference_app
DB_USERNAME=postgres
DB_PASSWORD=Welcome
```
In IntelliJ IDEA, environment variables can be set in menu: Run -> Edit configurations.

## Starting the app
In IntelliJ IDEA, one can navigate to
`src/main/java/com/prularsight/conferencedemo/ConferenceDemoApplication.java` and run `main()` function.

## Functionality and paths
- List all sessions: `http://localhost:5000/api/v1/sessions`
- Display a session with the supplied ID: `http://localhost:5000/api/v1/sessions/{ID}`
- Create a new session via a `POST` request to `http://localhost:5000/api/v1/sessions` with a JSON payload like:
```json
{
    "session_name": "test name",
    "session_description": "test description",
    "session_length": "45"
}
```
- Update existing session via a `PUT` request to `http://localhost:5000/api/v1/sessions/{ID}` with a JSON payload like:
```json
{
    "session_name": "updated name",
    "session_description": "updated description",
    "session_length": "30"
}
```
- Delete a session via a `DELETE` request to `http://localhost:5000/api/v1/sessions/{ID}`
- Similar functionality as above is available for speakers. In the path, instead of `sessions` use `speakers`. Example
  of JSON payload for creating a new speaker and updating existing one:
```json
{
    "first_name": "First name",
    "last_name": "Last name",
    "title": "Title",
    "company": "Company",
    "speaker_bio": "Info",
    "speaker_photo": null
}
```
