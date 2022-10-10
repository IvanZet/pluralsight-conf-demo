## Description
Coding along while doing Spring Framework 2: Creating Your First Spring Boot Application course by Dan Bunker on
Pluralsight.

This app demonstrates basic CRUD functionality against a database with conference sessions and related speakers. 

## Versions of this app
- `release-1` branch contains a version of the app which compiles into a `.jar` with Jetty container
  included. This version is deployed in the Heroku cloud. See links in Functionality and links section. 
- `release-2` branch compiles into a .war and requires an external Tomcat container

## Functionality and links
- [List](https://conference-demo-ivanzet.herokuapp.com/api/v1/sessions) all sessions
- [Display](https://conference-demo-ivanzet.herokuapp.com/api/v1/sessions/{ID}) a session with the supplied ID
- Create a new session via a `POST` request to the URL: `https://conference-demo-ivanzet.herokuapp.com/api/v1/sessions`
  with a JSON payload like:
```json
{
    "session_name": "test name",
    "session_description": "test description",
    "session_length": "45"
}
```
- Update existing session via a `PUT` request to the URL:
  `https://conference-demo-ivanzet.herokuapp.com/api/v1/sessions/{ID}` with a JSON payload like:
```json
{
    "session_name": "updated name",
    "session_description": "updated description",
    "session_length": "30"
}
```
- Delete a session via a `DELETE` request to the URL: `https://conference-demo-ivanzet.herokuapp.com/api/v1/sessions/{ID}`
- Similar functionality as above is available for speakers. In the URL, instead of `sessions` use `speakers`. Example
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
